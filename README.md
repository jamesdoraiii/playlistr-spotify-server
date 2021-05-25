# Playlistr Spotify Server

This repository is the code to run an authorization/authentication server to connect to the Spotify API. The server is to be used in conjunction with the client app of playlister found [here](https://github.com/jamesdoraiii/playlistr-client). While building my application Playlistr, I needed a server that could handle Spotify's [authorization](https://developer.spotify.com/documentation/general/guides/authorization-guide/) and [web API]("https://developer.spotify.com/documentation/web-api/") features. This server meets those needs.

## Tech/Framework Used

- Node.js
- Express.js
- axios

## Installation

This project requires [node](http://nodejs.org) and [npm](https://npmjs.com) installed globally.

Clone the repository to a directory of your choosing

```sh
$ git clone https://github.com/jamesdoraiii/playlistr-spotify-server.git
```

Navigate into playlistr-spotify-server and install the necessary packages

```sh
$ npm install
```

To run the server

```sh
$ npm start
```

### **Other requirement**

[The Spotify Developer Dashboard](https://developer.spotify.com/dashboard/login)

Create a new .env file in the root folder and add the following key value pairs to the file

```sh
CLIENT_ID = [client id optained from the Spotify Developer Dashboard]
CLIENT_SECRET = [client secret optained from the Spotify Developer Dashboard]
FRONT_URI = http://localhost:3000
RE_URI = http://localhost:4000/callback
REXP = /\.localhost:3000/
```

## Usage

This server is to be consumed by a front-end application - namely the Spotify clone at this [repo](https://github.com/JL978/spotify-clone-client)

The following endpoints are available

| Endpoint       | Method | Body       | Response                                                                                  |
| :------------- | :----- | :--------- | :---------------------------------------------------------------------------------------- |
| /              | POST   | {endpoint} | 200 with the returned data from the endpoint                                              |
| /login         | GET    | none       | redirect to the Spotify authentication page                                               |
| /refresh_token | GET    | none       | if a valid refresh token is available in the cookie, an access_token is sent back as data |
| /logout        | GET    | none       | clear the refresh token and effectively log the user out off the app                      |
