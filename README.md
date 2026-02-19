# Testing con Junit

Este es un ejemplo sencillo de pruebas unitarias usando Junit 5

Observa que este proyecto no tiene ninguna clase con el método `main`, no nos hace fatal. Además, tampoco tiene ningún `scanner` ni ningún `print`.

Haz un fork de este proyecto en tu repositorio de Github y contesta a las siguientes preguntas:

1. ¿Qué sentido puede tener este proyecto y para que lo podrías usar?
   
-Este proyecto tiene sentido en un entorno profesional donde se quiera garantizar la calidad del software mediante pruebas automatizadas. No está diseñado como una aplicación tradicional, ya que no utiliza Scanner, no tiene método main y tampoco incluye instrucciones println.

En lugar de trabajar con variables inicializadas dentro del propio programa, los valores se pasan como parámetros a los métodos. Esto permite probar directamente la lógica sin depender de la entrada por consola ni de la salida por pantalla, haciendo que las pruebas sean más limpias, controladas y fáciles de automatizar.

Al centrarse únicamente en la lógica de los métodos, el proyecto facilita la validación del comportamiento del código mediante pruebas unitarias, mejorando la mantenibilidad y reduciendo la probabilidad de errores en futuras modificaciones.

2. Revisa las pruebas de la suma y comenta lo que te parezca de interés
   
-Lo que me ha llamado la atención es que el test de la suma está  limpio porque no se usan variables intermedias. En vez de andar creando el valor1, el valor2 y el esperado fuera, mete la llamada a la función directamente en el assertEquals.

Lo bueno de usar el assertAll, a diferencia de un test normal, es que si la primera suma falla, el programa no se detiene ahí (lo que nos dejaría sin saber qué pasa con las demás). Aquí, al usar las lambdas (las flechitas ->), el test lanza todas las pruebas a la vez. Así, si la calculadora falla en una pero acierta en otra, te enteras de todo el "pastel" de golpe y no tienes que ir arreglando y probando una por una.

La única diferencia que hay respecto al resultado de las pruebas es que sumarPositivosMal da error debido al valor esperado, ya que el valor es de cuatro y, según las otras variables, debería ser cinco.


3. Realiza un estudio de caja negra de la división e implementa las pruebas en junit: Se realizará en markdown.


| Caso de Prueba | Entrada (Dividendo, Divisor) | Resultado Esperado | Tipo de prueba |
| :--- | :--- | :--- | :--- |
| **División exacta** | (18, 2) | 9 | Valor válido (Positivos) |
| **Resultado negativo** | (10, -2) | -5 | Valor válido (Signos) |
| **Dividendo cero** | (0, 9) | 0 | Valor limite |
| **División entera** | (15, 4) | 2 | Comportamiento truncado por el tipo de variable int |
| **División por cero** | (6, 0) | OperacionNoValidaException | Error (Excepción controlada) |
