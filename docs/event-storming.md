# EventStorming (Passione)

### Es Big Picture

![Es Big Picture](https://www.plantuml.com/plantuml/svg/hPFFIWCn4CRlUOgXdWl-GzI355kz2Q9FaDrajw7PHBAfHKMerQFWqOC73xv0QPKMjNs6v8sSM6nNJrtmaCjCVjzy-ORKSakDRMUIv2sXpgYX6UHDodH7g1GIAdDUw4GqRgL6jnMhQwaDT9h25liDdj2sj8TQsLDnoM5jan394mjMWn5fqm8JXiTMQ5MWGeMgL7Au8W3xsZ1kPlgHn86XzcVkIf8av9eim4f3PrGeE3Zdokw2UtHzzuvd16xgx_1qtQVxS6zkKWamZpQY8dsifOWla7jn0xpqwgPuVUnx_Xxy3T8zt_MtM9wuSP15ZIXYFFcbKTTPHXL3aMUSDdOJ__0ju4O_NX2Bj_bMl5F4JZXbSAGPbqW-1OU-v_e52hqCPgPNe_NbdZmCbXTSU2nPobyLzwwgUsNY96MYd-kN3PoKNz5yrd89_rj0Y_19ZIiMljON)

<details><summary>PlantUML source</summary>

```plantuml
@startuml
skinparam shadowing false
skinparam backgroundColor white
skinparam DefaultFontSize 14

left to right direction
skinparam rectangle {
  BorderColor black
  BackgroundColor #fff
}
rectangle "Domain Event: Заказ оформлен" #ffeb3b
rectangle "Policy: Уведомить сотрудника" #bbdefb
rectangle "Command: Принять заказ" #c8e6c9
rectangle "Read Model: Лента заказов" #ffe0b2
rectangle "Domain Event: Заказ готов" #ffeb3b

"Command: Принять заказ" -down-> "Domain Event: Заказ оформлен"
"Domain Event: Заказ оформлен" -down-> "Policy: Уведомить сотрудника"
"Policy: Уведомить сотрудника" -down-> "Read Model: Лента заказов"
"Command: Принять заказ" -down-> "Domain Event: Заказ готов"
@enduml

```

</details>

### Es Process

![Es Process](https://www.plantuml.com/plantuml/svg/bPJFJi8m7CVlVOe6pnnCr8W7GpBONNs2oifes5gp5KaymJngC9vCFE0h86f4_enN-FMDx2Pc0m7BOUkX_Nn_t_JxtSgX985i-HuAcunVaO3uE6mGHxGPTt6TU27DxLoIMjCDH8ixbl14WDiD9lFx5LedBK_QWiiBTaFn_W527grBB0KEcDkGs641hKacE4fMmbsFuaBrcd9vWi_EYp253vYf7ePOHJ1M7NMdrxY0zspRFYnLrb3m21FLWtU8SVA2LnZ042Q9pZ_WipuzNKoCOA0wC8AlFo9R9PxqkR5-FdyCpxN6pk0y7JnJ3oeoHTxIQJ4CCo1FMCBt2NSqqy-P6gb8tMFu_9NHh7LSFR9Awz6NpDOkM5_VtIonjfYdkkdTHkfMTJCKcMHUB9uQfemCox2aQ1W_shalwHJ3391nM4lUj_OE6TPpnUV6m95HApRvozTxhREb_g_UtROs8UFQRVAMVKUeJBcJ_0Q_0G)

<details><summary>PlantUML source</summary>

```plantuml
@startuml
skinparam shadowing false
skinparam backgroundColor white
skinparam DefaultFontSize 14

left to right direction
rectangle "Event: QR-меню открыто" #FFF59D
rectangle "Event: Блюдо добавлено" #FFF59D
rectangle "Event: Комментарий добавлен" #FFF59D
rectangle "Event: Заказ отправлен" #FFF59D
rectangle "Event: Заказ принят" #FFF59D
rectangle "Event: Заказ готов" #FFF59D

rectangle "Command: Отправить заказ" #C8E6C9
rectangle "Command: Принять заказ" #C8E6C9
rectangle "Command: Обновить статус" #C8E6C9

"Event: QR-меню открыто" --> "Event: Блюдо добавлено"
"Event: Блюдо добавлено" --> "Event: Комментарий добавлен"
"Event: Комментарий добавлен" --> "Command: Отправить заказ"
"Command: Отправить заказ" --> "Event: Заказ отправлен"
"Event: Заказ отправлен" --> "Command: Принять заказ"
"Command: Принять заказ" --> "Event: Заказ принят"
"Event: Заказ принят" --> "Command: Обновить статус"
"Command: Обновить статус" --> "Event: Заказ готов"
@enduml

```

</details>

### Es Design

![Es Design](https://www.plantuml.com/plantuml/svg/ZLBBJW914BpFLtJmJ2B65nmCxh9xCKQZNp3k3Ck6tHaoEuYFc21uyE3TWmVZ7n0VmQ3m3JD_PAzH0X5r3vrCqbLTrTLJJJLLkft496r6eaKLJI1jK2OxaGYXJkEKptIEQD0CbMmBvifOAkWq8ZtRh_4wRSVQbq8VHcSSIgk4j913Gmu59-Dn1Yvs-Ockm9vYNA5C0Su9WEA1fYAC4RaTXeg7LFClJ06Ml9BZUHlpC5Sc2HMi0kR1JCpGF9k1xTaRmEV0ZB26I7GtlNMtF4_qZhb0VNFxZGCpiLTONVDktioB6IFHz_srSerS_B70JgI31XS__E_BE0fEKU3Uzkqrs4iStRDTsqUBO_DgHhQF0evJytndddd0AODToNYCxBlCYUsPmQSRRzbP-NUDfqm9mtYSNI1NK4KykIXkBGYVBBZ759qZIf8hx-d4FE6HV15FP_uIAwbomRA__m4)

<details><summary>PlantUML source</summary>

```plantuml
@startuml
skinparam shadowing false
skinparam backgroundColor white
skinparam DefaultFontSize 14

package "Bounded Context: Ordering" {
  rectangle "Aggregate: Order" #E1BEE7
  rectangle "Command: Создать заказ" #C8E6C9
  rectangle "Event: Заказ оформлен" #FFF59D
}
package "Bounded Context: Kitchen" {
  rectangle "Policy: Пуш сотруднику" #BBDEFB
  rectangle "Read Model: Лента" #FFE0B2
  rectangle "Event: Заказ готов" #FFF59D
}
"Command: Создать заказ" -down-> "Aggregate: Order"
"Aggregate: Order" -down-> "Event: Заказ оформлен"
"Event: Заказ оформлен" -down-> "Policy: Пуш сотруднику"
"Policy: Пуш сотруднику" -down-> "Read Model: Лента"
@enduml

```

</details>

