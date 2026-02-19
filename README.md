# Testing con Junit

Este es un ejemplo sencillo de pruebas unitarias usando Junit 5

Observa que este proyecto no tiene ninguna clase con el método `main`, no nos hace fatal. Además, tampoco tiene ningún `scanner` ni ningún `print`.

Haz un fork de este proyecto en tu repositorio de Github y contesta a las siguientes preguntas:

1. ¿Qué sentido puede tener este proyecto y para que lo podrías usar?
-Este proyecto tiene sentido en un entorno profesional donde se quiera garantizar la calidad del software mediante pruebas automatizadas. No está diseñado como una aplicación tradicional, ya que no utiliza Scanner, no tiene método main y tampoco incluye instrucciones println.

En lugar de trabajar con variables inicializadas dentro del propio programa, los valores se pasan como parámetros a los métodos. Esto permite probar directamente la lógica sin depender de la entrada por consola ni de la salida por pantalla, haciendo que las pruebas sean más limpias, controladas y fáciles de automatizar.

Al centrarse únicamente en la lógica de los métodos, el proyecto facilita la validación del comportamiento del código mediante pruebas unitarias, mejorando la mantenibilidad y reduciendo la probabilidad de errores en futuras modificaciones.

2. Revisa las pruebas de la suma y comenta lo que te parezca de interés
- Lo que me ha llamado la atención es que el test de la suma está súper limpio porque pasa de usar variables intermedias. En vez de andar creando el valor1, el valor2 y el esperado fuera, mete la llamada a la función directamente en el assertEquals. Al final, lo que ves es: 'quiero un 5 y llamo a la suma con 1 y 4', sin dar rodeos.

Además, lo bueno de usar el assertAll es que no se rinde. En un test normal, si la primera suma falla, el programa se para ahí y no sabes qué pasa con las demás. Aquí, al usar las lambdas (las flechitas ->), el test lanza todas las pruebas a la vez. Así, si la calculadora falla en una pero acierta en otra, te enteras de todo el pastel de golpe y no tienes que ir arreglando y probando una por una

3. Realiza un estudio de caja negra de la división e implementa las pruebas en junit: Se realizará en markdown.



## Instrucciones

El alumno deberá hacer un fork de este proyecto e implementar la solución solicitada (preguntas y código).

>Se deberá utilizar este fichero, y los artefactos de código del proyecto, para resolver el ejercicio.


**Si no se puede acceder al repositorio la evaluación del ejercicio será de 0. No se evaluarán entregas modificadas/entregadas fuera del plazo establecido en la tarea**