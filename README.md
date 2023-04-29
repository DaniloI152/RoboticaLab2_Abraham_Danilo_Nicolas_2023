## Laboratorio 3 Robótica
### Integrantes: 
- Danilo Enrique Insuasty Delgado.
- Abraham Másmela Ramirez
- Nicolás Prieto Solano
## Descripción
Se hace un acercamiento a ROS  (Rootic Operative System) y sus comandos principales, realizano la conexión de ROS con Matlab y Python.
## Objetivos:
Escribir un código que permita operar una tortuga del paquete turtlesim con el teclado, cumpliendo con las siguientes especificaciones: <br>
• Movimiento hacia adelante y hacia atrás con las teclas W y S. <br>
• Giros en sentido horario y antihorario con las teclas D y A. <br>
• Retornar a la posición y orientación centrales con la tecla R. <br>
• Giro de 180° con la tecla ESPACIO. <br>
## Desarrollo:
### Comunicación con matlab:
En primer momento se realiza la comunicación con Matlab con el código propuesto en la guía, donde se logra mover la tortuga cada vez que es ejecutada la tercera sección del código.

<div>
  <p style = 'text-align:center;' align="center">
    <img src="https://github.com/DaniloI152/RoboticaLab3_Abraham_Danilo_Nicolas_2023/blob/main/Imagenes/Turtle.png" width="800px">
  </p>
  <p style = 'text-align:center;' align="center">
    Figura 1. Movimiento de la tortuga con Matlab.
  </p>
</div>
<div>
  <p style = 'text-align:center;' align="center">
    <img src="https://github.com/DaniloI152/RoboticaLab3_Abraham_Danilo_Nicolas_2023/blob/main/Imagenes/Códigos.png" width="800px">
  </p>
  <p style = 'text-align:center;' align="center">
    Figura 2. Visualización de las terminales.
  </p>
</div>
La creación del script se realizó en python como se muestra a continuación.<br>

### Comunicación con python:
<p>El <a href='/myTeleopKey.py'>codigo en python</a> que se encuentra en  esta dirección consiste en primer lugar de una funcion que recibe las teclas oprimidas dentro del sistema opertivo de linux diferente al objeto Keyboard ya que este da problemas en este sistema operativo, la funcion para obtener las teclas fue obtenida de un <a href='http://python4fun.blogspot.com/2008/06/get-key-press-in-python.html'>codigo</a> provisto en la guia de laboratorio.</p>
<p>Con la funcion que detecta las teclas del teclado se crea una función main que inicializa un nodo de ROS, que usa un Publisher, con el topic de cmd_vel para controlar la velocidad de la tortuga y por lo tanto su movimiento directo, y 2 ServiceProxy que utilizan el servicio de TeleportAbsolute para reiniciar la posicion de la tortuta y el servicio TeleportRelative para girar 180 grados la direccion actual de la tortuga. Dentro del ciclo while con condicional de siempre que ROS este activo, se crea una funcion que guarda el valor actual de la tecla precionada como un numero binario de 8 bits, se reincian los valores del mensaje a 0 para que las interaciones anteriores no afecten el funcionamiento, mediante una serie de condicionales se compara cual tecla fue presionada y en caso de ser 'w' o 's' se cambia la velocidad en x por 1 o -1 respectivamente, en caso de ser 'a' o 'd' se cambia la velocidad angular en z por 1 o -1 respectivamente, pero en caso de ser 'r' o ' ' se ejecuta el ServicePRoxy definido al inicio del codigo con los valores para reiniciar la posicin de la tortuga en caso de haber precionado 'r' o con una rotacion relativa de pi en caso de haber presionado la barra espaciadora. Esta funcion main esta dentro de un if que se ejecuta al llamar el nombre del programa que a su vez tienen un try-except.  </p>
