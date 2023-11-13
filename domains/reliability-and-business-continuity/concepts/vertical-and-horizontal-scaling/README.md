# Vertical & Horizontal Scaling

Da mesma forma em que os temas de elasticidade e escalabilidade, devem ser entendidos com elevada profundidade.

Ter pleno conhecimento dos conceitos de escalabilidade vertical e horizontal e quando utilizar cada estratégia é fundamental.

**Vertical Scaling**

Quando nos tratamos de *vertical scaling*, devemos pensar sempre em adicionar mais capacidade computacional a um recurso, pensando nos seguintes pilares:

- *disk* io (disco)
- *storage* (armazenamento)
- *CPU* (processamento)
- *Memory* (memória)

> No *vertical scaling* não estamos pensando em aumentar a quantidade de recursos, apenas adição de capacidade computacional

**Horizontal Scaling**

Já o *horizontal scaling* refere-se em aumentarmos a quantidade de recursos.

Podendo ser feita através das seguintes formas:

- Adding instances or nodes (adicionar instâncias ou nós)
- Adding Load Balancers
- Using Auto Scaling Groups
- Using Multi-AZ configurations

## AWS Services Examples

| Service | Vertical               | Horizontal                                  |
| ------- | ---------------------- | ------------------------------------------- |
| EC2     | Increase instance size | Add more instances / Configure Auto Scaling |
| RDS     | Increase instance size | Create read replicas                        |
