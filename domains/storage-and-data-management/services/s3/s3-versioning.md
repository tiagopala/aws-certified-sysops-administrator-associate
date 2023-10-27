# Versioning

O s3 Versioning permite o armazenamento de múltiplas versões de um mesmo objeto.

Possibilitando inclusive, a realização do *rollback* para versões anteriores.

Além de termos o *tracking* de todas as modificações realizadas naquele objeto, podendo inclusive acessá-las informando o *version id*.

> Não vem habilitado por *default*, devemos habilitá-lo manualmente.

## Delete Marker

Quando enviamos uma solicitação de deleção, não estaremos deletando aquele arquivo, iremos apenas aplicar um delete marker, informando que tal objeto foi "deletado".

Após habilitado o versionamento, se realmente quisermos deletar um objeto, devemos passar a informar o *version id* a ser deletado.

## Proteção dos arquivos

O versionamento pode ser visto também como uma ótima *feature* de segurança, pois o arquivo não será deletado de fato, ele apenas colocará um [delete marker](#delete-marker), conforme informado acima.