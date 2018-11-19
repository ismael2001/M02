# E1. Ejercicio 4. Estructura del sistema operativo.

## Introducción

Podemos dividir el sistema operativo en las siguientes partes:
- Núcleo
- administrador de memoria
- Gestor de entrada / salida
- administrador del sistema de archivos

## contenidos

Analicemos el comportamiento del sistema operativo en cada módulo. Usaremos los comandos de Linux para ver qué está sucediendo en un sistema operativo Linux.

## Entrega

### Núcleo

1. **¿Dónde reside el kernel en el disco?** Escriba el comando con la salida y diga exactamente dónde está el kernel.


Reside en la carpeta /boot, lo podemos ver con el comando uname -r 4.18.16-200.fc28.x86_64.


2. **¿Cómo podemos mostrar la versión real del kernel que está cargada en nuestro sistema?** Por favor muestra el resultado del comando


Con el comando uname -a.


Linux a11 4.18.7-100.fc27.x86_64 #1 SMP Thu Sep 13 18:41:39 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux


3. **¿Cómo podemos mostrar el hardware detectado por el kernel?** Por favor, muestre el resultado del comando.


Con el comando lspci.


00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H81 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
03:00.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 41)


4. **¿Cómo podemos mostrar los módulos (controladores) realmente en uso?** ¿Qué módulo se está utilizando para la tarjeta gráfica de video?


lsmod, se utiliza el módulo video 45056  1 i915.


### administrador de memoria

1. **¿Qué es la memoria 'caché' que muestra el comando 'free -m'?** Muestra también la salida del comando


La memoria caché es un tipo de memoria de acceso rápido, que guarda los programas para que no tenga que abrirlo el disco duro.




   total     used        free      shared  buff/cache   available

   Mem:     3831        1099         944         222        1787        2212



2. **¿Qué es la memoria 'swap' que muestra el comando 'free -m'?**


La memoria swap sirve para cuando nuestro pc se queda sin memoria.


Swap:          5116           0        5116

3. **¿Cómo maneja el administrador de memoria un problema de falta de memoria?**


Con el progama OOM Killer que lo que hace es matar procesos.


4. **¿Cómo podemos mostrar la 'puntación de memoria' real de una instancia de Gimp que se está ejecutando?**


COn el comando ps auxf | gimp.


### Administrador de entrada / salida

1. **¿Cómo podemos enumerar todas las interrupciones que conoce nuestro sistema operativo?** Mostrar también el resultado del comando


Con cat /proc/interrupts


   CPU0       CPU1       CPU2       CPU3
   0:         14          0          0          0   IO-APIC    2-edge      timer
   1:          0          0          0        678   IO-APIC    1-edge      i8042
   8:          0          0          0          0   IO-APIC    8-edge      rtc0
   9:          0         44          0          0   IO-APIC    9-fasteoi   acpi, INT0002
  18:          0          0          0          0   IO-APIC   18-fasteoi   i801_smbus
  32:     274131          0          0          0   IO-APIC   32-fasteoi   808622C1:00
  43:          0          0          0          0   IO-APIC   43-fasteoi   dw:dmac-1
  45:          0         52          0          0   IO-APIC   45-fasteoi   mmc0
 115:          0      20167      17178          0   PCI-MSI 311296-edge      ahci[0000:00:13.0]
 116:          0          0       6067          0   PCI-MSI 327680-edge      xhci_hcd
 117:          0          0      22311          0  chv-gpio   19  ELAN0501:00
 118:          0      37350       1471          0   PCI-MSI 32768-edge      i915
 119:          0          0          0          0  INT0002 Virtual GPIO    2  ACPI:Event
 120:          0          0          0          0   PCI-MSI 180224-edge      proc_thermal
 121:          0          0         26          0   PCI-MSI 425984-edge      mei_txe
 122:          0          0          0       8254   PCI-MSI 1048576-edge      iwlwifi
 123:       1096          0          0          0   PCI-MSI 442368-edge      snd_hda_intel:card0
 NMI:          9          7          7          6   Non-maskable interrupts
 LOC:     170319     109576     109830     107645   Local timer interrupts
 SPU:          0          0          0          0   Spurious interrupts
 PMI:          9          7          7          6   Performance monitoring interrupts
 IWI:         52         23         27         26   IRQ work interrupts
 RTR:          0          0          0          0   APIC ICR read retries
 RES:      28266      22196      24413      21395   Rescheduling interrupts
 CAL:      27428      28803      35834      32352   Function call interrupts
 TLB:      18873      21210      22177      22615   TLB shootdowns
 TRM:        279          0          0          0   Thermal event interrupts
 THR:          0          0          0          0   Threshold APIC interrupts
 DFR:          0          0          0          0   Deferred Error APIC interrupts
 MCE:          0          0          0          0   Machine check exceptions
 MCP:          3          3          3          3   Machine check polls
 HYP:          0          0          0          0   Hypervisor callback interrupts
 HRE:          0          0          0          0   Hyper-V reenlightenment interrupts
 HVS:          0          0          0          0   Hyper-V stimer0 interrupts
 ERR:          0
 MIS:          0
 PIN:          0          0          0          0   Posted-interrupt notification event
 NPI:          0          0          0          0   Nested posted-interrupt event
 PIW:          0          0          0          0   Posted-interrupt wakeup event
 


