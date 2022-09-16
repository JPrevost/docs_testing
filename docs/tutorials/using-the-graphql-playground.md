---
layout: home
title: Using the GraphQL Playground
parent: Tutorials
nav_order: 1
---

# Using the TIMDEX GraphQL Playground

## What is the Playground?

The Playground is a live web based tool that allows you to ender queries and view results.

The Playground includes autocomplete for query fields and validation for your queries. It is a great place to try out queries before you move into writing your own scripts or applications as you can copy/paste the queries into your preferred language once you know they work as expected.

The playground also includes the entire Schema and Documentation on the available queries and fields.

## Is this thing on?

Let's start out with a `ping` query to confirm how to access and write queries in the playground before we continue with more interesting queries.

### Step-by-step ping

- access the [TIMDEX GraphQL Playground](https://timdex.mit.edu/playground) in your preferred browser
- copy and paste this query (including the curly braces) into the left hand side

  ```graphql
  {
    ping
  }
  ```

- click the "play" button in the middle
- observe the results on the right

If you don't the following start these steps over and ensure you are copying/pasting the entire query.

```graphql
{
  "data": {
    "ping": "Pong!"
  }
}
```

Congratulations! You've just made a GraqphQL query in our TIMDEX API!

## Searching by keyword

Searching, also known as querying, is an essential part of using TIMDEX API. At the core of searching is helping the system understand what you are looking for so it can return the best results possible.

A good starting point, is a keyword search, by which we mean providing a simple unstructured string (i.e. text), and letting the system do it's best to get the most relevant records for you.

### Step-by-step searching by keyword

- access the [TIMDEX GraphQL Playground](https://timdex.mit.edu/playground) in your preferred browser
- copy and paste this query (including the curly braces) into the left hand side

  ```graphql
  {
    search(searchterm: "computer science") {
      hits
      records {
      timdexRecordId
        title
        summary
        links {
          url
          kind
        }
      }
    }
  }
  ```

  TIP: you can [jump start that query in the playground](../playground?query=%7B%0A%20%20search(searchterm%3A%20%22computer%20science%22)%20%7B%0A%20%20%20%20hits%0A%20%20%20%20records%20%7B%0A%20%20%20%20%20%20timdexRecordId%0A%20%20%20%20%20%20title%0A%20%20%20%20%20%20summary%0A%20%20%20%20%20%20links%20%7B%0A%20%20%20%20%20%20%20%20url%0A%20%20%20%20%20%20%20%20kind%0A%20%20%20%20%20%20%7D%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D)
- click the "play" button in the middle
- observe the results on the right

**Note:** GraphQL requires we ask for specific fields back. This tutorial doesn't cover all of the avaialble fields, but guides and reference documentation are avaialble for that. Additionally, the GraphQL playground will autocomplete valid fields and highlight any problems in your syntax. Don't be afraid to play around... it's a playground afterall!

If you are not getting useful results, and you are fairly certain the information you are looking for is indeed in TIMDEX, it may require doing more advanced searching including narrowing your search to specific fields, sources, or using aggregations to filter your result set. Those topics are outside the scope of this tutorial, but guides are available on each of those topics.

### Explore keyword searches on your own

To gain a better understanding:

- change the value of the searchterm in the example query to `buzz aldrin`
- try removing the `summary` field from the example above
- try adding the `citation` field to the example above

## Query Variables

The GraphQL Playground allows you to use variables instead of hard coding a specific value in a query. This is helpful if you intend to re-use the query later on in a script or application.

Let's change our keyword query query example above to not only work for "computer science" searches.

### Step-by-step searching by keyword using variables

- access the [TIMDEX GraphQL Playground](https://timdex.mit.edu/playground) in your preferred browser
- If the query from the above `Searching by keyword` section is no longer there, please copy it into the Playground and confirm it still works.
- Update the query from the previous example to use a variable for the searchterm like this

    ```graphql
    query ($searchterm: String) {
      search(searchterm: $searchterm) {
        hits
        records {
          timdexRecordId
          title
          summary
          links {
            url
            kind
          }
        }
      }
    }
    ```

- Now to set a value for that new variable, lick on "Variables" on the bottom of the window and add the variable by pasting

  ```json
  {
    "searchterm": "variable naming"
  }
  ```

- TIP: If you prefer, you can jump start the playground [with the example above](http://localhost:4000/playground?query=query%20(%24searchterm%3A%20String)%20%7B%0A%20%20search(searchterm%3A%20%24searchterm)%20%7B%0A%20%20%20%20hits%0A%20%20%20%20records%20%7B%0A%20%20%20%20%20%20timdexRecordId%0A%20%20%20%20%20%20title%0A%20%20%20%20%20%20summary%0A%20%20%20%20%20%20links%20%7B%0A%20%20%20%20%20%20%20%20url%0A%20%20%20%20%20%20%20%20kind%0A%20%20%20%20%20%20%7D%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D&variables=%7B%0A%20%20%22searchterm%22%3A%20%22variable%20naming%22%0A%7D)

### Explore variables on your own

To gain a better understanding:

- change the value of the `$searchterm` variable to something else

## coming soon bits

Include:

- searching (link to example docs in addition to walking through some interesting examples here in the tutorial)
- auto-complete for fields
- `Docs`
- `Schema`
- query variables
- history
- copy curl
- tool that powers it
