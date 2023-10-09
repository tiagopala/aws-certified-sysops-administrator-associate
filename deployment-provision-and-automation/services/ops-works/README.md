# AWS OpsWorks (Management & Governance)

<img height=100px; alt="ops-works" src="../../../images/ops-works.png" />

AWS OpsWorks é um **serviço gerenciado para automatização da configuração**, a qual permite o **gerenciamento centralizado** do SO (sistema operacional) e configurações de aplicação em EC2 ou sistemas on-premises.

Ele é considerado um serviço de ***Configuration as Code***, pois através de códigos, podemos **gerir e automatizar** toda a parte de configurações de nossos sistemas.

Uma das vantagens de se utilizar o OpsWorks é que não precisamos criar, gerir e manter nosso próprio sistema de gerenciamento de configurações, permitindo o foco nos sistemas *core* do nosso negócio.

Palavras-chave: *Configuration as Code*, *Chef* ou *Puppet*, *Stack consisting of multiple layers*.

## Features

### Chef Automate

É uma feature para aqueles que já tem familiaridade ou já trabalham com o *Chef*.

### OpsWorks for Puppet Enterprise

É uma feature para aqueles que já familiaridade ou já trabalham com o *Puppet*.

### OpsWorks Stacks

Feature que permite a modelagem da aplicação em *stacks* criadas à partir de diferentes *layers* (camadas).

Cada *layer* é configurado utilizando-se *Chef Recipes* ("receitas") e expressam como os serviços e instâncias devem ser configurados para compor o aplicativo.

Exemplos: Instalação da SDK e linguagem de programação, configurações de *deploy* e própria aplicação, instalação da base de dados, rodar *scripts* em *bash* ou *PowerShell*, entre outros.