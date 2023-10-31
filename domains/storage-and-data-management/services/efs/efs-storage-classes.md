# Classes de armazenamento do EFS (Storage Classes)

## EFS Standard

É a classe padrão utilizada para a maioria dos cenários, com acessos frequentes e alta disponibilidade.

## EFS Standard-Infrequent Access (IA)

Usada para arquivos que não são acessados frequentemente.

> Possui uma taxa adicional de recuperação.

## EFS One Zone

Mesmas características do EFS Standard, porém para arquivos que não necessitam de uma alta disponibilidade.

## EFS One Zone-IA

Mesmas características do EFS One Zone, porém para arquivos que não são acessados frequentemente.

> Importante ressaltar, caso a aws perca aquele *data center* a qual estão armazenados estes arquivos, seus arquivos serão permanentemente perdidos.

## Comparativo

| Classe           | Durabilidade   | Disponibilidade     | AZ's     | Observações                                       | Caso de uso                                                                            |
| ---------------- | -------------- | ------------------- | -------- | ------------------------------------------------- | -------------------------------------------------------------------------------------- |
| EFS Standard     | 99.(11x9's)%   | **99.99%**          | **>=3**  | N/A                                               | Dados com **alta criticidade** acessados **frequentemente** com alta disponibilidade   | 
| EFS Standard-IA  | 99.(11x9's)%   | **99.99%**          | **>=3**  | Taxa de recuperação por dado (gb)                 | Dados com **alta criticidade** acessados **ocasionalmente** com alta disponibilidade   |
| EFS One Zone     | 99.(11x9's)%   | **99.90%**          | **1**    | Baixa resiliência devido ter apenas 1 AZ          | Dados com **baixa criticidade** acessados **frequentemente** com baixa disponibilidade |
| EFS One Zone-IA  | 99.(11x9's)%   | **99.90%**          | **1**    | Baixa resiliência + taxa de recuperação dos dados | Dados com **baixa criticidade** acessados **ocasionalmente** com baixa disponibilidade |