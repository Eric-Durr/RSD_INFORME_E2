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

    Informe realizado por Éric Dürr Sierra y Noah Sanchez
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

A continuación se muestra una lista que contiene cada uno de los comandos empleados en ambas prácticas junto a sus argumentos. En cada uno de ellos se detalla dónde son empleados y su utilidad .
 
- **`ifconfig`**
> **Se ejecuta en:** Terminal Linux | host.

> **Función:** Ejecutado sin argumentos proporciona información sobre las interfaces de red activas, su estado y su configuración.
- **`ip addr show`**
> **Se ejecuta en:** Terminal Linux | host.

> **Función:** Se muestra información relativa a las direcciones de las tarjetas de red activas.
- **`ifconfig [INTERFAZ] [DIRECCIÓN HOST/MÁSCARA]`**
> **Se ejecuta en:**  Terminal Linux | host.

> **Función:** Permite configurar una interfaz de red para establecer una dirección IP .
- **`ip addr add [DIRECCIÓN HOST/MÁSCARA] dev [INTERFAZ]`**
> **Se ejecuta en:** Terminal Linux | host.

> **Función:** Permite añadir a una interfaz de red  una dirección IP .
- **`ip addr del [DIRECCIÓN HOST/MÁSCARA] dev [INTERFAZ]`**
> **Se ejecuta en:** Terminal Linux | host.

> **Función:** Permite eliminar a una interfaz de red su dirección IP.
- **`route -n`**
> **Se ejecuta en:** Terminal Linux | host.

> **Función:** Permite visualizar la tabla de enrutamiento del host en cuestión.
- **`ip route show`**
> **Se ejecuta en:** Terminal Linux | host .

> **Función:** Permite visualizar la tabla de enrutamiento del host en cuestión.
- **`route add default gw [DIRECCIÓN GATEWAY]`**
> **Se ejecuta en:**  Terminal Linux | host.

> **Función:** Añade una entrada a la tabla de enrutamiento.
- **`ip route add default via [DIRECCIÓN GATEWAY]`**
> **Se ejecuta en:** Terminal Linux | host.

> **Función:** Añade una entrada a la tabla de enrutamiento. 
- ```ps
    #/etc/networ/interfaces
    
    auto eth0
    iface eth0 inet static
    address 8.0.0.2/24
    gateway 8.0.0.1
  ```
> **Función:** Configurar de manera automática las interfaces de red de los host.
- **`ifup [INTERFAZ]`**
> **Se ejecuta en:** Terminal Linux | host.

> **Función:** Activar la interfaz de red 
- **`ifdown [INTERFAZ]`**
> **Se ejecuta en:** Terminal Linux | host.

> **Función:** Desactivar la interfaz de red
- **`vtysh`**
> **Se ejecuta en:** Terminal Linux | router.

> **Función:** Entrar a la linea de comandos de configuración del router.
- **`show interfaces`**
> **Se ejecuta en:** Terminal vtysh | router.

> **Función:** Ver las interfaces de red y su configuración. 
- **`show ip route`**
> **Se ejecuta en:** Terminal vtysh | router.

> **Función:** Ver la tabla de enrutamiento del router.
- **`configure terminal`**
> **Se ejecuta en:** Terminal vtysh | router.

> **Función:** Acceder a la interfaz de configuración del router.
- **`exit`**
> **Se ejecuta en:** Terminal de configuración | router.

> **Función:** Salir de la interfaz actual.
- **`no [COMANDO]`**
> **Se ejecuta en:** Terminal de configuración | router.

> **Función:** Se emplea para deshacer cualquier comando realizado en la configuración.
- **`write`**
> **Se ejecuta en:** Terminal de configuración | router.

> **Función:** Permite guardar los cambios de manera permanente.
- **`interface [INTERFAZ]`**
> **Se ejecuta en:** Terminal de configuración | router.

> **Función:** Permite acceder a la interfaz de configiuración de una interfaz de red dentro del router.
- **`ip address [DIRECCIÓN/MÁSCARA]`** 
> **Se ejecuta en:**Terminal de configuración parte de interfaz | router.

