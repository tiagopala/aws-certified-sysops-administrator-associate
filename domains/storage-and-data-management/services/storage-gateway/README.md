# Storage Gateway (Storage)

<img height=100px; alt="storage-gateway" src="../../../../images/storage-gateway.png" />

É um serviço de armazenamento para soluções híbridas, portanto teremos uma dupla convivência entre um *data center on-premises* e serviços de armazenamento em nuvem.

## Como funciona?

Através de um dispositivo (pode ser físico ou lógico/digital) a qual será instalado em seu *data center on-premises*, teremos a capacidade de integrar nosso ambiente *on-premises* com os serviços de armazenamento da aws, como por exemplo, um *bucket s3*.

## Benefícios

Um dos principais benefícios de utilizarmos o *storage gateway* é que ele provê soluções de armazenamento alternativas com melhor custo benefício do que soluções *on-premises*.

## Tipos

### File Gateway

Solução de armazenamento em que os dados são armazenados no s3, funcionando como um *file system* porém no s3.

Os dados podem ser armazenados tanto pelos protocolos SMB (*service message blocks*) ou nfs (network file system).

Devido os dados serem armazenados diretamente no s3, temos disponíveis para uso todas as features do s3, como: *bucket policies*, *versioning*, *lifecycle management*, *encryption*, entre outras.

Além de ser um solução de menor custo comparada a soluções de armazenamento on-premises.

> TODO: Criar um desenho arquitetural exemplificando o modelo acima.

### FSx Gateway

Solução de armazenamento para soluções windows, em que os dados serão armazenados no *Amazon FSx for Windows File Server*.

Os dados podem ser acessados somente através do protocolo SMB (service message blocks).

O *Amazon FSx for Windows File Server* é um *file system* compartilhado e totalmente gerenciado, ideal para aplicações windows e diretórios de usuários.

Ele possui adicionalmente integração com AD (*active directory*).

> TODO: Criar um desenho arquitetural exemplificando o modelo acima.

### Volume Gateway

Para o volume gateway temos duas opções atualmente: *Stored Mode* ou *Cached Mode*.

#### Stored Mode

Através do *stored mode*, todos os dados são armazenados localmente e somente o *backup* dos dados é transferido ao s3.

Este *backup* por sua vez é armazenado através de *EBS Snapshots* armazenados no s3.

O acesso aos dados é feito somente através do protocolo *iSCSI*.

> TODO: Criar um desenho arquitetural exemplificando o modelo acima.

#### Cached Mode

Através do *cached mode*, apenas os dados utilizados frequentemente são armazenados localmente, sendo o s3 a fonte primária de armazenamento.

Um dos principais benefícios do *cached mode* comparado ao *stored mode* é o fato de preciamos apenas de espaço suficiente para os dados acessados frequentemente.

Ou seja, sem grandes investimentos em armazenamento *on-premises*. 

O acesso aos dados também é feito somente através do protocolo *iSCSI*.

> TODO: Criar um desenho arquitetural exemplificando o modelo acima.

### Tape Gateway

Solução que permite utilizarmos *virtual tape libraries* para habilitar soluções de arquivamento de dados, como o *s3 Glacier*.

O principal benefício do *tape gateway* é que não precisamos investir em soluções de *backup* próprias.

Ele integra-se com os atuais sistemas de *backup* do mercado como: *NetBackup*, *Backup Exec*, *Veeam*, entre outros.

O acesso aos dados também é feito somente através do protocolo *iSCSI*.

> TODO: Criar um desenho arquitetural exemplificando o modelo acima.