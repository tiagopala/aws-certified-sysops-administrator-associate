# Cloudformation (Management & Governance)

<img height=100px; alt="cloudformation" src="../../../images/cloudformation.png" />

CloudFormation é o **serviço de IaC** (*Infrastructure as Code*) da AWS e pertence ao domínio de gerenciamento e governança (management & governance). Através dele podemos **gerenciar, configurar e provisionar ambientes inteiros** (*stacks*) na AWS.

Para provisionarmos nossos serviços/recursos (*resources*), devemos configurar um ***cloudformation template*** a qual será responsável por provisionar os serviços presentes nele. Este arquivo suporta os formatos ```.yaml``` ou ```.json```.

> O *cloudformation template* utilizado será armazenado em um *bucket s3*.

## Features

- [StackSets](./stacksets/README.md)

## Benefícios

- **Consistência**: Os recursos sempre serão provisionados de acordo com o template em todos os ambientes em que forem *"deployados"*.
- **Rapidez e Eficiência**: Menos tempo configurando coisas manualmente.
- **Versionamento**: Controle de versão e revisão de código.
- **Gerenciamento de atualizações**: Controle centralizado e gerenciamento de dependências.
- **Roll Back**: Devido ao controle de versão, podemos voltar para uma versão anterior em caso de falhas.
- **Preço**: [Modelo de Custos](#modelo-de-custos)

## Fluxo de Provisionamento

1. Criação do *Cloudformation template*.
2. Upload do *template* para um *bucket S3*.
3. *Cloudformation* irá interpretar o template e chamar as API's necessárias.
4. O resultado será a *stack* criada.

> Podemos acompanhar o provisionamento dos recursos em tempo real através do próprio console da aws.

## Anatomia do Template

A [Anatomia do Template](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/template-anatomy.html) pode ser consultada através da própria documentação oficial do *Cloudformation*.

### Sessões

- **Description**: Descrição do *template* que está sendo criado.
- **Metadata**: Informações referentes aos dados presentes no *template*.
- **Parameters**: Parâmetros de entrada a qual deverão ser informados no momento da criação/atualização da *stack*.
- **Rules**: Validação dos parâmetros informados.
- **Mappings**: Coleção de valores chave/valor a qual podem ser referenciados nas sessões *Resources/Outputs*.
- **Conditions**: Como o próprio nome diz, podemos criar condições em nosso cloudformation, exemplo: criar uma condição para o provisionamento, ou não, de um recurso.
- **Transform**: Uma das sessões mais importantes, através do Transform podemos referênciar códigos adicionais armazenados em um *bucket s3*, permitindo re-uso de código, como *template snippets*, pequenos pedaços de códigos *cloudformation* ou até códigos de *lambdas*.
- **Resources**: É a principal e única sessão obrigatória do template, é através dela que configuramos os serviços a qual serão provisionados.
- **Outputs**: Permite configurar outputs que poderão ser utilizados por outros *cloudformation templates*.

## Modelo de Custos

É serviço gratuito, porém os serviços provisionados seguem o mesmo modelo de pricing de cada serviço.

## Acompanhando/Realizando troubleshooting

Caso desejamos acompanhar o *deployment* da nossa *stack* ou realizar algum *troubleshooting* de um *deployment* já realizado, podemos consultar, através do próprio console da *aws*, todo o histórico de eventos que foram realizados durante o deploy, incluindo os status que eles passaram e mensagens de erro caso tenhamos algum problema durante o provisionamento de algum recurso.

### Erros Comuns

Geralmente, os erros mais comuns envolvendo o CloudFormation são:

- **Insufficient Permissions (IAM)**: Para cada recurso que iremos criar, devemos ver se temos as devidas permissões para criação daquele recurso. *Exemplo: ec2:StartInstances*.

- **Resource Limit Exceeded**: Quando atingimos algum *soft/hard limit* em nossa conta/região. *Exemplo: Máximo de 20 instâncias por região*.

- **Update_Rollback_Failed**: Se algum recurso presente em nossa *stack* for alterado por fora do nosso *cloudformation template*, podemos ter um erro de rollback. Pois o cloudformation não conseguirá retornar ao status do último *deploy* realizado com sucesso.

    Um exemplo de alteração realizada por fora é quando um recurso tiver sido excluído no ambiente, porém ainda está constando no template resultará na seguinte mensagem: *The resource no longer exists*. Para resolvermos este problema, devemos recriar manualmente este recurso de acordo com as propriedades presentes no template.

- **Sintaxe**: Quando nosso *cloudformation template* possui algum erro de *sintaxe* referente ao recurso que está sendo criado.