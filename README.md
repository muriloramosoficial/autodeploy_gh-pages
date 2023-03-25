# autodeploy_gh-pages

Primeiramente, para fazer um auto deploy no vuejs para o Github Pages, temos que fazer algumas confiugrações iniciais no projeto.
Incluir o código abaixo, no fim do arquivo vitest.config.js.



module.exports = {
  publicPath: '/freegameslist/'
}



**freegameslist é o nome do seu repositório no Github.

Crie o arquivo "deploy.sh" na raiz do seu projeto e informe o texto abaixo, alterando o link do seu repositório:



#!/usr/bin/env sh
set -e

npm run build

cd dist

git init
git add -A
git commit -m "New Deployment"
git push -f https://github.com/link_do_seu_repositório_github.git master:vuejspages

cd -



Adicione a linha abaixo em "scripts" no arquivo package.json:
"deploy": "sh deploy.sh"

Deve-se executar o comando npm run deploy no terminal bash do visual code.
Seu código será transferido para a Branch específicada no repositório escolhido.
