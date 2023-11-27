# RTO & RPO (Disaster Recovery)

São conceitos utilizados na construção de uma arquitetura resiliente e redundante à desastres naturais (*disaster recovery*).

Entender esses conceitos é fundamental para conseguirmos construir uma arquitetura que realmente esteja *compliance* com nosso *business*.

## RPO

O *Recovery Point Objective* (RPO) diz respeito a frequência em que os dados armazenados com redundância.

*"**How much** data can my application afford to lose?"*

Como pode ser visto na frase acima, aqui estamos falando sobre a **quantidade** de dados que estamos dispostos à perder. 

Exemplo: Geração de *backups* ou *snapshots* diariamente.

## RTO

Já o *Recovery Time Objective* (RTO), está vinculado ao tempo em que a aplicação demora para voltar a operar normalmente.

*"**How long** can I afford for my application to be down?"*

Dessa vez, estamos nos referindo ao **intervalo de tempo** que a aplicação pode ficar fora do ar.

Exemplo: Utilização do *RDS Multi-AZ*, aplicação ficará fora do ar por apenas enquanto ocorre o roteamento do tráfego para a base secundária.