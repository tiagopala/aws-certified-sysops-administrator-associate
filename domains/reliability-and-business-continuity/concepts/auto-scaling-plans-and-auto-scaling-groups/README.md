# Auto Scaling Plans vs Auto Scaling Groups

Atualmente temos duas opções de escalabilidade para trabalhar com instâncias ec2.

A primeira delas, refere-se ao *AWS Auto Scaling Groups* e a segunda é através do serviço *AWS Auto Scaling*.

**AWS Auto Scaling Groups**

Os *Auto Scaling Groups* é a forma mais conhecida de escalarmos instâncias EC2, sendo uma feature do próprio EC2.

**AWS Auto Scaling Plans**

A segunda forma, é através do serviço *AWS Auto Scaling* em que podemos criar planos de escalabilidade para instâncias EC2, assim como para outros serviços também. 

**Comparação**

Portanto, devemos usar os *Auto Scaling Groups* quando almejamos trabalhar somente com EC2, visto que ele se concentra unicamente em instâncias EC2.

Caso o objetivo seja criar planos de escalabilidade almejando uma variedade de serviços, devemos optar pelo *AWS Auto Scaling*.

> [Lista](../../services/aws-auto-scaling/README.md#serviços-aws-escaláveis) dos serviços suportados pelo *aws auto scaling plan*.