> **Función:** Establece una dirección IP para la interfaz que se configura.
- **`no ip address [DIRECCIÓN/MÁSCARA]`** 
> **Se ejecuta en:** Terminal de configuración parte de interfaz | router.

> **Función:** Elimina una dirección IP de la interfaz que se configura.
- **`no shutdown`**
> **Se ejecuta en:** Terminal de configuración parte de interfaz | router.

> **Función:** Activa la interfaz de red.
- **`link-detect`**
> **Se ejecuta en:** Terminal de configuración parte de interfaz | router.

> **Función:** Activa la detección de enlaces para la interfaz de red.
- **`ip route [DIRECCIÓN RED/MÁSCARA] [GATEWAY]`**
> **Se ejecuta en:** Terminal de configuración | router.

> **Función:** Añade una entrada a la tabla de enrutamiento del dispositivo de red.
- **`no ip route [DIRECCIÓN RED/MÁSCARA] [GATEWAY]`**
> **Se ejecuta en:** Terminal de configuración | router.

> **Función:** Elimina una entrada a la tabla de enrutamiento del dispositivo de red.

- **`ip route 0.0.0.0 0.0.0.0 [GATEWAY]`**
> **Se ejecuta en:** Terminal de configuración | router.

> **Función:** Establece una ruta por defecto para el router.

- **`router rip`**
> **Se ejecuta en:** Terminal de configuración | router.

> **Función:** Accede a la configuración del router para RIP.
- **`version 2`**
> **Se ejecuta en:** Terminal de configuración parte de rip | router.

> **Función:** Activa la versión 2 del protocolo RIP en el PC.
- **`network [DIRECCIÓN RED/MÁSCARA]`**
> **Se ejecuta en:** Terminal de configuración parte de rip | router.

> **Función:** Especifica rutas a las que se le va a aplicar RIP para publicarlas.
- **`ping [DIRECCIÓN DISPOSITIVO DESTINO]`**
> **Se ejecuta en:** Terminal Linux y vtysh | host y router. 

> **Función:** Envía una serie de paquuetes a otro dispositivo para comprobar la conexión.
- **`traceroute [DIRECCIÓN DISPOSITIVO DESTINO]`**
> **Se ejecuta en:** Terminal Linux y vtysh | host y router.

> **Función:** Emite un paquete que se emplea para determinar la ruta que se sigue para alcanzar el destino indicado.
- **`passive-interface [INTERFAZ]`**
> **Se ejecuta en:** Terminal de configuración parte de rip | router.

> **Función:** Configurar una interfaz de red como interfaz pasiva.
- **`neighbor [DIRECCIÓN DISPOSITIVO VECINO]`**
> **Se ejecuta en:** Terminal de configuración parte de rip | router.

> **Función:** Este comando le indica al protocolo que debe comunicarse con actualizaciones unicast a un vecino específico.

- **`key chain kal`**
> **Se ejecuta en:** Terminal de configuración | router.

> **Función:** Abre la interfaz de configuración de la clave del router.
- **`key [id]`**
> **Se ejecuta en:** Terminal de configuración parte de key | router.

> **Función:** Establece el número identificativo para una clave de autenticación
- **`key-string [TEXTO]`**
> **Se ejecuta en:** Terminal de configuración parte de key | router.

> **Función:** Establece el valor de cadena de texto para la clave.
- **`ip rip authentication mode text`**
> **Se ejecuta en:** Terminal de configuración parte de interfaz | router.

> **Función:** Establece un modo de autentificación mediante texto en la interfaz indicada
- **`ip rip authentication key-chain kal`**
> **Se ejecuta en:** Terminal de configuración parte de interfaz | router.

> **Función:** Activa la autentificación en la interfaz y configura la clave.
- **`default-information originate`**
> **Se ejecuta en:** Terminal de configuración parte de rip | router.

> **Función:** Activa un dispositivo de red como fuente de información por defecto.


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

###### eric

###### noah
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