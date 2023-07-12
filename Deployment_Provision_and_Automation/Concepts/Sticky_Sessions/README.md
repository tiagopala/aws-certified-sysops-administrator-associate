# Sticky Sessions

As *sticky sessions* é uma feature do [**Elastic Load Balancer**](../../Services/EC2/ELB/README.md) e vieram para solucionar o problema entre balanceamento de carga e *web servers* que guardam a sessão do usuário localmente, tendo como objetivo vincular as requisições com o primeiro *target* que recebeu aquela requisição.

Como iremos abordar/mencionar o conceito de [algoritmo de balanceamento](../../Services/EC2/ELB/README.md#algoritmos-de-roteamento-routing-algorithms) utilizado pelos ELBs, é importante entender como ele funciona.

Basicamente quando habilitamos as *sticky sessions*, estamos realizando um *override* (sobrecarga) no modelo de roteamento padrão por seu próprio algoritmo de roteamento que se baseia em um *session cookie* (cookie de sessão) capaz de identificar a requisição e enviar ao primeiro *target* que a recebeu, criando um vínculo entre o *client* e aquela instância enquanto o *cookie* for válido (não estiver expirado).

**Palavras-chave**: *Cookie session*, *cache session data locally*.

## Quando Habilitar

Devemos habilitá-lo quando nossa aplicação realiza o armazenamento das informações de sessão do usuário em um *cache* local, ou seja, dentro da própria instância. Caso o *sticky sessions* estivesse desabilitado, assim que este usuário fosse redirecionado à outra instância ele teria perdido a sessão e teria de logar-se novamente todas as vezes.

**Casos de uso**: *Shopping carts*, *e-commerces*, formulários online, *websites* em geral, entre outros.