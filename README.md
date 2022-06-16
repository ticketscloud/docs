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

## Точки доступа (endpoints)

- Стейдж (тестовая): `simple.stage.freetc.net:443`
- Продакшен: `simple.ticketscloud.com:443`

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
    stub = proto.simple.service_pb2_grpc.SimpleStub(ch)

    # Можем вызвать любой из сервисов как метод stub
    req = events_pb2.EventsRequest(ids=None)
    events = stub.Events(req, metadata=[('authorization', api_key)])
    for ev in events:
        print(ev)
    ```
