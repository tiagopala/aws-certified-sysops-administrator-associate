# EFS Throughput modes

O EFS é extremamente performático, suportando milhares de conexões simultaneamente.

Ainda referente a performance do EFS, temos atualmente 2 tipos de *throughput* disponíveis: *Bursting* e *Provisioned Throughput*. 

## Throughput Modes

### Bursting Throughput

É o tipo padrão (default) quando criamos um EFS.

Ele é desenhado para escalar conforme o crescimento do *file system*.

> Conforme o tamanho do *file system* aumenta, o *throughput* também aumenta.

Importante ressaltar que ele também suporta *periodic bursting* (aumento do throughput momentaneamente) para atender à picos de requisição.

#### Comparativo Tamanho/Throughput

- Mínimo: Todos os EFS file systems podem aumentar até o máximo de 100 MiB/s.
- Maior 1 TiB: Para file systems maiores que 1 TiB de na classe Standard, o *burst* pode chegar até 100 MiB/s por TiB armazenado.
> Exemplo: Armazenamento de 2,5 TiB o burst pode chegar até 200 MiB/s.
- 10 TiB: Se alcançarmos 10 TiB de  armazenamento, o *burst* pode chegar até 1.000 MiB/s de *metered throughput*.
> Metered Throughput: É a mistura das requisições de leitura e escrita. 

TODO: Transformar em uma tabela para facilitar a visualização.

#### Duração

Quanto maior o tamanho do *file system*, **maior a duração e o burst** do throughput.

### Provisioned Throughput

Esta opção foi desenvolvida para aplicações que consistentemente precisam de alta performance (maior throughput que o bursting mode oferece).

Exemplo: Iremos inicialmente armazenar até 1 TiB, porém o throughput mínimo necessário será de 200 MiB/s. Neste caso, o *Bursting Mode* não será suficiente para nosso caso de uso, portanto devemos optar pelo *Provisioned Mode*.

É possível, opcionalmente, definir o *throughput* desejado.

## Casos de Uso Reais

Na prática, sempre devemos optar por iniciar as operações utilizando o Bursting Mode e conforme haja a necessidade de expandirmos o *throughput* devido necessidades da aplicação, devemos optar por realizar a trocar do Bursting Mode para Provisioned Mode.