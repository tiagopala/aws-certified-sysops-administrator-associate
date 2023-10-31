# EFS - Elastic File System (Storage)

<img height=100px; alt="s3" src="../../../../images/efs.png" />

O EFS é um serviço de armazenamento compartilhado para cargas de trabalho com linux.

## Características

- **Managed NFS**: É um *Network File System* compartilhado, altamente escalável e disponível para trabalhos com instâncias linux.
- **Standard NFS Protocol**: Utiliza o padrão de protocolo NFS, já utilizado por sistemas linux.
- **Shared Access**: Permite que várias instâncias tanto na *cloud* quanto *on-premises* se conectem de uma só vez, permitindo compartilhamento de dados e arquivos.
- **Lifecycle Management**: Possui gerenciamento de ciclo de vida dos arquivos através dos diferentes [tipos de armazenamento](#classes-de-armazenamento-storage-classes).
- **Encryption**: A criptografia já vem habilitada por padrão, porém é possível desativá-la, lembrando que não poderemos habitá-la futuramente.
> Os tipos de criptografia utilizados pelo EFS são: *at rest* ou *in transit*.

## Features

- [Storage Classes](./efs-storage-classes.md)
- [Throughput Modes](./efs-throughput-modes.md)

## Cenários

- [EFS & Multi-AZ Applications](./efs-and-multi-az-apps.md)

## Encryption

A criptografia *at rest* (na fonte, no servidor) **APENAS** pode ser habilitada em **momento da criação**.

Caso seja necessário criptografar habilitar a criptografia do lado do servidor, será necessário criar um novo file system e migrar os arquivos.