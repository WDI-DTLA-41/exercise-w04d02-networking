# HTTP Battleship

![:image](https://upload.wikimedia.org/wikipedia/commons/c/ca/Chilean_battleship_Almirante_Latorre.jpg)

## Client Requests

Requests
- Get Requests must end in two empty lines
- Post requests must contain an empty line followed by the body data
- Post request's data must be key value pairs separated by equal signs and the pairs separated by ampersands.

Clients should use the following info to construct requests.

| Command | Method | Path             | Parameters
| :--     | :--    | :--              | :--       
| Radar   | GET    | /board           | row, col  
| Missle  | POST   | /board           | row, col  

> GET Request parameters should be written as a query string

```
GET /board?row=3&col=4


```

> POST Request parameters should be included in the body

```
POST /board

row=3&col=4
```

## Server Responses

Responses
- Must include a status code
- Must include a blank line
- Must include a body message

The Server can respond in the following ways

> GET requests to the path "/board"

> POST requests to the path "/board". Posts should contain data in the request's body

## Response Code
| Action       | Status Code | Body
| :--          | :--         | :--
| GET          | 404         | No ship found       
| GET          | 200         | OK!
| POST         | 201         | HIT!

# La Règle du jeu

Radar.
- If a client's GET request finds a ship, the server must return 200
- If a client's GET request misses a ship, the server must return 404

```
GET /board?row=2&col=3

```

Attacks.
- A Client cannot POST without first performing a GET request
- If a client's POST request strikes a ship, the server must return a 201
- A client's POST request must contain parameters in the body of the request
- After a 404 or 201 the turn is over.

```
POST /board

row=2&col=3
```

## You've sunk my battleship!
- If the battleship is sunk the server must respond with 500 internal server error
and the game ends.


