---
title: GIT explained for Subversion users
layout: post
comments: true
categories:
  - programming
  - system administration
tags:
  - git
  - subversion
  - svn
  - versioning
---
`This guide shows the most common procedures usually performed by SVN users, but using GIT.<br />
Why this guide should be better than the others already on-line? There isn't a particular reason ;) . I'm now a SVN user and I'm just migrating to GIT, so I'm going to find a way to perform with GIT all the operations that I usually do with Subversion: this will be useful for Subversion users who want to start using GIT quickly.`

<!--more-->

Git is a distributed revision control (DVCS) and source code management (SCM) system with an emphasis on speed. As a distributed VCS, every Git working directory is a full-fledged repository with complete history and full version tracking capabilities, not dependent on network access or a central server.

This is the most substantial difference with SVN where there is a central repository. With subversion, the developers working in a team used continuously exchange their code. This is deeply different with GIT because there is no a main central repository; so developer should use a given remote repository, and use it as the central one.

No more talk, I don&#8217;t like to talk: let&#8217;s start with GIT by examples.

We have two developers, obviously their user-names are Alice and Bob.

## GIT &#8211; Create a repository

Alice wants to create a new project named &#8220;lemon&#8221;. She simply creates an empty directory and then launch the command &#8216;git init&#8217;:

<pre lang="bash">[~/alice]$ mkdir lemon
[~/alice]$ cd lemon
[~/alice/lemon]$ git init
Initialized empty Git repository in /Users/fferrara/alice/lemon/.git/
[master][~/alice/lemon]$
</pre>

That&#8217;s all! Alice has now a brand new repository locally (note that this is more than a working copy). The main branch is called &#8220;master&#8221;. The shell prompt has the capability to detect and print the name of the current branch (this is the zsh shell default behaviour).

## GIT &#8211; Your first commit

Let&#8217;s prepare our first file commit. Lemon has one simple file &#8216;hello.js&#8217; containing the source code.

<pre lang="javascript">var prompt = require('prompt');

prompt.start();

prompt.get(['fruit'], function(err, result) {

    if (result) {
        console.log('Hey fruit ' + result.fruit);
        if ('lemon' == result.fruit) {
            console.log('I like yellow things :) ');
        };
    }
});</pre>

Also we have a package.json configuration file.

<pre lang="javascript">{
  "dependencies": {
    "prompt": "0.2.11"
  }
}
</pre>

As many of you know, in this type of application, we have to ignore the node_modules directory. So we have to create the .gitignore file containing the ignore-list.

<pre lang="bash">*[master][~/alice/lemon]$ echo "node_modules" &gt; .gitignore
</pre>

To see the status of our branch, you should use the command &#8216;git status&#8217;

<pre lang="bash">*[master][~/alice/lemon]$ git status
# On branch master
#
# Initial commit
#
# Untracked files:
#   (use "git add ..." to include in what will be committed)
#
#   .gitignore
#   hello.js
#   package.json
nothing added to commit but untracked files present (use "git add" to track)
</pre>

The file for now are all in the &#8216;untracked&#8217; status, that is the first state. To track these files we have to add them to the repository index.

<pre lang="bash">*[master][~/alice/lemon]$ git add .gitignore package.json hello.js
</pre>

Check the status again

<pre lang="bash">*[master][~/alice/lemon]$ git status
# On branch master
#
# Initial commit
#
# Changes to be committed:
#   (use "git rm --cached ..." to unstage)
#
#   new file:   .gitignore
#   new file:   hello.js
#   new file:   package.json
#
</pre>

The added files are now ready to be committed (aka tracked-file). The commit command resembles that of SVN.

<pre lang="bash">*[master][~/alice/lemon]$ git commit -m "my first git commit"
[master (root-commit) 7046414] my first git commit
 3 files changed, 19 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 hello.js
 create mode 100644 package.json
</pre>

Note that the number &#8216;7046414&#8217; is equivalent of the SVN revision number. Actually it is a commit hash and in this context is truncated to the first 7 characters. To see the entire commit identified we can print the commit log.

Use the &#8216;git log&#8217; command to see this:

<pre lang="bash">commit 7046414d2c9d3407f421987449c92877718248f9
Author: alice
Date:   Fri Nov 1 16:44:31 2013 +0100
     my first git commit
(END)
</pre>

## GIT &#8211; Share your commit with the team

What about the remote repository? Actually GIT doesn&#8217;t need a main remote repository, but can track several distributed repositories.

