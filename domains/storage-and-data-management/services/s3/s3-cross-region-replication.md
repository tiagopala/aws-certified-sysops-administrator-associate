# Cross Region Replication

É um feature do s3 a qual permite replicarmos nossos dados de uma região à outra, fornecendo maior disponibilidade (*availability*) dos dados.

Entre os principais benefícios, podemos destacar:

**Increase Efficiency** (Aumento na eficiência)

Para arquiteturas multi-regionais (*cross-region*), ou seja, a qual possuem serviços *deployados* em mais de uma região, a replicação dos dados para as mesmas regiões em que estão presentes os recursos computacionais resultará em uma maior eficiência computacional.

**Improving Latency** (Melhoria da latência)

Ao replicarmos os dados para regiões mais próximas dos usuários implicará em menores latências para consumo os dados.

**Compliance Objectives**

Caso nossa aplicação tenha algum regulatório para disposição e armazenamento dos dados, podemos utilizá-la também ficarmos *compliance* com estas leis.

## Enabling Cross-Region Replication

Para habitá-la devemos:

1. Criar os buckets nas devidas regiões.
2. Habilitar o versionamento (é uma premissa, obrigatório).
3. Criar uma Replication Rule, selecionando os buckets de origem e destino e uma role com as devidas permissões a ser utilizada (*execution role*).