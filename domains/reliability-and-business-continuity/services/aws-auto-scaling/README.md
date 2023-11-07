# AWS Auto Scaling (Management & Governance)

<img height=100px; alt="aws-auto-scaling" src="../../../../images/aws-auto-scaling.png" />

É um serviço de gerenciamento e governança responsável por auxiliar na configuração e manutenção da escalabilidade de seus recursos.

A criação de um *scaling plan* (plano de escalabilidade) nos permite escalar automaticamente nossos recursos.

Atualmente ele possui integração nativa para escalar uma série de serviços da AWS.

## Conceitos

### Scaling Plan

Para iniciarmos a configuração da escalabilidade de nossos recursos precisamos entender como configurar corretamente um *scaling plan*.

Através do *scaling plan*, definimos basicamente os direcionamentos para escalar cada recurso.

### Scaling Strategy

A *scaling strategy* (estratégia de escalabilidade), é basicamente uma série de instruções para o *AWS Auto Scaling* de como otimizar os recursos pensando em disponibilidade e custos.

### Dynamic Scaling

É uma das formas de escalar os recursos, através do *dynamic scaling* definimos *thresholds* de quando escalar um recurso.

Após configurados os *thresholds*, os recursos serão monitorados para automaticamente ajustar a capacidade em relação a sua utilização baseados no *threshold*.

### Predictive Scaling

É outra forma de escalar seus recursos, diferente do *dynamic scaling*, o *predictive scaling* não necessita configurarmos nenhum *threshold*.

Ele utiliza-se de *machine learning* e *forecasting* baseado no histórico de utilização para prever quando será necessário escalar.

## Quais formas de criar um scaling plan?

Podemos utilizar *scripts* do *cloudformation* para encontrar modelos aos nossos serviços.

Outra opção é escolher e incluir no *scaling plan* um ou mais *EC2 Auto Scaling Groups*.

E a última, é escolher os recursos através de *tags*.

## Serviços AWS Escaláveis

- **EC2**: Através de Auto Scaling Groups, para iniciar e terminar novas instâncias.
- **DynamoDb**: Permite que tabelas e *indexes* aumentem ou diminuem a capacidade de leitura e escrita.
- **ECS**: Ajustes nos serviços e *tasks* do ECS em detrimento da variação de cargas de trabalho.
- **Aurora**: Automaticamente ajusta o número de *read replicas* em um *Aurora Db Cluster*.