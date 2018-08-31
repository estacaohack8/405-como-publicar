# Como publicar uma aplicação com NodeJS e MongoDB

## Publicar o MongoDb no MLab

1- Acessar o [Mlab](http://mlab.com/)

2- Na área MongoDB Deployments, criar em `+ Create New`

3- Escolha o Plan Type `Sandbox` (Free)

4- Escolha uma região qualquer

5- Digite o nome do banco

6- Clique em `Submit Order`

7- Acesse o banco criado, clique na aba Users e adicione um usuário e senha de acesso ao banco

## Preparar a aplicação para execução no Heroku
1- Adicione um script `start` dentro do package.json que inicialize a aplicação

```
{
  "name": "rent-a-cat",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "node index.js"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "ejs": "^2.6.1",
    "express": "^4.16.3",
    "express-mongo-db": "^2.0.4"
  }
}
```

2- Na função listen, adicione a variável process.env.PORT
```
app.listen(process.env.PORT || 3000, () => {
    console.log('Servidor inicializado')
});
```

3- Altere a string de conexão com o banco para acessar o banco da Mlab
```
app.use(expressMongoDb('mongodb://bpimentel:aviao11@ds239682.mlab.com:39682/rent-a-cat'));
```

## Como publicar a aplicação na Heroku
1- Acessar o [Heroku](http://heroku.com/)

2- Criar um novo app através do menu `New -> Create new app`

3- Digite um nome para o novo app

4- Escolha uma região qualquer e clique em `Create app`

5- Vá na aba `Deploy` e clique no botão do Github em `Deployment Method`

6- Selecione o repositório que será vinculado à esse Heroku App

7- Clique no botão `Deploy branch` na seção `Manual deploy`
