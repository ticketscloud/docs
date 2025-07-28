## Что такое tc-simple
Это простой сервис интеграции с Ticketscloud. Предоставляет альтернативный способ совместной работы по сравнению с размещением виджета Ticketscloud на сайте продажи билетов. Представляет собой gRPC сервер, поддерживающий запросы на получение данных, необходимых для отображения формы заказа билетов. Сам заказ в Ticketscloud создаётся посредством [RESTful API](https://ticketscloud.readthedocs.io).

## Какие данные предоставляются?

[Сервисы:](doc/docs.md#simple)
- список мероприятий ([Events](doc/docs.md#Event));
- список групп периодических и повторяющихся мероприятий ([MetaEvents](doc/docs.md#MetaEvent));
- классификация мероприятий: теги ([Tags](doc/docs.md#Tag)) и категории ([Categories](doc/docs.md#CategoriesRequest));
- площадки проведения мероприятий ([Venues](doc/docs.md#Venue), схемы расположения ([Maps](doc/docs.md#Map)) зрительских мест ([Seats](doc/docs.md#Seat));
- справочник стран ([Countries](doc/docs.md#CountriesRequest)) и городов ([Cities](doc/docs.md#CitiesRequest));
- сведения об артистах ([Artists](doc/docs.md#Artist)).

## gRPC API -- поддерживаемые запросы и структуры данных

[API reference](doc/docs.md)

NB:
- Если данные (например, названия стран и городов) доступны на нескольких языках, можно указать предпочитаемый, добавив в метаданные запроса заголовок `preferred-language` (см. пример кода).
- Следует учитывать, что значение поля по умолчанию (обычно нулевое) передаётся [внутренней структурой Protobuf](https://developers.google.com/protocol-buffers/docs/proto3#default) как отсутствие значения.

## Точки доступа (endpoints)

- Стейдж (тестовая): `simple.stage.freetc.net:443`
- Продакшен: `simple.ticketscloud.com:443`

## Пример клиента на PHP (спасибо https://github.com/feldwebel)

Должно быть установлено расширение grpc, компилятор protobuf и собран grpc_php_plugin.

Компилируем .proto файлы:
```
protoc --proto_path=proto --php_out=generated --grpc_out=generated --plugin=protoc-gen-grpc=<путь к grpc_php_plugin> proto/*.proto
```

client.php:
```
#!/usr/bin/env php
<?php
require "vendor/autoload.php";
// Если используем composer, можно добавить в composer.json
// "autoload": {
//   "psr-4": {
//     "V2\\": "php_generated/V2/",
//     "GPBMetadata\\": "php_generated/GPBMetadata/"
//   }
// }

use Grpc\ChannelCredentials;
use V2\SimpleClient;
use V2\CountriesRequest;

$host = "simple.stage.freetc.net:443";
$key = "<key>";  // Вписать API ключ
$cred = [
    "credentials" => ChannelCredentials::createSsl(), // защищённое соединение
];
$opt = [
    "authorization" => [$key], // ключ упакован в массив
];

$client = new SimpleClient($host, $cred);

$countriesRequest = new CountriesRequest()->setIds(["ZM"]);

$countries = $client->Countries($countriesRequest, $opt)->responses();

foreach ($countries as $country) {
    var_dump($country->getName());
}
```

## Пример клиента на Python:

1. Получаем в ЛК или у менеджеров Ticketscloud ключ доступа (API key).

2. Устанавливаем компилятор .proto-файлов:

    ```pip install grpcio-tools```

3. Компилируем .proto-файлы в обёртки на Python:

    ```mkdir proto/build && python -m grpc_tools.protoc -Iproto --python_out=proto --grpc_python_out=proto ./proto/*.proto```

    В каталоге proto/build появятся *.py-файлы.

4. Запускаем в каталоге proto/build код на Python:

    ```python
    import grpc

    import service_pb2_grpc
    import events_pb2

    api_key = ''  # Ключ доступа
    endpoint = 'simple.stage.freetc.net:443'  # Точка доступа -- тестовая
    credentials = grpc.ssl_channel_credentials()
    ch = grpc.secure_channel(endpoint, credentials)
    stub = service_pb2_grpc.SimpleStub(ch)

    # Можем вызвать любой из сервисов как метод stub
    req = events_pb2.EventsRequest(ids=None)
    events = stub.Events(req, metadata=[('authorization', api_key), ('preferred-language', 'ru')])
    for ev in events:
        print(ev)
    ```
