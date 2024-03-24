# Atividade [12/01/24]

Nessa primeira atividade foi criado um *Dockerfile* para conteinerização de uma aplicação feita com Python e Flask.  

O comando a seguir constrói uma imagem **Docker** a partir do *Dockerfile* criado.  

```
docker build --tag flask-app:0.1 .
```

A opção `--tag` ou `-t` serve para nomear e versionar a imagem. Ela é usada no formato `--tag <nome-da-imagem>:<versão-da-imagem>`. O `.` representa o diretóro atual. Se certifique de executar o comando acima no diretório em que está o *Dockerfile*.  

O próximo comando executa um contêiner utilizando a imagem criada.  

```
docker run --detach --publish 80:8080 flask-app:0.1
```

A opção `--detach` ou `-d` é utilizada para executar um contêiner em segundo plano, devolvendo somente o ID do contêiner. Já a opção `--publish` ou `-p` faz o mapeamento entre portas do contêiner e portas do hospedeiro. Ela é usada no formato `--publish <porta-do-hospedeiro>:<porta-do-contêiner>`. No caso acima, o serviço que roda na porta `8080` do contêiner será ficará disponível na porta `80` do hospedeiro.  

A aplicação pode ser acessada pelo navegador no endereço `http://localhost:80`.  

