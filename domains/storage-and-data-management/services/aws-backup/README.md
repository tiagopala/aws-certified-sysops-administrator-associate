# AWS Backup (Storage)

<img height=100px; alt="aws-backup" src="../../../../images/aws-backup.png" />

É um serviço de armazenamento totalmente gerenciado com foco no gerenciamento centralizado de *backups*.

Através dele podemos definir um plano de *backup* uma só vez e aplicá-lo para diversos recursos.

O AWS Backup também possui uma feature para realizar *on-demand backups*, para eventuais necessidades.

> Os *backups* são comumente chamados também de *recovery points*.

## Como funciona?

1. Criar um *backup plan*.
2. Criar as *backup rules*.
3. Criar uma *resource assignment role* e selecionar os recursos desejados.

### Backup Plan

Primeiro devemos realizar a criação de uma plano de *backup* a qual será composto por uma ou mais *Backup Rules*.

### Backup Rules

As *backup rules* consistem basicamente em:

- [Backup Schedule](#backup-schedule)
- [Lifecycle Rules](#lifecycle-rule)
- [Backup Vault](#backup-vault)
- [Tags](#tags)

#### Backup Schedule

Para configurarmos o agendamento do backup devemos definir:

- A frequência em que o backup será realizado (diariamente, semanalmente, mensalmente).
- O *Recovery Point Objective* (RPO).
- A janela em que o backup será realizado (sempre das 23:00 às 00:00).

#### Lifecycle Rule

Podemos adicionalmente configurar **regras de ciclo vida** para o *backup* e **períodos de retenção**.

Uma regra comum é de mover o *backup* para um *cold storage* (exemplo s3 glacier) após determinado tempo.

E ainda deletar o *backup* após a expiração do período de retenção.

#### Backup Vault

Definição de onde o *backup* em si será armazenado, por padrão a AWS já cria para nós um *backup vault*.

Após a criação dos *backups*, eles serão disponibilizados como *recovery points* (pontos de recuperação) no *backup vault*.

#### Tags

Definição das tags a serem utilizadas nos *backups*, com intuito de facilitar o gerenciamento.

## Serviços Integrados

Atualmente o *aws backup*, possui integração com diversos serviços, entre eles:

- s3
- FSx
- EC2
- EBS Volumes
- RDS
- DynamoDB
- VMWare on-premises/AWS
- ...

Para a lista completa, podemos conferir a página a [FAQ](https://aws.amazon.com/pt/backup/faqs/) oficial do AWS Backup.