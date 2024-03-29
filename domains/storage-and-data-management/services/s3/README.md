# S3 - Simple Storage Service (Storage)

<img height=100px; alt="s3" src="../../../../images/s3.png" />

O s3 é um serviço de armazenamento de objetos, simples e altamento escalável.

Nele podemos armazenar uma série de arquivos, como: imagens, vídeos, códigos, documentos, arquivos de texto, entre outros.

## Definição

- *Object Storage*: Através do s3 podemos armazenar objetos de forma segura (secure), durável (durable) e altamente-escalável (highly-scalable).
- *Simple*: API's de fácil utilização para armazenamento e captura dos objetos.
- *Scalable*: Permite o armazenamento de objetos de forma praticamente ilimitada com baixo custo.

> Importante lembrar que os arquivos são realmente armazenados como objetos por baixo dos panos em vez de *file systems* ou *data blocks*. Por este motivo, NÃO pode ser usado para o *boot* (inicialização) de sistemas operacionais.

## Características Gerais

### S3 e Buckets

- *Unlimited Storage*: O volume total (tamanho) assim como o próprio número de arquivos que podem ser armazenados é ilimitado.
- *Max Object Size*: O tamanho máximo para cada arquivo é de 5 TB (terabytes).
- *Buckets*: Os objetos são armazenados dentro de *buckets*, podemos entender como pastas virtuais.
- *Universal Namespace*: Como todas as contas compartilham o mesmo namespace do s3, os nomes dos buckets são únicos universalmente.
- *s3 URL's*: As URL's são construídas de acordo com o seguinte modelo: https://bucket-name.s3.region.amazonaws.com/object-key-name.
- *Disabled Public Access*: Por padrão, os *buckets* e objetos não permitem acesso público, se realmente desejarmos habilitá-lo, devemos configurá-lo manualmente.

### Objetos

- *Key*: É o nome do objeto que iremos realizar o download/upload. Exemplo: Tiago.png
- *Value*: É a representação do binário em si.
- *Version Id*: Versão do arquivo.
- *Metadata*: Dados sobre os próprios dados. Exemplo: Content-type, last-modified, entre outros.

## Disponibilidade e Durabilidade

### Disponibilidade

Desenvolvido para 99.5 ~ 99.99% de disponibilidade de acordo com o *tier* escolhido.

### Durabilidade

Desenvolvido para 99.99999999999 (11 9's) de durabilidade também de acordo com *tier*.

## Controlando accessos aos objetos

Atualmente temos duas opções para controle de acessos em nossos objetos: *ACL's* e *Bucket Policies*.

### ACL

Através do *ACL - Access Control Lists*, podemos definir políticas de **controle de acessos à objetos individuais**.

Podemos adicionalmente definir quais contas ou grupos e qual tipo de acesso referente aquele objeto em específico.

### Bucket Policies

As *Bucket Policies* permitem a realização do controle de acesso em nível de bucket, ou seja, ele aplica-se à todos os objetos pertencentes à aquele *bucket*.

Permite definirmos quais *actions* (ações) são permitidas ou NÃO naquele *bucket*.

#### Restringir acesso por IP

Através das *bucket policies* podemos adicionalmente restringir acesso através de *ranges* ("intervalos") de endereços de IP.

**Caso de uso**: Imagine que os departamentos de uma companhia estão divididos por IP e exista um bucket contendo informações confidenciais provenientes do departamento financeiro e somente eles podem acessar tais informações. Através das *bucket policies* podemos restringir o acesso para aquele *range* de IP que comporta o departamento financeiro.

> Podemos também, criar regras para bloquear especificamente alguns acessos, usando ainda o exemplo acima, podemos criar uma *condition* que bloqueie o departamento de marketing especificamente de acessar tal *bucket*.

## Features

- [Tiering](./s3-storage-classes-tiering.md)
- [Lifecycle Policies](./s3-lifecycle-polices.md)
- [Versiong](./s3-versioning.md)
- [Encryption](./s3-encryption.md)
- [Static Website Hosting](./s3-static-website-hosting.md)
- [Pre-signed URL's](./s3-pre-signed-urls.md)
- [s3 Inventory](./s3-inventory.md)
- [Cross-Region Replication](./s3-cross-region-replication.md)

## Integração com o AWS Config

As principais *aws managed rules* disponibilizadas pelo *AWS Config* para o *S3* são:

- **s3-bucket-public-read-prohibited**: Verifica se os *buckets* estão com acesso de leitura público.
- **s3-bucket-public-write-prohibited**: Verifica se os *buckets* estão com acesso de escrita público.
- **s3-bucket-versioning-enabled**: Verifica se existem buckets com versionamento desligado.
- **s3-bucket-server-side-encryption-enabled**: Verifica se existem buckets sem *server-side-encryption*.