# S3 Pre Signed URL's

É uma feature do s3, a qual nos permite liberar acesso temporário a um arquivo (objeto) através de uma URL.

## Tecnologias

Podemos criar pre-signed URL's utilizando-se tanto do *AWS CLI*, SDK ou através do console da AWS.

## Expiração

Como toda URL possui um período que ela será válida, sempre devemos configurar em horas e minutos quanto tempo aquela URL será válida.

O máximo de tempo é de 12 horas.

## Controle de Acessos

Quando criamos uma pre-signed URL, as permissões associadas à *role* ou usuário que a criou são usadas para determinar quais ações podem ser utilizadas através daquela URL.

A URL em si não possui nenhum controle de acessos, apenas é uma URL que permite acesso temporário ao objeto.

Exemplo, se a role/usuário utilizado para criá-la possui as devidas permissões para visualizá-la portanto todos com aquela URL terão acesso para visualizá-la.

Para restringir acessos, devemos garantir que a role utilizada na criação tenha as devidas policies para limitar o acesso. 