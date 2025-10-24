# Passione — Спецификация (Lab 3)

### Usecase

![Usecase](https://www.plantuml.com/plantuml/svg/VL9DI-j05DtFhxXqfJnKgbL1H2n-BENnYbsv6PD9EvXE93D1K8IsFdWB7-h2XIjT-0TgKLgirhzmvnzv9uabTU4YoPapzvnpvqusjU6nILeXqqTI7VEOjq0tkH-TIDM0W8TQ57OEkNVKYAD4-LjH6CLmqfIckByj0fw4PZTIfYPF1PGhZ8KYC60YY6MZQS2NiV2CZ1JZdY67kjJIVRc6UaxL30y2HzHoekgtf794bJ6dvgeH2lZDjIOV0MSC8D72urh0_bRP5PRmmRPnR3luHk-kRGE15totLp3pPtzXPs-sD2LQp4ItECOdx64VXoJw3xGOsIjynZ5W7_2LlDeum24PNKmRB6K6z_PlMlFsPJ0WjrTw1WTgvbVgG7jPArtiKUKGXzzwgUG7eDAHlR3_g2orUYUYRo_nfU1gBwUrovdsZYhIaBmDsqdJkcJNAQYnDwrUoTIF-46DkIcCx7MM_UFmLZFP3SNrSEGYwLGKK4oYralidB4wpCrjk5kQeCK9McAr75KcQ9bLSxGoGQkCkO6lpwSNjmPIUM7Y2-PMALaka9j2-Uxl_WG)

<details><summary>PlantUML source</summary>

```plantuml
@startuml
skinparam shadowing false
skinparam backgroundColor white
skinparam DefaultFontSize 14

left to right direction
actor Visitor as V
actor Staff as S
actor Admin as A

rectangle Passione {
  usecase UC1 as "Просмотр меню (RU/EN)"
  usecase UC2 as "Добавить блюдо в корзину"
  usecase UC3 as "Оформить заказ\n(+ комментарии)"
  usecase UC4 as "Получать новые заказы"
  usecase UC5 as "Изменить статус заказа"
  usecase UC6 as "Управлять меню (RU/EN)"
  usecase UC7 as "Аналитика заказов"
}

V --> UC1
V --> UC2
V --> UC3
S --> UC4
S --> UC5
A --> UC6
A --> UC7

UC3 <. UC2 : include
UC2 <. UC1 : include
@enduml

```

</details>

### Activity Order

![Activity Order](https://www.plantuml.com/plantuml/svg/RP8nJy9G4CVtVefB9qXCZ8aJ7SGeZYIYRYvLMcWeBMbBI9ng6Hmm34JZfl4RGALfHU4ptFj6_j-3629ExNjtz_lTNLiD8pE8-brN2pkErpC3iqjXsspw0yThaMsweRKLkJ5lEwt0xtlD4z_r0ngqdMWxVchPPj-Dpdmlkd3kB3eur3Gbq2hypWkUyf8B4VEAKvwAH3pIUSD0x5Kal12n6Aax_kQCbs9CZQlzMjtG79jAF14Zdl5An8J7bnZpdAT7POhQbeSe3cMDgC9FOC_WIU5Hh9JWHHddN00wD92cWC_YVfs1C8nhPuAsOYGMEsW9dm2RoJ8k_Y_xlFPAElmPvuGcXt9aVOzqD21bSl1CByiMB2mMy2LuYSHRNjEnrGHlI9g3A5Knx9ivSWmb5vWRlrdgkDbZxVAOeFw0AL7hNP5uK0JPIrtkL8ql4kd_Qw_mYyJlV05aghx2oEzfLRpB7-K7)

<details><summary>PlantUML source</summary>

```plantuml
@startuml
skinparam shadowing false
skinparam backgroundColor white
skinparam DefaultFontSize 14

start
:Сканировать QR;
:Открыть меню RU/EN;
if (Выбор блюда?) then (да)
  :Добавить в корзину;
  if (Есть комментарии?) then (да)
    :Ввести комментарий\n("без лука", "острое");
  else (нет)
  endif
  :Подтвердить заказ;
  :Показать ETA ("готово через N минут");
else (нет)
  :Закрыть меню;
endif
stop
@enduml

```

</details>

### Activity Staff

![Activity Staff](https://www.plantuml.com/plantuml/svg/RL7FIiCm6B_dAJvsSWSFWgSMTA1u5do2QDirh4j6apBmD2lYOQ87xyhUe8XbjTezmvStyaiAeuSHGZxo-nioqORdffXdJC-4NF2Spq6dF59B8QUGy4p70-IMtysckIfaTA4obSCo5MQ8NyO9Bp9pfQIv4VSnd9movWDOS5teD03iS8TVTeq_W5kiiAMz3Lc07xR4rgxisfRs1V0NQ-neV1pGdD9HF-tAZLZJsVJqbYx-Q7aHLWx09cGYWIFSEBfz9eHIpyTWqbZIzJTMOmP0TbvRawut6_c0XZJUtY6ZaCKo4Wc5Rxm_5RCFS7os9tVspTESdUjLE_--MuSL5IJ14x5UmqCUxnHM-ZVjo4CRjM0J2dI_yWy)

<details><summary>PlantUML source</summary>

```plantuml
@startuml
skinparam shadowing false
skinparam backgroundColor white
skinparam DefaultFontSize 14

start
:Push: новый заказ;
:Открыть ленту заказов;
:Проверить комментарии;
if (Срочный?) then (да)
  :Пометить "Приоритет";
endif
:Статус -> "Принят";
:Передать на кухню;
:Статус -> "Готово";
stop
@enduml

```

</details>

### Class Core

![Class Core](https://www.plantuml.com/plantuml/svg/JL51JiCm4Bpx5QiSGQsen2b2LICdG4JK8D8YSJIncrfrR6GxgW3b02_Y0EB66z8VOIS5vJQpipEpbXV64csRMY2pu_A9Q5A3sHAgzbnMi272i97oICfTfLKZALP2QTXlkHthCTkGHjXB9Mt1NnZCpX4g1J46xhdXrZbU4S2fOSPm9LCQmdgTnduaYAn2AAnsjPuhJPc-viPvdaF87BZ8_MYEscDYJuSyFWegDIEMqSY643kmuZNhAosnZGa7Lz6JVblLDPFslxb5J3RrUAjlm7T9j4fyVeHnSZj0dEStwVBA8QV63tuIBN6IPKvjqT-3Wra0ama4PzFfIN0yEeJ3M_VJVNUVtKVtTNY7ELemIVql_08)

<details><summary>PlantUML source</summary>

```plantuml
@startuml
skinparam shadowing false
skinparam backgroundColor white
skinparam DefaultFontSize 14

class Visitor {
  +sessionId: UUID
  +lang: String
  +orderHistory: List<Order>
}
class Order {
  +id: UUID
  +createdAt: DateTime
  +status: OrderStatus
  +comment: String
}
enum OrderStatus {
  CREATED
  ACCEPTED
  COOKING
  READY
  CANCELLED
}
Visitor "1" -- "0..*" Order : создает >
@enduml

```

</details>

### Class Menu

![Class Menu](https://www.plantuml.com/plantuml/svg/PP31IiD048Rl-nH3ZfKM2ptbL30A7hnOyW2JPDiCdUoMtLaB5YzUlFLPYk15NsBpHcwgbA2tuVl_cVzdbbxGIUXO-IsP7JhimBVOs3sP3QoHlHuf5TRRZRF1D3UMhODzIpBM2xt6m79dZQpeMSDyeLJDw3qyQ1FWe02kgCcXBE-BOHOIreyXXvMub7T1j-Q2NduF5EJR_mSCTd_s1p9QJsJdgDPvwbPJXtmchHLREXwxy0c9iUBahApbb7kkdCqpc4oda5tFPfFifqKEyJr-ng_-sB_5K_peNzLIcsPuuZS)

<details><summary>PlantUML source</summary>

```plantuml
@startuml
skinparam shadowing false
skinparam backgroundColor white
skinparam DefaultFontSize 14

class Menu {
  +id: UUID
  +titleRu: String
  +titleEn: String
}
class Dish {
  +id: UUID
  +nameRu: String
  +nameEn: String
  +price: Decimal
  +photoUrl: String
  +available: bool
}
Menu "1" *-- "0..*" Dish : включает
@enduml

```

</details>

### Class Comment

![Class Comment](https://www.plantuml.com/plantuml/svg/JOyx2y9048Jx-nLBMZ4OiB8on6WJ7tXQMCcPsyJWFUHkWo_yxvv18TqtEpixxDIJSDHgnVobCLVXX0P_5jBU6bD39PJ7ddCIvQLsjZKoiyewk9qRwliph4IhQ6uDyUQ9a8mPAvNm7ZAhDHg25mCO4Dvf0fnSwEZquugJ_yek2FPcQ5hT7tN9rNgxJ8i0QL7asyKX4D-aooFVyqsUxK9ixIGwY988x708qIYE0_xEi2aQ-Ntr0m)

<details><summary>PlantUML source</summary>

```plantuml
@startuml
skinparam shadowing false
skinparam backgroundColor white
skinparam DefaultFontSize 14

class Comment {
  +text: String
  +type: CommentType
}
enum CommentType {
  NORMAL
  ALLERGY
  SPAM_SUSPECT
}
Order "1" o-- "0..1" Comment
@enduml

```

</details>

### Class Staff

![Class Staff](https://www.plantuml.com/plantuml/svg/JO_1Qi9048Rl-nH3ZehIG4yvYAMna5DAOkfvwcvqoMPNTZS450-c3z1NgOMUIliCkszar8DUXe_vvlzXfiQYjaqjYAcutA366imQgMgvN469mh0xyuxBQgLL8-cp4af3k-RstiUin4RO5oLjphSCmaT2bWADWTnYMSAE00mvZQ0ealZCMWaMNMNM8zaJ9flwjhWa5a_9V9Rra1Uli-mjoTEiFxms1c40en443-Fn881KKwOX0lVlZkwldz_krt-w7z-1F_ZEVVdEV_W3JCYKINh--WG)

<details><summary>PlantUML source</summary>

```plantuml
@startuml
skinparam shadowing false
skinparam backgroundColor white
skinparam DefaultFontSize 14

class Staff {
  +id: UUID
  +role: StaffRole
}
enum StaffRole {
  WAITER
  SUPERVISOR
}
Staff "1" -- "0..*" Order : обновляет статус >
@enduml

```

</details>

### Class Admin

![Class Admin](https://www.plantuml.com/plantuml/svg/JP11IWD154JtSufFja8Wu6eM4d4GNGI4CGVuJlzCFkdf3h-x4rG4ZGVmAeCW28fUeVj6pYGHPbTGhwgWfiwZ-D3epAtOh56m0RT4PRTiQbYWTZHmxh1QrMA3KHTMMu7jaltGBsY1GVjBQtp93mIJqoohD3e7vwfX0uyPm0ch7ERpwwBNr23h74eltLpsz0yRrFUUAtS8uAOkIJPSqIqtb4CH13rRqtjM58cx8RcoGNAOuRfhEOoD9YCOZyy6RJd4t_GSVz9B_8vjsdNwCxx7DdwatJ7K1sPaGiUcrptTTiHNUjipKpAg_-eF)

<details><summary>PlantUML source</summary>

```plantuml
@startuml
skinparam shadowing false
skinparam backgroundColor white
skinparam DefaultFontSize 14

class Admin {
  +id: UUID
  +email: String
}
class Analytics {
  +avgServiceTime: Duration
  +ordersPerHour: Map
}
Admin "1" ..> Analytics : просматривает
Admin ..> Menu : управляет
@enduml

```

</details>

### Seq Scan Order

![Seq Scan Order](https://www.plantuml.com/plantuml/svg/LP7FJi904CRl-nGJJXf3HEF90m4KZPB8tvJpGXVOKBPDkms99wX732UlwYiWqV17v1bctyXfGs8zR3OxtpVVRp9R23JtTJXoM32KokC-7q4muBOxbgeFFUu48gLqU7VOzzrGsLUku_em7aYTrgz5ZuUEld6LRif70MSNZF6k9gSb0ndVF02BaLdBhlIuqf2fDw0jEaNFoyHY-xzO8g1GDXHhTubS-YzNfEuEX88MxpX29uuAOnPayz26Iy0t4-7MJCpCHEOPweqixl0BVyoSjMDFYJotvHQSZeGAuSZXgd_CIf0zj2VL-sRr8PNuWdlym0KkSPraqkFRpF4Jzt02k2LrTs14k30JNEFcZrMhDWdc-hRmWvYJXmfLlJ0OKF8hzIxD33U0Am9iwQnImvpdSb2j4AJSAiQ9LBRYWTwfBV4IBXx8J1DoP9xCb1LeT_7V_W8)

<details><summary>PlantUML source</summary>

```plantuml
@startuml
skinparam shadowing false
skinparam backgroundColor white
skinparam DefaultFontSize 14

actor Visitor as V
participant "QR WebApp" as W
participant "Backend API" as B
participant "Kitchen Tablet" as K

V -> W : Открыть QR-меню
W -> B : GET /menu (lang)
B --> W : menu JSON
V -> W : Добавить блюдо + комментарий
W -> B : POST /orders
B -> K : push: Новый заказ
B --> W : 200 OK + ETA
W --> V : Показать статус
@enduml

```

</details>

### Seq Repeat

![Seq Repeat](https://www.plantuml.com/plantuml/svg/LT31IWCn40RWUvvYRjL3QHLF7gIBMqKyRA65FKztqpPqcon9bb9FfLTz1ds58jHAnVeAapSogMBNGo3vv-TZICTOrBQQ5SnCXInHumpC17Cr5t8C8omChqs6c4t7MbKolrQ5qZ2V25kVnto4LM5lbBHzyS3Xx88npAnlnZDXzGBGGCnyrufCb2Wjf7mOmlHV6FNkGXWn5aFp2bAu17fsAzgvfNjqA_S4zEMMz4uVjAStsj2dlszO6igHBzzs1z1IEkVQj0eqbaNG_7N2CmcJ8zsW5y-yUdyVq1z_IslQ-RDj7DbUqlzpuIHJvUAq9f-tsv3SXxOFuh1oO0y6hGzeTn2n3fTv-Erl)

<details><summary>PlantUML source</summary>

```plantuml
@startuml
skinparam shadowing false
skinparam backgroundColor white
skinparam DefaultFontSize 14

actor Dmitry as D
participant Web as W
participant API as A

D -> W : Открыть приложение
W -> A : GET /orders/last
A --> W : lastOrder
D -> W : 'Повторить заказ'
W -> A : POST /orders (copy)
A --> W : 200 OK
W --> D : Показать ETA
@enduml

```

</details>

### Seq Staff Flow

![Seq Staff Flow](https://www.plantuml.com/plantuml/svg/ZP2nJiCm48PtFyMz0AcGc2A1QYL1i4Ka2-CrSHghhXtPZYeneQxb5U0P40mL7V8CvpV26P2AM1Xk-VxlxgH_wJnQFsuLSnkf1xIu1TTZQtPIhw53vSHPii9cixPcr6rcbB6mwwK_ptFHuQZyhT6-aay2BgyOmyP7i_BOTO0EAXPLBniveFPGuqe9F_Fw5-Vb_GmvOnmkRg2658RHzIdGAqtq4Gxq1NIaTph5ERBgHwAtiATJU0w7i0ylVnGUbPBNsHqiZ6s5TOjKjX0hyAExvbbMb7MHioH9W3vfYgVYBveWWd_iFnGyVsHBeTkvpcy)

<details><summary>PlantUML source</summary>

```plantuml
@startuml
skinparam shadowing false
skinparam backgroundColor white
skinparam DefaultFontSize 14

actor Staff as S
participant Tablet as T
participant API as A

A -> T : push: Новый заказ
S -> T : Открыть заказ
S -> A : PATCH /orders/:id status=ACCEPTED
... готово ...
S -> A : PATCH /orders/:id status=READY
@enduml

```

</details>

### Seq Admin Menu

![Seq Admin Menu](https://www.plantuml.com/plantuml/svg/LP31IWCn48RlUOevAbAqrfC7wL8HUhAGxWECctGtD9kKP9Q2n-9HFFaWAXu4OPyXUIDdBKfx6kR_lfc1cKR2G5rhHLmRjy60BSG6bTyQLyCARTG7v06hTHryvzJCMnzWsnWwvBTwXPsbE-z8caSDuoiXi28s2zKQ1nYX4AoIgSm67UtZSZw0SdvC5hyfbwDOyZAizO3aH8W2HZSy2TUGNbEVtjDR-aXVUPUVWPll_98-KozOO4rEM5kKIyXFgS-x_tounE1UBk5ScTZe22Uj9eGpw88z5GCV_Psvl1Z3B6WahSHKEpLyxWS)

<details><summary>PlantUML source</summary>

```plantuml
@startuml
skinparam shadowing false
skinparam backgroundColor white
skinparam DefaultFontSize 14

actor Admin as A
participant AdminUI as UI
participant API as API
participant Storage as S3

A -> UI : Добавить блюдо
UI -> S3 : PUT фото
UI -> API : POST /dishes (meta + url)
API --> UI : 201 Created
@enduml

```

</details>

### Seq Error Offline

![Seq Error Offline](https://www.plantuml.com/plantuml/svg/RP7FQi904CRl-nHpinwqjlJKWnZw1qeF2egvzBAQLHVZhYHhBJrfIc--G-aRfA8ebSPNc7sZpWOBjfGGTlFDx_jcTbEB3O_CP1IoU2ZLc4Ty1F601tegLHzwF8p5KQN3kyD-f2SgkDAXZc0waEQuVYrwV1AQMwrCKpuBEBjWZ7SDaMqPIxVo6DgCO2ExSioL0LzqdEZ_4ht6dHCznjfGge8Fbu1lcE7A9hZ4jPtX2hSsiGl03QRuIU-6-L1w0e_GHhtPWbCT1IAAuGI_o920dRi5jqMcj16W7qK4FiM-OsPVAJ0bxcyau8wQkktEBgYUFQXyZBo8QKuNyCE-q3Yk1qKbkC_3bcHTEqk1bSlbGtSNlYHeJa-ITypeUqjeIie2Y7IdgFvtYhrZoPNPMP5vK3fSotcb0lLxvoAX_NDFnmFUj3nM4ofm__WR)

<details><summary>PlantUML source</summary>

```plantuml
@startuml
skinparam shadowing false
skinparam backgroundColor white
skinparam DefaultFontSize 14

actor Visitor as V
participant Web as W
participant API as A

V -> W : Подтвердить заказ
W -x A : POST /orders (нет сети)
note over W: Сохранить заказ локально\nПоказать 'будет отправлено'
... сеть восстановилась ...
W -> A : POST /orders (повтор)
A --> W : 200 OK
W --> V : Показать ETA
@enduml

```

</details>

### Components

![Components](https://www.plantuml.com/plantuml/svg/PPB1JkCm48RlVefHJwcqLGJTqnuGXO3eQXULkbBFqyHf8XAxnBQgSa9mW0CW7W09xHli0IG4TFSLd3TYaaXLKM_s_t_Z-SVshZPO69jdJ9-cSeO5vg0JZDGybLE8CTDYpPbWU3ejb9NHlifK0VCaDUj-86AqcJbKql3qNC3MTyP2bS-K5D90Qp3kWNSo1FVeNjool6-t03MGkWwvF-vVULbUb5VksItTgti3ppsvT_UNIcxSItdPb8rwUr_A7WZ_87pPSVyhbbgybxSrsWj-zu_NuTwW3zuXQaCB_rXeyvCtXzAUHMXmWbfGNgNDj13yv5Tj1byQ3aMKQehsLjwLDpvblgPi5zJrsRqsXmqFWZvdOQPi12rkL85J0Hxl-iFj1k1TTcQ5hJfPdVXZNgjZpbXrKvtEJfK7Vi3HQ3JWuEL2MbyLaIXqcz7ucqHZ-lIcnX9Jpxr9KUv4w6-04hE5ISEA9B_YWZt2QDwLKCz0MeXX8loPdMWxMPcyIqvEzu0hQLp1KfaqNW35Y6EsAsHK_QzF)

<details><summary>PlantUML source</summary>

```plantuml
@startuml
skinparam shadowing false
skinparam backgroundColor white
skinparam DefaultFontSize 14

component "PWA (QR Меню)" as PWA
component "Сотрудник (Планшет)" as TAB
component "Админ-панель" as ADMIN
component "API (FastAPI/NestJS)" as API
database "PostgreSQL" as DB
component "Redis (кэш/очереди)" as REDIS
cloud "Storage (S3/R2)" as S3
queue "Push/WS" as WS

PWA --> API : HTTPS (menu/orders)
TAB --> API : HTTPS (orders/status)
ADMIN --> API : HTTPS (dishes, analytics)
API --> DB : SQL
API --> REDIS : cache/pubsub
API --> S3 : media
API --> WS : notify staff
@enduml

```

</details>

### Packages

![Packages](https://www.plantuml.com/plantuml/svg/LP312i8m38RlVOhW0mY2PzdS42OUfaCyo0xHrgtOjQFD62Y-kzlOj3ib-VFb_qi3HsYfgHHpJwbhj5Y1Av6RLke27gYSy3Otl3yBQnhD8wECXRQKvEzZyS16qSveokHBm6hDMDtTO25W4IafD2tWpG2kwINC-nhoIkfpahFF7znsZT1y9CCq6SYzkRaP5YFXv6OS5LPanyE0dWINRkWoChQ3-xiX4fRBpMZvYvvfwJJxbfuyMdlABoBetjn_v1S)

<details><summary>PlantUML source</summary>

```plantuml
@startuml
skinparam shadowing false
skinparam backgroundColor white
skinparam DefaultFontSize 14

package "Client" {
  [PWA]
  [AdminUI]
}
package "Backend" {
  [API]
  [Jobs]
}
package "Data" {
  [PostgreSQL]
  [Redis]
  [Storage]
}
[PWA] ..> [API]
[AdminUI] ..> [API]
[API] ..> [PostgreSQL]
[API] ..> [Redis]
[API] ..> [Storage]
@enduml

```

</details>

### Deployment

![Deployment](https://www.plantuml.com/plantuml/svg/PP51IyGm58Jl-HMFtXSHFNcGtKqH1S582fvVsxTjt3GfIReBYl_Tf85Gz3QPRtWpaBqFwC8oQURFoipeS08_Oc-loWnmGkrfGrhipeEpY-cvrTR1TLHXosiwuQB3apL1gY-2stl6ZEq9AguLcH035zMHh-2R0MGYfpXW7gsX2j23IAh01bjDOGLP5Y9uZdFsKohiqcyl7-OP9BaBkJKQdmNLnosfZxwGj_QJkW0oM8T3dXIjMCBMPR3RFQPBy03FJICaoxF-sZSVaWd-Bvnqyc9XzEJxQt5YHtBku21Us9vCdxxa5m)

<details><summary>PlantUML source</summary>

```plantuml
@startuml
skinparam shadowing false
skinparam backgroundColor white
skinparam DefaultFontSize 14

node "Client Devices" {
  node "Smartphone" as Phone
  node "Tablet" as Tablet
  node "PC" as PC
}
node "Cloud" {
  node "App Server" as App
  node "DB Server" as DBs
  node "Object Storage" as Obj
}

Phone --> App : HTTPS
Tablet --> App : HTTPS/WS
PC --> App : HTTPS
App --> DBs : SQL
App --> Obj : S3 API
@enduml

```

</details>

### Erd

![Erd](https://www.plantuml.com/plantuml/svg/RP9HJy8m58NVzojkzgJ44J4-xGbbc3GHPXmGtfRBMbX3rsBRIHJyxtQRkX7tqgJVxJtdt9kEZKLjoq9uPi_b0JKMO7AawiZb3hOe3EjKDfZjTrgLaawKK1gEERVTUiIsM0hxfAHD-2U3qRtdCMcv_G1_nGstIYVC6Awa3sXWbS390nYOXgMSGWZB9OaS309t27GXGbXCrmllgvMAkCbhWQZfx_P9B5Ygoz-k7y1a2mwQPynTvylPz9LChaQtDtVN5S-LLMcfHViKtv4Bt8Zg-MCSFtT3n9eoNQU8_wV8D4FBQ8gs4YEpQR9ucBsuWbktBKthq3Twfeh2kVGCNdiIouh6bpJ6gg8N2WFgDdH1tbnx26HUoxczdyz1e4ukUWZ-Q3WS-5xynqWBepuuPf9MF-OR)

<details><summary>PlantUML source</summary>

```plantuml
@startuml
skinparam shadowing false
skinparam backgroundColor white
skinparam DefaultFontSize 14

entity "VisitorSession" as VS {
  *session_id : UUID
  --
  lang : TEXT
}

entity "Dish" as D {
  *id : UUID
  name_ru : TEXT
  name_en : TEXT
  price : NUMERIC(10,2)
  photo_url : TEXT
  available : BOOL
}

entity "Order" as O {
  *id : UUID
  created_at : TIMESTAMP
  status : TEXT
  session_id : UUID
  comment : TEXT
}

entity "OrderItem" as OI {
  *order_id : UUID
  *dish_id : UUID
  qty : INT
}

VS ||--o{ O : "1..*"
O ||--o{ OI : "1..*"
D ||--o{ OI : "1..*"
@enduml

```

</details>

### Orm

![Orm](https://www.plantuml.com/plantuml/svg/NL5DQyCm3BtxLuWU1oqKTWgZTAmR10Q3PTtTYzL4r1-ThL2siVy-EIb9relHUvAUzEHjOXsvSrQb8_cJZjf1QhK9P_8D7BHDECjywFhOnD1vyn1iY71kYUVv7HvqP_afUAxe6s5zgrHjTKhm4Wr6-540P0hOxykTX7L4pMZkkO2T16_aK5ZPYBjK32rL3pABAL7m1RnJ8Wwn6d0MP7HI_ao9x_gUKeXDbW_EeHVnYgEuKR_pNN9Hlq_8w39DeA7KoZho2lZahmB8yzYQ-MiNNZjyxSOf0_7ePyGfKeqYYZKvRKUn_qvwsOlBSbAtsZSp1yCTbyiDBDQhrSrYCgCcMpdTEvYghwwsHM_of_y1)

<details><summary>PlantUML source</summary>

```plantuml
@startuml
skinparam shadowing false
skinparam backgroundColor white
skinparam DefaultFontSize 14

class Order {
  id: UUID
  createdAt: DateTime
  status: OrderStatus
  session: VisitorSession
  items: List<OrderItem>
  comment: String
}
class OrderItem {
  order: Order
  dish: Dish
  qty: int
}
class Dish {
  id: UUID
  nameRu: String
  nameEn: String
  price: Decimal
}
class VisitorSession {
  sessionId: UUID
  lang: String
}
Order --> "1..*" OrderItem
OrderItem --> Dish
Order --> VisitorSession
@enduml

```

</details>



## Сценарии для диаграммы вариантов использования

### Сценарий A: «Кастомизация десерта»
1) Гость сканирует QR, открывает **Меню (RU/EN)**.  
2) Выбирает блюдо, нажимает **Добавить в корзину**.  
3) Вводит комментарий: _«без лука, соус отдельно»_.  
4) Подтверждает заказ, получает ETA.  
5) Если пропала сеть — заказ сохраняется локально и отправляется при восстановлении.

### Сценарий B: «Повторить предыдущий»
1) Гость открывает приложение и видит кнопку **Повторить прошлый заказ**.  
2) Система подтягивает состав последнего заказа и создаёт новый.  
3) Гость подтверждает. Система показывает ETA.

### Сценарий C: «Работа сотрудника в час-пик»
1) На планшет падает push «Новый заказ».  
2) Сотрудник открывает карточку, видит метки аллергенов/комментарий.  
3) Ставит **Принят** → **Готово**.  
4) Приоритетные заказы помечаются цветом.

### Сценарий D: «Редактирование меню администратором»
1) Администратор загружает фото блюда, сохраняет карточку RU/EN.  
2) Цена и доступность обновляются, изменения сразу видны в QR-меню.

### Сценарий E: «Отчёт Product Owner»
1) Открывает раздел аналитики, сравнивает время обслуживания «до/после».  
2) Экспортирует CSV/PDF для презентации.
