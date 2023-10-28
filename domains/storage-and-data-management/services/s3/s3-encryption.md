# Encryption (Criptografia)

Criptografia é uma boa prática de segurança, em que o dado é transformado utilizando-se de cifras (cyphers), sendo praticamente impossível descobrirmos o conteúdo daquele arquivo sem termos a chave de criptografia utilizada. Ou seja, é uma forma de proteger os dados contra acessos não autorizados.

## Modelos de Criptografia no s3

### Client Side Encryption

Neste modelo realizamos a criptografia do dado no cliente (exemplo: browser) do próprio usuário.

### Encryption In Transit

É o modelo de criptografia utilizado pelos navegadores (browsers), em que os dados trafegados entre o *backend* (servidor) e *frontend* (cliente) são criptografados.

Dessa forma, caso ocorra uma tentativa de capturar esses dados, exemplo *man in the middle*, mesmo que o atacante consiga, os arquivos estaram criptografados.

Os protocolos mais utilizados é o HTTPS, utilizando-se dos seguintes certificados: SSL (antigo) e TLS (atual).

### Server Side Encryption

Modelo de criptografia dos dados do lado do servidor.

O s3 disponibiliza hoje os 3 seguintes opções:

- **SSE-S3**: Opção *default* quando é criado um novo *bucket*, o s3 é responsável por controlar as chaves.
> Utiliza o padrão do mercado, AES 256-bit.
- **SSE-KMS**: Utilização do KMS (serviço de gerenciamento de chaves), nós fornecemos as chaves e o KMS gerencia.
- **SSE-C**: O cliente fornece, armazena e gerencia as chaves por conta própria.