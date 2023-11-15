# Elasticache (Database)

<img height=100px; alt="elasticache" src="../../../../images/elasticache.png" />

ElastiCache é o serviço de *caching* da aws, através dele podemos implantar (deploy), escalar (scale) e gerenciar o *caching* de nossas aplicações.

Ele funciona à partir do armazenamento em um *memory-cache* na nuvem das queries mais frequentemente realizadas.

## Cache Hit/Miss

Para enterdemos como funciona de fato, o *caching* de uma aplicação é super importante entendermos o significado de dois conceitos: *Cache Hit & Cache Miss*.

**Cache Hit** é o termo utilizado quando a *query* solicitada já está *"cacheada"* e apenas é retornada para a aplicação. Já o **Cache Miss** refere-se a uma consulta que não foi encontrada em *cache*, portanto a aplicação precisou conversar diretamente com o banco de dados para capturar tais informações.

## Benefícios

**Melhoria da Latência/Throughput:**

Através do *caching* a aplicação não precisará consultar diretamente a base de dados, retornando o conteúdo já *"cacheado"*, tendo portanto uma latência menor.

Casos de uso: 

- **Read-heavy application workloads**, exemplo: redes sociais, *gaming*, compartilhamento de arquivos e portais de dúvidas.
- **Compute-intense workloads**, exemplo: Motor de recomendações.

**Melhoria na performance:**

Armazenamento de dados críticos em *cache* para recuperação rápida.

Neste sentido os dados que são usualmente *cacheadas* são: 

- Resultados de *IO-intense database queries*.
- Resultados de cálculos computacionais intensos.

## Tipos

Atualmente, temos duas *engine's* disponíveis: *MemcacheD* e *Redis*.

Sendo o Redis mais completo, para trabalhos mais complexos e o MemcacheD para trabalhos mais simples.

Uma das principais qualidades de ambos é que os dois são ótimos em *data partitioning* e *sub-millisecond latency*.

## Criando um Cluster do ElastiCache

1. Selecionar a engine a qual será utilizada (MemcacheD/Redis).
2. Configuração da engine, exemplo: *node type*, *number of replicas*, *multi-AZ* e *security group*.
3. Habilitar o *Inbound Traffic* no *Security Group*.
4. Conectar e *"cachear"* os dados.

## Monitoramento do ElastiCache

- *CPU Utilization*: Configurar a política de escalabilidade dos nós através de um *threshold*.
- *Swap Usage*: Caso a quantidade de memória seja excedida, alocar mais memória.
- *Evictions*: Caso itens estejam sendo removidos sem estarem expirados, podemos escalar com mais nós ou aumentar o tamanho dos nós.
- *Concurrent Connection*: Indica possivelmente um problema de aplicação.

## ElastiCache vs Redshift

O *ElastiCache* deve ser utilizado por aplicações que possuem uma alta taxa de leitura de informações que não são raramente acessados.

Já o *RedShift* deve ser uma opção para aplicações em que o banco de dados está sobrecarregado devido a *OLAP transactions*.