# Elastic IP's

<img height=100px; alt="elastic-ips" src="../../../../../images/elastic-ips.png" />

É uma feature do EC2 a qual nos permite termos um endereço de IP estático vinculado à uma instância.

Dessa forma, ele é considerado uma ótima ferramenta para criar aplicações tolerantes à falha.

Caso a instância seja parada (*stopped*) ou terminada (*terminated*), apesar de internamente o endereço de IP mudar o endereço de IP elástico se manterá o mesmo.

Resumindo, o principal objetivo da utilização dos *Elastic IP's* é a **possibilidade de remapearmos o tráfego de rede em um cenário de falhas**. 

## Características

- *Elastic IP's* são endereços IPV4 estáticos públicos.
- As contas AWS são limitadas à somente 5 *Elastic IP's* por região.