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
***
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

***

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
En esta parte del entregable la práctica se centra en cuestiones teóricas tales como: la asignación de direcciones IPv4 o la manipulación del enrutamiento de la red por medio de las interfaces de red ( *ethX* ) y la tabla de enrutamiento.

Además se introducirán todos los pasos y comandos básicos necesarios para la configuración de las interfaces de red de los host y los router, la comprobación de sus estados y el enrutamiento entre las redes de la organización. Estos comandos se encuentran detallados en el [listado del apartado 4 del informe](#id4)

<br>
<br>

### **Descripción del concepto**


La asignación de direcciones IPv4 va a requerir de una serie de cálculos explicados en la teoría de la asignatura. En base al número de bloques, redes y el prefijo global de la red ( que lo suministra el ISP y debe ser indicado ) se determinará un prefijo a cada una de las redes del sistema que debemos configurar. En resumen esto nos permitirá hallar datos necesarios para la configuración como:

- Dirección de red
- Máscara de red
- Dirección broadcast
- Dirección de cada uno de los host de nuestra red

Cabe destacar que en la asignación de redes a cada host no podemos asignar ni la dirección de red ni la dirección broadcast, ya que estos son reservados para este propósito.

Para aplicar el direccionamiento IPv4 debemos tener en cuenta una serie de aspectos que son cruciales para su cálculo:

- Las direcciones IP se componen por 32 bits, separados por grupos de 8 bits, que son separados por un punto y escritos en notación decimal. Van desde *0.0.0.0* hasta *255.255.255.255* .

- Estas direcciones se dividen en dos componentes uno de **red**; que denota la red en la que estamos direccionando y uno de **host** que indica el dispositivo concreto al que estamos haciendo referencia. 

- Para distinguir el número de bits al que corresponde cada división empleamos la máscara de red. Esta es un número de 32 bits similar a la dirección IPv4 donde los *1´s* indican la parte de red y los *0's* la de host.

- Se pueden emplear la notacion decimal o, en nuestro caso, la CIDR que indicará el número de bits que corresponden a la parte de red tras una barra ( **/n** ). El número de bits de host se deduce como  32 - n, donde n es la cifra en CIDR.

Tal como se menciona, la notación a emplear es la CIDR para las máscaras de red. De esta manera pretendemos indicar que se emplea un direccionamiento sin clases. Este tipo de direccionamiento nos permite un uso más economizado de la red por medio de una asignación VLSM (Virtual Length Subnet Mask) de las máscaras de red, cuyo tamaño de bloque ajusta el número de bloques necesarios respecto al número de hosts.

El encaminamiento que se emplea es estático, por ende las rutas entre cada par de nodos es permanente. El cómputo de la ruta a seguir dentro de la red en este sistema emplea algoritmos de caminos mínimos tales como *Dijksta* o *Bellman-Ford*.

Se detalla la función de reenvío de la capa de red aplicando la tabla de enrutamiento de los dispositivos de red. Es en este punto donde estableceremos las interfaces de red y sus redes relacionadas. Se debe destacar que cada router debe disponer de su propia tabla de enrutamiento. Nos deben quedar claros los dos apartados que la componen:

- Patrón: Que denota la entrada a la que se dirige por medio de la red y su máscara.

- Acción: Que denota la red hacia la que se va a redirigir.

Las entradas de la tabla de enlace podrán ser:

- Directas: que indican las redes directamente conectadas al dispositivo. Por ejemplo en nuestra práctica, para el dispositivo *QuaggaRouter-1* son las redes *A* y *D* tal y como se puede apreciar en [la plantilla](#plantilla)

- No Directas: que requieren de, al menos ,pasar por otro dispositivo de red y que a diferencia de las directamente conectadas requieren que se les indique un *gateway*. El ***gateway*** no es otra cosa que la dirección de la interfaz de red del primer salto efectuado para el acceso a la red. Esta se indica en el apartado de acción. Para el dispositivo *QuaggaRouter-1* son las redes *B*, *C* y *E*. Para este el gateway de acceso a la red *C* sería la dirección introducida en el *eth0* del *QuaggaRouter-2*.

Conceptos más avanzados del direccionamiento y la redirección tales como la sumarización de redes o el uso de algoritmos de enrutamiento serán aplicados y expuestos en el [apartado 3 de este informe](#id3).




<br>
<br>

### **Descripción de los pasos realizados**

Para realizar la práctica partimos de una plantilla que contiene la estructura básica de las redes que componen el sistema. Los dispositivos están conectados pero no configurados por lo que no hay tráfico de red entre ellos. Nuestra labor es, por medio de cada una de las interfaces, configurar todos los aspectos necesarios para su comunicación en calidad de que se establezca un enrutamiento estático.

La plantilla sobre la que se va a operar consta de 3 router interconectados entre sí, donde dos de ellos se disponen a los extremos y cada uno de ellos sirve de enlace para cada una de las redes de hosts, que también son 3. Cada una de las redes de hosts contiene de un número de equipos concreto que, en orden, son: 50, 127 y 30.


<div id="plantilla"></div>


![imagen de la plantilla de la red](.images/)

Una vez hemos aclarado la topología de nuestra red se puede comenzar con el diseño de la misma. De esta manera el primer paso es realizar una asignación de las  direcciones de nuestra red. Para ello hay que tener en cuenta los aspectos teóricos mencionados en el anterior apartado ya que vamos a aplicar un método VLSM de direccionamiento IPv4. 

De esta manera vamos a deducir el tamaño de los bloques hallando la primera potencia de 2 que se ajuste al número de hosts más las dos direcciones especiales de broadcast y red:

- Para A: 50 + 2 &#8594; 2^6 = 64
- Para B: 127 + 2 &#8594; 2^8 = 256
- Para C: 30 + 2 &#8594; 2^5 = 32

y para el tamaño de los bloques de las redes de interconexión de los router debemos aplicar las dos direcciones de la conexión punto a punto más las dos especiales:

- Para D: 2 + 2 &#8594; 2^2 = 4
- Para E: 2 + 2 &#8594; 2^2 = 4

Una vez tenemos el tamaño de los bloques se puede deducir fácilmente el número de la máscara de red en CIDR. Este se obtiene restando a 32 (que son todas las direcciones posibles) el número de la potencia de la que se obtiene el bloque (que indica la cantidad de hosts direccionables), este resultado no es otro que la parte de red de la máscara así pues:

- Para A: 32 - 6 = /26 
- Para B: 32 - 8 = /24
- Para C: 32 - 5 = /27
- Para D: 32 - 2 = /30
- Para E: 32 - 2 = /30

Para finalizar la asignación de las direcciones IPv4 solo quedaría disponer todo en una tabla ordenando las redes de mayor a menor número de hosts y calcular cada una de las direcciones de red realizando el desplazamiento del tamaño del bloque dentro del prefijo. El broadcast será el resultado de la suma entre la dirección base y el tamaño del bloque - 1.

Una vez disponemos de los prefijos de cada subred solo quedaría asignar una dirección a cada uno de los dipositivos del esquema de manera que estas direcciones se encuentren dentro de su parte de la red y no ocupen ni la dirección de red ni la de broadcast.

En este caso se asignan en el siguiente orden: **[ router  ]&#8594; [ PC-1 ]&#8594; [ PC-2 ] · · · &#8594; [ PC-N ]**

(Este orden no condiciona los resultados)

    Por ejemplo en la red A (8.0.1.0/26):

        Router 1 = 8.0.1.1/26
        Router 2 = 8.0.1.2/26
        Router 3 = 8.0.1.3/26

Para asignar estas direcciones debemos emplear una serie de comandos a través de la consola de cada uno de los dispositivos de red y de los PC que vamos a conectar. 

Comenzando por los PC de la red el proceso puede optar por varias soluciones. La primera de ellas es acceder a la linea de comandos *(click derecho sobre el dispositivo > abrir consola)* y una vez allí activar de forma manual la interfaz de red que vayamos a conectar con la dirección IP que le corresponde:

1. Visualizar el estado de las interfaces de red, usamos: ```ifconfig ``` o ```ip addr show```
    > Esto nos permitirá evaluar los cambios que debemos aplicar y en qué interfaz.

2. Para establecer una dirección de red a una interfaz se emplea: &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;```ifconfig [INTERFAZ] [DIRECCIÓN IPv4/MÁSCARA]``` o ```ip addr add [DIRECCIÓN IPv4/MÁSCARA] dev [INTERFAZ]```

    > para poder aplicar estos comandos debe ingresar como super usuario. Para reasignar con **ifconfig** solo se repite el comando con una dirección nueva, pero con **ip addr** se debe borrar la anterior dirección asignada a la interfaz.

Sin embargo esta configuración no permanecerá tras el reinicio de las máquinas. Para poder establecer unas direcciones que permanezcan activas se debe editar un fichero que contiene la confifuración de las interfaces de red: ```/etc/network/interfaces```. Este será leido por el sistema operativo de los ordenadores para que, en el arranque, sean configuradas estas interfaces. Se debe editar de la siguiente manera:
```bash

    auto [INTERFAZ]
    iface [INTERFAZ] inet static
    address [DIRECCIÓN IPv4/MÁSCARA]
    gateway [DIRECCIÓN GATEWAY]

    #auto otrainterfaz
    iface otrainterfaz inet dhcp

```
Tal y como se puede apreciar en el fragmento de código anterior hay que efectuar una serie de pasos:

1. descomentar la linea auto de la interfaz a establecer.
    >Esto va a permitir configurar la interfaz en el arranque del sistema.
2. cambiar la inet de ***dhcp*** a ***static***.
    > Para aplicar enrutamiento estático.
3. añadir la dirección de red del dispositivo junto con su máscara en CIDR.
4. añadir la dirección del ***gateway*** (sin máscara ya que en este caso no aplica)
    > El *gateway* corresponde con la dirección de red de la primera interfaz contactada a la hora de realizar un salto hacia otra red (la interfaz del router que conecta con el PC) 

Una vez terminado de editar este fichero se debe guardar y ejecutar: ```ifup [INTERFAZ]```

Este último paso activará la interfaz y aplicará la configuración. En caso de necesitar resetear la interfaz se debe volver a encender con el mismo comando tras apagarla usando: ```ifdown [INTERFAZ]```

Esta configuración se debe aplicar a todos los PC's de la red que estamos configurando en base a sus interfaces y sus direcciones IP.

Tras haber configurado los PC's habrá que configurar los router mediante la linea de comando de los mismos. Para ello debemos abrir la terminal del router tal y como se ha hecho con los PC. Una vez dentro accederemos a la plataforma Quagga que permite la configuración mediante un sistema Linux. Para acceder a la configuración:

1. Ejecutar el comando `vytsh`
    >Esto abrirála interfaz de comandos del sistema de enrutamiento Quagga. Por defecto como usuario privilegiado.
2. Ejecutar `configure terminal`
    >En este punto ya podremos ejecutar los comandos de cinfiguración del dispositivo de red.
3. Ejecutar `interface [INTERFAZ]`
    >Tras esto accederemos específicamente a la configuración de la interfaz de red indicada
4. Asignar la dirección IP a la interfaz mediante: `ip address [DIRECCIÓN IP/MÁSCARA]`.
5. Debemos activar la interfaz para que se ponga en marcha: `no shutdown`.
6. También activaremos la detección del enlace: `link-detect`.
7. Debemos salir de la interfaz de configuración con: `exit`.

Este proceso debe repetirse con cada una de las interfaces del router. Una vez hecho se sale del modo de configuración ejecutando `exit` y antes de finalizar con este router se deben guardar los cambios ejecutando `write` , de lo contrario al reiniciar el sistema esta configuración será deshecha.

La configuración de las interfaces debe repetirse con todos los router de la red y una vez esto se haya finalizado tendremos establecidas conexiones punto a punto. Estas conexiones las podremos comprobar ejecutando el comando `ping [DIRECCIÓN]` con cada una de las conexiones directas de cada red, sin embargo no será posible acceder a redes no directamente conexas. Para solucionar esto, dado que el enrutamiento es estático se deben configurar manualmente cada una de las tablas de enrutamiento de cad auno de los dispositivos de red.

![imagen de ping exitoso en punto a punto](./images/)

![imagen de ping fallido a otra red](./images/)

1. Volver a entrar a la interfaz de configuración de la terminal del router: consola > `vtysh` > `configure terminal` 

2. Ejecutar: `ip route [DIRECCIÓN/MÁSCARA] [GATEWAY]`
> Con este comando introducimos el enlace de destino y el gateway al que queremos acceder, añadiendo así de manera estática una entrada en la tabla de enrutamiento.

Esto se debe hacer con cada una de las redes que queramos conectar en cada router de la topología. De nuevo cabe recordar que si queremos que se guarde el cambio se debe executar `write` en la interfaz de ***vtysh***. De lo contrario la configuración, al reiniciar las máquinas, desaparecería.

En este punto ya podríamos ejecutar el comando `ping [DIRECCIÓN]` y se debería de poder acceder a cualquier red desde cualquier dispositivo. En caso negativo ejecutar el comando `traceroute` nos dará pistas del disposit6ivo que está mal configurado y donde puede localizarse el error.

![imagen de ping exitoso entre dos redes](./images/)

El último paso que restaría sería configurar las rutas por defecto en los router para resolver solicitudes en la tabla que no coincidad con las entradas ya dispuestas. En este caso se envía la ruta por defecto hacia ***QuaggaRouter-1***. Por ende, en cada uno de los router debemos seguir los siguientes pasos:

1. Entrar en la interfaz de configuración del router como se ha hecho anteriormente: consola > `vtysh` > `configure terminal` 

2. Ejecutar ``ip route 0.0.0.0 0.0.0.0 [GATEWAY]``
> Este comando añade una entrada a la tabla de enrutamiento que hará coincidir en caso de no asignarse a ninguna de las redes previstas. Esta debe ser todo 0 y su máscara de red debe ser igualmente todo 0. Por otro lado la interfaz a la que se dirige debe ser el gateway hacia *QuaggaRouter-1*.

Esto debe repetirse en todos los router.

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

###### eric

###### noah

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