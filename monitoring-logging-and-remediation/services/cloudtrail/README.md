# CloudTrail (Management & Governance)

<img height=100px; alt="cloudtrail" src="../../../images/cloudtrail.png" />

É um serviço de gerenciamento e governança responsável por realizar o **armazenamento das atividades dos usuários** em sua conta AWS.

O CloudTrail armazena os logs das chamadas de **criação, modificação e deleção de recursos AWS** feitos à partir do **console** ou **aws cli**.

> As chamadas feitas via ssh/rdp não são logadas pois a comunicação está sendo realizada diretamente com a instância.

Atualmente a grande maioria dos serviços já possui integração ao CloudTrail, para consultar os serviços que não são suportados acessar o [link](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-unsupported-aws-services.html0).

## Características

- **Enable by default**: Habilitado por padrão desde a criação da conta.
- **Retention**: Retenção dos logs até **90 dias**, porém se criarmos o *Trail* através do console, os dados serão armazenados indefinitivamente em um *bucket s3*.
- **Encrypted by default**: Os logs são *server side encrypted* (criptografados do lado do servidor) por padrão e possuem **validação de integridade**, ou seja, todos os logs são assinados digitalmente portanto podemos detectar qualquer alteração ou deleção.
- **All Regions**: O Trail criado no console aplica-se para todas as regiões.
- **Near Real-Time**: Os logs podem demorar até 15 minutos para estarem disponíveis no CloudTrail, e caso os dados sejam replicados ao s3, podemos adicionar aproximadamente mais 5 minutos pois o CloudTrail sincroniza esses dados à cada 5 minutos.

## Casos de Uso

- **Incident Investigation**: Investigação de incidentes (após ter ocorrido) e análise dos logs para identificar possíveis causas.
- **Security Analysis**: Análises de segurança das atividades dos usuários em *near real-time* (tempo próximo ao tempo real).
- **Compliance**: Pode ser usado como uma ferramenta de compliance, regulatórios e para auditoria.

## Exemplo

Como pode ser visto no exemplo abaixo, podemos identificar:

- ```arn```: O usuário que realizou determinada ação.
- ```eventTime```: Quando a ação ocorreu.
- ```eventName```: O que ocorreu.
- ```awsRegion```: Aonde ocorreu.
- ```SourceIp```: Ip de origem da requisição.
- ```requestParameters```: Parâmetros de entrada.
- ```responseElements```: Response da requisição.

```json
{
    "Records": [
        {
            "eventVersion": "1.08",
            "userIdentity": {
                "type": "IAMUser",
                "principalId": "EXAMPLE6E4XEGITWATV6R",
                "arn": "arn:aws:iam::123456789012:user/Mateo",
                "accountId": "123456789012",
                "accessKeyId": "AKIAIOSFODNN7EXAMPLE",
                "userName": "Mateo",
                "sessionContext": {
                    "sessionIssuer": {},
                    "webIdFederationData": {},
                    "attributes": {
                        "creationDate": "2023-07-19T21:11:57Z",
                        "mfaAuthenticated": "false"
                    }
                }
            },
            "eventTime": "2023-07-19T21:17:28Z",
            "eventSource": "ec2.amazonaws.com",
            "eventName": "StartInstances",
            "awsRegion": "us-east-1",
            "sourceIPAddress": "192.0.2.0",
            "userAgent": "aws-cli/2.13.5 Python/3.11.4 Linux/4.14.255-314-253.539.amzn2.x86_64 exec-env/CloudShell exe/x86_64.amzn.2 prompt/off command/ec2.start-instances",
            "requestParameters": {
                "instancesSet": {
                    "items": [
                        {
                            "instanceId": "i-EXAMPLE56126103cb"
                        },
                        {
                            "instanceId": "i-EXAMPLEaff4840c22"
                        }
                    ]
                }
            },
            "responseElements": {
                "requestId": "e4336db0-149f-4a6b-844d-EXAMPLEb9d16",
                "instancesSet": {
                    "items": [
                        {
                            "instanceId": "i-EXAMPLEaff4840c22",
                            "currentState": {
                                "code": 0,
                                "name": "pending"
                            },
                            "previousState": {
                                "code": 80,
                                "name": "stopped"
                            }
                        },
                        {
                            "instanceId": "i-EXAMPLE56126103cb",
                            "currentState": {
                                "code": 0,
                                "name": "pending"
                            },
                            "previousState": {
                                "code": 80,
                                "name": "stopped"
                            }
                        }
                    ]
                }
            },
            "requestID": "e4336db0-149f-4a6b-844d-EXAMPLEb9d16",
            "eventID": "e755e09c-42f9-4c5c-9064-EXAMPLE228c7",
            "readOnly": false,
            "eventType": "AwsApiCall",
            "managementEvent": true,
            "recipientAccountId": "123456789012",
            "eventCategory": "Management",
            "tlsDetails": {
                "tlsVersion": "TLSv1.2",
                "cipherSuite": "ECDHE-RSA-AES128-GCM-SHA256",
                "clientProvidedHostHeader": "ec2.us-east-1.amazonaws.com"
            },
            "sessionCredentialFromConsole": "true"
        }
    ]
}
```

