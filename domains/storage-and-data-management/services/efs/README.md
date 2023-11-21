# EFS - Elastic File System (Storage)

<img height=100px; alt="s3" src="../../../../images/efs.png" />

O EFS é um serviço de armazenamento compartilhado para cargas de trabalho com linux.

## Características

- **Managed NFS**: É um *Network File System* compartilhado, altamente escalável e disponível para trabalhos com instâncias linux.
- **Standard NFS Protocol**: Utiliza o padrão de protocolo NFS, já utilizado por sistemas linux.
- **Shared Access**: Permite que várias instâncias tanto na *cloud* quanto *on-premises* se conectem de uma só vez, permitindo compartilhamento de dados e arquivos.
- **Lifecycle Management**: Possui gerenciamento de ciclo de vida dos arquivos através dos diferentes [tipos de armazenamento](#classes-de-armazenamento-storage-classes).
- **Encryption**: A criptografia já vem habilitada por padrão, porém é possível desativá-la, lembrando que não poderemos habitá-la futuramente.

## Features

- [Storage Classes](./efs-storage-classes.md)
- [Throughput Modes](./efs-throughput-modes.md)

## Cenários

- [EFS & Multi-AZ Applications](./efs-and-multi-az-apps.md)
- [Fault Tolerance EFS](./efs-fault-tolerant-architecture.md)

## High Availability & Durability

Os dados armazenados no EFS são escritos em 3 AZ's, estando disponíveis para quaisquer AZ's presentes naquela região, oferecendo **99.99% de disponibilidade**.

## Integração com outros serviços

Atualmente o EFS pode se integrar com diversos serviços de container (*ECS*, *EKS*, entre outros), *Lambdas* e *EC2*'s.

Além de também se integrar nativamente com o *AWS Backup* para *backups* automáticos.

## Encryption

Os tipos de criptografia disponíveis no EFS são: *at rest* ou *in transit*.

Para criptografia *at rest*, podemos utilizar o serviço do KMS para criação e gerenciamento das chaves e a criptografia dos dados.

Já no caso da criptografia *in transit*, devemos utilizar o protocolo TLS através na comunicação os *mount targets* através do *EFS mount helper*.

Importante lembrar que a criptografia *at rest* (na fonte, no servidor), **APENAS** pode ser habilitada em **momento da criação** do *file system*.

Não é possível habilitar a criptografia de um *file system* já criado, caso desejarmos criptografar os dados presentes nele, será necessário criar um novo *file system* com criptografia habilitada e migrar os arquivos para este novo *file system*.