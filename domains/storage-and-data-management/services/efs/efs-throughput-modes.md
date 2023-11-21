# EFS Throughput modes

O EFS é extremamente performático, suportando milhares de conexões simultaneamente.

Ainda referente a performance do EFS, temos atualmente 2 tipos de *throughput* disponíveis: *Bursting* e *Provisioned Throughput*. 

## Throughput Modes

### Bursting Throughput

É o tipo padrão (default) quando criamos um EFS.

Ele é desenhado para escalar conforme o crescimento do *file system*.

> Conforme o tamanho do *file system* aumenta, o *throughput* também aumenta.

Importante ressaltar que ele também suporta *periodic bursting* (aumento do throughput momentaneamente) para atender à picos de requisição.

#### Relação de Tamanho/Throughput

- Mínimo: Todos os EFS file systems podem aumentar até o máximo de 100 MiB/s.
- Maior 1 TiB: Para file systems maiores que 1 TiB de na classe Standard, o *burst* pode chegar até 100 MiB/s por TiB armazenado.
> Exemplo: Armazenamento de 2,5 TiB o burst pode chegar até 200 MiB/s.
- 10 TiB: Se alcançarmos 10 TiB de  armazenamento, o *burst* pode chegar até 1.000 MiB/s de *metered throughput*. 

**Comparação**

| Tamanho        | Burst                             |
| -------------- | --------------------------------- |  
| 0 < 1 TiB      | 100 MiB/s                         |
| 1 TiB < 10 TiB | 100 MiB/s por TiB                 |
| >= 10 TiB      | 1.000 MiB/s de metered throughput |

***Metered Throughput*** é o nome dado para a junção de todas as requisições de leitura e escrita somadas.

#### Duração

Quanto maior o tamanho do *file system*, **maior a duração e o burst** do throughput.

> Importante ressaltar que ele utiliza *burst credit system* (sistema de créditos) para determinar a quantidade de *burst* "disponível"

### Provisioned Throughput

Esta opção foi desenvolvida para aplicações que consistentemente precisam de alta performance (maior throughput que o *bursting mode* oferece).

Exemplo: Iremos inicialmente armazenar até 1 TiB, porém o *throughput* mínimo necessário será de 200 MiB/s. Neste caso, o *Bursting Mode* não será suficiente para nosso caso de uso, portanto devemos optar pelo *Provisioned Mode*.

É possível, opcionalmente, definir o *throughput* desejado.

> Diferente do *Bursting Mode*, *throughput* é fixo independente do *system size*.
>
> Ele pode escalar a qualquer momento porém apenas reduz o *throughput* após 24 horas da última redução ocorrida.

## Casos de Uso Reais

Na prática, sempre devemos optar por iniciar as operações utilizando o *Bursting Mode* e conforme haja a necessidade de expandirmos o *throughput* devido necessidades da aplicação, devemos optar por realizar a trocar do *Bursting Mode* para *Provisioned Mode*.

## Custos

O EFS apenas cobra pela capacidade consumida além de poder escalar para suprir a capacidade de armazenamento e *throughput*.