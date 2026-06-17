# Protocol Documentation
<a name="top"></a>

## Table of Contents

- [artists.proto](#artists-proto)
    - [Artist](#v3-Artist)
    - [ArtistsRequest](#v3-ArtistsRequest)
  
- [events.proto](#events-proto)
    - [Event](#v3-Event)
    - [Event.Deal](#v3-Event-Deal)
    - [Event.LegalRu](#v3-Event-LegalRu)
    - [Event.TicketSet](#v3-Event-TicketSet)
    - [Event.TicketSet.Rule](#v3-Event-TicketSet-Rule)
    - [Event.TicketSet.Rule.SimpleType](#v3-Event-TicketSet-Rule-SimpleType)
    - [EventsRequest](#v3-EventsRequest)
  
    - [Event.EventStatus](#v3-Event-EventStatus)
    - [Event.LegalRu.IPTaxes](#v3-Event-LegalRu-IPTaxes)
    - [Event.LegalRu.LTDTaxes](#v3-Event-LegalRu-LTDTaxes)
    - [Event.LegalRu.Type](#v3-Event-LegalRu-Type)
    - [Event.LegalRu.VAT](#v3-Event-LegalRu-VAT)
    - [Event.SmartTicketSetting](#v3-Event-SmartTicketSetting)
    - [Event.TicketSet.Rule.Type](#v3-Event-TicketSet-Rule-Type)
    - [EventsRequest.Status](#v3-EventsRequest-Status)
  
- [generic.proto](#generic-proto)
    - [Coordinates](#v3-Coordinates)
    - [Lifetime](#v3-Lifetime)
    - [LiftimeFilter](#v3-LiftimeFilter)
    - [Media](#v3-Media)
    - [Percentage](#v3-Percentage)
    - [TimestampFilter](#v3-TimestampFilter)
  
- [geo.proto](#geo-proto)
    - [CitiesRequest](#v3-CitiesRequest)
    - [City](#v3-City)
    - [CountriesRequest](#v3-CountriesRequest)
    - [Country](#v3-Country)
  
- [meta_events.proto](#meta_events-proto)
    - [MetaEvent](#v3-MetaEvent)
    - [MetaEventsRequest](#v3-MetaEventsRequest)
  
- [mods.proto](#mods-proto)
    - [Mod](#v3-Mod)
    - [ModPromotionType](#v3-ModPromotionType)
    - [ModPromotionType.LevelsCountFix](#v3-ModPromotionType-LevelsCountFix)
    - [ModPromotionType.LevelsCountFix.Level](#v3-ModPromotionType-LevelsCountFix-Level)
    - [ModPromotionType.LevelsCountPercentage](#v3-ModPromotionType-LevelsCountPercentage)
    - [ModPromotionType.LevelsCountPercentage.Level](#v3-ModPromotionType-LevelsCountPercentage-Level)
    - [ModPromotionType.LevelsFix](#v3-ModPromotionType-LevelsFix)
    - [ModPromotionType.LevelsFix.Level](#v3-ModPromotionType-LevelsFix-Level)
    - [ModPromotionType.LevelsPercentage](#v3-ModPromotionType-LevelsPercentage)
    - [ModPromotionType.LevelsPercentage.Level](#v3-ModPromotionType-LevelsPercentage-Level)
  
    - [Mod.ModType](#v3-Mod-ModType)
  
- [seats.proto](#seats-proto)
    - [Seat](#v3-Seat)
    - [SeatsRequest](#v3-SeatsRequest)
  
    - [Seat.TicketStatus](#v3-Seat-TicketStatus)
    - [SeatsRequest.Status](#v3-SeatsRequest-Status)
  
- [service.proto](#service-proto)
    - [Simple](#v3-Simple)
  
- [tags.proto](#tags-proto)
    - [CategoriesRequest](#v3-CategoriesRequest)
    - [Category](#v3-Category)
    - [Tag](#v3-Tag)
    - [TagsRequest](#v3-TagsRequest)
  
- [venues.proto](#venues-proto)
    - [Map](#v3-Map)
    - [Map.Seat](#v3-Map-Seat)
    - [Map.Seat.Point](#v3-Map-Seat-Point)
    - [Map.Sector](#v3-Map-Sector)
    - [Map.SvgEntry](#v3-Map-SvgEntry)
    - [MapsRequest](#v3-MapsRequest)
    - [Venue](#v3-Venue)
    - [VenuesRequest](#v3-VenuesRequest)
  
- [Scalar Value Types](#scalar-value-types)



<a name="artists-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## artists.proto



<a name="v3-Artist"></a>

### Artist



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | id артиста |
| name | [string](#string) |  | название артиста |






<a name="v3-ArtistsRequest"></a>

### ArtistsRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ids | [string](#string) | repeated | фильтр по id артиста |





 

 

 

 



<a name="events-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## events.proto



<a name="v3-Event"></a>

### Event



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | id мероприятия |
| meta | [string](#string) |  | [O] id группы мероприятий (отсутствует, если мероприятие одиночное) |
| name | [string](#string) |  | название мероприятия |
| description | [string](#string) |  | [O] описание мероприятия |
| status | [Event.EventStatus](#v3-Event-EventStatus) |  | статус мероприятия |
| org | [string](#string) |  | id организатора |
| venue | [string](#string) |  | id площадки |
| map | [string](#string) |  | [O] id схемы зала |
| lifetime | [Lifetime](#v3-Lifetime) |  | дата и время начала и конца мероприятия |
| category | [string](#string) |  | id категории мероприятия |
| tags | [string](#string) | repeated | id жанров мероприятия |
| artists | [string](#string) | repeated | id артистов мероприятия |
| age_rating | [string](#string) |  | [O] возрастной рейтинг мероприятия |
| media | [Media](#v3-Media) |  | обложки |
| open_date | [bool](#bool) |  | признак мероприятия с открытой датой начала |
| deal | [Event.Deal](#v3-Event-Deal) |  | [O] сделка, если мероприятие запрашивает распространитель |
| org_extra | [Percentage](#v3-Percentage) |  | [O] % сервисного сбора организатора, если мероприятие запрашивает организатор |
| legal_ru | [Event.LegalRu](#v3-Event-LegalRu) |  | [O] реквизиты продавца мероприятия |
| sets | [Event.TicketSet](#v3-Event-TicketSet) | repeated | категории билетов |
| tickets_amount | [uint32](#uint32) |  | количество всего билетов в мероприятии |
| tickets_amount_vacant | [uint32](#uint32) |  | количество свободных к продаже билетов в мероприятии |
| smart_tickets | [Event.SmartTicketSetting](#v3-Event-SmartTicketSetting) |  | настройки смарт-билетов |
| mods | [Mod](#v3-Mod) | repeated | дополнительная информация по скидкам на мероприятие |
| additional | [google.protobuf.Any](#google-protobuf-Any) |  | служебное поле |






<a name="v3-Event-Deal"></a>

### Event.Deal



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | id сделки |
| org | [Percentage](#v3-Percentage) |  | % организатора |
| agent | [Percentage](#v3-Percentage) |  | % распространителя снизу от номинала билета |
| extra | [Percentage](#v3-Percentage) |  | % распространителя сверху от номинала билета |






<a name="v3-Event-LegalRu"></a>

### Event.LegalRu



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | id реквизитов |
| type | [Event.LegalRu.Type](#v3-Event-LegalRu-Type) |  | типа юр. лица |
| name | [string](#string) |  | название юр. лица |
| inn | [string](#string) |  | ИНН |
| address | [string](#string) |  | юридический адрес |
| ogrn | [string](#string) |  | ОГРН |
| ogrnip | [string](#string) |  | ОРГНИП |
| ltd | [Event.LegalRu.LTDTaxes](#v3-Event-LegalRu-LTDTaxes) |  |  |
| ip | [Event.LegalRu.IPTaxes](#v3-Event-LegalRu-IPTaxes) |  |  |
| nds | [bool](#bool) | optional |  |
| vat_rate | [Event.LegalRu.VAT](#v3-Event-LegalRu-VAT) | optional |  |






<a name="v3-Event-TicketSet"></a>

### Event.TicketSet



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | id категории |
| name | [string](#string) |  | название категории |
| description | [string](#string) |  | [O] описание категории |
| pos | [int32](#int32) |  | порядковый номер категории |
| sector | [string](#string) |  | [O] id сектора |
| with_seats | [bool](#bool) |  | признак категории с рассадкой |
| amount | [uint32](#uint32) |  | количество всего билетов в категории |
| amount_vacant | [uint32](#uint32) |  | количество свободных к продаже билетов в категории |
| rules | [Event.TicketSet.Rule](#v3-Event-TicketSet-Rule) | repeated | правила изменения цен на категорию |






<a name="v3-Event-TicketSet-Rule"></a>

### Event.TicketSet.Rule



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | id правила продажи категории |
| type | [Event.TicketSet.Rule.Type](#v3-Event-TicketSet-Rule-Type) |  | тип правила продажи категории |
| lifetime | [Lifetime](#v3-Lifetime) |  |  |
| simple | [Event.TicketSet.Rule.SimpleType](#v3-Event-TicketSet-Rule-SimpleType) |  |  |






<a name="v3-Event-TicketSet-Rule-SimpleType"></a>

### Event.TicketSet.Rule.SimpleType



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| price | [uint64](#uint64) |  | цена правила продажи категории |






<a name="v3-EventsRequest"></a>

### EventsRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ids | [string](#string) | repeated | фильтр по id мероприятий |
| meta | [string](#string) |  | фильтр по id конкретных групп мероприятий |
| without_meta | [bool](#bool) |  | фильтр для получения только одиночных мероприятий, не объединенных ни в какие группы |
| org | [string](#string) |  | фильтр по id организаторов мероприятий |
| status | [EventsRequest.Status](#v3-EventsRequest-Status) |  | фильтр по статусу мероприятий |
| lifetime | [LiftimeFilter](#v3-LiftimeFilter) |  |  |





 


<a name="v3-Event-EventStatus"></a>

### Event.EventStatus


| Name | Number | Description |
| ---- | ------ | ----------- |
| STAND_BY | 0 | продажи остановлены |
| PUBLIC | 1 | продажи активны |



<a name="v3-Event-LegalRu-IPTaxes"></a>

### Event.LegalRu.IPTaxes


| Name | Number | Description |
| ---- | ------ | ----------- |
| IP_USN | 0 |  |
| IP_OSN | 1 |  |
| IP_NPD | 2 |  |
| IP_PSN | 3 |  |



<a name="v3-Event-LegalRu-LTDTaxes"></a>

### Event.LegalRu.LTDTaxes


| Name | Number | Description |
| ---- | ------ | ----------- |
| LTD_USN | 0 |  |
| LTD_OSN | 1 |  |



<a name="v3-Event-LegalRu-Type"></a>

### Event.LegalRu.Type


| Name | Number | Description |
| ---- | ------ | ----------- |
| LTD | 0 | ООО |
| IP | 1 | ИП |
| SE | 2 | Самозанятый |



<a name="v3-Event-LegalRu-VAT"></a>

### Event.LegalRu.VAT


| Name | Number | Description |
| ---- | ------ | ----------- |
| VAT_0 | 0 |  |
| VAT_5 | 1 |  |
| VAT_7 | 2 |  |
| VAT_20 | 3 |  |
| VAT_22 | 4 |  |



<a name="v3-Event-SmartTicketSetting"></a>

### Event.SmartTicketSetting


| Name | Number | Description |
| ---- | ------ | ----------- |
| NONE | 0 | смарт-билеты не используются на мероприятии |
| ONLY | 1 | на мероприятие возможна продажа только смарт-билетов |
| ANY | 2 | на мероприятие можно продавать и электронные билеты и смарт-билеты |



<a name="v3-Event-TicketSet-Rule-Type"></a>

### Event.TicketSet.Rule.Type


| Name | Number | Description |
| ---- | ------ | ----------- |
| SIMPLE | 0 | простой тип правила, правила продажи сменяют друг друга с течением времени |



<a name="v3-EventsRequest-Status"></a>

### EventsRequest.Status


| Name | Number | Description |
| ---- | ------ | ----------- |
| ANY | 0 | без фильтрации по состоянию |
| STAND_BY | 1 | продажи остановлены |
| PUBLIC | 2 | продажи активны |


 

 

 



<a name="generic-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## generic.proto



<a name="v3-Coordinates"></a>

### Coordinates



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| longitude | [double](#double) |  |  |
| latitude | [double](#double) |  |  |






<a name="v3-Lifetime"></a>

### Lifetime



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| start | [google.protobuf.Timestamp](#google-protobuf-Timestamp) |  |  |
| finish | [google.protobuf.Timestamp](#google-protobuf-Timestamp) |  |  |






<a name="v3-LiftimeFilter"></a>

### LiftimeFilter



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| start | [TimestampFilter](#v3-TimestampFilter) |  |  |
| finish | [TimestampFilter](#v3-TimestampFilter) |  |  |






<a name="v3-Media"></a>

### Media



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| cover | [string](#string) |  | [O] |
| cover_small | [string](#string) |  | [O] |
| cover_original | [string](#string) |  | [O] |






<a name="v3-Percentage"></a>

### Percentage



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| units | [int32](#int32) |  | Whole units part of the amount |
| nanos | [fixed32](#fixed32) |  | Nano units of the amount (10^-9) Must be same sign as units |






<a name="v3-TimestampFilter"></a>

### TimestampFilter



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| gte | [google.protobuf.Timestamp](#google-protobuf-Timestamp) |  |  |
| gt | [google.protobuf.Timestamp](#google-protobuf-Timestamp) |  |  |
| lte | [google.protobuf.Timestamp](#google-protobuf-Timestamp) |  |  |
| lt | [google.protobuf.Timestamp](#google-protobuf-Timestamp) |  |  |





 

 

 

 



<a name="geo-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## geo.proto



<a name="v3-CitiesRequest"></a>

### CitiesRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ids | [int32](#int32) | repeated | фильтр по id гороода |
| name | [string](#string) |  | фильтр по названию города |
| suggest | [string](#string) |  | фильтр по части названия города |
| country | [string](#string) |  | фильтр по стране |






<a name="v3-City"></a>

### City



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [int32](#int32) |  | id города |
| name | [string](#string) |  | название города |
| country | [string](#string) |  | id страны |
| timezone | [string](#string) |  | таймзона города |
| coordinates | [Coordinates](#v3-Coordinates) |  | координаты города |
| population | [int64](#int64) |  | численность населения города |






<a name="v3-CountriesRequest"></a>

### CountriesRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ids | [string](#string) | repeated | фильтр по id страны |






<a name="v3-Country"></a>

### Country



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | id страны |
| name | [string](#string) |  | название страны |
| currency | [string](#string) |  | валюта страны |
| iso | [string](#string) |  | код страны по ISO 3166-1 |
| iso3 | [string](#string) |  | код страны по ISO 3166-3 |
| iso_numeric | [uint32](#uint32) |  | код страны по ISO 3166-1 numeric |





 

 

 

 



<a name="meta_events-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## meta_events.proto



<a name="v3-MetaEvent"></a>

### MetaEvent



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | id группы мероприятий |
| name | [string](#string) |  | название группы мероприятий |
| description | [string](#string) |  | [O] описание группы мероприятий |
| org | [string](#string) |  | id организатора |
| age_rating | [string](#string) |  | [O] возвратной рейтинг мероприятия |
| media | [Media](#v3-Media) |  | обложка группы мероприятий |
| first_start | [google.protobuf.Timestamp](#google-protobuf-Timestamp) |  | начало первого мероприятия в группе |
| last_finish | [google.protobuf.Timestamp](#google-protobuf-Timestamp) |  | конец последнего мероприятия в группе |
| additional | [google.protobuf.Any](#google-protobuf-Any) |  | служебное поле |






<a name="v3-MetaEventsRequest"></a>

### MetaEventsRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ids | [string](#string) | repeated | фильтр по id группы мероприятий |





 

 

 

 



<a name="mods-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## mods.proto



<a name="v3-Mod"></a>

### Mod



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  |  |
| type | [Mod.ModType](#v3-Mod-ModType) |  | тип модификатора |
| promotion | [ModPromotionType](#v3-ModPromotionType) |  | промоакции |






<a name="v3-ModPromotionType"></a>

### ModPromotionType



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| lifetime | [Lifetime](#v3-Lifetime) |  | время действия промоакции |
| sets | [string](#string) | repeated | список категорий билетов, к которым применяется промоакция |
| discount_percentage | [Percentage](#v3-Percentage) |  | процент скидки |
| discount_fix | [uint64](#uint64) |  | фиксированная скидка |
| levels_percentage | [ModPromotionType.LevelsPercentage](#v3-ModPromotionType-LevelsPercentage) |  | &#34;лесенка&#34; процентов |
| levels_fix | [ModPromotionType.LevelsFix](#v3-ModPromotionType-LevelsFix) |  | &#34;лесенка&#34; фиксированных значений |
| levels_count_percentage | [ModPromotionType.LevelsCountPercentage](#v3-ModPromotionType-LevelsCountPercentage) |  | &#34;лесенка&#34; процентов по билетам |
| levels_count_fix | [ModPromotionType.LevelsCountFix](#v3-ModPromotionType-LevelsCountFix) |  | &#34;лесенка&#34; фиксированных значений по билетам |






<a name="v3-ModPromotionType-LevelsCountFix"></a>

### ModPromotionType.LevelsCountFix



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| levels | [ModPromotionType.LevelsCountFix.Level](#v3-ModPromotionType-LevelsCountFix-Level) | repeated |  |






<a name="v3-ModPromotionType-LevelsCountFix-Level"></a>

### ModPromotionType.LevelsCountFix.Level



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| level | [uint64](#uint64) |  | количество билетов в заказе с которого применяется скидка |
| value | [uint64](#uint64) |  | фиксированная скидка |






<a name="v3-ModPromotionType-LevelsCountPercentage"></a>

### ModPromotionType.LevelsCountPercentage



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| levels | [ModPromotionType.LevelsCountPercentage.Level](#v3-ModPromotionType-LevelsCountPercentage-Level) | repeated |  |






<a name="v3-ModPromotionType-LevelsCountPercentage-Level"></a>

### ModPromotionType.LevelsCountPercentage.Level



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| level | [uint64](#uint64) |  | количество билетов в заказе с которого применяется скидка |
| value | [Percentage](#v3-Percentage) |  | процент скидки |






<a name="v3-ModPromotionType-LevelsFix"></a>

### ModPromotionType.LevelsFix



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| levels | [ModPromotionType.LevelsFix.Level](#v3-ModPromotionType-LevelsFix-Level) | repeated |  |






<a name="v3-ModPromotionType-LevelsFix-Level"></a>

### ModPromotionType.LevelsFix.Level



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| level | [uint64](#uint64) |  | количество денег в заказе с которого применяется скидка |
| value | [uint64](#uint64) |  | фиксированная скидка |






<a name="v3-ModPromotionType-LevelsPercentage"></a>

### ModPromotionType.LevelsPercentage



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| levels | [ModPromotionType.LevelsPercentage.Level](#v3-ModPromotionType-LevelsPercentage-Level) | repeated |  |






<a name="v3-ModPromotionType-LevelsPercentage-Level"></a>

### ModPromotionType.LevelsPercentage.Level



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| level | [uint64](#uint64) |  | количество денег в заказе с которого применяется скидка |
| value | [Percentage](#v3-Percentage) |  | процент скидки |





 


<a name="v3-Mod-ModType"></a>

### Mod.ModType


| Name | Number | Description |
| ---- | ------ | ----------- |
| UNKNOWN | 0 |  |
| PROMOTION | 1 | модификатор-промоакция |


 

 

 



<a name="seats-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## seats.proto



<a name="v3-Seat"></a>

### Seat



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| sector | [string](#string) |  | id сектора |
| row | [string](#string) |  | номер ряда |
| number | [string](#string) |  | номер места |
| event | [string](#string) |  | id мероприятия |
| set | [string](#string) |  | id категории билета |
| ticket | [string](#string) |  | id билета |
| status | [Seat.TicketStatus](#v3-Seat-TicketStatus) |  | статус билета |
| ticket_reserved_till | [google.protobuf.Timestamp](#google-protobuf-Timestamp) |  | [O] время до которого билет забронирован, заполнено только у билетов в статусе &#39;RESERVED&#39; |






<a name="v3-SeatsRequest"></a>

### SeatsRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| sector | [string](#string) |  |  |
| row | [string](#string) |  |  |
| number | [string](#string) |  |  |
| event | [string](#string) |  | фильтр по id мероприятия, обязательный параметр |
| sets | [string](#string) | repeated |  |
| tickets | [string](#string) | repeated |  |
| status | [SeatsRequest.Status](#v3-SeatsRequest-Status) |  |  |





 


<a name="v3-Seat-TicketStatus"></a>

### Seat.TicketStatus


| Name | Number | Description |
| ---- | ------ | ----------- |
| VACANT | 0 | билет доступен к продаже |
| RESERVED | 1 | билет забронирован |
| SOLD | 2 | билет продан |



<a name="v3-SeatsRequest-Status"></a>

### SeatsRequest.Status


| Name | Number | Description |
| ---- | ------ | ----------- |
| ANY | 0 | любой статус билета |
| VACANT | 1 | билет доступен к продаже |
| RESERVED | 2 | билет забронирован |
| SOLD | 3 | билет продан |


 

 

 



<a name="service-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## service.proto


 

 

 


<a name="v3-Simple"></a>

### Simple


| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| Artists | [ArtistsRequest](#v3-ArtistsRequest) | [Artist](#v3-Artist) stream |  |
| Categories | [CategoriesRequest](#v3-CategoriesRequest) | [Category](#v3-Category) stream |  |
| Cities | [CitiesRequest](#v3-CitiesRequest) | [City](#v3-City) stream |  |
| Countries | [CountriesRequest](#v3-CountriesRequest) | [Country](#v3-Country) stream |  |
| Events | [EventsRequest](#v3-EventsRequest) | [Event](#v3-Event) stream |  |
| Maps | [MapsRequest](#v3-MapsRequest) | [Map](#v3-Map) stream |  |
| MetaEvents | [MetaEventsRequest](#v3-MetaEventsRequest) | [MetaEvent](#v3-MetaEvent) stream |  |
| Seats | [SeatsRequest](#v3-SeatsRequest) | [Seat](#v3-Seat) stream |  |
| Tags | [TagsRequest](#v3-TagsRequest) | [Tag](#v3-Tag) stream |  |
| Venues | [VenuesRequest](#v3-VenuesRequest) | [Venue](#v3-Venue) stream |  |

 



<a name="tags-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## tags.proto



<a name="v3-CategoriesRequest"></a>

### CategoriesRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ids | [string](#string) | repeated | фильтр по id категории |






<a name="v3-Category"></a>

### Category



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | id категории |
| name | [string](#string) |  | название категории |






<a name="v3-Tag"></a>

### Tag



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | id жанра |
| category | [string](#string) |  | id категории |
| name | [string](#string) |  | название жанра |
| generic | [bool](#bool) |  |  |






<a name="v3-TagsRequest"></a>

### TagsRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ids | [string](#string) | repeated | фильтр по id жанра |





 

 

 

 



<a name="venues-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## venues.proto



<a name="v3-Map"></a>

### Map



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | id схемы зала |
| name | [string](#string) |  | название схемы зала |
| description | [string](#string) |  | [O] описание схемы зала |
| venue | [string](#string) |  | id площадки |
| sectors | [Map.Sector](#v3-Map-Sector) | repeated | перечисление секторов |
| seats | [Map.Seat](#v3-Map-Seat) | repeated | перечисление мест |
| svg | [Map.SvgEntry](#v3-Map-SvgEntry) | repeated | svg со схемами |






<a name="v3-Map-Seat"></a>

### Map.Seat



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| sector | [string](#string) |  |  |
| row | [string](#string) |  | номер ряда |
| number | [string](#string) |  | номер места |
| point | [Map.Seat.Point](#v3-Map-Seat-Point) |  |  |






<a name="v3-Map-Seat-Point"></a>

### Map.Seat.Point
координаты места на схеме зала


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| x | [int32](#int32) |  |  |
| y | [int32](#int32) |  |  |
| r | [int32](#int32) |  | radius |






<a name="v3-Map-Sector"></a>

### Map.Sector



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | id сектора |
| name | [string](#string) |  | название сектора |
| description | [string](#string) |  | [O] описание сектора |
| with_seats | [bool](#bool) |  | признак сектора с рассадкой |






<a name="v3-Map-SvgEntry"></a>

### Map.SvgEntry



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| key | [string](#string) |  |  |
| value | [string](#string) |  |  |






<a name="v3-MapsRequest"></a>

### MapsRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ids | [string](#string) | repeated | фильтр по id схемы зала |
| venue | [string](#string) |  | фильтр по id площадки, можно получить все схемы зала конкретной площадки |






<a name="v3-Venue"></a>

### Venue



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | id площадки |
| name | [string](#string) |  | название площадки |
| description | [string](#string) |  | [O] описание площадки |
| city | [int32](#int32) |  | id города |
| address | [string](#string) |  | [O] адрес площадки |
| coordinates | [Coordinates](#v3-Coordinates) |  | [O] координаты площадки |
| with_mosbilet | [bool](#bool) |  | признак наличия интеграции с mosbilet.ru |






<a name="v3-VenuesRequest"></a>

### VenuesRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ids | [string](#string) | repeated | фильтр по id площадки |





 

 

 

 



## Scalar Value Types

| .proto Type | Notes | C++ | Java | Python | Go | C# | PHP | Ruby |
| ----------- | ----- | --- | ---- | ------ | -- | -- | --- | ---- |
| <a name="double" /> double |  | double | double | float | float64 | double | float | Float |
| <a name="float" /> float |  | float | float | float | float32 | float | float | Float |
| <a name="int32" /> int32 | Uses variable-length encoding. Inefficient for encoding negative numbers – if your field is likely to have negative values, use sint32 instead. | int32 | int | int | int32 | int | integer | Bignum or Fixnum (as required) |
| <a name="int64" /> int64 | Uses variable-length encoding. Inefficient for encoding negative numbers – if your field is likely to have negative values, use sint64 instead. | int64 | long | int/long | int64 | long | integer/string | Bignum |
| <a name="uint32" /> uint32 | Uses variable-length encoding. | uint32 | int | int/long | uint32 | uint | integer | Bignum or Fixnum (as required) |
| <a name="uint64" /> uint64 | Uses variable-length encoding. | uint64 | long | int/long | uint64 | ulong | integer/string | Bignum or Fixnum (as required) |
| <a name="sint32" /> sint32 | Uses variable-length encoding. Signed int value. These more efficiently encode negative numbers than regular int32s. | int32 | int | int | int32 | int | integer | Bignum or Fixnum (as required) |
| <a name="sint64" /> sint64 | Uses variable-length encoding. Signed int value. These more efficiently encode negative numbers than regular int64s. | int64 | long | int/long | int64 | long | integer/string | Bignum |
| <a name="fixed32" /> fixed32 | Always four bytes. More efficient than uint32 if values are often greater than 2^28. | uint32 | int | int | uint32 | uint | integer | Bignum or Fixnum (as required) |
| <a name="fixed64" /> fixed64 | Always eight bytes. More efficient than uint64 if values are often greater than 2^56. | uint64 | long | int/long | uint64 | ulong | integer/string | Bignum |
| <a name="sfixed32" /> sfixed32 | Always four bytes. | int32 | int | int | int32 | int | integer | Bignum or Fixnum (as required) |
| <a name="sfixed64" /> sfixed64 | Always eight bytes. | int64 | long | int/long | int64 | long | integer/string | Bignum |
| <a name="bool" /> bool |  | bool | boolean | boolean | bool | bool | boolean | TrueClass/FalseClass |
| <a name="string" /> string | A string must always contain UTF-8 encoded or 7-bit ASCII text. | string | String | str/unicode | string | string | string | String (UTF-8) |
| <a name="bytes" /> bytes | May contain any arbitrary sequence of bytes. | string | ByteString | str | []byte | ByteString | string | String (ASCII-8BIT) |