For this example I&#8217;m borrowing to Alice this remote https://github.com/fsferrara/lemon.git repository. She should set this uri in her local repository, and then verify with the command &#8216;git remote -v&#8217;.

<pre lang="bash">[master][~/alice/lemon]$ git remote -v
[master][~/alice/lemon]$ git remote add origin https://github.com/fsferrara/lemon.git
[master][~/alice/lemon]$ git remote -v
origin  https://github.com/fsferrara/lemon.git (fetch)
origin  https://github.com/fsferrara/lemon.git (push)
</pre>

Nice&#8230; a remote (by default called &#8216;origin&#8217;) to share our branch!

Yes, you&#8217;ve got it right. With GIT we always share branches. Alice now have to push her master branch to the origin repository.

<pre lang="bash">[master][~/alice/lemon]$ git push -u origin master
Counting objects: 5, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (4/4), done.
Writing objects: 100% (5/5), 514 bytes, done.
Total 5 (delta 0), reused 0 (delta 0)
To https://github.com/fsferrara/lemon.git
 * [new branch]      master -&gt; master
Branch master set up to track remote branch master from origin.
</pre>

In a team, were developer used to often share their code with SVN, this operation should be performed after every commit.

Only the first time we share a branch we should use the -u flag, in order to set the upstream. In a nutshell an upstream is a tracking reference, in order to set Alice&#8217;s master branch to track the remote master branch (we can refer to it as origin/master or remotes/origin/master).

The &#8216;git branch -a&#8217; command prints out the entire lists of branches.

<pre lang="bash">[master][~/alice/lemon]$ git branch -a
* master
  remotes/origin/master
</pre>

## GIT &#8211; Create a branch

Now Alice want to write down a killer feature&#8230; maybe it can be a custom message not only for lemons, but also for all kinds of citrus fruit. The first thing to do is to create a branch&#8230;

<pre lang="bash">[master][~/alice/lemon]$ git branch citrus
[master][~/alice/lemon]$ git branch -a
  citrus
* master
  remotes/origin/master
</pre>

The branch citrus is created only locally. That means that the origin (aka remote repository) doesn&#8217;t have this branch. Alice can share this branch with others by pushing it to origin.

<pre lang="bash">[master][~/alice/lemon]$ git push -u origin citrus
Total 0 (delta 0), reused 0 (delta 0)
To https://github.com/fsferrara/lemon.git
 * [new branch]      citrus -&gt; citrus
Branch citrus set up to track remote branch citrus from origin.
[master][~/alice/lemon]$ git branch -a
  citrus
* master
  remotes/origin/citrus
  remotes/origin/master
</pre>

## GIT &#8211; Switch to a branch

But Alice can&#8217;t start working because is still using the master branch. The &#8216;git checkout&#8217; command is launched to change the current branch.

Yes poor SVN users&#8230; with GIT the checkout command doesn&#8217;t means &#8216;create a brand new working copy&#8217;, but has now a new meaning: now checkout is used to switch branch or revert a modified file or directory.

Let&#8217;s start by simply change the current branch:

<pre lang="bash">[master][~/alice/lemon]$ git checkout citrus
Switched to branch 'citrus'
[citrus][~/alice/lemon]$ git branch -a
* citrus
  master
  remotes/origin/citrus
  remotes/origin/master
</pre>

## GIT &#8211; Clone an existing repository

Bob, a team mate of Alice, awakens, and start working at the project lemon. The first thing is to clone an existing repository by using the given uri.

<pre lang="bash">[~/bob]$ git clone https://github.com/fsferrara/lemon.git lemon
Cloning into 'lemon'...
remote: Counting objects: 5, done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 5 (delta 0), reused 5 (delta 0)
Unpacking objects: 100% (5/5), done.
[~/bob]$ cd lemon
[master][~/bob/lemon]$ git branch -a
* master
  remotes/origin/HEAD -&gt; origin/master
  remotes/origin/citrus
  remotes/origin/master
</pre>

## GIT &#8211; Share a commit on an existing file

Ops&#8230; there is a minor bug! The &#8216;hello&#8217; string doesn&#8217;t contains the point. Bob choose to treat it as a hot bugfix, and to commit this change directly on the master branch.

He first edit the hello.js file, and then:

