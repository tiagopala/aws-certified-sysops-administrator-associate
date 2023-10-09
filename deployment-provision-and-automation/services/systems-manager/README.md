# AWS Systems Manager - SSM (Management & Governance)

<img height=100px; alt="systems-manager" src="../../../images/systems-manager.png" />

O Systems Manager é um serviço da aws de visibilidade e gerenciamento de múltiplos recursos.

## Key Points

- **Management Tool**: Visualização e agrupamento de múltiplos recursos.
- **Inventory of EC2 Instances**: Ótima integração com instâncias EC2, sendo capaz de organizá-las por aplicação, environment (ambiente), *Business Units* (BU) e assim por diante. Permite também incluirmos ambientes on-premises.
- **Automation**: A principal característica do SSM é automatização de tarefas operacionais em larga escala (múltiplos sistemas) simultaneamente, como: *patching*, instalação, rodar *scripts*, entre outros.

## Quando utilizá-lo?

Sempre que tivermos que realizar uma operação em várias instâncias, devemos optar pelo SSM, pois através dele podemos realizar tal operação em todos os recursos selecionados (agrupados) de uma só vez de forma simultânea sem precisarmos nos logar em cada uma delas.

## Features

### Run Command

Através do *Run Command* podemos realizar as seguintes tarefas em 1 ou mais instâncias:

- Rodar comandos ou scripts definidos.
- Parar (stop), restartar, terminar ou redimensionar.
- Attach/detach EBS volumes.
- Instalar *patches* (correções) ou *packages* (pacotes).

> Não é necessária nenhuma configuração adicional como: SSH, RDP ou Bastion Host, para utilizarmos o Run Command.

### Patch Manager

Permite realizarmos o *patch* (aplicação de correção) em múltiplas instâncias EC2 simultaneamente.