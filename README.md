# Node API 2 Guided Project Starter Code

Guided project starter code for **Node API 2** module.

In this project we will learn how to create a very simple Web API using `Node.js` and `Express`, and cover how to use `Express Routers` to break up the application to make it more maintainable.

## Prerequisites

- a REST client like [insomnia](https://insomnia.rest/download/) or [Postman](https://www.getpostman.com/downloads/) installed.

## Project Setup

- [ ] fork and clone this repository.
- [ ] **CD into the folder** where you cloned **your fork**.
- [ ] type `npm i` to download dependencies.

Please follow along as the instructor builds the API step by step.


# Node API 2 Guided Project Starter Code

Guided project starter code for **Node API 2** module.

In this project we will learn how to create a very simple Web API using `Node.js` and `Express`, and cover how to use `Express Routers` to break up the application to make it more maintainable.

## Prerequisites

- a REST client like [insomnia](https://insomnia.rest/download/) or [Postman](https://www.getpostman.com/downloads/) installed.

## Project Setup

- [ ] fork and clone this repository.
- [ ] **CD into the folder** where you cloned **your fork**.
- [ ] type `npm i` to download dependencies.

Please follow along as the instructor builds the API step by step.

REST GUIDELINES RECOMMENDATIONS:

| RESOURCES | HTTP METHOD| HYPERMEDIA |
|:----------| :----------|:--------   |
|  NOUNS    |  ACTIONS   |  LINKS     |
| CLIENTS   |  CRUD      |  METADATA  |
|  USERS    |  GET       |  PAGINATION|<----- /// How do i get to the next page or previouse page//
|  PROFILES |  POST      |  PREV      |
|  TICKETS  | PUT/DELETE |  NEXT/CATCH|



|  Action        |   Non RESTful way  |  RESTful Design   |
|:----------     | :---------------   |  :-------------   |
|Add a client    |   /newClient       |  POST /clients    |<----- CREATE A LIST 
|List all clients|  /clientList       |  GET /clients     |<-----  GET a list of clients or users


iS REST A STANDARD:
 No not a standards it is a list of guidelines

 REST APIs have six constraints:
 1) client-server architecture 
 2) Stateless architecture each request should not matter. No shared state.
 3) CACHABLE: improves nerwork performance
      a) GET, PUT and DELETE should be idempotent(the same command executed several times, the state if the resoures on the server is exactly the same, much like pure functions)
      b) POST is NOT idempotent
      c) Caching is a way to store and retrieve data that so future request can be fulfilled faster without repeating expensive calculatins or operations.
4) LAYERED SYSTEM: component A(a client) might or might not communicate directly with component B(the server). There may be other layers between them like logging, caching, DNS srevers, load balancers, and authentication.

5) CODE ON DEMAND:
    a) the API returns the resource and code to act on it.
    b) The client only needs to know how to execute the code.
    c) Makes the API more flexable, upgradable and extendable.
    d) Most web applications, send JavaScript code along with the data.

6)  UNIFORM INTERFACE:
    a) Each resource should be accessible through the URL , Not a hard requirement, but RECOMMENDED!!!
    b) We should be able to manage through these representations(the URL)
    c) every interaction with the resorce should happen through the URL identifier we gave to it!!!
    d) Self-descriptive messages
    e) HATEOAS ((H)ypermedia (A)s (T)he (E)ngine (O)f (A)pplication (S)tate). Much like a (CHOOSE YOUR ADVENTURE BOOK) the pages are not read in order, 
       You start at page 1 and based on the information available the reader(CLIENT) chooses the action to take moving them to a diffrent page. A good example of a hypermedia AOI id the GITHUB API.


EXAMPLE OF A SERVER FRAMEWORKS  
-------------------------------
http://localhost:8000

|  /api    |<---this is the folder that the api is found and built on ---->
| :--------|
|  /admin  |<--- This the file within the API folder when refrencing in your POST----->
| :--------|
|/employess|<---These are the  resources --->
| /vehicles|
| /roles   |


-------------------------------
ORGANIZING API FILES
____________________

- by type
  - /routes/routers 
    - clientsRouter.js
    - profilesRouter.js
  
  - /models
    - clientsModel.js
    - profileModel.js  
    
  - /tests
    - clients.test.js
    - profiles.test.js 


    OR


by feature/resource  
- /clients
    - client.router.js 
    - client.model.js 
    - client.test.js 

  - /vehicals


  - /profiles



###   Query string
https://www.google.com
/search

? --> marks the begining  of the query string 
------------
q=mdn+query+string
&
rlz=1C2FHFK_enUS968US968&sxsrf=AOaemvIMaM4DEAqMI-e1j4iAKwEbpVkcRw%3A1638037013601

source=hp ----> Key value pairs
& ---> seprerates key/value pairs


ei=FXaiYaaDIqrG0PEPloe_2Ag

&

iflsig=ALs-wAMAAAAAYaKEJf3puXOVMMBRkV4HfRl3g3WtwH7u&oq=
&

```js
req.query = {
  source: hp,
  ei: "FXaiYaaDIqrG0PEPloe_2Ag",
  q: "mdn+query+string",
};
```

  --------------------------------------------------------------

  - When you need to look up query strings go to MDN query strings for refrence 



  ### SUB ROUTES


  Chat

-org
  -channels
    -messages
     -reactions ---> emojis

 - /orgs CRUD
 - /channels { orgid: 1, ...channelData}, POST, GET /orgs/23/channels; DELETE /channels/23
 - /messages  
 - /reactions ---->>>>> sub route candidate, it does not make sense outside of a message.
 - /emojis  