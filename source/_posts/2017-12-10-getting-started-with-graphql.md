---
title: Getting Started With GraphQL
layout: post
comments: true
categories:
  - programming
tags:
  - api
  - graphql
  - rest
---
<div>
  What is GraphQL? The <a href="http://facebook.github.io/graphql/October2016/">draft RFC specification</a> (October 2016), defines it as &#8220;a query language created by Facebook in 2012 for describing the capabilities and requirements of data models for client‐server applications&#8221;. More simply, GraphQL is a language specification for API. It defines in which way the client should query the server, and in which way the server should execute those queries.
</div>

<!--more-->

<div>
  From the definition above, it is clear that GraphQL can be adopted as an alternative to REST. Let&#8217;s now analyze its features with an example in order to understand GraphQL base concepts.<br /> Think about your favourite website for booking hotel rooms, that is obviously <a href="https://www.hotels.com/">hotels.com</a>, and let&#8217;s try to design a GraphQL service that provides the reservation list for a specific user.
</div>

## Data model

<div>
  The first thing to do is defining the graph of the data provided by the service.
</div>

<div>
  The <strong>data model</strong> we are going to define follows this structure:
</div>

<div>
  <pre class="striped:false nums:false lang:default highlight:0 decode:true">+--------------------------------------+         +----------------------------+         +---------------------+
| QueryType                            |         | ReservationType            |         | HotelType           |
+--------------------------------------+         +----------------------------+         +---------------------+
|                                      |         |                            |         |                     |
| reservationList: [ReservationType!]! +-------&gt; | hotelId: ID!               |         | hotelName: String!  |
|                                      |         | checkIn: String!           |         | fullAddress: String |
+--------------------------------------+         | checkOut: String!          |         | starRating: Int!    |
                                                 | hotelDetails: HotelType!   +-------&gt; |                     |
                                                 | status: ReservationStatus! |         +---------------------+
                                                 |                            |
                                                 +----------------------------+</pre>

  <p>
    GraphQL models your data as a graph but it still needs entry points to that graph. Those entry points are the queries defined in the QueryType, that is the root of all the queries.<br /> In this example, it is defined only one query named &#8220;reservationList&#8221; that returns a list of &#8220;ReservationType&#8221;. In turn, ReservationType describes a hotel reservation and HotelType describe a hotel.
  </p>

  <h2>
    GraphQL Schema definition
  </h2>

  <p>
    Using the &#8220;<em>GraphQL schema language</em>&#8220;, explained in the <a href="http://graphql.org/learn/schema/">official GraphQL website</a>, our <strong>data model</strong> can be described in this way:
  </p>
</div>

<div>
  <pre class="lang:default highlight:0 decode:true">schema {
    query: QueryType
}
 
type QueryType {
  reservationsList(userId: ID!): [ReservationType!]!
}
 
type ReservationType {
  hotelId: ID!
  checkIn: String!
  checkOut: String!
  hotelDetails: HotelType!
  status: ReservationStatus!
}
 
type HotelType {
  hotelName: String!
  fullAddress: String
  starRating: Int!
}
 
enum ReservationStatus {
  UPCOMING
  COMPLETED
  CANCELLED
}</pre>

  <p>
    In very short, in this graphql<strong> schema definition</strong> we have:
  </p>
</div>

<div>
  <ul>
    <li>
      the keyword &#8220;schema&#8221;, that is the root of the schema;
    </li>
    <li>
      ID, String, and Int are built-in <a href="http://graphql.org/learn/schema/#scalar-types">Scalar Types</a>;
    </li>
    <li>
      ReservationStatus is an <a href="http://graphql.org/learn/schema/#enumeration-types">Enumeration Type</a>;
    </li>
    <li>
      the others are <a href="http://graphql.org/learn/schema/#object-types-and-fields">Object Types</a>.
    </li>
  </ul>
</div>

<div>
  This GraphQL schema can be parsed in order to be used for a real service. For instance, Apollo &#8220;<a href="https://github.com/apollographql/graphql-tools">graphql tools</a>&#8221; is a javascript utility for parsing such a schema.
</div>

## Query example

<div>
  This is an example of a query, valid for our schema:
</div>

<div>
  <pre class="lang:default highlight:0 decode:true">{
  reservationsList(userId: 12345) {
    hotelId
    checkIn
    checkOut
    hotelDetails {
      hotelName
      fullAddress
      starRating
    }
    status
  }
}</pre>

  <p>
    This query is sent from the client to the server in order to request the list of hotel ids in which the user number 12345 has made a reservation. Once the server receives this query, it is validated against the defined schema and then it is executed.
  </p>

  <h2>
    Response example
  </h2>

  <p>
    The generated response is JSON with the exact shape of the request:
  </p>
