Instrucciones de instalación de CHC Masternode
-----------------------------------

Por favor cree un nuevo VM usando  Ubuntu 18.04 de 64 bit

Que hay por hacer
-----------------------

- ansible playbook role
~~- documentos en español~~
- vagrant with docker
- vagrant with lxd
- test with molecule
- test with travisCI
- test with centos

-----------------------

Después, inicie sesión como root y cree un nuevo usuario. Otorgue a ese nuevo usuario derechos de sudo

ejecuta estos comandos
--------------------
adduser < newUsername >  
`(without the < >)`  
Example:  
```bash
adduser awesomeUser101

```
--------------------

usermod -aG sudo < newUsername >  
`(without the < >)`  
Example:
```
usermod -aG sudo awesomeUser101

```
--------------------

¡Éxito! Ahora cierre la sesión de root y vuelva a iniciar sesión en el VM como su nuevo usuario

Ahora, descargue un cliente FTP como fileZilla.
Cargue el archivo de instalación en su nuevo directorio de usuarios ubicado aquí:

/home/newUsername  

Example:
```bash
devops@localhost>$ /home/awesomeUser101
```

 Alternativamente a fileZilla, ejecute estos comandos:

```bash
devops@localhost>$ sudo apt-get install git
```

Ahora navegue al directorio de inicio de sus usuarios:

```bash
devops@localhost>$  cd /home/newUsername
```

Ejemplo:

```bash
devops@localhost>$ cd /home/awesomeUser101

```

 Instale el script ejecutando:
```bash
devops@localhost>$ devops@localhost>$ sudo git clone https://github.com/jeffward01/Chaincoin-MN-SetupScript.git

devops@localhost>$ cd Chaincoin-MN-SetupScript

```
 Alternativamente, puede activar directamente el script desde el repositorio de github:
 Navegue al directorio de inicio de sus usuarios:
```bash
cd /home/newUsername

```
 Example:
```bash
devops@localhost>$ cd /home/awesomeUser101

```
 Descargue el script a través de:
```bash

devops@localhost>$ wget https://raw.githubusercontent.com/jeffward01/Chaincoin-MN-SetupScript/master/MasternodeSetupScript

```

--------------------
Antes de comenzar, asegurémonos de que el usuario recién creado tenga el permiso adecuado para ejecutar MasternodeSetupScript, ejecute estos comandos:

Asegúrese de estar en el directorio donde descargó el MasternodeSetupScript. No debería necesitar navegar fuera de su directorio actual.
```bash
devops@localhost>$ cd /home/myUserName/Chaincoin-MN-SetupScript

```
 Conceder permisos:

```bash
devops@localhost>$ sudo chmod 777 MasternodeSetupScript
devops@localhost>$ sudo chmod 777 username:sudo MasternodeSetupScript

```
_Ejemplo_:

```bash
devops@localhost>$ cd /home/awesomeUser101/Chaincoin-MN-SetupScript
devops@localhost>$ sudo chmod 777 MasternodeSetupScript
devops@localhost>$ sudo chmod 777 awesomeUser101:sudo MasternodeSetupScript

```
-----------------------



Ahora que ha cargado el archivo de instalación en el directorio de su usuario, regrese al terminal VPS SSH y ejecute la herramienta:

```bash
devops@localhost>$ ./MasternodeSetupScript (this starts the install process)

```

1. El archivo de intercambio ahora se editará para evitar que el sistema falle

(Se abrirá un nano editor, agregue esto a la última línea y guarde)

```
/var/swap.img none swap sw 0 0

```
  Para guardar, haga clic en CTRL + X y luego, CTRL + y



2. Ahora se instalarán las dependencias. Presione enter para continuar y presione y para todas las indicaciones



3. Ahora se instalará el software Chaincoin. Presione enter para continuar


4. Luego se abrirá un nano editor. Reemplace las etiquetas <\ replaceThis \> con su información y pegue el bloque en el editor de código
 No incluya el <>

