
## What is xtix-simple

This is a lightweight integration service for XTIX. It provides an alternative way to work together compared to embedding the XTIX widget on a ticket sales website. It is a gRPC server that supports requests for retrieving data needed to display a ticket ordering form. The actual order in XTIX is created using the [RESTful API](https://ticketscloud.readthedocs.io).

## What data is provided?

[Services:](doc/docs.md#simple)  
- List of events ([Events](doc/docs.md#Event))  
- List of periodic and recurring event groups ([MetaEvents](doc/docs.md#MetaEvent))  
- Event classification: tags ([Tags](doc/docs.md#Tag)) and categories ([Categories](doc/docs.md#CategoriesRequest))  
- Event venues ([Venues](doc/docs.md#Venue)), seating maps ([Maps](doc/docs.md#Map)), and seats ([Seats](doc/docs.md#Seat))  
- Country ([Countries](doc/docs.md#CountriesRequest)) and city ([Cities](doc/docs.md#CitiesRequest)) directories  
- Artist information ([Artists](doc/docs.md#Artist))

## gRPC API – Supported Requests and Data Structures

[API reference](doc/docs.md)

**Note:**
- If data (e.g. country or city names) is available in multiple languages, you can specify the preferred one by adding the `preferred-language` header to the request metadata (see code example).
- Keep in mind that default values (usually zero) are interpreted by the [Protobuf internal structure](https://developers.google.com/protocol-buffers/docs/proto3#default) as absence of a value.

## Endpoints

- Staging (test): `simple.xtix.dev:443`  
- Production: `simple.xtix.ai:443`

## Example Python client

1. Obtain an API key from the XTIX dashboard or from your account manager.

2. Install the `.proto` file compiler:

    ```bash
    pip install grpcio-tools
    ```

3. Compile the `.proto` files into Python wrappers:

    ```bash
    mkdir proto/build && python -m grpc_tools.protoc -Iproto --python_out=proto --grpc_python_out=proto ./proto/*.proto
    ```

    The compiled `*.py` files will appear in the `proto/build` directory.

4. Run Python code in the `proto/build` directory:

    ```python
    import grpc

    import service_pb2_grpc
    import events_pb2

    api_key = ''  # Access key
    endpoint = 'simple.stage.freetc.net:443'  # Test endpoint
    credentials = grpc.ssl_channel_credentials()
    ch = grpc.secure_channel(endpoint, credentials)
    stub = service_pb2_grpc.SimpleStub(ch)

    # You can call any of the services as a stub method
    req = events_pb2.EventsRequest(ids=None)
    events = stub.Events(req, metadata=[('authorization', api_key), ('preferred-language', 'ru')])
    for ev in events:
        print(ev)
    ```
