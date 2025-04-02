# Protocol Documentation
<a name="top"></a>

## Table of Contents

- [artists.proto](#artists-proto)
    - [Artist](#-Artist)
    - [ArtistsRequest](#-ArtistsRequest)

- [events.proto](#events-proto)
    - [Deal](#-Deal)
    - [Event](#-Event)
    - [EventsRequest](#-EventsRequest)
    - [LegalRu](#-LegalRu)
    - [TicketSet](#-TicketSet)
    - [TicketSet.Rule](#-TicketSet-Rule)
    - [TicketSet.Rule.SimpleType](#-TicketSet-Rule-SimpleType)

    - [EventStatus](#-EventStatus)
    - [EventsRequest.Status](#-EventsRequest-Status)
    - [LegalRu.Type](#-LegalRu-Type)
    - [SmartTicketSetting](#-SmartTicketSetting)
    - [TicketSet.Rule.Type](#-TicketSet-Rule-Type)

- [generic.proto](#generic-proto)
    - [Coordinates](#-Coordinates)
    - [Lifetime](#-Lifetime)
    - [LiftimeFilter](#-LiftimeFilter)
    - [Media](#-Media)
    - [Percentage](#-Percentage)
    - [TimestampFilter](#-TimestampFilter)

- [geo.proto](#geo-proto)
    - [CitiesRequest](#-CitiesRequest)
    - [City](#-City)
    - [CountriesRequest](#-CountriesRequest)
    - [Country](#-Country)

- [meta_events.proto](#meta_events-proto)
    - [MetaEvent](#-MetaEvent)
    - [MetaEventsRequest](#-MetaEventsRequest)

- [mods.proto](#mods-proto)
    - [Mod](#-Mod)
    - [ModPromotionType](#-ModPromotionType)
    - [ModPromotionType.LevelsFix](#-ModPromotionType-LevelsFix)
    - [ModPromotionType.LevelsFix.Level](#-ModPromotionType-LevelsFix-Level)
    - [ModPromotionType.LevelsPercentage](#-ModPromotionType-LevelsPercentage)
    - [ModPromotionType.LevelsPercentage.Level](#-ModPromotionType-LevelsPercentage-Level)

    - [ModType](#-ModType)

- [seats.proto](#seats-proto)
    - [Seat](#-Seat)
    - [SeatsRequest](#-SeatsRequest)

    - [SeatsRequest.Status](#-SeatsRequest-Status)
    - [TicketStatus](#-TicketStatus)

- [service.proto](#service-proto)
    - [Simple](#-Simple)

- [tags.proto](#tags-proto)
    - [CategoriesRequest](#-CategoriesRequest)
    - [Category](#-Category)
    - [Tag](#-Tag)
    - [TagsRequest](#-TagsRequest)

- [venues.proto](#venues-proto)
    - [Map](#-Map)
    - [Map.Seat](#-Map-Seat)
    - [Map.Seat.Point](#-Map-Seat-Point)
    - [Map.Sector](#-Map-Sector)
    - [Map.SvgEntry](#-Map-SvgEntry)
    - [MapsRequest](#-MapsRequest)
    - [Venue](#-Venue)
    - [VenuesRequest](#-VenuesRequest)

- [Scalar Value Types](#scalar-value-types)



<a name="artists-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## artists.proto



<a name="-Artist"></a>

### Artist
Artist structure.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | Artist id (oid) |
| name | [string](#string) |  | Artist name |






<a name="-ArtistsRequest"></a>

### ArtistsRequest
Request for Artists.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ids | [string](#string) | repeated | Filtering by Artist id |















<a name="events-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## events.proto



<a name="-Deal"></a>

### Deal



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | Deal id |
| org | [Percentage](#Percentage) |  | Share (percent) of the organizer |
| agent | [Percentage](#Percentage) |  | Share of nominal ticket price got by agent |
| extra | [Percentage](#Percentage) |  | Share in excess of nominal ticket price, got by agent |






<a name="-Event"></a>

### Event
Event structure.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | Event id |
| meta | [string](#string) |  | [O] Event group id (absent for single Events) |
| name | [string](#string) |  | Event title |
| description | [string](#string) |  | [O] description |
| status | [EventStatus](#EventStatus) |  | status |
| org | [string](#string) |  | Organizer id |
| venue | [string](#string) |  | Venue id |
| map | [string](#string) |  | [O] Auditorium map id |
| lifetime | [Lifetime](#Lifetime) |  | Event start and end datetime |
| category | [string](#string) |  | Event category id |
| tags | [string](#string) | repeated | Event genres id |
| artists | [string](#string) | repeated | id of artists participating |
| age_rating | [string](#string) |  | [O] Age restrictions |
| media | [Media](#Media) |  | Media covers |
| deal | [Deal](#Deal) |  | [O] deal, if request is performed by agent |
| org_extra | [Percentage](#Percentage) |  | [O] commission percentage, if request is performed by organizer |
| legal_ru | [LegalRu](#LegalRu) |  | [O] seller&#39;s bank details |
| sets | [TicketSet](#TicketSet) | repeated | ticket sets |
| tickets_amount | [uint32](#uint32) |  | total amount of tickets in the Event |
| tickets_amount_vacant | [uint32](#uint32) |  | amount of vacant tickets in the Event |
| smart_tickets | [SmartTicketSetting](#SmartTicketSetting) |  | smart tickets settings |
| mods | [Mod](#Mod) | repeated | extra info on discounts |
| additional | [google.protobuf.Any](#google-protobuf-Any) |  | reserved field(s) |






<a name="-EventsRequest"></a>

### EventsRequest
Request for Events.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ids | [string](#string) | repeated | Filtering by Event id |
| meta | [string](#string) |  | Filtering by Event group id |
| without_meta | [bool](#bool) |  | Filter to get only single Events, that are not included into groups |
| org | [string](#string) |  | Filtering by organizer id |
| status | [EventsRequest.Status](#EventsRequest-Status) |  | Filtering by Event status |
| lifetime | [LiftimeFilter](#LiftimeFilter) |  |  |






<a name="-LegalRu"></a>

### LegalRu



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | Legal id |
| type | [LegalRu.Type](#LegalRu-Type) |  | Legal type |
| name | [string](#string) |  | Name |
| inn | [string](#string) |  | Tax ID |
| address | [string](#string) |  | Legal address |
| ogrn | [string](#string) |  | State registry number |
| ogrnip | [string](#string) |  | Individual Enterpreneur state registry number |






<a name="-TicketSet"></a>

### TicketSet
Ticket set structure.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | Set id |
| name | [string](#string) |  | Set name |
| description | [string](#string) |  | [O] Description |
| pos | [int32](#int32) |  | Set ordinal number |
| sector | [string](#string) |  | [O] sector id |
| with_seats | [bool](#bool) |  | Whether tickets are bound to seats |
| amount | [uint32](#uint32) |  | Total amount of tickets in set |
| amount_vacant | [uint32](#uint32) |  | Amount of tickets available for sale in set |
| rules | [TicketSet.Rule](#TicketSet-Rule) | repeated | Price rules for set |






<a name="-TicketSet-Rule"></a>

### TicketSet.Rule



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | Sales rule id |
| type | [TicketSet.Rule.Type](#TicketSet-Rule-Type) |  | Rule type |
| lifetime | [Lifetime](#Lifetime) |  |  |
| simple | [TicketSet.Rule.SimpleType](#TicketSet-Rule-SimpleType) |  |  |






<a name="-TicketSet-Rule-SimpleType"></a>

### TicketSet.Rule.SimpleType



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| price | [uint64](#uint64) |  | Price for ticket set |








<a name="-EventStatus"></a>

### EventStatus
Supported Event statuses.

| Name | Number | Description |
| ---- | ------ | ----------- |
| STAND_BY | 0 | Sales are temporarily suspended |
| PUBLIC | 1 | Sales are going |



<a name="-EventsRequest-Status"></a>

### EventsRequest.Status


| Name | Number | Description |
| ---- | ------ | ----------- |
| ANY | 0 | No filtering by status |
| STAND_BY | 1 | Sales are temporarily suspended |
| PUBLIC | 2 | Sales are going |



<a name="-LegalRu-Type"></a>

### LegalRu.Type


| Name | Number | Description |
| ---- | ------ | ----------- |
| LTD | 0 | Limited Liability Company |
| IP | 1 | Individual Enterpreneur |



<a name="-SmartTicketSetting"></a>

### SmartTicketSetting
Smart tickets options.

| Name | Number | Description |
| ---- | ------ | ----------- |
| NONE | 0 | Smart tickets are not used on the Event |
| ONLY | 1 | Smart tickets are the only used on the Event |
| ANY | 2 | Both smart and usual tickets can be sold for the Event |



<a name="-TicketSet-Rule-Type"></a>

### TicketSet.Rule.Type


| Name | Number | Description |
| ---- | ------ | ----------- |
| SIMPLE | 0 | Simple rule: sales rules are going one after another. |










<a name="generic-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## generic.proto



<a name="-Coordinates"></a>

### Coordinates
Geo coordinates


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| longitude | [double](#double) |  |  |
| latitude | [double](#double) |  |  |






<a name="-Lifetime"></a>

### Lifetime



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| start | [google.protobuf.Timestamp](#google-protobuf-Timestamp) |  |  |
| finish | [google.protobuf.Timestamp](#google-protobuf-Timestamp) |  |  |






<a name="-LiftimeFilter"></a>

### LiftimeFilter



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| start | [TimestampFilter](#TimestampFilter) |  |  |
| finish | [TimestampFilter](#TimestampFilter) |  |  |






<a name="-Media"></a>

### Media



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| cover | [string](#string) |  | [O] |
| cover_small | [string](#string) |  | [O] |
| cover_original | [string](#string) |  | [O] |






<a name="-Percentage"></a>

### Percentage



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| units | [int32](#int32) |  | Whole units part of the amount |
| nanos | [fixed32](#fixed32) |  | Nano units of the amount (10^-9). Must be same sign as units |






<a name="-TimestampFilter"></a>

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



<a name="-CitiesRequest"></a>

### CitiesRequest
Request for cities.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ids | [int32](#int32) | repeated | Filtering by city id |
| name | [string](#string) |  | Filtering ny city name |
| suggest | [string](#string) |  | Prefix search |
| country | [string](#string) |  | Filtering by country |






<a name="-City"></a>

### City



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [int32](#int32) |  | City id |
| name | [string](#string) |  | Name |
| country | [string](#string) |  | Country id |
| timezone | [string](#string) |  | Timezone |
| coordinates | [Coordinates](#Coordinates) |  | Coordinates |
| population | [int64](#int64) |  | City population |






<a name="-CountriesRequest"></a>

### CountriesRequest
Request for countries.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ids | [string](#string) | repeated | Filtering by country id |






<a name="-Country"></a>

### Country



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | Country id |
| name | [string](#string) |  | Name |
| currency | [string](#string) |  | Currency |
| iso | [string](#string) |  | ISO 3166-1 code |
| iso3 | [string](#string) |  | ISO 3166-3 code |
| iso_numeric | [uint32](#uint32) |  | ISO 3166-1 numeric code |















<a name="meta_events-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## meta_events.proto



<a name="-MetaEvent"></a>

### MetaEvent



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | Group id |
| name | [string](#string) |  | Group name |
| description | [string](#string) |  | [O] Description |
| org | [string](#string) |  | Organizer id |
| age_rating | [string](#string) |  | [O] Age restrictions |
| media | [Media](#Media) |  | Media cover |
| first_start | [google.protobuf.Timestamp](#google-protobuf-Timestamp) |  | Time when the first Event begins |
| last_finish | [google.protobuf.Timestamp](#google-protobuf-Timestamp) |  | Time when the last Event ends |
| additional | [google.protobuf.Any](#google-protobuf-Any) |  | Reserved field(s) |






<a name="-MetaEventsRequest"></a>

### MetaEventsRequest
Request for Event groups.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ids | [string](#string) | repeated | Filtering by group id |















<a name="mods-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## mods.proto



<a name="-Mod"></a>

### Mod



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  |  |
| type | [ModType](#ModType) |  |  |
| promotion | [ModPromotionType](#ModPromotionType) |  | Promotion settings |






<a name="-ModPromotionType"></a>

### ModPromotionType



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| lifetime | [Lifetime](#Lifetime) |  |  |
| sets | [string](#string) | repeated | Ticket sets discount is related to |
| discount_percentage | [Percentage](#Percentage) |  | Percentage discount |
| discount_fix | [uint64](#uint64) |  | Fixed discount |
| levels_percentage | [ModPromotionType.LevelsPercentage](#ModPromotionType-LevelsPercentage) |  | Levels for percentage discount |
| levels_fix | [ModPromotionType.LevelsFix](#ModPromotionType-LevelsFix) |  | Levels for fixed discount |






<a name="-ModPromotionType-LevelsFix"></a>

### ModPromotionType.LevelsFix



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| levels | [ModPromotionType.LevelsFix.Level](#ModPromotionType-LevelsFix-Level) | repeated |  |






<a name="-ModPromotionType-LevelsFix-Level"></a>

### ModPromotionType.LevelsFix.Level



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| level | [uint64](#uint64) |  |  |
| value | [uint64](#uint64) |  |  |






<a name="-ModPromotionType-LevelsPercentage"></a>

### ModPromotionType.LevelsPercentage



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| levels | [ModPromotionType.LevelsPercentage.Level](#ModPromotionType-LevelsPercentage-Level) | repeated |  |






<a name="-ModPromotionType-LevelsPercentage-Level"></a>

### ModPromotionType.LevelsPercentage.Level



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| level | [uint64](#uint64) |  |  |
| value | [Percentage](#Percentage) |  |  |








<a name="-ModType"></a>

### ModType
Discount modifier type.

| Name | Number | Description |
| ---- | ------ | ----------- |
| PROMOTION | 0 |  |










<a name="seats-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## seats.proto



<a name="-Seat"></a>

### Seat



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| sector | [string](#string) |  | Sector id |
| row | [string](#string) |  | Row number |
| number | [string](#string) |  | Seat number |
| event | [string](#string) |  | Event id |
| set | [string](#string) |  | Ticket set id |
| ticket | [string](#string) |  | Ticket id |
| status | [TicketStatus](#TicketStatus) |  | Ticket status |
| ticket_reserved_till | [google.protobuf.Timestamp](#google-protobuf-Timestamp) |  | [O] Reserve expiration time, only for tickets wits status=&#39;RESERVED&#39; |






<a name="-SeatsRequest"></a>

### SeatsRequest
Request for seats.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| sector | [string](#string) |  |  |
| row | [string](#string) |  |  |
| number | [string](#string) |  |  |
| event | [string](#string) |  | Filtering by Event id (required) |
| sets | [string](#string) | repeated |  |
| tickets | [string](#string) | repeated |  |
| status | [SeatsRequest.Status](#SeatsRequest-Status) |  |  |








<a name="-SeatsRequest-Status"></a>

### SeatsRequest.Status


| Name | Number | Description |
| ---- | ------ | ----------- |
| ANY | 0 | Any ticket status |
| VACANT | 1 | Ticket is available for sell |
| RESERVED | 2 | Ticket is reserved |
| SOLD | 3 | Ticket is sold |



<a name="-TicketStatus"></a>

### TicketStatus


| Name | Number | Description |
| ---- | ------ | ----------- |
| VACANT | 0 | Ticket is available for sell |
| RESERVED | 1 | Ticket is reserved |
| SOLD | 2 | Ticket is sold |










<a name="service-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## service.proto









<a name="-Simple"></a>

### Simple


| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| Countries | [.CountriesRequest](#CountriesRequest) | [.Country](#Country) stream |  |
| Cities | [.CitiesRequest](#CitiesRequest) | [.City](#City) stream |  |
| Venues | [.VenuesRequest](#VenuesRequest) | [.Venue](#Venue) stream |  |
| Maps | [.MapsRequest](#MapsRequest) | [.Map](#Map) stream |  |
| Categories | [.CategoriesRequest](#CategoriesRequest) | [.Category](#Category) stream |  |
| Tags | [.TagsRequest](#TagsRequest) | [.Tag](#Tag) stream |  |
| Artists | [.ArtistsRequest](#ArtistsRequest) | [.Artist](#Artist) stream |  |
| Events | [.EventsRequest](#EventsRequest) | [.Event](#Event) stream |  |
| MetaEvents | [.MetaEventsRequest](#MetaEventsRequest) | [.MetaEvent](#MetaEvent) stream |  |
| Seats | [.SeatsRequest](#SeatsRequest) | [.Seat](#Seat) stream |  |





<a name="tags-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## tags.proto



<a name="-CategoriesRequest"></a>

### CategoriesRequest
Request for categories.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ids | [string](#string) | repeated | Filtering by category id |






<a name="-Category"></a>

### Category



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | Category id |
| name | [string](#string) |  | Category name |






<a name="-Tag"></a>

### Tag



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | Genre id |
| category | [string](#string) |  | Category id |
| name | [string](#string) |  | Genre name |
| generic | [bool](#bool) |  | Is generic |






<a name="-TagsRequest"></a>

### TagsRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ids | [string](#string) | repeated | Genre id |















<a name="venues-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## venues.proto



<a name="-Map"></a>

### Map



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | Map id |
| name | [string](#string) |  | Map name |
| description | [string](#string) |  | [O] Description |
| venue | [string](#string) |  | Venue id |
| sectors | [Map.Sector](#Map-Sector) | repeated | Sectors list |
| seats | [Map.Seat](#Map-Seat) | repeated | Seats list |
| svg | [Map.SvgEntry](#Map-SvgEntry) | repeated | svg maps |






<a name="-Map-Seat"></a>

### Map.Seat



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| sector | [string](#string) |  |  |
| row | [string](#string) |  | Row number |
| number | [string](#string) |  | Seat number |
| point | [Map.Seat.Point](#Map-Seat-Point) |  |  |






<a name="-Map-Seat-Point"></a>

### Map.Seat.Point
Seat coordinates on the map


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| x | [int32](#int32) |  |  |
| y | [int32](#int32) |  |  |
| r | [int32](#int32) |  | radius |






<a name="-Map-Sector"></a>

### Map.Sector



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | Sector id |
| name | [string](#string) |  | Sector name |
| description | [string](#string) |  | [O] description |
| with_seats | [bool](#bool) |  | Whether sector has seats |






<a name="-Map-SvgEntry"></a>

### Map.SvgEntry



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| key | [string](#string) |  |  |
| value | [string](#string) |  |  |






<a name="-MapsRequest"></a>

### MapsRequest
Request for maps.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ids | [string](#string) | repeated | Filtering by map id |
| venue | [string](#string) |  | Filtering by venue id to get all auditoria maps |






<a name="-Venue"></a>

### Venue



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [string](#string) |  | Venue id |
| name | [string](#string) |  | Name |
| description | [string](#string) |  | [O] Description |
| city | [int32](#int32) |  | City id |
| address | [string](#string) |  | [O] Address |
| coordinates | [Coordinates](#Coordinates) |  | [O] Geo coordinates |
| with_mosbilet | [bool](#bool) |  | [O] Whether venue is affiliated with Mosbilet |






<a name="-VenuesRequest"></a>

### VenuesRequest
Request for venues.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ids | [string](#string) | repeated | Filtering by venue id |















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
