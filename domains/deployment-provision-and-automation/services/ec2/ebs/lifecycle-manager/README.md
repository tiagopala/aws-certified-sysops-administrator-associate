# Amazon Data Lifecycle Manager

O *Data Lifecycle Manager* é uma *feature* do EC2 (EBS) responsável por automatizar a criação, retenção e deleção de *EBS snapshots* e *EBS-backed AMI's*.

## How it works?

Os tipos de de *lifecycle policy* que podemos criar são:

- *EBS Snapshot policy*
- *EBS-backed AMI policy*
- *Cross-Account Event policy*

Após a escolha do tipo de *policy*, devemos especificar:

- Quais os recursos serão replicados através de TAGs
- Qual a *execution role* será utilizada

Para finalizar devemos realizar as configurações de agendamento (*schedule*), nela iremos informar a frequência, horário de início e tipo de retenção.

Adicionalmente também podemos habilitar a replicação para outra região e habilitar a criptografia (KMS) das cópias criadas.

Resumindo o fluxo, temos:

1. Escolher tipo de *policy*.
2. Identificação/Especificação dos recursos.
3. Realizar as configurações de agendamento.