<pre lang="bash">*[master][~/bob/lemon]$ git status
# On branch master
# Changes not staged for commit:
#   (use "git add ..." to update what will be committed)
#   (use "git checkout -- ..." to discard changes in working directory)
#
#   modified:   hello.js
#
no changes added to commit (use "git add" and/or "git commit -a")
*[master][~/bob/lemon]$ git add hello.js
*[master][~/bob/lemon]$ git commit -m "hot bugfix"
[master c6538cc] hot bugfix
 1 file changed, 1 insertion(+), 1 deletion(-)
[master][~/bob/lemon]$ git push origin master
Counting objects: 5, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 346 bytes, done.
Total 3 (delta 1), reused 0 (delta 0)
To https://github.com/fsferrara/lemon.git
   7046414..c6538cc  master -&gt; master
[master][~/bob/lemon]$
</pre>

## GIT &#8211; Create a tag

Bob want to freeze the current master version to a given tag. We&#8217;re familiar with tags since we currently are SVN users :) but in the GIT case there isn&#8217;t a folder that contains all the tag. Tags are treated like commits, and refers to a snapshot of the source code.

The &#8216;git tag&#8217; command is used here. After the tag is created, there is need to push it in order to share it with the team.

<pre lang="bash">[master][~/bob/lemon]$ git tag -l
[master][~/bob/lemon]$ git tag -a v0.1.0 -m "Released on `date`"
[master][~/bob/lemon]$ git tag -l
v0.1.0
[master][~/bob/lemon]$ git push --tags origin master
Counting objects: 1, done.
Writing objects: 100% (1/1), 184 bytes, done.
Total 1 (delta 0), reused 0 (delta 0)
To https://github.com/fsferrara/lemon.git
 * [new tag]         v0.1.0 -&gt; v0.1.0
</pre>

## GIT &#8211; Check if a branch is rebased

Alice is working on branch &#8216;citrus&#8217; and in the meanwhile Bob committed a fix on the master branch. How Alice can check if the branch she is currently working on has to be rebased? The first thing to do is to &#8216;fetch&#8217; updates from origin.

<pre lang="bash">[citrus][~/alice/lemon]$ git fetch
remote: Counting objects: 6, done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 4 (delta 1), reused 4 (delta 1)
Unpacking objects: 100% (4/4), done.
From https://github.com/fsferrara/lemon
   7046414..c6538cc  master     -&gt; origin/master
 * [new tag]         v0.1.0     -&gt; v0.1.0
</pre>

Now Alice&#8217;s repository has information about Bob&#8217;s commits and tags. In order to know if the current branch is rebased with master Alice can use the &#8216;git cherry&#8217; command. Another option are the more powerful commands:

gitk citrus..origin/master

git log citrus..origin/master

The range notation &#8220;citrus..master&#8221; means &#8220;show everything that is included in master but is not included in citrus&#8221;.

<pre lang="bash">[citrus][~/alice/lemon]$ git cherry citrus origin/master
+ c6538cc3b3fed65bd5c9cfe708961f1f5f2e1616</pre>

## GIT &#8211; Rebase a branch with master

Expected surprise! There is a commit (c6538cc3b3fed65bd5c9cfe708961f1f5f2e1616) not included in the current branch. Now is very important to note all the branches present in Alice&#8217;s repository:

<pre lang="bash">[citrus][~/alice/lemon]$ git branch -a
* citrus
  master
  remotes/origin/citrus
  remotes/origin/master
</pre>

There are two local branches (citrus and master), and two remote tracked branches (origin/citrus and origin/master). At the moment origin/master is updated, but master isn&#8217;t updated yet. That&#8217;s because &#8216;git fetch&#8217; only download new information but doesn&#8217;t perform any merge operation.

The choice is to work with remote branches, or update local branches and work with locals. Alice choose to work with the remote ones.

<pre lang="bash">[citrus][~/alice/lemon]$ git rebase origin/master citrus
First, rewinding head to replay your work on top of it...
Fast-forwarded citrus to origin/master.
[citrus][~/alice/lemon]$ git status
# On branch citrus
# Your branch is ahead of 'origin/citrus' by 1 commit.
#
nothing to commit (working directory clean)
[citrus][~/alice/lemon]$ git push origin citrus
Total 0 (delta 0), reused 0 (delta 0)
To https://github.com/fsferrara/lemon.git
   7046414..c6538cc  citrus -&gt; citrus
[citrus][~/alice/lemon]$ git status
# On branch citrus
nothing to commit (working directory clean)
</pre>

