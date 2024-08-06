
# Manual Técnico

## Sección 1: Navegando por las Direcciones IP 🖧

Tabla descriptiva de dispositivos para red de servicio de courier:

|Dispositivo ⚙️ |Dirección IP 🔍|Direccion MAC 🔗   |Máscara de Subred 🎭|Nivel 🎚️|Area 📍|
|----------------|:-------------:|:-----------------:|:--------------------:|--------|--------|
|🌐 Gateway 1   |192.168.27.1   |-                   |255.255.255.0       |Primer nivel |Recepcion             |
|🎛️ Switch 1    |-              |-                   |-                   |Primer nivel |Recepcion             |
|💻 VPC 1       |192.168.27.2   |00:50:79:66:68:01   |255.255.255.0       |Primer nivel |Recepcion             |
|💻 VPC 2       |192.168.27.3   |00:50:79:66:68:02   |255.255.255.0       |Primer nivel |Recepcion             |
|💻 VPC 3       |192.168.27.4   |00:50:79:66:68:03   |255.255.255.0       |Primer nivel |Almacenamiento        |
|💻 VPC 4       |192.168.27.5   |00:50:79:66:68:04   |255.255.255.0       |Primer nivel |Almacenamiento        |
|🎛️ Switch 2    |-              |-                   |-                   |Segundo nivel|Atencion al Cliente   |
|💻 VPC 8       |192.168.27.10  |00:50:79:66:68:05   |255.255.255.0       |Segundo nivel|Atencion al Cliente   |
|💻 VPC 9       |192.168.27.11  |00:50:79:66:68:06   |255.255.255.0       |Segundo nivel|Atencion al Cliente   |
|💻 VPC 10      |192.168.27.12  |00:50:79:66:68:07   |255.255.255.0       |Segundo nivel|Atencion al Cliente   |
|💻 VPC 11      |192.168.27.13  |00:50:79:66:68:08   |255.255.255.0       |Segundo nivel|Atencion al Cliente   |
|💻 VPC 12      |192.168.27.16  |00:50:79:66:68:09   |255.255.255.0       |Segundo nivel|Oficina Administrativa|
|💻 VPC 13      |192.168.27.15  |00:50:79:66:68:0a   |255.255.255.0       |Segundo nivel|Oficina Administrativa|
|💻 VPC 14      |192.168.27.14  |00:50:79:66:68:0b   |255.255.255.0       |Segundo nivel|Oficina Administrativa|
|🎛️ Switch 3    |-              |-                   |-                   |Tercer nivel |Gerencia              |
|💻 VPC 15      |192.168.27.21  |00:50:79:66:68:0c   |255.255.255.0       |Tercer nivel |Gerencia              |
|💻 VPC 16      |192.168.27.20  |00:50:79:66:68:0d   |255.255.255.0       |Tercer nivel |Gerencia              |
|💻 VPC 17      |192.168.27.22  |00:50:79:66:68:0e   |255.255.255.0       |Tercer nivel |Operaciones           |
|💻 VPC 18      |192.168.27.23  |00:50:79:66:68:0f   |255.255.255.0       |Tercer nivel |Operaciones           |
|💻 VPC 19      |192.168.27.24  |00:50:79:66:68:10   |255.255.255.0       |Tercer nivel |Operaciones           |


## Sección 2: Hardware necesario para Implementacion 🚀

Componentes de Hardware indispensables para realizacion fisica de la instalacion de la red simulada (Marca y modelo pueden cambiar segun se ajusten a los requerimientos o presupuestos).

- 🌐 **Router Principal:**
  - Marca: Linksys
  - Nombre del modelo: E7350
  - Características especiales: Modo de invitado, Indicador LED, Control Parental, WPS, Modo invitado
  - Clase de banda de frecuencia: Banda Doble
  - Estándar de comunicación inalámbrica: 802.11ax
  - Dispositivos compatibles: Consola de juegos, Televisión inteligente, Computadora personal, Impresora, Teléfono inteligente, Tableta, Cámara de seguridad,Consola de juegos, Televisión inteligente, Computadora personal, Impresora, Teléfono inteligente, Tableta, Cámara de seguridad,
  - Frecuencia: 5 GHz
  - **Cantidad: 1**

- 🎛️ **Switch:**
  - Marca: Linksys
  - Nombre del modelo: SE3008
  - Número de puertos: 8
  - Dispositivos compatibles: Escritorio
  - **Cantidad: 3**

- 💻 **Computadoras:**
  - Marca: Dell
  - Sistema operativo: Windows 10 Pro
  - Capacidad de almacenamiento de memoria: 256 GB
  - Tamaño de la memoria RAM: 8 GB
  - Nombre del modelo: OptiPlex 3000
  - Modelo de CPU: Core i5-10505 
  - Características especiales: Microphone
    - Monitor
        - Marca:  Dell
        - Modelo: E1920H
        - Pantalla 18.5" LED
        - Resolución 1366 x 768
        - Tipo de Panel TN
        - Tasa Refresco 60 Hz
        - Relación de aspecto 16:9
        - Tiempo de respuesta 5 ms
        - Cubierta para tornillos VESA
        - 1 x Salida VGA
        - 1 x DisplayPort
    - Teclado
        - Marca: Dell
        - Modelo: SK-3205
        - USB 2.0
    
    - Mouse
        - Marca: Dell
        - Modelo: 09NK2
        - USB 2.0


  - **Cantidad: 16**

