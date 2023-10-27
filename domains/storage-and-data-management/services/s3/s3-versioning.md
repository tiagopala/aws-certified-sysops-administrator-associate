# Versioning (Versionamento)

O s3 Versioning permite o armazenamento de múltiplas versões de um mesmo objeto.

Possibilitando inclusive, a realização do *rollback* para versões anteriores.

Além de termos o *tracking* de todas as modificações realizadas naquele objeto, podendo inclusive capturá-las através do *version id*.

> Não vem habilitado por *default*, devemos habilitá-lo manualmente.

## Delete Marker

Quando enviamos uma solicitação de deleção, não estaremos deletando aquele arquivo, iremos apenas aplicar um *delete marker*, informando que tal objeto foi "deletado".

## Protegendo Objetos 

### Versionamento

O versionamento pode ser visto também como uma ótima *feature* de segurança, pois o arquivo não será deletado de fato, ele apenas colocará um [delete marker](#delete-marker).

Após habilitado o versionamento, se realmente quisermos deletar um objeto, devemos passar a informar o *version id* a ser deletado.

### MFA Delete

Podemos adicionalmente habilitar  o *MFA Delete* - deleção do objeto após uma autenticação de múltiplos fatores - para acrescentar mais uma camada de segurança contra deleções acidentais ou mal intencionadas.