Examining the log (with git log or gitk) we can see that now citrus and origin/citrus branches have exactly the commit c6538cc3b3fed65bd5c9cfe708961f1f5f2e1616 in their log. That means that this commit is now in common with the master branch.

## GIT &#8211; Reintegrate a branch

Alice worked hard on her branch, and a the end commits the killer feature.

<pre lang="bash">[citrus][~/alice/lemon]$ vim hello.js
*[citrus][~/alice/lemon]$ git add hello.js
*[citrus][~/alice/lemon]$ git commit -m "Add the killer feature"
[citrus b306b5c] Add the killer feature
 1 file changed, 3 insertions(+)
[citrus][~/alice/lemon]$ git push origin citrus
Counting objects: 5, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 447 bytes, done.
Total 3 (delta 1), reused 0 (delta 0)
To https://github.com/fsferrara/lemon.git
   c6538cc..b306b5c  citrus -&gt; citrus
</pre>

Ops&#8230; she forgot something :( . Another commit is necessary:

<pre lang="bash">[citrus][~/alice/lemon]$ vim hello.js
*[citrus][~/alice/lemon]$ git add hello.js
*[citrus][~/alice/lemon]$ git commit -m "This actually add the killer feature"
[citrus ae073c3] This actually add the killer feature
 1 file changed, 3 insertions(+)
[citrus][~/alice/lemon]$ git push origin citrus
Counting objects: 5, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 370 bytes, done.
Total 3 (delta 1), reused 0 (delta 0)
To https://github.com/fsferrara/lemon.git
   b306b5c..ae073c3  citrus -&gt; citrus
</pre>

Bob wants now to integrate Alice&#8217;s commits in the master branch. So the first thing to do is to fetch the updates.

<pre lang="bash">[master][~/bob/lemon]$ git fetch
remote: Counting objects: 8, done.
remote: Compressing objects: 100% (5/5), done.
remote: Total 6 (delta 2), reused 5 (delta 1)
Unpacking objects: 100% (6/6), done.
From https://github.com/fsferrara/lemon
   7046414..ae073c3  citrus     -&gt; origin/citrus
</pre>

Now Bob has to merge all the Alice&#8217;s commit in the master branch. The following command &#8216;squash&#8217; these commits into one commit, and add the change-set to the GIT index:

<pre lang="bash">[master][~/bob/lemon]$ git merge --squash origin/citrus
Updating c6538cc..ae073c3
Fast-forward
Squash commit -- not updating HEAD
 hello.js | 6 ++++++
 1 file changed, 6 insertions(+)
</pre>

The working branch of Bob now has all the changes introduced by Alice. To see the difference Bob should use the command &#8216;git diff &#8211;staged&#8217;.

Finally to reintegrate the branch:

<pre lang="bash">*[master][~/bob/lemon]$ git commit -m "Reintegrate branch citrus into master"
[master cd84dc7] Reintegrate branch citrus into master
 1 file changed, 6 insertions(+)
[master][~/bob/lemon]$ git push origin master
Counting objects: 5, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 538 bytes, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/fsferrara/lemon.git
   c6538cc..cd84dc7  master -&gt; master
</pre>

## GIT &#8211; Delete a branch

At the end Bob can delete the branch he previously integrated on master. The &#8216;git branch -d&#8217; command is used.

<pre lang="bash">[master][~/bob/lemon]$ git branch -d citrus
warning: deleting branch 'citrus' that has been merged to
 'refs/remotes/origin/citrus', but not yet merged to HEAD.
Deleted branch citrus (was ae073c3).
[master][~/bob/lemon]$ git push --delete origin citrus
To https://github.com/fsferrara/lemon.git
 - [deleted]         citrus
</pre>

Note that the command &#8216;git branch -d&#8217; ensures that the changes in the citrus branch are already in the current branch. If not, you should use the option -D instead.

## What&#8217;s next&#8230;

Time is over :/ . Next operation I usually perform with SVN are:

  * GIT &#8211; Return to a revision
  * GIT &#8211; Return to a tag
  * GIT &#8211; Reverse merge
  * GIT &#8211; Undo a wrong commit (or a list&#8230; remeber the order)
  * GIT &#8211; Create a diff-file and perform a patch
  * GIT &#8211; Stash
  * GIT &#8211; Export

Asap I&#8217;ll write about these operation. In the meanwhile I suggest you these manual page: &#8216;man gittutorial&#8217; and the very interesting &#8216;man gittutorial-2&#8217;

Goodbye and happy versioning :)
