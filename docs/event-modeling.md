# Event Modeling (Passione)

### Event Modeling

![Event Modeling](https://www.plantuml.com/plantuml/svg/bLJDIiD06BplKoprt4D1nGfAoTzPg7ZVDfjsQR8hoTQ28cW4Js913nuKmJS8LMcnM5_Xonkv2HItrf1u22JvlfbCPYPfHPA4SXZuA1emVan24k2eJrmnOho7FU97L9jqI7VG2yMGkwRmHOX7VIRrkKKzClIb8xXiirEA6vi8-TIJM0eSibvVOfU5j2kPu4WX9ClESEs8HKoAi8RF4CRPdF2UJxFxTBIBuGdUuJEzhU4Dmx1inrXTCaKG4EwglUSqXg_q0XAOm2oDqniCKtNneOwf0fixzhRPN0NR9vHB1NrOxc5OQ2ppxCaAwZZELjD2vxfeGtb1kRic-Y0KNHf5YlHESSnX1c-GfDTAqLZJ0ucYjHhcfbskA5CpKmwCqxX0IriIpyE7fEDJMUJYO-vY38ckOW6JKbjVCf2oyogzt8Fxt1y5WqLrIr-N85q-MektNj-l72Ugd7lEMYbdLB4EEMFbcD4_6b6aLM_0dofNAfApbAMEodlnAu_27g1APIbwjvzoe9Rwdh9VqJS)

<details><summary>PlantUML source</summary>

```plantuml
@startuml
skinparam shadowing false
skinparam backgroundColor white
skinparam DefaultFontSize 14

left to right direction
partition "Visitor" {
  rectangle "View: Меню" #BBDEFB
  rectangle "Command: Отправить заказ" #C8E6C9
  rectangle "Event: Заказ отправлен" #FFF59D
}
partition "Backend" {
  rectangle "Process: Валидация заказа" #D1C4E9
  rectangle "Event: Заказ принят" #FFF59D
}
partition "Staff Tablet" {
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

