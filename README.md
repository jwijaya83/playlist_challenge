Playlist Challenge
==========================

> Build a single page web application for creating playlists from a library of
> songs!

Included in this folder is a Node.js web server which includes an API and a
skeleton for your browser-based playlist application.

The API includes endpoints to complete the challenge. You don't need to change,
but you can if it helps.

feel free to get idea from spotify app and make your test prettier.(you can find the picture in the root directory).
feel free to use react or create-react-app to complete task or you can add react to this project.
feel free to use any css librarries but if you use custom css will have extra points.

To install and start the web server (Tested with node v12.13, npm v6.12):

```bash
npm install
npm start
```

Features
-----------------------------

Start by building out these features:

Frontend:
1. Load the library of songs and show it in the browser. 
2. Add songs from the library to a playlist. 
3. Name and save a playlist.
4. List saved playlists. 
5. Load saved playlists.
6. Search/filtering for songs.
7. Search for a particular entry/song criteria (ie: music length, by artist, by genre, etc) from the backend GraphQL API.

Backend:
1. Change the simple express REST API with GraphQL API.
2. Design and implement GraphQL query and resolver. Think of it as you are loading the data from database instead of hardcoded JS Object.
3. Design and implement GraphQL mutation query.


You do **not** have to do any of the following:

1. Deal with authentication. 🔐
2. Work across browsers. Pick your favourite and get it working there. 🏄

*We reserve the right to ask you about how to implement them later 😀*


API
-------------------------------

Everything from `/public/` is served at http://localhost:5000/.

The Simple REST API provides the following methods:


`GET /library/`
---------------

Returns a JSON array of songs.

Request:

```bash
curl http://localhost:5000/library/
```

Response:

```json
[
    {
        "id": 0,
        "artist": "The Black Keys",
        "album": "Brothers",
        "title": "Everlasting Light",
        "length": 203,
        "track": 1
    },
    {
        "id": 1,
        "artist": "The Black Keys",
        "album": "Brothers",
        "title": "Next Girl",
        "length": 198,
        "track": 2
    },
    ...
]
```

`GET /library/:id/`
---------------------

Returns a JSON object for a song with given `id`.

Request:

```bash
curl http://localhost:5000/library/200/
```

Response:

```json
{
  "album": "Nothing But The Beat",
  "duration": 196,
  "title": "Sweat (Snoop Dogg vs. David Guetta) [Remix]",
  "id": 200,
  "artist": "David Guetta"
}
```

`GET /playlist/`
---------------------

Returns a JSON array of playlists.

Request:

```bash
curl http://localhost:5000/playlist/
```

Response:

```json
[
  {
    "id": 0,
    "name": "Ryan's Megamix",
    "songs": [
      20,
      21,
      56,
      80,
      99
    ]
  },
  {
    "id": 1,
    "name": "Ryan's Megamix 2",
    "songs": [
      20,
      21,
      56,
      80,
      99
    ]
  },
  ...
]
```

`GET /playlist/:id/`
---------------------

Returns a JSON object with the playlist with given `id`.

Request:

```bash
curl http://localhost:5000/playlist/0/
```

Response:

```json
{
    "id": 0,
    "name": "Ryan's Megamix",
    "songs": [
        20,
        21,
        56,
        80,
        99
    ]
}
```

`POST /playlist/` or `POST /playlist/:id/`
-------------------------------------------

Saves a playlist and returns the id. May create a new playlist or override an
old one.

Request:

```bash
curl http://localhost:5000/playlist/ -X POST -d '{ "name": "Hi", "songs": [1,2,3,4]}' -H "Content-Type: application/json"
```


Response:

```json
{
    "id": 100
}
```


`DELETE /playlist/:id`
-------------------------

Deletes a playlist.

Request:

```bash
curl http://localhost:5000/playlist/10/ -X DELETE
```

Response:

```json
{}
```
