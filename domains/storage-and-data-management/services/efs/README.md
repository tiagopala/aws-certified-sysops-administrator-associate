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

## Classes de armazenamento (Storage Classes)

### EFS Standard

É a classe padrão utilizada para a maioria dos cenários, com acessos frequentes e alta disponibilidade.

### EFS Standard-Infrequent Access (IA)

Usada para arquivos que não são acessados frequentemente.

> Possui uma taxa adicional de recuperação.

### EFS One Zone

Mesmas características do EFS Standard, porém para arquivos que não necessitam de uma alta disponibilidade.

### EFS One Zone-IA

Mesmas características do EFS One Zone, porém para arquivos que não são acessados frequentemente.

> Importante ressaltar, caso a aws perca aquele *data center* a qual estão armazenados estes arquivos, seus arquivos serão permanentemente perdidos.

Comparativo entre os diferentes tiers:

| Classe           | Durabilidade   | Disponibilidade     | AZ's     | Observações                                       | Caso de uso                                                                            |
| ---------------- | -------------- | ------------------- | -------- | ------------------------------------------------- | -------------------------------------------------------------------------------------- |
| EFS Standard     | 99.(11x9's)% | **99.99%**          | **>=3**  | N/A                                               | Dados com **alta criticidade** acessados **frequentemente** com alta disponibilidade   | 
| EFS Standard-IA  | 99.(11x9's)% | **99.99%**          | **>=3**  | Taxa de recuperação por dado (gb)                 | Dados com **alta criticidade** acessados **ocasionalmente** com alta disponibilidade   |
| EFS One Zone     | 99.(11x9's)% | **99.90%**          | **1**    | Baixa resiliência devido ter apenas 1 AZ          | Dados com **baixa criticidade** acessados **frequentemente** com baixa disponibilidade |
| EFS One Zone-IA  | 99.(11x9's)% | **99.90%**          | **1**    | Baixa resiliência + taxa de recuperação dos dados | Dados com **baixa criticidade** acessados **ocasionalmente** com baixa disponibilidade |

## Encryption

A criptografia *at rest* (na fonte, no servidor) **APENAS** pode ser habilitada em **momento da criação**.

Caso seja necessário criptografar habilitar a criptografia do lado do servidor, será necessário criar um novo file system e migrar os arquivos.