# Lifecycle Policies (Políticas de ciclo de vida)

É uma feature do S3 que permite criação de políticas (*policies*) ciclos de vida para nossos arquivos de forma automatizada.

Seu principal objetivo é de economizar, ou seja, iremos garantir que os objetos estão sempre utilizando sempre o tier com melhor custo benefício em todo seu ciclo de vida.

## Lifecycle Rules

Essas transições são configuradas através das *lifecycle rules* (regras de ciclo de vida).

Devemos definir basicamente em que momento será realizada e qual a ação a ser realizada.

Atualmente podemos:

- Mover objetos para *tiers* de armazenamento mais baratos.
- Arquivar objetos.
- Excluir.

> Importante lembrarmos que a data início para contagem de tempo das movimentações dos objetos entre os tiers sempre levam em consideração a data de criação daquele objeto em específico.

## Quando utilizar?

As lifecycle rules são ótimas opções para objetos com o ciclo de vida bem definidos.

### Exemplos

- Mover arquivos de *logs* transacionais para um *tier tipo infrequent access* pois não serão mais consumidos com frequência após 90 dias.
- Arquivar objetos para o *Glacier* ou *Glacier Deep Archive* após 1 ano.
- Expirar arquivos que não terão mais uso após 1 ano.
> Após marcados como expirados, o s3 irá automaticamente deletar os arquivos.
- Mover/Arquivar/Expirar os logs provenientes do acesso a outros *buckets* s3 se a *flag: Server Access Logging* estiver habilitada.