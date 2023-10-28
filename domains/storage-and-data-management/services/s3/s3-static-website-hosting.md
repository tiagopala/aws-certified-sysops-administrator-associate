# Static Website Hosting

O s3 permite criarmos websites státicos de maneira fácil, prática, segura e de baixo-custo.

## Configurando um site estático

Devemos realizar os seguintes passos:

- Editar as propriedades do *bucket*, habilitando o *static website hosting*.
- Desabilitar as configurações de bloqueio para acesso público (*Disable Block Public Access*).
- Criar um uma *bucket policy* permitindo a leitura anônima de seus objetos. 

## Integração com frameworks

Devido SPA's (Single Page Applications) produzirem um arquivo ```.html``` durante o deploy, o *static website hosting* pode ser inclusive uma opção de hospedagem para seu site.

Os exemplos mais conhecidos de SPA's hoje em dia são: Angular e React.