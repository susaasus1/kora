# Soap

## Dependency

```groovy
implemenation 'ru.tinkoff.kora:soap-client'
```

## Soap client

Для взаимодействия с системами по SOAP kora предоставляет возможность генерировать клиенты
во время компиляции на основании аннотаций из пакетов `javax.jws.WebService`/`jakarta.jws.WebService`.
Просто сегенерируйте классы с помощью любимого плагина для вашей системы сборки по wsdl файлу,
а annotation processor сгенерирует по интерфейсам реализации с суффиксом Impl в том же пакете.

Для работы приложению потребуется пакет `ru.tinkoff.kora:soap-client`. 

Так как аннотации представляет не наш фреймворк, мы не можем добавить необходимую для нас информацию в них и нам не хватает данных,
чтобы сгенерировать модуль для приложения, а значит необходимо добавить этот класс в контейнер руками, объявив метод.
Конструктор принимает два параметра: `HttpClient` и `SoapServiceConfig`.


## Реактивная реализация
Хотя мы и ограничены сгенерированным согласно спецификации jax-ws интерфейсом, в сгенерированной реализации присутствуют
неблокирующие методы с суффиксом "Reactive". Они принимают те же аргументы, что и метод в интерфейсе, но возвращают `Mono<T>`.
