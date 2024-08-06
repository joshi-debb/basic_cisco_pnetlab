
# Manual Técnico

## Sección 1: Tabla de direcciones IP utilizadas 🖧

#### Tabla descriptiva de dispositivos de red:

|Dispositivo ⚙️|Interfaz 🔌|Dirección IP 🔍|Máscara de Subred 🎭|
|----|:----:|:----:|----|
|🌐 Central|s1/0|10.0.0.1|255.255.255.252|
|🌐 Central|e0/0|128.168.1.2|255.255.255.248|
|🌐 Central|e0/1|128.168.2.2|255.255.255.248|
|🌐 R2|e0/0|128.168.1.1|255.255.255.248|
|🌐 R2|e0/1|128.168.0.2|255.255.255.0|
|🌐 R3|e0/0|128.168.2.1|255.255.255.248|
|🌐 R3|e0/1|128.168.0.3|255.255.255.0|
|🌐 R2-R3|Virtual|128.168.0.1|255.255.255.0|
|💻 VPC 11|eth0|128.168.0.4|255.255.255.0|
|🌐 Villa_Nueva|s1/0|10.0.0.2|255.255.255.252|
|🌐 Villa_Nueva|e0/0|128.178.1.1|255.255.255.248|
|🌐 Villa_Nueva|e0/1|128.178.2.1|255.255.255.248|
|🌐 R5|e0/0|128.178.1.2|255.255.255.248|
|🌐 R5|e0/1|128.178.0.2|255.255.255.0|
|🌐 R6|e0/0|128.178.2.2|255.255.255.248|
|🌐 R6|e0/1|128.178.0.3|255.255.255.0|
|🌐 R5-R6|Virtual|128.178.0.1|255.255.255.0|
|💻 VPC 12|eth0|128.178.0.4|255.255.255.0|


## Sección 2: Tabla de rangos de IP disponibles 🖧

|ID de Red 🆔|Máscara de Subred 🎭|Total IPs disponibles 📚|Primera IP ⬇️|Ultima IP ⬆️|Direccion Broadcast 📍|Tipo Red📡|
|----|:----:|:----:|:----:|:----:|:----:|----|
|🌐 10.0.0.x|255.255.255.252|2|10.0.0.1|10.0.0.2|10.0.0.3|Clase A|
|🌐 128.168.0.x|255.255.255.0|254|128.168.0.1|128.168.0.254|128.168.0.255|Clase B|
|🌐 128.168.1.x|255.255.255.248|6|128.168.1.1|128.168.1.6|128.168.1.7|Clase B|
|🌐 128.168.2.x|255.255.255.248|6|128.168.2.1|128.168.2.6|128.168.2.7|Clase B|
|🌐 128.178.0.x|255.255.255.0|254|128.178.0.1|128.178.0.254|128.178.0.255|Clase B|
|🌐 128.178.1.x|255.255.255.248|6|128.178.1.1|128.178.1.6|128.178.1.7|Clase B|
|🌐 128.178.2.x|255.255.255.248|6|128.178.2.1|128.178.2.6|128.178.2.7|Clase B|



## Sección 3: Configuraciones 🚀

##### Router Central:

- interface Ethernet0/0
- ip address 128.168.1.2 255.255.255.248
- duplex auto

- interface Ethernet0/1
- ip address 128.168.2.2 255.255.255.248
- duplex auto

- interface Serial1/0
- ip address 10.0.0.1 255.255.255.252
- serial restart-delay 0

- ip route 128.168.0.0 255.255.255.0 128.168.1.1
- ip route 128.168.0.0 255.255.255.0 128.168.2.1
- ip route 128.178.0.0 255.255.255.0 10.0.0.2
- ip route 128.178.1.0 255.255.255.248 10.0.0.2
- ip route 128.178.2.0 255.255.255.248 10.0.0.2

##### Router R2:

- interface Ethernet0/0
- ip address 128.168.1.1 255.255.255.248
- duplex auto

