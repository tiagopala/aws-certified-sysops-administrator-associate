# StackSets

O StackSets é uma feature do *cloudformation* que permite realizarmos diversas operações em várias contas *aws* e regiões ao mesmo tempo. Através dele podemos *criar, alterar e remover* nossas *cloudformation stacks* em diversas contas com apenas uma única operação.

## Realizando deploy em outra conta

Para conseguirmos realizar o *deploy* de nossa *stack* através do *stacksets* em uma outra conta, devemos primeiramente configurar algumas ***cross-account roles***.

1. Criar uma *role* de execução na conta de origem.

2. Criar uma ***trust policy*** que permita o ```sts:assumeRole``` pelo *cloudformation*.

3. Criar uma *role* de execução (*execution role*) na conta destino. 

4. Adicionar as devidas permissões para conseguir prover os recursos na role de execução.

5. Criar uma ***trust policy*** que permita o ```sts:assumeRole``` pela conta de origem.

> Conta Destino: Conta em que os recursos serão provisionados.
> 
> Conta Origem: Conta em que será utilizado o *stacksets*.