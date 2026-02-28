# Testing con Junit

Este es un ejemplo sencillo de pruebas unitarias usando Junit 5

Observa que este proyecto no tiene ninguna clase con el método `main`, no nos hace fatal. Además, tampoco tiene ningún `scanner` ni ningún `print`.

Haz un fork de este proyecto en tu repositorio de Github y contesta a las siguientes preguntas:

1. ¿Qué sentido puede tener este proyecto y para que lo podrías usar?
   
-Este proyecto tiene sentido en un entorno profesional donde se quiera garantizar la calidad del software mediante pruebas automatizadas. No está diseñado como una aplicación tradicional, ya que no utiliza Scanner, no tiene método main y tampoco incluye instrucciones println.

En lugar de trabajar con variables inicializadas dentro del propio programa, los valores se pasan como parámetros a los métodos. Esto permite probar directamente la lógica sin depender de la entrada por consola ni de la salida por pantalla, haciendo que las pruebas sean más limpias, controladas y fáciles de automatizar.

Al centrarse únicamente en la lógica de los métodos, el proyecto facilita la validación del comportamiento del código mediante pruebas unitarias, mejorando la mantenibilidad y reduciendo la probabilidad de errores en futuras modificaciones.

¿Para qué usa JUnit una empresa?

-JUnit es una herramienta muy extendida en el mundo Java y las empresas la incorporan en su día a día por motivos bastante prácticos.
El más evidente es que ahorra tiempo. Cada vez que alguien del equipo modifica el código, las pruebas corren solas y avisan si algo dejó de funcionar, sin que nadie tenga que revisar nada a mano antes de que el problema llegue a los usuarios.

También resulta útil cuando se incorpora gente nueva al proyecto. En lugar de pedir a alguien que explique cómo funciona cada parte del sistema, basta con mirar las pruebas para entender qué se espera de cada método. Son como una guía que se mantiene actualizada sola.
Otro punto a favor es la tranquilidad que da a la hora de tocar código que ya funciona. Si necesitas mejorar algo o corregir un error, sabes que si metes la pata en otro sitio, JUnit te lo va a decir enseguida.

Y por último, el hecho de que los métodos reciban los datos como parámetros en lugar de pedirlos por consola no es un capricho, sino una forma de trabajar que hace que todo sea más ordenado y fácil de probar, que es justo lo que se valora en un entorno profesional.

2. Revisa las pruebas de la suma y comenta lo que te parezca de interés
   
-Lo que me ha llamado la atención es que el test de la suma está  limpio porque no se usan variables intermedias. En vez de andar creando el valor1, el valor2 y el esperado fuera, mete la llamada a la función directamente en el assertEquals.

Lo bueno de usar el assertAll, a diferencia de un test normal, es que si la primera suma falla, el programa no se detiene ahí (lo que nos dejaría sin saber qué pasa con las demás). Aquí, al usar las lambdas (las flechitas ->), el test lanza todas las pruebas a la vez. Así, si la calculadora falla en una pero acierta en otra, te enteras de todo el "pastel" de golpe y no tienes que ir arreglando y probando una por una.

La única diferencia que hay respecto al resultado de las pruebas es que sumarPositivosMal da error debido al valor esperado, ya que el valor es de cuatro y, según las otras variables, debería ser cinco.


3. Realiza un estudio de caja negra de la división e implementa las pruebas en junit: Se realizará en markdown.

## Particiones de equivalencia

Analizamos cada una de las dos variables del sistema para determinar sus clases de equivalencia.

### Variable B (divisor) — la más crítica:

| Clase | Valor | ¿Válida? |
| :--- | :--- | :--- |
| Clase 1 | b es número negativo (ej: -5) | Válida |
| Clase 2 | b = 0 | Error |
| Clase 3 | b es número positivo (ej: 5) | Válida |

### Variable A (dividendo):

| Clase | Valor | ¿Válida? |
| :--- | :--- | :--- |
| Clase 1 | a es número negativo (ej: -10) | Válida |
| Clase 2 | a = 0 | Válida (resultado siempre es 0) |
| Clase 3 | a es número positivo (ej: 10) | Válida |

## Valores límite

| Variable | Valor límite | Razón |
| :--- | :---: | :--- |
| b | -1 | Justo antes del cero por la izquierda |
| b | 0 | El límite exacto del error |
| b | 1 | Justo después del cero por la derecha |
| a | -1 | Justo antes del cero por la izquierda |
| a | 0 | Dividendo neutro |
| a | 1 | Justo después del cero por la derecha |

## Casos de prueba combinados

| # | Dividendo (a) | Divisor (b) | Resultado esperado |
| :-- | :---: | :---: | :--- |
| 1 | 10 | 5 | 2 |
| 2 | -10 | 5 | -2 |
| 3 | 10 | -5 | -2 |
| 4 | -10 | -5 | 2 |
| 5 | 0 | 5 | 0 |
| 6 | 10 | 0 | Error, genera una excepcion |
| 7 | 0 | 0 | Error, genera una excepcion |
| 8 | 1 | 1 | 1 |
| 9 | -1 | 1 | -1 |
| 10 | 1 | -1 | -1 |
| 11 | 10 | 1 | 10 (límite divisor) |
| 12 | 10 | -1 | -10 (límite divisor) |

