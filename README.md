Servidor criado dia 23/05/2025: numero do servidor 3000

Type ".help" for more information.
> const http = require('http');
undefined
>
> const server = http.createServer((req, res) => {
...   res.writeHead(200, { 'Content-Type': 'text/html' });
...   res.end('<h1>Olá, Mundo!</h1>');
... });
undefined
>
> server.listen(3000, () => {
...   console.log('Servidor rodando na porta 3000');
... });
<ref *1> Server {
  maxHeaderSize: undefined,
  insecureHTTPParser: undefined,
  requestTimeout: 300000,
  headersTimeout: 60000,
  keepAliveTimeout: 5000,
  connectionsCheckingInterval: 30000,
  requireHostHeader: true,
  joinDuplicateHeaders: undefined,
  rejectNonStandardBodyWrites: false,
  _events: [Object: null prototype] {
    request: [Function (anonymous)],
    connection: [Function: connectionListener],
    listening: [ [Function: setupConnectionsTracking], [Function] ]
  },
  _eventsCount: 3,
  _maxListeners: undefined,
  _connections: 0,
  _handle: TCP {
    reading: false,
    onconnection: [Function: onconnection],
    [Symbol(owner_symbol)]: [Circular *1]
  },
  _usingWorkers: false,
  _workers: [],
  _unref: false,
  _listeningId: 2,
  allowHalfOpen: true,
  pauseOnConnect: false,
  noDelay: true,
  keepAlive: false,
  keepAliveInitialDelay: 0,
  highWaterMark: 16384,
  httpAllowHalfOpen: false,
  timeout: 0,
  maxHeadersCount: null,
  maxRequestsPerSocket: 0,
  _connectionKey: '6::::3000',
  [Symbol(IncomingMessage)]: [Function: IncomingMessage],
  [Symbol(ServerResponse)]: [Function: ServerResponse],
  [Symbol(shapeMode)]: false,
  [Symbol(kCapture)]: false,
  [Symbol(async_id_symbol)]: 33,
  [Symbol(kUniqueHeaders)]: null
}
> Servidor rodando na porta 3000
-----------------------------------------------------------------------------------------------------------------------------
import express from 'express'

const app = express()

app.get('/usuarios', (req, res) => {
    res.send('ok, tudo certo')
})

app.listen(3000)


/*
   
    1) Tipo de Rota / Método HTTP
    2)Endereço

*/
-----------------------------------------------------------------------------------------------------------------------------
{
  "name": "api",
  "version": "1.0.0",
  "type": "module",
  "main": "app.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "node serve.js"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "description": "",
  "dependencies": {
  "express": "^5.1.0"
  }
}
-----------------------------------------------------------------------------------------------------------------------------
const express = require("express");
const app = express();

app.get("/", (req, res) => {
  res.send("Servidor funcionando!");
});

app.listen(3000, () => {
  console.log("Servidor rodando em http://localhost:3000");
});