-----------------------

```bash
rpcuser=< any-username >

rpcpassword=< any-unique-password >

server=1

```
-----------------------

 EJEMPLO:
-----------------------

```bash
rpcuser=testUser101

rpcpassword=password123

server=1

```
-----------------------

 Después de pegar el bloque de texto, guarde.
 Para guardar, haga clic en CTRL + X y luego, CTRL + y


5)
  5a. A continuación, verá una salida de su dirección de billetera Masternode. Por favor, guárdelo y guárdelo en un archivo de texto en su máquina local. Deberá financiar esta dirección con ** 1000.00 CHC **

 5b. A continuación, verá una salida de su clave privada Masternode. Por favor, guárdelo y guárdelo en un archivo de texto en su máquina local.


 6.) Ahora verá el editor de nano texto con su bloque de texto anterior que ha guardado. Pegue este texto debajo de su bloque anterior
 No incluya el <>

-----------------------

```bash
listen=1

masternode=1

masternodeprivkey=< masternode-wallet-private-key >

masternodeaddr=< your server ip >:11994

```
-----------------------
 EJEMPLO:
-----------------------

```bash
listen=1

masternode=1

masternodeprivkey=554asd545asd454d5qw6d4qwd56qewfw23

masternodeaddr=55.555.55.555:11994

```

-----------------------

 7. Ahora necesitamos financiar su masternode y sincronizarlo. Envíe su 1000.00 CHC a su dirección de masternode y ** haga clic en [ENTRAR] ** cuando esté completo
 Nota: Su masternode debe recibir exactamente 1000.00 CHC en la transacción. Si está utilizando la billetera de escritorio CHC, envíe 1000.00 CHC a la dirección
 Si está utilizando una billetera diferente, como una billetera de cambio, envíe 1000.001, donde el .001 es la tarifa de traslación incurrida por la transacción.

 Nota: El siguiente paso es la sincronización, y puede demorar hasta 4 horas. Estás descargando la cadena de bloques CHC a tu masternode local. También está incurriendo en más de 15 confirmaciones en su depósito de 1000.00 CHC. Después de tener más de 15 confirmaciones, puede comenzar su masternode.


 Complete el instalador y, en 4 horas, regrese e inicie su masternode ejecutando este comando:

 inicio de masternode chaincoind
-------------------------------
 ¡Instalación completa!

-------------------------------
 Si desea iniciar su masternode antes de las 4 horas (se sugieren 4 horas para asegurarse de que el masternode termine de sincronizarse), siga estas instrucciones:

 ejecuta este comando:

```bash
 watch chaincoind getinfo

```
Una vez que su nodo termine de sincronizarse, verá el ** 1000.00 CHC ** en su saldo.
Presione Ctrl + C para salir de la pantalla "ver".

 Para verificar el recuento de transacciones, ejecute esto:

```bash
 chaincoind listtransactions

```
 (una vez que el recuento de transacciones para el 1000.00 inicial sea superior a 15, inicie el masternode)


-------------------------
-------------------------


 Comandos útiles:


-------------------------
 Iniciar ChainCoin
```bash
chaincoind -daemon

```
-------------------------

-------------------------
 Stop ChainCoin
```bash
chaincoind stop

```
-------------------------


-------------------------
 Iniciar Masternode
```bash
chaincoind masternode start

```
-------------------------

-------------------------
 Obtener dirección de Masternode:
```bash
chaincoind getaccountaddress 0

```
-------------------------

-------------------------
 Obtenga la clave privada de Masternode:
```bash
chaincoind masternode genkey

```
-------------------------

-------------------------
 Obtener el estado de Masternode:

```bash
chaincoind getinfo

```
-------------------------


-------------------------
 Obtener el estado de Masternode (actualizar continuamente):
```bash
watch chaincoind getinfo

```
 presione Ctrl + C para salir

-------------------------


 Si te gustó este script, por favor dale una ESTRELLA en la esquina superior derecha
