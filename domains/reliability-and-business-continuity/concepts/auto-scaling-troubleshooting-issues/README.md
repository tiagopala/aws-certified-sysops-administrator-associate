# Auto Scaling Troubleshooting Issues

Os principais problemas que podemos ter envolvendo o *Auto Scaling Groups* são:

- Auto Scaling Group - Not Found
- Auto Scaling Service - Not Enabled 
- Auto Scaling Config - Not Working Correctly

Além dos erros provenientes da criação, configuração e permissionamento dos nosso Auto Scaling Groups.

Podemos ter outros erros que podem acabar "impactando", dentre eles podemos ressaltar:

**Relacionado a Compute/Storage:**

- *Invalid EBS device mapping*: De/para inválido para aquele EBS. 
- *Instance type not compatible in AZ*: Tipo de instância não compatível com aquele AZ
- *Attempting to attach EBS block device to an instance-store AMI*: Tentativa de vincular um EBS block em uma instância efêmera.
- *AZ no longer supported*: AZ selecionada não está mais disponível (raro).

**Relacionado a Security:**

- *Associated key pair doesn't exist*: Key Pair selecionado não existe.
- *Security Group doesn't exist*: Security Group selecionado não existe.

## Dicas

É importante termos bem claro os conceitos e diferenças de cada um dos métodos de escalabilidade informados.

Quando identificarmos que o problema ocorre nos *AWS Auto Scaling Groups*, devemos utilizar o console do próprio EC2.

E no caso do *AWS Auto Scaling Plans*, é indicado utilizarmos o console do próprio *AWS Auto Scaling*.