- 🔌 **Cables:**
    - Cable Ethernet
        - Marca: StarTech.com
        - Tipo de conector: RJ45
        - Tipo de cable: Ethernet
        - Dispositivos compatibles: Servidor, Rúter, Computadores
        - Categoría de cable Ethernet: Cat 6
        - Longitud de cable variable
        - Aproximadamente 32 Conectores
    - Cables de alimentacion
    - Fuentes de energia (Recomendado UPS)
        - Marca: Forza Power Technologies
        - Composición de las celdas de la batería: Plomo-Ácido
        - Dimensiones del artículo LxWxH: 16 x 6 x 11 pulgadas
        - Voltaje: 750 Voltios

        - Uno por Area (Aproximadamente 6 unidades )

- 🛠️ **Herramientas de monjate:**
    - Tornillos
    - Tuercas
    - Abrazaderas
    - Alicates de crimpado
        - Marca: KNIPEX
    - Pelacables
        - Marca: IRWIN
    - Portadores de cables
        - Estilo: Ganchos de anillo en D
        - Marca: StarTech.com
        - Dimensiones del artículo LxWxH: 25,91 x 1,5 x 2,61 pulgadas
        - Talla: 0U | Vertical | 3 ft
        - Material: Acero aleado

- 🔖 **Documentacion y etiquetado:**
    - Etiquetas para identificar cables y dispositivos
        - Rotuladora
            - Marca: DYMO
            - Tecnología de impresión: Termal
            - Características especiales: Magnético

- 🌀 **Elementos de Enfriamiento:**
    - Ventiladores o sistemas de refrigeración si es necesario.
        - Marca: Lasko
        - Diseño de ventilador eléctrico: Ventilador de Piso
        - Fuente de alimentación: Corded Electric
        - Estilo: Contemporáneo
        - Características especiales: Control remoto
        - Usos Recomendados Para Producto: Cooling, Air Circulation
        - Tipo de montaje: Window Mount     


## Sección 3: Configuración de las VPCs 💻

Ejemplo de configuracion de VPCs segun nivel por medio de comandos.

### VPC Nivel 1 
- Paso 1 - Asignar direccion IP:
    - Ingresar a la maquina VPC1
    - Ingresar Comando: ip 192.168.27.x/24 192.168.27.1
        - Donde x es igual al id de host valido
        - Donde /24 indica la mascara de subred
            - Es equivalente a 255.255.255.0
        - Donde 27.1 indica Gateway

- Paso 2 - Conectar VPC a Switch:
    - Conectar cable desde el switch al VPC

- Paso 3 - Verificar Coneccion entre el mismo nivel:
    - Ingresar comando: 
        - ping 192.168.27.x

- Resultado 💻 VPC 1:
    - Dirección IP: 192.168.27.2
    - Máscara de Subred: 255.255.255.0
    - Direccion MAC: 00:50:79:66:68:01


### VPC Nivel 2 
- Paso 1 - Asignar direccion IP:
    - Ingresar a la maquina VPC8
    - Ingresar Comando: ip 192.168.27.x/24 192.168.27.1
        - Donde x es igual al id de host valido
        - Donde /24 indica la mascara de subred
            - Es equivalente a 255.255.255.0
        - Donde 27.1 indica Gateway

- Paso 2 - Conectar VPC a Switch:
    - Conectar cable desde el switch al VPC

- Paso 3 - Verificar Coneccion entre el mismo nivel:
    - Ingresar comando: 
        - ping 192.168.27.x

- Resultado 💻 VPC 8:
    - Dirección IP: 192.168.27.10
    - Máscara de Subred: 255.255.255.0
    - Direccion MAC: 00:50:79:66:68:05

### VPC Nivel 3 
- Paso 1 - Asignar direccion IP:
    - Ingresar a la maquina VPC8
    - Ingresar Comando: ip 192.168.27.x/24 192.168.27.1
        - Donde x es igual al id de host valido
        - Donde /24 indica la mascara de subred
            - Es equivalente a 255.255.255.0
        - Donde 27.1 indica Gateway

- Paso 2 - Conectar VPC a Switch:
    - Conectar cable desde el switch al VPC

- Paso 3 - Verificar Coneccion entre el mismo nivel:
    - Ingresar comando: 
        - ping 192.168.27.x

- Resultado 💻 VPC 16:
    - Dirección IP: 192.168.27.20
    - Máscara de Subred: 255.255.255.0
    - Direccion MAC: 00:50:79:66:68:0d


