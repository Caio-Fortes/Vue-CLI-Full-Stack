# Vue-CLI-Full-Stack
Vue CLI Full Stack - API Express, MongoDB and published on Heroku.

Server API

npm init

npm i express cors

npm i express cors body-parser mongodb

npm i -d nodemon

 "scripts": {
    "test": "node server/index.js",
    "dev": "nodemon server/index.js"
  },

rodar server: npm run dev

username: root
password: root

requests

get: http://localhost:5000/api/posts

post: http://localhost:5000/api/posts
body 
{
  "text": "post 2"
}

delete: http://localhost:5000/api/posts/_id
example: http://localhost:5000/api/posts/665ea5f33770c1eb119b4f8d

Client 

npm i -g @vue/cli

no git bash

vue create client

criar gitignore e colocar 
/client
node_modules

rodar comandos

git init
git add . && git commit -m 'initial backend created'

cd client

rodar vue: npm run serve

npm i axios

Publicação

trocar: const url = "http://localhost:5000/api/posts/"
para: const url = "api/posts/"

na pasta raiz do client: vue.config.js (obs: caso não tiver necessário criar)

configuração:
const { defineConfig } = require('@vue/cli-service')
const path = require('path')

module.exports = defineConfig({
  transpileDependencies: true,
  devServer:{
    proxy:{
      '/api':{
        target: 'http://localhost:5000'
      }
    }
  }
})

reinicie para ver se a os dados ainda estã sendo capturados.

rode o comando na pasta client:
npm run build

depois coloque essa configuração no server/index.js

if(process.env.NODE_ENV === 'production'){
    app.use(express.static(__dirname + '/public'));
    app.get(/.*/, (req, res) => res.sendFile(__dirname + '/public/index.html'))
}

vá para raiz do projeto e commite as alterações

entre no site do heroku, baixe e instale o executavel para o sistema operacional
https://devcenter.heroku.com/articles/heroku-cli

rode 

npm install -g heroku

e faça login 

heroku login

heroku login

heroku open

rode o comando 
heroku create

va para o site 
https://dashboard.heroku.com/apps

nas aplicações criadas selecione a que acabou de criar e após vá no menu e selecione deploy
https://dashboard.heroku.com/apps/sheltered-temple-80291/deploy/heroku-git

na segunda opção de comandos coloque o ultimo que ele faz o exemplo:

exemplo: 

Create a new Git repository
Initialize a git repository in a new or existing directory

$ cd my-project/
$ git init
$ heroku git:remote -a sheltered-temple-80291 (este)

rode 
git push heroku master

video da aplicação:
https://www.youtube.com/watch?v=W-b9KGwVECs&list=PLEHxjuvUU2QrilipaMLO-mWn3MEX6J-Oo&index=5&ab_channel=TraversyMedia