</div>

<div>
  <pre class="lang:default decode:true">{
  "data": {
    "reservationsList": [
      {
        "hotelId": "103",
        "checkIn": "2018-11-29",
        "checkOut": "2018-11-30",
        "hotelDetails": {
          "hotelName": "Hotel Campanile Metz Nord - Talange",
          "fullAddress": "Zone Actipole, Talange, Moselle, 57525, France",
          "starRating": 5
        },
        "status": "UPCOMING"
      }
    ]
  }
}</pre>
</div>

<div>
  Please note that the client asks only for the data it needs, and with only one query. This is an advantage of using GraphQL because, in general, it <span style="text-decoration: underline;">reduces the number of roundtrips</span> and <span style="text-decoration: underline;">minimizes the amount of data transferred on the network</span>.
</div>

## Query execution

<div>
  But what happened on the server when a query is executed?
</div>

<div>
  Every field has a function associated with it, and every time the server needs to produce that field then that function is executed. Those functions are named <strong>resolvers</strong>.
</div>

<div>
  In this specific example, it is defined a custom resolver for &#8220;reservationList&#8221; that provides a list of reservations and a custom resolver for &#8220;hotelDetails&#8221; that provides the necessary details for each hotel. For all the others fields, a built-in resolver is used to produce a scalar value.
</div>

<div>
  If you are interested in analyzing the entire source code for this example, with the complete resolvers definition, you can find a really nice <a href="https://github.com/fsferrara/from-rest-to-graphql-meetup">javascript implementation on github</a> :-).
</div>

<div>
</div>

<div>
  The execution aspect of a GraphQL server is described <a href="http://graphql.org/learn/execution/">here</a>. Once again, GraphQL is not an implementation: it only defines aspect for servers to execute queries. Even if GraphQL is not a ready-to-use library, there are already <a href="http://graphql.org/code/">several GraphQL implementations</a> such as graphql.js, graphql-ruby, graphql-java, and so on.
</div>

## Introspection

<div>
  A really cool feature of a GraphQL service is the <a href="http://graphql.org/learn/introspection/">ability to introspect</a> itself. Every GraphQL server has a special schema field at the query root named &#8220;__schema&#8221;:
</div>

<div>
  <pre class="lang:default decode:true">{
  __schema {
    ...
  }
}</pre>

  <p>
    Using that field, the service can expose the definition of every object and every field it can provide. This leads to really nice features like:
  </p>
</div>

  * <span style="text-decoration: underline;">Auto documentation</span>: the client knows the exact GraphQL schema.
  * <span style="text-decoration: underline;">Code generation</span>: the client can use a client generated from the schema.
  * <span style="text-decoration: underline;">Static validation</span>: the GraphQL client can validate the query before sending it to the server

<div>
  As a consequence, there are available very useful tools like <a href="https://github.com/graphql/graphiql">GraphiQL</a>, that is a kind of schema explorer for GraphQL. It is really useful to try and discover server features.
</div>

## HTTP Caching

<div>
  We get a lot of advantages using GraphQL, but there are also drawbacks. The one I faced is HTTP caching.
</div>

<div>
  A GraphQL endpoint can receive queries in different formats and it is really hard to define a caching policy server-side. Often the solution is to use a client-side cache. There are already libraries to implement normalized cache client-side, such as <a href="https://www.apollographql.com/">Apollo</a> and <a href="http://facebook.github.io/relay/">Relay</a>.
</div>

<div>
  Even if caching on the client is a good solution in most cases, I believe this situation can be improved in the future.
</div>

<div>
  For instance, a &#8220;smart&#8221; cache system can analyze a GraphQL request and understand which part of the query can take advantage of the cache.
</div>

## Conclusion

<div>
  Personally, I am quite happy in using GrapQL server-side and I tend to prefer it over REST. I think the most valuable advantage is the fact that clients already know how to query a GraphQL service and this makes integration straightforward.
</div>

<div>
  Anyway, this article covers only a few GraphQL features. There are more such as mutations, subscriptions, deferred queries, live queries, and batch operations. Please refer to the official <a href="http://graphql.org/">GraphQL website</a> for further information.
</div>

<div>
  A really useful resource is <a href="https://www.howtographql.com/">https://www.howtographql.com/</a> which contains free tutorials to learn all about GraphQL covering several GraphQL implementations.
</div>
