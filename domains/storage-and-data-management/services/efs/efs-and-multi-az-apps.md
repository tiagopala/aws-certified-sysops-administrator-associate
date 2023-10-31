# EFS & Multi-AZ Applications

O EFS fornece um *mount target* (imagine um *endpoint*, *DNS*) para que as instâncias possam se conectar e utilizá-lo.

Porém dependendo do modelo de armazenamento escolhido e da quantidade de AZ's que nossa aplicação utiliza, teremos diferentes cenários.

Os principais são:  

## Aplicação Multi-AZ e EFS One Zone

Se o modelo de armazenamento for One Zone, teremos apenas um *mount target* sendo disponibilizado na mesma AZ em que foi criado o EFS.

Caso a aplicação (instância) que está consumindo este *mount target* esteja em outra AZ, seremos penalizados com uma taxa adicional por acesso aos dados em AZ's diferentes.

Vale também ressaltar que neste cenário se por alguma motivo perdermos a comunicação com esta AZ e consequentemente com este *mount target*, iremos impactar todas as instâncias em todas as AZ's.

## Aplicação Multi-ZA e EFS Standard

No cenário em que estamos utilizando o tipo de armazenamento Standard, iremos ter um *mount target* para cada AZ.

Dessa forma, cada instância pertencente à aquela AZ irá se conectar no *mount target* respectivo, sem cobranças adicionais.

Diferente do primeiro cenário, aqui temos maior resiliência e maior disponibilidade, pois caso uma AZ "morra", ainda teremos as outras.