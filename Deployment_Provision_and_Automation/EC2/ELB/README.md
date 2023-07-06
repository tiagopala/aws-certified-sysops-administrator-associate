# ELB - Elastic Load Balancer

<img height=100px; alt="ebs" src="../../../Images/elb.png" />

O ELB representa o serviço de load balancers da AWS, através dele podemos distribuir o tráfego de rede entre nossos web servers, realizando o balanceamento de carga entre as instâncias que estão registradas naquele target group.

Uma feature importante para termos em mente é a possibilidade de realizar verificações de *health check* periodicamente e assim que for identificado uma instância *unhealthy* ele automaticamente irá remover esta instância do target group temporariamente e irá direcionar o tráfego para outra instância até que ela volte a ficar *healthy*.

Um ponto positivo do elb é a facilidade de aumentar a capacidade de processamento, pois basta apenas provisionar mais instâncias e registrá-las naquele *target group*.

## Tipos

### Application Load Balancer (ALB)

O ALB pode ser usado para distribuição de tráfego **HTTP/HTTPS** pois ele está ocorre na **camada de aplicação** (*layer 7*) do modelo OSI, devido à isso podemos caracterizá-lo como '*application aware*', ou seja, através dele também é possível criar roteamentos que utilizam como base algum parâmetro proveniente da requisição.

**Caso de uso**: Aplicações que necessitam realizar um **"roteamento inteligente"** através do endpoint solicitado ou headers provenientes da requisição.

**Palavras chave**: *Application aware*, *advanced request routing*, *application aware*.

### Network Load Balancer (NLB)

O NLB deve ser usado para distribuição de tráfego TCP pois ele opera na camada de transporte (layer 4) do modelo OSI, sendo capaz de distribuir o tráfego de milhões de requisições mantendo ainda uma latência super baixa.

**Caso de uso**: Aplicações em que a performance é de extrema importância.

**Palavras chave**: Performance.