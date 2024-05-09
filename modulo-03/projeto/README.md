# Projeto de Rede de Computadores
O projeto final do módulo de Redes de Computadores consistiu em criar um topografia de redes para uma pequena empresa, incluindo setores de tecnologia, recursos humanos e finanças. Foi utilizado o Cisco Packat Tracer para a modelagem do cenário.  

## Captura de Tela do Projeto
![Imagem com quatro blocos coloridos — verde, amarelo, azul e vermelho — representando quatro subredes, contendo servidores e computadores ligados entre si.](/modulo-03/projeto/projeto-captura-de-tela.png "Captura de tela do projeto final do módulo de Redes de Computadores no Cisco Packet Tracer")
> Projeto final do módulo de Redes de Computadores utilizando o Cisco Packet Tracer.

## Descrição do Projeto

Usando o Cisco Packet Tracer, foram criadas quatro subredes. Três delas correspondem ao setores de Finanças, Recursos Humanos e Tecnologia da Informação de uma empresa fictícia. A quarta subrede contém apenas dois roteadores e é usada para estabelecer a comunicação entre as demais subredes.

A configuração da rede incluiu três servidores, um para cada setor. Os servidores do setor de finanças e do setor de recursos humanos executam o mesmo papel dentro de suas respectivas subredes. Cada um deles disponibiza um serviço de DHCP para atribuição automática de IPs em sua subrede. Além disso, eles hospedam e disponibilizam os websites dos seus respectivos setores via HTTP.

Por fim, o servidor do setor de Tecnologia da Informação é responsável pelo serviço de DNS que resolve os domínios das subredes dos outros setores.