- interface Ethernet0/1
- ip address 128.168.0.2 255.255.255.0
- glbp 1 ip 128.168.0.1
- glbp 1 priority 200
- duplex auto

- ip route 10.0.0.0 255.255.255.252 128.168.1.2
- ip route 128.168.1.0 255.255.255.248 128.168.1.2
- ip route 128.178.0.0 255.255.255.0 128.168.1.2
- ip route 128.178.1.0 255.255.255.248 128.168.1.2
- ip route 128.178.2.0 255.255.255.248 128.168.1.2

- GBLP
    - enable
    - configure terminal
    - hostname R2
    - interface Ethernet 0/1
    - ip address 128.168.0.2 255.255.255.0
    - no shutdown
    - glbp 1 ip 128.168.0.1
    - glbp 1 preempt
    - glbp 1 priority 150
    - glbp 1 load-balancing round-robin
    - do write

##### Router R5:

- interface Ethernet0/0
- ip address 128.178.1.2 255.255.255.248
- duplex auto

- interface Ethernet0/1
- ip address 128.178.0.2 255.255.255.0
- standby version 2
- standby 0 priority 109
- standby 0 preempt
- standby 1 ip 128.178.0.1
- duplex auto

- ip route 10.0.0.0 255.255.255.252 128.178.1.1
- ip route 128.168.0.0 255.255.255.0 128.178.1.1
- ip route 128.168.1.0 255.255.255.248 128.178.1.1
- ip route 128.168.2.0 255.255.255.248 128.178.1.1
- ip route 128.178.1.0 255.255.255.248 128.178.1.1

- HSRP
    - enable
    - configure terminal
    - hostname R5
    - interface Ethernet 0/1
    - ip address 128.178.0.2 255.255.255.0
    - no shutdown
    - standby version 2
    - standby 21 ip 128.178.0.1
    - standby 21 priority 109
    - standby 21 preempt
    - do write

##### Switch SW7:

- configure terminal
- interface range e0/2-3
- channel-group 1 mode active
- no shutdown

##### VPC11:
- Paso 1 - Asignar direccion IP:
    - Ingresar a la maquina VPC11
    - Ingresar Comando: ip 128.168.0.x/24 128.168.0.1
        - Donde x es igual al id de host valido
        - Donde /24 indica la mascara de subred
            - Es equivalente a 255.255.255.0
        - Donde 0.1 indica Gateway

- Paso 2 - Conectar VPC a Switch:
    - Conectar cable desde el switch al VPC

- Paso 3 - Verificar Coneccion:
    - Ingresar comando: 
        - ping 128.178.0.4

- Resultado 💻 VPC11:
    - Dirección IP: 128.168.0.4
    - Máscara de Subred: 255.255.255.0


## Sección 4: Comandos ⌨️

### Comandos Utilizados - Ruta Estatica

- Central
    - ip route 128.168.0.0 255.255.255.0 128.168.1.1
    - ip route 128.168.0.0 255.255.255.0 128.168.2.1
    - ip route 128.178.0.0 255.255.255.0 10.0.0.2
    - ip route 128.178.1.0 255.255.255.248 10.0.0.2
    - ip route 128.178.2.0 255.255.255.248 10.0.0.2

- Villa_Nueva
    - ip route 128.168.0.0 255.255.255.0 10.0.0.1
    - ip route 128.168.1.0 255.255.255.248 10.0.0.1
    - ip route 128.168.2.0 255.255.255.248 10.0.0.1
    - ip route 128.178.0.0 255.255.255.0 128.178.1.2
    - ip route 128.178.0.0 255.255.255.0 128.178.2.2

- R2
    - ip route 10.0.0.0 255.255.255.252 128.168.1.2
    - ip route 128.168.1.0 255.255.255.248 128.168.1.2
    - ip route 128.178.0.0 255.255.255.0 128.168.1.2
    - ip route 128.178.1.0 255.255.255.248 128.168.1.2
    - ip route 128.178.2.0 255.255.255.248 128.168.1.2

