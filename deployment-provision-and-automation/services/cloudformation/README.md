# Cloudformation

<img height=100px; alt="cloudformation" src="../../../images/cloudformation.png" />

CloudFormation é o **serviço de IaC** (*Infrastructure as Code*) da AWS e pertence ao domínio de gerenciamento e governança (management & governance). Através dele podemos **gerenciar, configurar e provisionar ambientes inteiros** (*stacks*) na AWS.

Para provisionarmos nossos serviços/recursos (*resources*), devemos configurar um ***cloudformation template*** a qual será responsável por provisionar os serviços presentes nele. Este arquivo suporta os formatos ```.yaml``` ou ```.json```.

> O *cloudformation template* utilizado será armazenado em um *bucket s3*.

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
- **Metadata**: Informações referentes ao dados presentes no *template*.
- **Parameters**: Parâmetros de entrada a qual deverão ser informados no momento da criação/atualização da *stack*.
- **Rules**: Validação dos parâmetros informados.
- **Mappings**: Coleção de valores chave/valor a qual podem ser referenciados nas sessões *Resources/Outputs*.
- **Conditions**: Criar condições, exemplo: provisionamento ou não de um recurso.
- **Transform**: Uma das sessões mais importantes, através do Transform podemos referênciar códigos adicionais armazenados em um *bucket s3*, permitindo re-uso de código, como *template snippets*, pequenos pedaços de códigos *cloudformation* ou até códigos de *lambdas*.
- **Resources**: É a principal e única sessão obrigatória do template, é através dela que configuramos os serviços a qual serão provisionados.
- **Outputs**: Permite configurar outputs que poderão ser utilizados por outros *cloudformation templates*.

## Modelo de Custos

É serviço gratuito, porém os serviços provisionados seguem o mesmo modelo de pricing de cada serviço.