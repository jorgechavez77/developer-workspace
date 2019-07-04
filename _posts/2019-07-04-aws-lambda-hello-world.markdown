---
layout: post
title:  "Funciones Lambda (AWS)"
date:   2019-07-04 16:40:44 -0400
categories: AWS Lambda
---

# Cómo creare funciones Lambda desde cero

- *Necesitaras una cuenta AWS.*
- *Todos estos pasas estan hechos desde la consola AWS.*

#### __Crear un role AWS__

Lo primero importante que se debe de hacer antes de crear una funcion `Lambda`, es crear un `role`. El cual será utilizado por las funciones que crees en el futuro.

Es una buena practica crear un `role`, y reutilzarlo para cada funcion que crees en vez de crear un `role` cada vez que creas una función.

Para crear un role, lo primero que debes hacer es ir al menú superior de la consola de AWS, ahí en __Services__ busca: `IAM`.

Cuando te encuentres en el menú `IAM`, en el panel de la izquierda podras visualizar varias opciones, para este caso en particular dale click a la opción `Create role`, luego selecciona `AWS service` donde indica __Select type of trusted entity__ y selcciona `Lambda` donde indica __Choose the service that will use this role__.

Continua dando click en `Next: Permissions`. Busca `AWSLambdaBasicExecutionRole`, selecciona el elemento cuyo `Policy Name` sea `AWSLambdaBasicExecutionRole` y  continua `Next: Tags` si, deseas agrega `tags`.

Pon un nombre apropiado al `role` para que identifique que este es para las funciones _lambdas_. Para este ejemplo llamaré al `role`: __my-lambda-role__ finaliza haciendo click en `Create role`.

#### __Create your own Lambda function__

Ahora para crear una funcion debemos ir al menu superior `services` y buscar por la palabra `lambda`. Damos click en `create function`, y seleccionamos `Author from scratch`, ponle un nombre a tu funcion en el campo _Funcion name_, por ejemplo `hello-world-lambda`, selcciona un _Runtime_ de la lista, para este ejemplo escogeré `Node.js 10.x`. En `Permissions` vamos a buscar y seleccionar el permiso `role` que creamos previamente.

En _Execution role_, busca por `Use an existing role` y en _Existing role_ seleccionamos el role que creamos previamente, para mi caso sería __my-lambda-role__ y hacemos click en `Create Function`.

#### __Test your Lambda function__
Luego de haber creado la funcion, __AWS__ nos mostrara muchas opciones. Lo primero que haremos es revisar el codigo. Buscar por `Function code` y veremos el codigo fuente, similar a lo que se muestra a continuación:
```javascript
exports.handler = async (event) => {
    // TODO implement
    const response = {
        statusCode: 200,
        body: JSON.stringify('Hello from Lambda!'),
    };
    return response;
};
```

Para poder probar que nuestra funcion, en parte superior hay un botón `Test`. Al hacer click a este botón, este nos mostrara la opcion para configurar en evento de prueba `Configure Test Event`. Escribamos por ejemplo `test01` (o cualquier nombre que prefieran), observen el `JSON` que se muestra y hagan click en `Create`. Con esto hemos creado un simple escenario de prueba para nuestra función `Lambda`.

Luego presionemos el botón `Test` nuevamente y este ejecutará la función que hemos creado. Al ir a la parte superior de la pantalla encontraremos un mensaje similar a este

```
Execution result: succeeded(logs)
  Details
```

Al hacer click en _Details_ podran ver la respuesta generada por la funcion `Lambda` que hemos creado, algo similar a:

```
{
  "statusCode": 200,
  "body": "\"Hello from Lambda!\""
}
```

Con esto hemos finalizado como crear un `Lambda Function` usando la consola __AWS__.
