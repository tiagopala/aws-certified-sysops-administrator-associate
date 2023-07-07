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

### Classic Load Balancer (CLB)

É a opção "legado" entre os *load balancers*, através dele podemos tanto fazer o balanceamento de carga HTTP/HTTPS quanto TCP, porém sem a mesma performance do NLB.

Porém, ele possui algumas features interessantes que são importantes termos conhecimento:

- *Sticky Sessions*: Serve para atrelar o client que originou a requisição com o web server que está servindo aquele conteúdo.

- *X-Forwarded-For*: É basicamente um *header* que faz encapsulamento do ip de origem do *client*.

### Gateway Load Balancer (GLB)

Permite o balanceamento de carga de aplicações de terceiros adquiridas dentro do ambiente aws, como por exemplo, compradas via aws marketplace. Pode integrar-se com as seguintes tecnologias: *Firewalls*, *Intrusion Detection* e *Prevention Systems*.

Algumas companhias que prestam tais serviços são: *Fortinet*, *Palo Alto*, *Juniper*, *Cisco*, *CheckPoint*, *Trend Micro*, entre outras.

## Erros Comuns envolvendo ELB's

### Server Side Errors

- **HTTP 504 Gateway Timeout**: Ocorre geralmente quando a aplicação por trás do *load balancer* está com algum erro, não sendo possível estabelecer uma conexão com o *load balancer* dando um *timeout*.

> Erro mais comum e um dos mais cobrados no exame, por isso está sendo citado primeiro.

- **HTTP 502 Bad Gateway**: Ocasionado em grande parte das vezes como erros de permissão, quando o *security group* do *load balancer* não permite a comunicação com o *security group* do *target* (instância ec2, lambda, entre outros).

- **HTTP 503 Service Unavailable**: Trata-se basicamente da falta de *listeners/target groups* registrados à aquele load balancer.

### Client Side Errors

- **HTTP 400 Bad Request**: Erros de validação da requisição.

- **HTTP 408 Request Timeout**: O *client* não respondeu no período esperado para finalizar determinado operação.

- **HTTP 464 Incompatible Protocol**: O protocolo da requisição é incompatível com o protocolo do *target group*.