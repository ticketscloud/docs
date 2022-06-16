## Сборка документации из .proto файлов:

1. Скачиваем компилятор:

    ```docker pull pseudomuto/protoc-gen-doc```

2. Собираем:

    ```docker run --rm -v $(pwd)/doc:/out -v $(pwd)/proto:/protos pseudomuto/protoc-gen-doc --doc_opt=markdown,docs.md```
