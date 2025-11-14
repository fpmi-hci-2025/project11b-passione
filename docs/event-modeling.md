# Event Modeling (Passione)

### Event Modeling

![Event Modeling](https://www.plantuml.com/plantuml/svg/bLBDIiD06BplKoprt4EXYXNqaB-pKF6-RJRfqdIt95iBYg0HF8a5FNXG1D-WLAN5Ods5Rz_8JQ0sjOR4Go39zytixCn4NSRx92Gz77M8AuQC-zWZGKHHz3DfaNRN3yM0kwO8H8Y77IQpSujwP118Ht3PPASKr-e81TIJM0eSChyZiSj2sfPCSDJNNCIdk7BC8YP5MC5d2EDaIhWVfF_fS0_34xp3fxgju2t3i6p7M5yoHQz7kAltdbKCN-e2nZ21cOhL3OQf_lZGprI3pLrxnsoiW-qJogM6FYptC2moBFFaP0rr76UxOQ7pbMH3lr3kRaW-34MRHf6clDCCSvZ16upLjTOpogY1iIQrQcRTBjQJQ9df-uzK_AUIfYIUXuz8Aw0opy77rC4OnbaD2vWKMlgIWBILL-fo7-vJRpGC5kNjV5s2ikBHHhJLwa7fA57fp5FMKXcZabL86Kk7ZFxHXpojsVnHOK5IbgBKKN4lVkMHsmDKgYnvTrkLuni0)

<details><summary>PlantUML source</summary>

```plantuml
@startuml
skinparam shadowing false
skinparam backgroundColor white
skinparam DefaultFontSize 14

left to right direction
package "Visitor" {
  rectangle "View: Меню" #BBDEFB
  rectangle "Command: Отправить заказ" #C8E6C9
  rectangle "Event: Заказ отправлен" #FFF59D
}
package "Backend" {
  rectangle "Process: Валидация заказа" #D1C4E9
  rectangle "Event: Заказ принят" #FFF59D
}
package "Staff Tablet" {
  rectangle "View: Лента заказов" #BBDEFB
  rectangle "Command: Статус=Готово" #C8E6C9
  rectangle "Event: Заказ готов" #FFF59D
}

"View: Меню" --> "Command: Отправить заказ"
"Command: Отправить заказ" --> "Event: Заказ отправлен"
"Event: Заказ отправлен" --> "Process: Валидация заказа"
"Process: Валидация заказа" --> "Event: Заказ принят"
"Event: Заказ принят" --> "View: Лента заказов"
"View: Лента заказов" --> "Command: Статус=Готово"
"Command: Статус=Готово" --> "Event: Заказ готов"
@enduml

```

</details>

