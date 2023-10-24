# AWS Health Dashboard

<img height=100px; alt="aws-health-dashboard" src="../../../images/aws-health-dashboard.png" />

É um serviço de monitoramento de todos os serviços em todas as regiões da aws.

Ele está dividido atualmente basicamente em 2 categorias: 

- *Service health*: Ocorrências de todos os serviços da aws.
- *Account health*: Ocorrências dos serviços que de fato estamos utilizando em nossa conta, em outras palavras, são as ocorrências que "de fato nos impactam".

## Service Health

Como comentado acima, aqui temos uma visão de todos os serviços disponíveis, qual seu status atual e o histórico das ocorrências.

- *Open and Recent Issues*: Ocorrências abertas ou recentes.
- *Service History*: Temos o histórico de todas as ocorrências de erros nos últimos 12 meses em todas as regiões.

## Account Health

Aqui temos uma visão mais personalizada dos serviços utilizados em nossa conta.

- *Open and Recent Issues*: Ocorrências abertas ou recentes em nossa conta nas últimas 24 horas.
- *Scheduled Changes*: Alterações programadas.
- *Other Notifications*: Notificações e informações gerais que possam nos impactar de alguma forma.

> Podemos verificar adicionalmente quais foram os *affected resources* (recursos afetados) por alguma ocorrência e quais serão afetados em um alteração programada.