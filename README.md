# JSONPathUtil

`JSONPathUtil` es una utilidad para trabajar con JSON y JSONPath en Java, permitiendo realizar consultas, verificaciones y lecturas sobre datos JSON utilizando expresiones JSONPath.

## Funcionalidades

Esta clase ofrece las siguientes funcionalidades:

1. **exists**: Verifica si un atributo y/o valor de un atributo existe en el JSON para el JSONPath dado.
2. **read**: Lee el valor del JSON en la ruta especificada y devuelve el objeto.
3. **readWithDefault**: Lee un valor de un JSON usando un JSONPath dado, y en caso de no encontrar el valor, devuelve un valor predeterminado.
4. **isValidJson**: Verifica si el JSON es válido.
5. **isValidPath**: Verifica si el JSONPath dado es válido.

### Ejemplo de JSON de prueba

Para los ejemplos a continuación, utilizamos el siguiente JSON como entrada:

```json
{
    "firstName": "John",
    "lastName": "doe",
    "age": 26,
    "address": {
        "streetAddress": "naist street",
        "city": "Nara",
        "postalCode": "630-0192"
    },
    "phoneNumbers": [
        {
            "type": "iPhone",
            "number": "0123-4567-8888"
        },
        {
            "type": "home",
            "number": "0123-4567-8910"
        }
    ]
}
```
## Métodos

### 1. `exists(String jsonString, String jsonPath)`

Este método verifica si un valor específico existe en el JSON utilizando una expresión JSONPath. Retorna `true` si el valor existe, y `false` si no.

#### Ejemplo de uso:

```java
String jsonString = "{...}";  // JSON de prueba
String jsonPath = "$.firstName";  // Path al valor "firstName"
boolean exists = JSONPathUtil.exists(jsonString, jsonPath);
```

#### Salida esperada:
`true`

Si el valor no existe, retornará `false`.

### 2. `read(String jsonString, String jsonPath)`

Este método lee el valor en la ruta especificada y devuelve el objeto asociado. Si ocurre algún error o no se encuentra el valor, devuelve: 

```text
"ERROR_READ"

``` 

#### Ejemplo de uso:

```java
String jsonString = "{...}";  // JSON de prueba
String jsonPath = "$.address.city";  // Path al valor "city" en "address"
String result = JSONPathUtil.read(jsonString, jsonPath);
```

#### Entrada:
`jsonPath: $.address.city`

#### Salida esperada:
```text
"Nara"

```

Si no se encuentra el valor o hay un error, retornará
```text
"ERROR_READ"

```

### 3. `readWithDefault(String jsonString, String jsonPath, String defaultValue)`

Este método lee un valor de un JSON usando el JSONPath dado. Si no se encuentra el valor, devuelve un valor predeterminado especificado por el usuario.

#### Ejemplo de uso:

```java
String jsonString = "{...}";  // JSON de prueba
String jsonPath = "$.address.country";  // Path inexistente
String defaultValue = "Unknown";
String result = JSONPathUtil.readWithDefault(jsonString, jsonPath, defaultValue);
```

#### Salida esperada:
```text
"Unknown"

```

Si el valor existe, retornará el valor encontrado. Si no existe, retornará el valor predeterminado.

### 4. `isValidJson(String jsonString)`

Este método verifica si el JSON dado es válido. Retorna `true` si el JSON es válido, y `false` si no lo es.

#### Ejemplo de uso:

```java
String jsonString = "{...}";  // JSON de prueba
boolean isValid = JSONPathUtil.isValidJson(jsonString);
```

#### Salida esperada:
`true`

Si el JSON es inválido, retornará `false`.

### 5. `isValidPath(String jsonPath)`

Este método verifica si la expresión JSONPath dada es válida. Retorna `true` si el JSONPath es válido y `false` si es inválido.

#### Ejemplo de uso:

```java
String jsonPath = "$.address.streetAddress";  // JSONPath válido
boolean isValidPath = JSONPathUtil.isValidPath(jsonPath);
```

#### Salida esperada:
`true`

Si el JSONPath es inválido, retornará `false`.
