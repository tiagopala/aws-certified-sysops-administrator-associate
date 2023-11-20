# Single Or Multi-AZ Deployment

Quando vamos relizar o *deployment* (implantação) de um serviço, aplicação ou infraestrutura.

Um dos trabalhos realizados por um *sysops admins* é de compreender o contexto apresentado e verificar qual o tipo de *"deploy"* mais aderente.

Neste sentido, muita vezes iremos optar ou por um *single AZ* ou *multi-AZ deployment*.

## Premissas

Entre algumas premissas que devem ser consideradas, podemos destacar:

- **Fault Tolerance**: Algum componente da aplicação necessita estar em outra AZ em caso de falhas?
- **Cost**: Economia (custo) é um fator relevante para a saúde do projeto?
- **Availability**: A aplicação deveria estar disponível em diversas AZ's para suprir o tráfego?

## Casos de Uso

### Single AZ

Optamos geralmente pela utilização do *single AZ deployment* nos seguintes cenários:

- Aplicações em desenvolvimento e/ou *testing*.
- Arquiteturas e cargas de trabalho não críticas.
- Aplicações em que a tolerância a falhas (pontos únicos de falha) e disponibilidade não são pontos decisivos.
- Aplicações que necessitam de um baixo custo para serem rentáveis.

### Multi-AZ

Já no caso do *Multi-AZ deployment*, podemos destacar:

- Aplicações em ambiente produtivo que necessitam de alta disponibilidade, alta performance e com recuperação rápida à falhas.
- Arquitetura e cargas de trabalho extremamente críticas.

Para conseguirmos atingir estes objetivos, temos algumas boas práticas e modelos à serem seguidos, entre eles:

- Uso de *load balancers* para realizar o balanceamento de carga entre as AZ's para aumento de disponibilidade e performance.
- Uso de *Multi-AZ deployments* no *RDS* possibilita a geração de *backups*, *patches* e *upgrades* sem impactos na performance (sem consumo direto da base primária).