---
title: A GIT branching model for medium-size companies
layout: post
comments: true
categories:
  - programming
  - system administration
tags:
  - branching-model
  - collaboration
  - devops
  - git
  - teams
---
This article explains how a medium size company, which has several teams, can adopt GIT for the source code management. As a software configuration management, GIT serves two different functions. The first one is the management support for controlling changes to software products, and the second one is merely development support for coordinating file changes among product developers. In particular here I want to talk about the branching model.

<!--more-->



The following branching model is for a single product, whereas only the last product version is maintained (i.e. a web site or a mobile app). Additionally this branching model support an agile process model, where a new product version is released (hopefully) at the end of each team sprint.

This proposal is based on the &#8220;branch-by-purpose&#8221; model (@see [The Importance of Branching Models in SCM](http://svn.haxx.se/users/archive-2007-10/att-0101/SCMBranchingModels.pdf)), but it also provide a branch for the next release.

Main actors here are:

  * **Developers**, one or more developer teams
  * **Release manager**, or a release team
  * **System administrator**, or a sysadm team

This branching model is inspired by the work of [Vincent Driessen](http://nvie.com/about/).

## Branches organization

A good branching model for medium-size technology department should absolutely have these characteristics:

  * Parallel Development
  * Collaboration
  * Release Staging
  * Support for emergency fixes (hotfix)

The proposed branching model has three branches, each with an infinite life. System administrators will always use the &#8216;master&#8217; branch: everything is happy and deployable in master. Developers should always use the &#8216;develop&#8217; branch, and all teams share this branch to commit their features. Also developers can&#8217;t commit anything in the master branch, the release manager is in charge of this operation. The release manager has its own branch &#8216;candidate&#8217; in order to integrate in it the team&#8217;s patches, test these patches, promote versions, and then commit stable versions in the &#8216;master&#8217; branch. The original work [GitFlow](http://nvie.com/posts/a-successful-git-branching-model/) does not have the &#8216;candidate&#8217; branch, but uses a new branch for each release. I, instead, prefer to have the integration branch always with the same name: this can be useful in the future for the dependencies management.

## Creating the three branches

Once created the repository with the master branch, you can create &#8216;candidate&#8217; and &#8216;develop&#8217; branches.

<pre lang="bash">[~/git]$ git clone https://github.com/fsferrara/lemon.git
Cloning into 'lemon'...
remote: Counting objects: 12, done.
remote: Compressing objects: 100% (11/11), done.
remote: Total 12 (delta 2), reused 10 (delta 0)
Unpacking objects: 100% (12/12), done.
[~/git]$ cd lemon

[master][~/git/lemon]$ git branch -a
* master
  remotes/origin/HEAD -&gt; origin/master
  remotes/origin/master

[master][~/git/lemon]$ git branch candidate master
[master][~/git/lemon]$ git branch develop candidate

[master][~/git/lemon]$ git push origin candidate
Total 0 (delta 0), reused 0 (delta 0)
To https://github.com/fsferrara/lemon.git
 * [new branch]      candidate -&gt; candidate

[master][~/git/lemon]$ git push origin develop
Total 0 (delta 0), reused 0 (delta 0)
To https://github.com/fsferrara/lemon.git
 * [new branch]      develop -&gt; develop</pre>

Now we have these three branches:

<pre>
   develop        candidate        master
      +               +               +
      |               |               |
      |               |               |
      |               |               |
      |               |               |
      |               |               |
      |               |               |
      |               |               |
      |               |               |
      |               |               |
      |               |               |
      |               |               |
      |               |               |
      |               |               |
      |               |               |
      |               |               |
      |               |               |
      |               |               |
      |               |               |
      |               |               |
      |               |               |
      v               v               v
</pre>

## The features

Any new feature should be developed in a separate branch. So, a developer that is on &#8216;develop&#8217; branch&#8230;

<pre lang="bash">[master][~/git/lemon]$ git checkout develop
Switched to branch 'develop'
[develop][~/git/lemon]$ git branch -a
  candidate
* develop
  master
  remotes/origin/HEAD -&gt; origin/master
  remotes/origin/candidate
  remotes/origin/develop
  remotes/origin/master</pre>

&#8230;must start a feature branch, and share it with its team:

<pre lang="bash">[develop][~/git/lemon]$ git checkout -b myteam/amazing_feature
Switched to a new branch 'myteam/amazing_feature'

[myteam/amazing_feature][~/git/lemon]$ git push origin myteam/amazing_feature
Total 0 (delta 0), reused 0 (delta 0)
To https://github.com/fsferrara/lemon.git
 * [new branch]      myteam/amazing_feature -&gt; myteam/amazing_feature</pre>

Rebasing keeps our code working, merging easy, and history clean. Developer should maintain this branch always rebased with remote branches &#8216;origin/devel&#8217; and &#8216;origin/myteam/amazing_feature&#8217;, by doing these operations:

<pre lang="bash">[myteam/amazing_feature][~/git/lemon]$ git fetch origin
[develop][~/git/lemon]$ git rebase origin/develop
Current branch develop is up to date.
[develop][~/git/lemon]$ git rebase origin/myteam/amazing_feature
Current branch develop is up to date.</pre>

The branch &#8216;myteam/amazing_feature&#8217; contains all the feature commits. These commit should not be done directly on the &#8216;develop&#8217; branch because anything committed to this branch can be delivered on-line without any notice. Once the feature is done, the feature branch is reintegrated in the &#8216;develop&#8217; branch.

<pre>
   feature         develop
                      +
                      |
      +               |
      |               O
      | _____________/|
      |/              |
      O               |
      |               |
      O               |
      |               |
      O               |
      |\_____________ |
      |              \|
      |               O
      v               |
                      |
                      |
                      |
                      |
                      v
</pre>

At this point a &#8220;merge request&#8221; can be created also to manage the code review process. To finish a feature, perform these operations:

<pre lang="bash">[myteam/amazing_feature][~/git/lemon]$ git fetch
[myteam/amazing_feature][~/git/lemon]$ git rebase -i origin/develop
Successfully rebased and updated refs/heads/myteam/amazing_feature.

[master][~/git/lemon]$ git checkout develop
Switched to branch 'develop'

[develop][~/git/lemon]$ git fetch
[develop][~/git/lemon]$ git merge origin/develop
Already up-to-date.

[develop][~/git/lemon]$ git merge --no-ff myteam/amazing_feature
Merge made by the 'recursive' strategy.
 hello.js | 4 ++--
 1 file changed, 2 insertions(+), 2 deletions(-)

[develop][~/git/lemon]$ git push origin develop
Counting objects: 1, done.
Writing objects: 100% (1/1), 241 bytes, done.
Total 1 (delta 0), reused 0 (delta 0)
To https://github.com/fsferrara/lemon.git
   cd84dc7..ee499c9  develop -&gt; develop</pre>

The option &#8220;&#8211;no-ff&#8221; preserves feature history and easy full-feature reverts merge. Now we can delete the feature branch:

<pre lang="bash">[develop][~/git/lemon]$ git branch -d myteam/amazing_feature
Deleted branch myteam/amazing_feature (was a30b140).

[develop][~/git/lemon]$ git push --delete origin myteam/amazing_feature
To https://github.com/fsferrara/lemon.git
 - [deleted]         myteam/amazing_feature</pre>

## Integration phase and release

At any time the release engineer can merge the new content of &#8216;devel&#8217; and start an integration phase, as this picture show:

<pre>
   develop        candidate        master
      +               +               +
      |               |               |
      |               |               |
      O               |               |
      |\_____________ |               |
      |              \|               |
      |               O code chill    |
      |               |               |
      |               |               |
      |               O               |
      | _____________/| bugfixes      |
      |/              O               |
      O _____________/|               |
      |/              |               |
      O               O code freeze   |
      |               |\_____________ |
      |               |              \|
      |               |               O tag
      |               |               |
      |               |               |
      |               |               |
      v               v               v
</pre>

The integration starts with the _code chill_ phase, that is the phase in which only small bugfixes are allowed. Personally I hate these bugfixes, and I prefer to perform all kind of tests directly on &#8216;devel&#8217; branch: for me the integration phase should be only the final check. Once the code is ready to be deployed in production, we have the reintegration with &#8216;master&#8217;. At this point the release engineer can create the tag directly on master. Optionally the tag to be created can point before to the head of &#8216;candidate&#8217; branch and then can be updated to point to &#8216;master&#8217;.

## Deploying and emergency fixes

Everything is happy and up-to-date in master: the system administrator can use tags created by the release engineer to deploy a specific version of the product. This support the deploy of the latest version and also the roll-back to a previous version. Once reintegrated the branch &#8216;candidate&#8217; into &#8216;master&#8217;, a new tag is created following these steps:

<pre lang="bash">[master][~/git/lemon]$ git tag -a 1.2.3 -m "Promoted on `date`"
[master][~/git/lemon]$ git tag -l
1.2.3

[master][~/git/lemon]$ git push --tags
Counting objects: 1, done.
Writing objects: 100% (1/1), 182 bytes, done.
Total 1 (delta 0), reused 0 (delta 0)
To https://github.com/fsferrara/lemon.git
 * [new tag]         1.2.3 -&gt; 1.2.3

[master][~/git/lemon]$ git ls-remote --tags origin
83fd280e796bc4134c2e7b31106b9f8ed85ecf2c    refs/tags/1.2.3
cd84dc74b39607706e8f1b110411b4a508c6f3e8    refs/tags/1.2.3^{}</pre>

If for testing purpose you already created the tag 1.2.3 pointing the &#8216;candidate&#8217; branch, now you can move this tag by using the option &#8220;-f&#8221;.

Also the emergency bug fixes (hotfix) are supported by this model, as shown in this picture:

<pre>
   master          hotfix
      +
      |
      |               +
  tag O v1.2.3        |
      |\_____________ |
      |              \|
      |               O
      |               |
      |               O
      |               |
      |               O
      | _____________/|
      |/              |
  tag O v1.2.4        |
      |               |
      |               v
      |
      v
</pre>

## Useful configuration

Autosetup rebase so that pulls operations rebase by default

<pre lang="bash">git config --global branch.autosetuprebase always</pre>

## DOs and DON&#8217;Ts

No DO or DON&#8217;T is sacred. You&#8217;ll obviously run into exceptions, and develop your own way of doing things. However, these are guidelines I&#8217;ve found useful.

### DOs

  * _do_ master must always be deployable.
  * _do_ all changes are made through feature branches
  * _do_ use a &#8220;merge request&#8221; (aka &#8220;pull request&#8221;) to manage code-reviews
  * _do_ rebase to avoid/resolve conflicts before to merge
  * _do_ keep master in working order
  * _do_ rebase your feature branches often
  * _do_ tag releases
  * _do_ learn to rebase and merge

### DON&#8217;Ts

  * _don&#8217;t_ fork
  * _don&#8217;t_ merge broken code.
  * _don&#8217;t_ commit onto master directly.
  * _don&#8217;t_ hotfix onto master! use a specific hotfix branch.
  * _don&#8217;t_ rebase master.
  * _don&#8217;t_ merge with conflicts. Handle conflicts upon rebasing.
