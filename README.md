<div align="center">

# To Do App

Lista de tarefas com Node.js, Express, Handlebars e MySQL, feita no ensino médio técnico em Informática (2023)

<img src="https://img.shields.io/badge/Node.js-0D0D0D?style=for-the-badge&logo=nodedotjs&logoColor=FF1A2B" alt="Node.js" />
<img src="https://img.shields.io/badge/Express-0D0D0D?style=for-the-badge&logo=express&logoColor=FF1A2B" alt="Express" />
<img src="https://img.shields.io/badge/Handlebars-0D0D0D?style=for-the-badge&logo=handlebarsdotjs&logoColor=FF1A2B" alt="Handlebars" />
<img src="https://img.shields.io/badge/MySQL-0D0D0D?style=for-the-badge&logo=mysql&logoColor=FF1A2B" alt="MySQL" />
<img src="https://img.shields.io/badge/CSS3-0D0D0D?style=for-the-badge&logo=css&logoColor=FF1A2B" alt="CSS3" />
<img src="https://img.shields.io/badge/JavaScript-0D0D0D?style=for-the-badge&logo=javascript&logoColor=FF1A2B" alt="JavaScript" />

</div>

## Sobre

Projeto feito em 2023 no ensino médio técnico em Informática, para praticar uma aplicação web com servidor Node.js, páginas renderizadas com Handlebars e dados em MySQL. A proposta é uma lista de tarefas com criação, conclusão, filtros e tema claro/escuro. O código está no estado em que foi entregue: o último commit registra que o `scripts.js` não foi concluído, e várias rotas ficaram inacabadas.

## Funcionalidades

O que o código implementa ou começou a implementar:

- Listagem das tarefas da tabela `tarefas`, com contagem das ativas (`GET /`).
- Formulário para criar tarefa (`POST /criar`).
- Rotas para marcar como completa (`POST /completar`), desmarcar (`POST /descompletar`), excluir (`/excluir`) e apagar todas (`GET /limparTarefas`).
- Filtros de tarefas ativas (`GET /ativas`) e completas (`GET /completas`).
- Alternância de tema claro/escuro salva no `localStorage`.

## Tecnologias

- Node.js
- Express
- express-handlebars
- mysql2
- nodemon (desenvolvimento)
- CSS e JavaScript no front

## Como executar

Requer Node.js e um servidor MySQL.

1. Crie o banco e a tabela. O repositório não traz script SQL; a estrutura abaixo foi deduzida das consultas do `index.js`:

   ```sql
   CREATE DATABASE todoapp;
   USE todoapp;
   CREATE TABLE tarefas (
     id INT AUTO_INCREMENT PRIMARY KEY,
     descricao VARCHAR(255) NOT NULL,
     completa TINYINT(1) NOT NULL DEFAULT 0
   );
   ```

2. Defina as variáveis de conexão. `DB_PASSWORD` não tem valor padrão; as demais usam `localhost`, `root`, `todoapp` e `3306` se não forem definidas. O arquivo `.env.example` lista as cinco variáveis como referência; o projeto não carrega `.env` sozinho, então defina-as no terminal.

   PowerShell:

   ```powershell
   $env:DB_HOST = "localhost"
   $env:DB_USER = "root"
   $env:DB_PASSWORD = "sua_senha"
   $env:DB_NAME = "todoapp"
   $env:DB_PORT = "3306"
   ```

   bash:

   ```bash
   export DB_HOST=localhost
   export DB_USER=root
   export DB_PASSWORD=sua_senha
   export DB_NAME=todoapp
   export DB_PORT=3306
   ```

3. Instale as dependências e suba o servidor no mesmo terminal:

   ```bash
   npm install
   npm run dev
   ```

   O servidor sobe em `http://localhost:3000` depois de conectar ao MySQL.

## Estrutura

```
todo-app/
├── index.js                 # servidor Express, rotas e conexão MySQL
├── .env.example             # variáveis de conexão (referência)
├── package.json
├── views/
│   ├── layouts/main.handlebars
│   ├── home.handlebars
│   ├── ativas.handlebars
│   └── completas.handlebars
└── public/
    ├── css/styles.css
    ├── js/scripts.js        # tema e chamadas de completar/excluir
    └── imagens/             # fundos e ícones
```

---
<div align="center"><sub>Feito por <a href="https://github.com/gabriel-rodrigues0">Gabriel Rodrigues</a></sub></div>
