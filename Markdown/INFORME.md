# Informe 2 | Direccionamiento IP y enrutamiento

<br>


**Redes y Sistemas Distribuidos - Escuela Superior de Ingeniería y Tecnología de la ULL**


<br>
<br>
<br>
<br>
<br>
<br>
<br>

![imagen de portada del informe, grafismo de nodos interconectados](../images/routing.png)


<br>
<br>
<br>
<br>
<br>
<br>
<br>

    Informe realizado por Eric Dürr Sierra y Noah Sanchez
                           (alu0101027005)   (alu00000000)
<br>
<br>
<br>
<br>

<!-- fin de la página de portada --->

El siguiente documento contiene los distintos apartados que comprenden el informe sobre las prácticas 1 y 2 del entregable 2. A grandes rasgos pretenden hacer un repaso sobre los procesos de la capa de red (capa 4 en TCP/IP). 

También contiene un resumen de los comandos empleados así como una conclusión de evidencias del trabajo en grupo.

<br>
<br>
<br>


<div id="init"></div>

**Índice**

1. [Introducción](#id1)
2. [Enruitamiento estático](#id2) 
3. [Enruitamiento dinámico](#id3)
4. [Resumen de comandos](#id4)
5. [Evidencias del trabajo en grupo](#id5)
6. [Referencias](#id6)


<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<!-- fin de la página de índice --->
<br>
<br>
<br>
<br>



<div id="id1"></div>

## 1. INTRODUCCIÓN

<br>
<br>

### **Descripción general del entregable**

Esta entrega de prácticas se va a centrar específicamente en las particularidades de la capa de red, concretamente en los aspectos relativos al Direccionamiento IP y al enrutamiento, tanto estático como dinámico. El volumen de trabajo se ha dividido en dos prácticas distintas; la primera  de ellas se centra en el enrutamiento estático y la asignación de direcciones IP en función de las características de la red. La segunda práctica tratará de forma más específica los aspectos del enrutamiento dinámico y la sumarización de redes, asumiendo aspectos de la práctica primera no sin ponerlos en uso. 


<br>
<br>

### **Objetivos de la parte de enrutamiento estático**

La práctica 1 tiene como principales objetivos:

- Entender el proceso de asiganción de direcciones.
> Se nos proporcionan datos mediante los que deducir y calcular las direcciones IP.
- Entender el funcionamiento del enrutamiento.
> Mediante la configuración de los dispositivos de red se pretende introducir estos conceptos.
- Saber asignar direcciones a las interfaces de un host y/o router.
- Saber configurar la puerta de enlace por defecto de un host.
- Saber añadir / eliminar entradas de la tabla de enrutamiento.
- Saber añadir una ruta por defecto a los router
> Todas las anteriores son técnicas que tendremos que aprender a aplicar a la configuración de la red.


A modo de resumen esta práctica pretende introducir conceptos básicos de asignación de direcciones en una red y el enrutamiento de sus dispositivos. Es un primer contacto con
las funcionalidades que manipularemos en la red.

<br>
<br>

### **Objetivos de la parte de enrutamiento dinámico**

La práctica 2 tiene como principales objetivos:
- Conocer el funcionamiento del protocolo RIP y sus características.
- Ser capaz de hacer funcionar el enrutamiento dinámico mediante RIP en una red.
- Comprender la unidad de los comandos network y neighbor, además de la diferencia entre ellos.
- Denominar el concepto de interfaz pasiva, saber cuando se aplica y conocer los comandos necesarios.
- Saber ccómo configurar para que propague una ruta por defecto.

Se puede apreciar como en este caso se extiende de la práctica 1 y asumimos tareas que ya se han empleado anteriormente para pasar, en esta ocasión, a la configuración de los protocolos de red. Concretamente debemos adaptar los router para intercomunicarse mediante RIP (Routing Information Protocol) extendiendo también conceptos aplicados anteriormente que serán cruciales para una configuracdión "limpia" de una red con este protocolo

<br>
<br>

### **Tecnologías usadas**

En ambas prácticas debemos simular distintas redes junto a sus dispositivos de red, hosts y demás características. Para ello se emplea una interfaz gráfica de simulación de red denominada GNS3 (Graphical Network Simulator - 3) que nos facilita un entorno aislado donde cada dispositivo dispone de todas las utilidades de una máquina real.

Emplea Dynamips, un software que permite simular Cisco IOS (Cisco Internetwork Operating Systems). Que no es otra cosa que el sistema operativo empleado en múltiples routers y switches de Cisco.

Además esta herramienta de simulación nos permitirá hacer capturas de la red con el uso de Wireshark entre las distintas interfaces del entorno que estemos emulando.

![Imagen del logotipo de GNS3](./images/)

<br>
<br>
<br>
<br>


<div id="id2"></div>


## 2. ENRUTAMIENTO ESTÁTICO

contenido aquí


<br>
<br>

### Descripción del concepto

contenido aquí


<br>
<br>

### Descripción de los pasos realizados

contenido aquí


<br>
<br>
<br>
<br>


<div id="id3"></div>


## 3. ENRUTAMIENTO DINÁMICO

contenido aquí


<br>
<br>

### Descripción del concepto

contenido aquí


<br>
<br>

### Descripción de los pasos realizados

contenido aquí


<br>
<br>
<br>
<br>


<div id="id4"></div>

## 4. RESUMEN DE COMANDOS

contenido aquí

<br>
<br>
<br>
<br>


<div id="id5"></div>


## 5 .EVIDENCIAS DEL TRABAJO EN GRUPO

<br>
<br>
<br>
<br>


<div id="id6"></div>

## 6. REFERENCIAS

- [**referencia**](enlace.com)






<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>



&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&uarr;  [**Volver al inicio**](#init)