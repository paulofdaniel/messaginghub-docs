### Agendamento
| Endereço                        | URI base     | Permissões requeridas   | C#               |
|---------------------------------|--------------|-------------------------|------------------|
| postmaster@scheduler.msging.net | /schedules   | Envio de mensagens (automática) | [SchedulerExtension](https://github.com/takenet/messaginghub-client-csharp/blob/master/src/Takenet.MessagingHub.Client/Extensions/Scheduler/SchedulerExtension.cs) |

A extensão **agendamento** permite o agendamento do envio de mensagens em nome dos contatos para uma data e horário específico. Qualquer tipo de mensagem pode ser agendada, inclusive mensagens de **envio em massa** (para uma lista de distribuição). O horário do agendamento deve ser realizado no fuso GMT 0.

As notificações são encaminhadas ao contato quando recebidas pela extensão.

#### Exemplos
1 - Agendando uma nova mensagem para o dia 25/07/2016 às 17:50h (GMT 0):
```json
{  
  "id": "1",
  "to": "postmaster@scheduler.msging.net",
  "method": "set",
  "uri": "/schedules",
  "type": "application/vnd.iris.schedule+json",
  "resource": {  
    "message": {  
      "id": "ad19adf8-f5ec-4fff-8aeb-2e7ebe9f7a67",
      "to": "destination@msging.net",
      "type": "text/plain",
      "content": "Teste agendamento"
    },
    "when": "2016-07-25T17:50:00.000Z"
  }
}
```
Resposta em caso de sucesso:
```json
{ 
  "id": "1",
  "from": "postmaster@scheduler.msging.net/#irismsging1",
  "to": "contact@msging.net/default",
  "method": "set",
  "status": "success"
}
```

#### Delegação
Esta extensão já possui permissões de envio em nome dos contatos, portanto não é necessário a realização de delegação.
