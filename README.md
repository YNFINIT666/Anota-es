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
----------------------------------------------------------------------------------------------------------------------------
{
  "name": "servidor_backend",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "expres": "^0.0.5",
    "express": "^5.1.0"
  },
  "description": ""
}
----------------------------------------------------------------------------------------------------------------------------
const express = require("express");
const router = express.Router();

router.post("/cadastro", (req, res) => {
  const { nome, email } = req.body;

  if (!nome || !email) {
    return res.status(400).json({ erro: "Nome e email são obrigatórios." });
  }

  res.status(201).json({
    mensagem: "Usuário cadastrado com sucesso!",
    usuario: { nome, email }
  });
});

module.exports = router;
----------------------------------------------------------------------------------------------------------------------------
const express = require("express");
const fs = require("fs");
const router = express.Router();
const dbPath = "./dados/fakeDB.json";

router.get("/:id", (req, res) => {
  const db = JSON.parse(fs.readFileSync(dbPath));
  const produto = db.produtos.find(p => p.id === req.params.id);
  if (produto) {
    res.json(produto);
  } else {
    res.status(404).send("Produto não encontrado");
  }
});

module.exports = router;
----------------------------------------------------------------------------------------------------------------------------
app.get("/api/products/:id", (req, res) => {
  const { id } = req.params;

  // Exemplo de produtos salvos em memória
  const produtos = [
    {
      id: "abc123",
      name: "Refrigerante X",
      ingredients: ["Água", "Açúcar", "Corante", "Aromatizante artificial"],
      seal: "Não possui selo de sustentabilidade",
      warning: "Alto teor de açúcar"
    }
  ];

  const produto = produtos.find(p => p.id === id);

  if (produto) {
    res.json(produto);
  } else {
    res.status(404).json({ message: "Produto não encontrado" });
  }
});
----------------------------------------------------------------------------------------------------------------------------
const express = require("express");
const router = express.Router();
const userController = require("../controllers/userController");

router.post("/register", userController.registerUser);
router.post("/login", userController.loginUser);
router.get("/:id", userController.getUser);
router.post("/:id/favorites", userController.addFavorite);
router.post("/:id/history", userController.addHistory);

module.exports = router;
----------------------------------------------------------------------------------------------------------------------------
const express = require('express');
const cors = require('cors');

const app = express();

// Middlewares
app.use(cors());
app.use(express.json());

// Rotas
const userRoutes = require('./routes/users');
const productRoutes = require('./routes/products');

app.get('/', (req, res) => {
  res.send('Servidor funcionando!');
});

app.use('/api/users', userRoutes);
app.use('/api/products', productRoutes);

// Inicialização do servidor
app.listen(3000, () => {
  console.log('Servidor rodando em http://localhost:3000');
});
