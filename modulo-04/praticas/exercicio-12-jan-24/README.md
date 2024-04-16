# Exercício — 12 de janeiro de 2024
O objetivo deste exercício é conteinerizar uma aplicação *flask* simples.  

Para isso foi criado um arquivo *Dockerfile* no diretório raiz do projeto. Esse arquivo instrui a criação de uma nova imagem Docker a partir de uma imagem oficial do Python disponível no DockerHub. As instrunções do *Dockerfile* instalam as dependências do *flask* e, então, copiam e executam o projeto usado como exemplo.  

Para criar a imagem Docker, executa-se o seguinte comando no diretório raiz do projeto:  

```docker build . --tag flask-project-image```

A opção `--tag` ou `-t` serve para nomearmos a imagem como "flask-project-image". Com essa opção, também é possível adicionar uma etiqueta à imagem usando o formato `--tag nome-da-imagem:etiqueta`.  

O seguinte comando executa (`run`) um container chamado "flask-project-ctn" a partir da imagem "flask-project-image" criada anteriormente.  

```docker run --detach --publish 5000:5000 --name flask-project-ctn flask-project-image```

A opção `--detach` ou `-d` executa o container em segundo plano e retorna o ID do container. Já a opção `--publish` ou `-p` faz o mapeamento entre as portas do container e as portas do sistema hospedeiro. O formato utilizado nesse mapeamento é `--publish porta-do-hospedeiro:porta-do-container`.

Agora que o cantainer está em execução, podemos acessar a aplicação através de um navegador no endereço `localhost:5000`.  

## Crédito do projeto Python/Flask
Repositório do projeto Python utilizado nessa atividade:
- https://github.com/do-community/flask_auth_scotch

