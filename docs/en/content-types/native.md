### Conteúdo nativo
| MIME type                            | C#                                 |
|--------------------------------------|------------------------------------|
| application/json                     | [Lime.Protocol.JsonDocument](https://github.com/takenet/lime-csharp/blob/master/src/Lime.Protocol/JsonDocument.cs) |

Permite o envio de um conteúdo nativo de um canal, no formato JSON. Desta forma, é possível utilizar todos os recursos disponíveis em um canal mesmo que não haja mapeamento para um tipo canônico do BLiP.

Note que desta forma, no caso de um chatbot **multicanal**, a responsabilidade de enviar o tipo correto para cada canal é do bot.

#### Exemplos

1 - Enviando uma mensagem do tipo **[texto](https://developers.facebook.com/docs/messenger-platform/send-api-reference/)** do Messenger:
```json
{  
  "id":"1",
  "to":"949839515125748@messenger.gw.msging.net",
  "type":"application/json",
  "content":{  
    "text": "hello, world!"
  }
}
```  
2 - Enviando uma mensagem do tipo **[cartão de embarque](https://developers.facebook.com/docs/messenger-platform/send-api-reference/airline-boardingpass-template)** do Messenger:
```json
{  
  "id":"2",
  "to":"949839515125748@messenger.gw.msging.net",
  "type":"application/json",
  "content":{  
    "attachment":{  
      "type":"template",
      "payload":{  
        "template_type":"airline_boardingpass",
        "intro_message":"You are checked in.",
        "locale":"en_US",
        "boarding_pass":[  
          {  
            "passenger_name":"SMITH\/NICOLAS",
            "pnr_number":"CG4X7U",
            "travel_class":"business",
            "seat":"74J",
            "auxiliary_fields":[  
              {  
                "label":"Terminal",
                "value":"T1"
              },
              {  
                "label":"Departure",
                "value":"30OCT 19:05"
              }
            ],
            "secondary_fields":[  
              {  
                "label":"Boarding",
                "value":"18:30"
              },
              {  
                "label":"Gate",
                "value":"D57"
              },
              {  
                "label":"Seat",
                "value":"74J"
              },
              {  
                "label":"Sec.Nr.",
                "value":"003"
              }
            ],
            "logo_image_url":"https://www.example.com/en/logo.png",
            "header_image_url":"https://www.example.com/en/fb/header.png",
            "qr_code":"M1SMITH/NICOLAS  CG4X7U nawouehgawgnapwi3jfa0wfh",
            "above_bar_code_image_url":"https://www.example.com/en/PLAT.png",
            "flight_info":{  
              "flight_number":"KL0642",
              "departure_airport":{  
                "airport_code":"JFK",
                "city":"New York",
                "terminal":"T1",
                "gate":"D57"
              },
              "arrival_airport":{  
                "airport_code":"AMS",
                "city":"Amsterdam"
              },
              "flight_schedule":{  
                "departure_time":"2016-01-02T19:05",
                "arrival_time":"2016-01-05T17:30"
              }
            }
          },
          {  
            "passenger_name":"JONES/FARBOUND",
            "pnr_number":"CG4X7U",
            "travel_class":"business",
            "seat":"74K",
            "auxiliary_fields":[  
              {  
                "label":"Terminal",
                "value":"T1"
              },
              {  
                "label":"Departure",
                "value":"30OCT 19:05"
              }
            ],
            "secondary_fields":[  
              {  
                "label":"Boarding",
                "value":"18:30"
              },
              {  
                "label":"Gate",
                "value":"D57"
              },
              {  
                "label":"Seat",
                "value":"74K"
              },
              {  
                "label":"Sec.Nr.",
                "value":"004"
              }
            ],
            "logo_image_url":"https://www.example.com/en/logo.png",
            "header_image_url":"https://www.example.com/en/fb/header.png",
            "qr_code":"M1JONES/FARBOUND  CG4X7U nawouehgawgnapwi3jfa0wfh",
            "above_bar_code_image_url":"https://www.example.com/en/PLAT.png",
            "flight_info":{  
              "flight_number":"KL0642",
              "departure_airport":{  
                "airport_code":"JFK",
                "city":"New York",
                "terminal":"T1",
                "gate":"D57"
              },
              "arrival_airport":{  
                "airport_code":"AMS",
                "city":"Amsterdam"
              },
              "flight_schedule":{  
                "departure_time":"2016-01-02T19:05",
                "arrival_time":"2016-01-05T17:30"
              }
            }
          }
        ]
      }
    }
  }
}
```

### Mapeamento nos canais

| Canal              | Tipo                    | 
|--------------------|-------------------------|
| BLiP App           | Não suportado           |
| Messenger          | Suportado (o valor de `content` se refere ao elemento `message` da [Send API](https://developers.facebook.com/docs/messenger-platform/send-api-reference/) do Messenger |
| SMS                | Não suportado           |
| Skype              | Não suportado           |
| Telegram           | Não suportado           |