- R3
    - ip route 10.0.0.0 255.255.255.252 128.168.2.2
    - ip route 128.168.2.0 255.255.255.248 128.168.2.2
    - ip route 128.178.0.0 255.255.255.0 128.178.2.2
    - ip route 128.178.1.0 255.255.255.248 128.168.2.2
    - ip route 128.178.2.0 255.255.255.248 128.168.2.2

- R5
    - ip route 10.0.0.0 255.255.255.252 128.178.1.1
    - ip route 128.168.0.0 255.255.255.0 128.178.1.1
    - ip route 128.168.1.0 255.255.255.248 128.178.1.1
    - ip route 128.168.2.0 255.255.255.248 128.178.1.1
    - ip route 128.178.1.0 255.255.255.248 128.178.1.1

- R6
    - ip route 10.0.0.0 255.255.255.252 128.178.2.1
    - ip route 128.168.0.0 255.255.255.0 128.178.2.1
    - ip route 128.168.1.0 255.255.255.248 128.178.2.1
    - ip route 128.168.2.0 255.255.255.248 128.178.2.1
    - ip route 128.178.2.0 255.255.255.248 128.178.2.1


### Comandos Utilizados - Creacion de PortChannel con PAGP

- SW9
    - configure terminal
    - interface range e0/2-3
    - channel-group 1 mode desirable
    - no shutdown

- SW10
    - configure terminal
    - interface range e0/0-1
    - channel-group 1 mode auto
    - no shutdown

### Comandos Utilizados - Creacion de PortChannel con LACP

- SW7
    - configure terminal
    - interface range e0/2-3
    - channel-group 1 mode active
    - no shutdown

- SW8
    - configure terminal
    - interface range e0/0-1
    - channel-group 1 mode passive
    - no shutdown

### Comandos Utilizados - Creacion de IP virtual HSRP

- R5
    - enable
    - configure terminal
    - hostname R5
    - interface Ethernet 0/1
    - ip address 128.178.0.2 255.255.255.0
    - no shutdown
    - standby version 2
    - standby 21 ip 128.178.0.1
    - standby 21 priority 109
    - standby 21 preempt
    - do write

- R6
    - enable
    - configure terminal
    - hostname R6
    - interface Ethernet 0/1
    - ip address 128.178.0.3 255.255.255.0
    - no shutdown
    - standby version 2
    - standby 21 ip 128.178.0.1
    - do write


### Comandos Utilizados - Creacion de IP virtual GLBP

- R2
    - enable
    - configure terminal
    - hostname R2
    - interface Ethernet 0/1
    - ip address 128.168.0.2 255.255.255.0
    - no shutdown
    - glbp 1 ip 128.168.0.1
    - glbp 1 preempt
    - glbp 1 priority 150
    - glbp 1 load-balancing round-robin
    - do write

- R3
    - enable
    - configure terminal
    - hostname R3
    - interface Ethernet 0/1
    - ip address 128.168.0.3
    - no shutdown
    - glbp 1 ip 128.168.0.1
    - glbp 1 load-balancing round-robin
    - do write

### Comandos Utilizados - Configuracion de VPC

- Ingresar Comando: ip 128.168.0.x/24 128.168.0.1
    - Donde x es igual al id de host valido
    - Donde /24 indica la mascara de subred
        - Es equivalente a 255.255.255.0
    - Donde 0.1 indica Gateway


## Sección 5: Comandos para verificacion ⌨️

##### Verificacion de PAGP & LACP
- show etherchannel summary
- show pagp neighbor
- show lacp neighbor

##### Verificacion de HSRP & GLBP
- show glbp brief
- show standby brief

##### Verificacion de IP en VPCs
- show ip

##### Verificacion de rutas estaticas
- show ip route
- show running-config | section ip route

##### Verificacion de Configuracion routers
- show run | do show run