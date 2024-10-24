# graphql

## Running the application
- npm install
- node server.js
If successfully started we can see this console message
Running a GraphQL API server at http://localhost:4000/graphql

browse to http://localhost:4000/graphql you can try out this API.

## Ways to access these APIs
- Curl
- Through javascript client code
- Through GraphiQL (pronounced as GRAPHICAL)

### Curl
curl -X POST \
-H "Content-Type: application/json" \
-d '{"query": "{ hello }"}' \
http://localhost:4000/graphql

### Through Javascript client code
```
var dice = 3
var sides = 6
var query = /* GraphQL */`query RollDice($dice: Int!, $sides: Int) {
  hello,
  rollDice(numDice: $dice, numSides: $sides),
  getDie(numSides: $sides) {
    rollOnce
    roll(numRolls: $dice)
  }
}`
fetch("/graphql", {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
    Accept: "application/json",
  },
  body: JSON.stringify({ 
    query,  
    variables: { dice, sides },
  }),
})
  .then(r => r.json())
  .then(data => console.log("data returned:", data))
```

### GraphiQL
If you navigate to http://localhost:4000, you should see an interface that lets you enter queries; now you can use the GraphiQL IDE tool to issue GraphQL queries directly in the browser.

If you navigate to http://localhost:4000, you should see an interface that lets you enter queries; now you can use the GraphiQL IDE tool to issue GraphQL queries directly in the browser.