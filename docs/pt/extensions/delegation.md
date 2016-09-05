### Delegação
| Endereço              | URI base     | Permissões requeridas   | C#                 |
|-----------------------|--------------|-------------------------|--------------------|
| postmaster@msging.net (endereço padrão, não é necessário informar) | /delegations | Nenhuma | [DelegationExtension](https://github.com/takenet/messaginghub-client-csharp/blob/master/src/Takenet.MessagingHub.Client/Extensions/Delegation/DelegationExtension.cs) |

A extensão **delegação** permite o contato dar permissões a outras identidades do **Blip Messaging Hub** de realizar ações em seu nome, particularmente o envio de mensagens. O uso da **delegação** é requerido por outras extensões, como **envio em massa** e **agendamento**. 

É necessário efetuar a delegação apenas uma vez para cada identidade.

#### Exemplos
1 - Dando permissões de envio de mensagens à identidade **postmaster@broadcast.msging.net**:
```json
{  
  "id": "1",
  "method": "set",
  "type": "application/vnd.lime.delegation+json",
  "uri": "/delegations",
  "resource": {  
    "target": "postmaster@broadcast.msging.net",
    "envelopeTypes": [  
      "message"
    ]
  }
}
```
Resposta em caso de sucesso:
```json
{
  "method": "set",
  "status": "success",
  "id": "1",
  "from": "postmaster@msging.net/#irismsging1",
  "to": "contact@msging.net/default"
}
```

2 - Revogando as mesmas permissões:
```json
{  
  "id": "2",
  "method": "delete",
  "uri": "/delegations/postmaster@broadcast.msging.net?envelopeTypes=message"
}
```
Resposta em caso de sucesso:
```json
{
  "method": "delete",
  "status": "success",
  "id": "2",
  "from": "postmaster@msging.net/#irismsging1",
  "to": "contact@msging.net/default"
}
```

Para mais detalhes, consulte a especificação do recurso **delegation** no [protocolo LIME](http://limeprotocol.org/resources.html#delegation).