2. **En los sistemas multiprocesador, ¿cómo distribuye el sistema operativo las interrupciones de forma predeterminada?** ¿Cómo podemos cambiar el comportamiento predeterminado?


El sistema operativo las distruye en cada núcleo, podemos cambiar el comportamiento con el comando tuned-adm list.


3. **¿Cómo controla un sistema operativo un dispositivo que no tiene interrupciones?** Explique el proceso


Lo hace mediante Polling, que lo que hace es solicitar datos a los dispositivos y se los proporciona.


4. **¿Qué ocurrirá si dos aplicaciones desean enviar datos a través de un dispositivo de red al mismo tiempo?**


Dará prioridad al que mas importancia tenga.


### administrador del sistema de archivos


1. **¿Cuál es la típica estructura de carpetas de Linux?** Describe qué es y el uso de cada carpeta.

- bin: aquí estan los comandos que pueden usar todos los usuarios.

- arranque: aquí está todo lo relacionado con el arranque del sistema.

- dev: aquí estan todos los dispositivos de nuestra máquina.

- etc: aquí se encuentran todas las configuraciones.

- casa: lugar donde se almacenan las cuentas de usuarios.

- lib: aquí están las librerías que se necesitan para el sistema.

- lib64: igual que el lib pero para 64 bits.

- perdido + encontrado: es un directorio que almacena archivos que no se cerraron correctamente.

- medios de comunicación: punto de montaje para sistema de archivos montados localmente.

- mnt: archivos montandos temporalmente.

- opt: paquetes de software opcionales.

- proc: sistema de archivos virtual de información de procesos y del kernel.

- raíz: directorio de inicio de root.

- correr: es una carpeta que almacena procesos. 

- sbin: aquí se encuentran los comandos de administración.

- srv: contiene datos para servicios.

- sys: carpetas con las variables del kernel.

- tmp: archivos temporales.

- usr: contiene subdirectorios.

- var contiene archivos del sistema.


2. **¿Cómo podemos:?**
- Mueva un archivo que reside en /usr/local/src/file.md a la carpeta / opt: mv /usr/local/src/file.md/opt


- Copie un archivo que reside en /usr/local/src/file.md a la carpeta / opt: cp /usr/local/src/file.md/opt


- Mueva un archivo en /usr/file.md a / usr / local si estamos actualmente en la ruta / usr / local: mv /usr/local/src/file.md


- Cree el archivo .gitignore usando el comando 'tocar' y luego intente listarlo (ls). ¿Lo que pasa? No se puede mostrar porqué los archivos que comienzan por . son ocultos.
