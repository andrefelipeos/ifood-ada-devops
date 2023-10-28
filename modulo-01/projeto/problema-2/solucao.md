# Problema 2

> Crie uma Pasta qualquer e 5 arquivos de texto. Em seguida define as permissões 400 para a pasta e todos os arquivos recursivamente. Use esse exemplo para explicar o que são as permissões de arquivo no Linux e como elas são representadas de forma mais detalhada possível.

# Solução do problema 2

A descrição do problema pede que uma permissão numérica seja aplicada recursivamente a um diretório e cinco arquivos dentro dele. A permissão numérica 400 representa a permissão simbólica "w--------". Essa permissão significa que usuário dono do diretório e dos arquivos - e somente ele - terá acesso de leitura, mas não de escrita ou execução. Qualquer outro usuário não-*root* não terá qualquer permissão sobre esse diretório e esses arquivos.

## Criando o diretório e os arquivos

Nessa parte utilizei um *script*, que chamei de *cria_arquivos.sh*, porque imaginei que teria de executar esse teste mais de uma vez. O conteúdo do *script* era o seguinte:

    #!/bin/bash
    mkdir ./pasta
    i=1
    while [ $i -le 5 ]
    do
        echo "Texto do arquivo $i" > ./pasta/arquivo-$i.txt
        ((i++))
    done

Após rodar o *script*, havia a seguinte estrutura de diretórios e arquivos.

![Listagem de arquivos mostrando diretório e arquivos criados.](./capturas-de-tela/captura-de-tela-1.png)

## Mudando as permissões

Após criar o diretório e os arquivos, o comando executado conforme a descrição do problema foi:

    $ chmod 400 --recursive pasta/

O resultado desse comando, no entanto, foram várias mensagens de erro. Uma para cada arquivo.

![Erros de permissão ao executar o comando recursivo.](./capturas-de-tela/captura-de-tela-2.png)

Acontece que, ao mudar as permissões do diretório para somente leitura pelo usuário dono, perdemos acesso aos arquivos dentro do diretório. A execução recursiva do comando não consegue modificar os arquivos dentro do diretório, apesar de saber que eles existem.

## Discussão sobre permissões

Ao executar o comando `ls -lR` novamente, ainda é possível visualizar os arquivos dentro do diretório. Porém qualquer ação, como listar suas permissões, não pode ser executada.

![Listagem do diretório e seus arquivos, mas sem acesso aos arquivos e suas permisões.](./capturas-de-tela/captura-de-tela-3.png)

Isso ocorre porque a permissão de execução em um diretório influencia outras permissões. Até é possível listar os arquivos em um diretório sem premissão de execução (fazendo uso da permissão de leitura). No entanto, não é possível executar operações nesse diretório, como criar ou deletar arquivos, entrar no diretório e, nesse caso, listar ou modificar as permissões dos arquivos dentro do diretório.

## Referências
MCBRIEN, Scott. **Linux file permissions-explained**. RedHat: Enable SysAdmin. 2023. Disponível em: https://www.redhat.com/sysadmin/linux-file-permissions-explained. Acesso em: 26 de outubro de 2023.

