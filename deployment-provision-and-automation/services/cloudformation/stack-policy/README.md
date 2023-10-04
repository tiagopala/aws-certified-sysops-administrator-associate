# Stack Policy

As Stack Policies é uma feature do *cloudformation* que permite **protegermos a alteração de recursos críticos** de mudanças mal intencionadas ou erro humano.

## How it works?

As stack policies são documentos em ```.json``` formado por um ou mais *statements*, que descrevem quais as ações permitidas a serem realizadas em determinado recurso e quais os grupos de usuários que podem realizar tais ações.

**Exemplo**:

```json
{
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "Update:*",
            "Principal": "*",
            "Resource": "*"
        },
        {
            "Effect": "Deny",
            "Action": "Update:*",
            "Principal": "*",
            "Resource": "LogicalResourceId/ProductionDatabase"
        }
    ]
}
```

Como podemos ver no exemplo acima, esta *stack policy* permite realizar o *update* em todos os recursos presentes naquele *template* com exceção ao banco de dados de produção, a qual possui um *statement* com um *explicit deny* para todas as *actions* de atualização.