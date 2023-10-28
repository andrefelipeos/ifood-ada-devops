# Problema 1

> Descreva o processo para criar um novo usuário no Linux, incluindo os comandos e opções utilizadas de forma mais detalhada possível.

# Solução do Problema 1

Para criar um novo usuário no Linux, usa-se o comando `useradd`.
Já o comando `userdel` é usado para deletar um usuário.

Somente usuários com privilégios de administrador podem utilizar esses comandos.
Isso é, o usuário *root* ou qualquer outro configurado para poder utilizar o comando `sudo`.

Cada distribuição Linux tem seus próprios padrões na hora de criar um usuário com `useradd`.
No Fedora, por exemplo, um diretório de usuário é criado automaticamente para novos usuários.
Em outras distribuições, pode se necessário adicionar uma opção explícita ao comando `useradd`.

## Adicionando um usuário

O seguinte comando cria um usuário chamado *felipe*, configurado para expirar no dia 31 de dezembro de 2023.

    # useradd felipe --create-home --comment "Felipe Oliveira" --expiredate 2023-12-31

A opção `--create-home` cria um diretório para o usuário.
Por padrão, os diretórios de usuários são criados no diretório `/home`.

A opção `--comment` associa informações do usuário ao usuário criado.
Geralmente, essa opção é utilizada para definir o nome de exibição do usuário.

Já a opção `--expiredate` define uma data de expiração para o usuário.
Nesse caso, o usuário *felipe* será deletado após o dia 31 de dezembro de 2023.

## Configurando a senha do novo usuário

Novos usuários são criados sem uma senha definida.
Para definir a senha de um usuário, utiliza-se o comando `passwd` como a seguir.

    # passwd felipe

Uma nova senha é solicitada, sendo necessário confirmá-la em seguida.

## Outras opções do comando `useradd`

O comando `useradd` aceita ainda outras opções na hora de criar um usuário.

### Especificando o diretório do usuário

Ao criar um diretório para o usuário, é possível definir um local diferente do padrão `/home`.
Para isso basta utilizar a opção `--home` com o diretório de sua escolha.
Por exemplo:

    # useradd nome_do_usuario --create-home --home /meu/diretorio/customizado

Se o diretório `/meu/diretorio/personalizado` não existir, ele será criado.

### Especificando o ID do usuário

Cada usuário no Linux possui um número positivo como identificador único.
Esse identificador é atribuído automaticamente pelo sistema ao criar um novo usuário.
Mas é possível usar um identificador específico com a opção `--uid`.

    # useradd nome_do_usuario --uid 2048

O comando acima especifica 2048 com identificador do usuário a ser criado.

### Especificando o shell do usuário

Também é possível especificar qual *shell* será usado pelo usuário sempre que ele fizer login.

    # useradd nome_do_usuario --shell /bin/sh

### Especificando os grupos do usuário

Grupos são utilizados para definir privilégios de acesso a determinados recursos do sistema.
No Fedora, por exemplo, para que um novo usuário possa utilizar o comando `sudo`, é preciso adicioná-lo ao grupo *wheel*.
É possível fazer isso durante a criação do usuário, com o comando `useradd`.

    # useradd nome_do_usuario --groups wheel

A opção `--groups` é utilizada para definir os grupos secundários do usuário.
Por padrão, um grupo primário é criado para o usuário com o mesmo nome do usuário.

## Deletando usuários

Para deletar um usuário, basta utilizar o comando `userdel` como a seguir.

    # userdel --remove felipe

A opção `--remove` apaga o diretório do usuário e seu *mail spool*.

## Referências:

HESS, Ken. **Linux GECOS information demystified**. RedHat: Enable SysAdmin. 2021. Disponível em: https://www.redhat.com/sysadmin/linux-gecos-demystified. Acesso em: 26 de outubro de 2023.

JAHODA, Mirek; SINHA, Ankur. **Adding a user to sudoers**. Fedora Docs: Quick Docs - Usage and customisation. 2023. Diponível em: https://docs.fedoraproject.org/en-US/quick-docs/adding_user_to_sudoersi_file. Acesso em: 26 de outubro de 2023.

LINUXIZE. **How to Create Users in Linux (useradd Command)**. 2020. Disponível em: https://linuxize.com/post/how-to-create-users-in-linux-using-the-useradd-command. Acesso em: 26 de outubro de 2023.

LINUXIZE. **How to Delete/Remove Users in Linux (userdel Command)**. 2019. Disponível em: https://linuxize.com/post/how-to-create-users-in-linux-using-the-useradd-command. Acesso em: 26 de outubro de 2023.

