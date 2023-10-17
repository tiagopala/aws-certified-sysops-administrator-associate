# AWS Config (Management & Governance)

<img height=100px; alt="config" src="../../../images/aws-config.png" />

É um serviço com foco no **monitoramento da configuração de seus recursos AWS**.

Através dele podemos definir quais são as **configurações desejadas** para cada recurso.

Caso determinado recurso não esteja em conformidade com a configuração desejada podemos enviar notificações e até triggar ações previamente definidas.

## Características

- **Dashboard Inventory**: Devido ser uma ferramenta de monitoramento, possui um *dashboard* informando todos os serviços/recursos que estão em compliance ou não.
- **Change History**: Possui um histórico de alterações armazenados no S3.
- **Compliance**: Ótima ferramenta de segurança e compliance (criação e configurações de *guardrails*).
- **Compatibility**: Compatível com grande parte dos serviços atualmente.
- **Automatic Remediation**: Ação que será desencadeada caso alguma *rule* não esteja em conformidade.

## Terminologia

- **Rule**: É o nome dado à configuração desejada para aquele recurso/serviço.
- **Managed Rule**: Configurações previamente configuradas pela própria aws.
- **Conformance Packs**: Uma série de regras e de ações de remediação que podem ser implantadas de uma só vez, pode incluir vários recursos, exemplo: Melhores práticas para S3, EC2 e IAM em um só *pack* (pacote).

### Rule

Ao criar uma nova *rule*, devemos informar qual o *evaluation mode* destinado à aquela regra.

> A *rule* já pode ser executada imediatamente após sua criação.

#### Evaluation Mode

O *evaluation mode* indica basicamente ao *aws config* quando ele deve avaliar uma regra, sendo dividida nos seguintes tipos: 

- *All Changes*: Sempre que qualquer serviço/recurso for alterado.
- *Resources*: Somente para aquele recurso em que a regra irá atuar.
- *Tags*: Somente nos serviços/recursos que possuire aquela determinada tag.

O *default* e boa prática quando houver a possibilidade é utilizarmos o tipo *resources*, pois ele irá avaliar aquela regra em específico somente quando alterarmos algum recurso daquele escopo em específico.

## Exemplo

*Rule*: Os *guardrails* da companhia não permitem que instâncias EC2 possuem um endereço de IP público.

Monitoramento: 1 instância não está em conformidade com a configuração desejada acima.

Ação de remediação: Realizar o *stop* desta determinada instância.