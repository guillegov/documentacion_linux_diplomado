#Linux#
##Tema # 1 Comandos de Linux##
###1. - Comandos de Archivos y Directorios###
> **ls**
> Lista los archivos del directorio

-----
> **ls -al**
> Lista los archivos ocultos del directorio

---
> **ls -al**
> Lista los archivos ocultos del directorio

---
> **ls -la**
> Lista los archivos con descripciones

-----
> **cd**
> Salir del directorio

-----
> **cd  /**
> Sale a directorio home

-----
> **pwd**
> Muestra el directorio actual

-----
> **mkdir  nombre_directorio**
> Crea un directorio

-----
> **rm nombre_directorio**
> Borra Directorio

-----
> **rm nombre_directorio**
> Borra Directorio

-----
> **passad**
> Cambia la contraseña del equipo

-----
> **touch nombre_de_archivo**
> Crea o actualiza un archivo

-----
> **passad**
> Cambia la contraseña del equipo

-----
> **more file**
> Muestra el contenido del archivo

-----
> **apt-get update**
> Actualiza Muestra el contenido del archivo

-----
> **apt-get install nombre_paquete**
> Instala el paquete

-----
> **man comando**
> Muestra la ayuda del comando

###2. - Comandos de Redes###

> **ifconfig**
> Muestra la configuración de la interfaz de red

-----
> **ifconfig eth0 down**
> Baja el servicio de la red de la interfaz eth0

-----
> **ifconfig eth0 up**
> Subir el servicio de red de la interfaz eth0

-----
> **ping dirección_host**
> Muestra los resultados de conexión al host

-----
> **networking stop**
>Para el servicio de red

-----
> **networking restart**
>Reinicia el servicio de red

-----
> **/etc/init.d/networking stop**
>Para el servicio de red

-----
> **/etc/init.d/networking restart**
>Reinicia el servicio de red

###3. - Comandos para Permisos###

> **chmod**
> Cambia permisos a un archivo o directorio

-----
> **chmod 777 nombre_archivo**
> Da permiso de leer, escribir y ejecutar al archivo

-----
> **chmod 777 nombre_directorio**
> Da permiso de leer, escribir y ejecutar al directorio

##Tema # 2 KVM##
###1. - Instalación de KVM###
> **grep vmx/proc/cpuinfo**
> Muestra si el computador con procesador intel soporta virtualización

-----
> **grep svm/proc/cpuinfo**
> Muestra si el computador con procesador amd soporta virtualización

-----
> **apt-get install qemu-kvm libvirt-bin virtinst virt-viewer**
> Instalación de KVM

-----
> **apt-get install virt-manager**
> Instalación del administrador de virtuales

-----
> **adduser nombre_usuario kvm && adduser nombre_usuario libvirt**
> Añade el usuario como usuario del kvm y del administrador de virtuales


##Tema #2 DEBIAN##
###1. - Pasos de instalación###

----
> **Bootear el cd**

----
> **Seleccionar INSTALL**

----
> **Seleccionar idioma Spanish**

----
> **Seleccionar país Bolivia**

----
> **Seleccionar teclado Latinoamericano**

----
> **Escribir el nombre de equipo**

----
> **Escribir contraseña root**

----
> **Escribir otro usuario y contraseña**

----
> **PARTICIONAR LOS DISCOS DUROS**

-----
> **Seleccionar manual**

-----
> **Crear 4 particiones**

-----
> **boot					256MB			ext2			/boot**

-----
> **swap					256MB			areaintercambio	/swap**	

-----
> **raiz					1GB			ext4			/**

-----
> **home					10GB			ext4			/home**	

-----
> **datos(punto de montaje manual)	256MB			ext4			/datos**

-----
> **Particionar y confirmar**

-----
> **Instalar los DVDs seleccionar No**

-----
> **Instalar la red seleccionar No**

-----
> **Instalar el GRUB seleccionar Si**


###2. - Aumentar Tamaño del Disco###

-----
> **lvextend -L +100M /dev/mapper/nombre_grupo_volumen-PARTICION**
> Aumenta el tamaño del disco en 100 megas

-----
> **umount /dev/mapper/nombre_grupo_volumen-PARTICION**
> Desmonta el disco

-----
> **e2fsck -f /dev/mapper/nombre_grupo_volumen-PARTICION**
> Verifica la partición

-----
> **resize2fs /dev/mapper/nombre_grupo_volumen-PARTICION**
> Redimensiona el sistema de archivo de la particion indicada

-----
> **mount /dev/mapper/nombre_gruupo_volumen-PARTICION**
> Monta la partición


###3. - Reducir Tamaño del Disco###

-----
> **umount /dev/mapper/nombre_grupo_volumen-PARTICION**
> Desmontar el disco

-----
> **e2fsck -f /dev/mapper/nombre_grupo_volumen-PARTICION**
> Verifica la partición

-----
> **resize2fs /dev/mapper/nombre_grupo_volumen-PARTICION  tamaño_disco_a_llegar**
> Redimensiona el sistema de archivo de la particion indicada al tamaño de disco a llegar

-----
> **mount /dev/mapper/nombre_gruupo_volumen-PARTICION**
> Monta la partición

-----
> **lvreduce -L tamaño_a_reducir_disco /dev/directorio_grupo/directorio_particion**
> Reduce el tamaño del disco a la cantidad indicada


###4. - Partición Fisica, Grupo de Volumen y Volumen Lógico###

-----
> **fdisk -l**
> Muestra particiones del disco

-----
> **cfdisk /dev/sda (ruta del disco)**
> Crea partición del disco

-----
> **pvcreate /dev/sda1 (ruta de la particion del disco)**
> Crea partición fisica

-----
> **vgcreate nombre_volumen_grupo /dev/sda1 (ruta de la particion del disco)**
> Crea volumen de grupo

-----
> **lvcreate -L tamaño_particion_disco -n nombre_particion nombre_volumen_grupo**
> Muestra nuevo volumen fisico

-----
> **lvs**
> Muestra nuevo volumen

-----
> **mkfs.ext3 -m 0 /dev/mapper/nombre_volumnen_grupo-nombre_particion**
> Da Formato de archivos a la particion indicada

-----
> **mkdir /mnt/nombre_particion**
> Crea directorio con nombre de la partición

-----
> **mount /dev/mapper/nombre_volumen_grupo-nombre-particion   /mnt/nombre_particion**
> Monta la grupo de volumen de disco de la particion en el directorio creado

-----
> **nano /etc/fstab**
> Editar el archivo fstab para que monte automaticamente la particion

-----
> **dev/mapper/nombre_volumen_grupo-nombre-particion   /mnt/nombre_particion ext3 defaul   0   2**


###5. - Particionar Graficamente con Gparted Live###

-----
> **sudo qemu-img resize lvm1.img  +7GB**
> Aumenta el tamaño del disco virtual en 7 GB

-----
> **Bootear gpartedlive**
> Expandir la partición extendida con la flecha hasta el tamaño deseado

----
> **Expandir la partición LVM con la flecha hasta del tamaño deseado**
> Aplicar los cambios

-----
> **Reiniciar la maquina virtual**
> fdisk -l /dev/sda (ruta del disco)

-----
> **Muestra que la partición ha sido redimensionada**


###6. - Administración de las redes en Debian###

-----
> **gnome-control-center network**
> Configuración en modo grafico

-----
> **nano /etc/network/interfaces**
> Configuración en modo texto

-----
> **ls -l /sys/class/net**
> Ver redes

-----
> **nano etc/network/interfaces**
> Abrimos el archivo de configuración de la interfaz de red y adicionamos

-----
> **iface eth0 inet DHCP**
> Configura la interfaz de red eth0 como DHCP

-----
> **iface eth1 inet static**
> **address 192.168.122.100**
> **netmask 255.255.255.0**
> **gateway 192.168.122.1**

-----
> **service networking restart**
> Reinicia el servicio de red


###7. - Administración del Servicio SSH###

-----
> **apt-get install ssh**
> Instalando el paquete ssh

-----
> **netstat -natp**
> Ver puertos abiertos

-----
> **service ssh restart**
> Reinicia el servicio

-----
> **ssh usuario@192.168.5.100**
> Se conecta con el usuario


###8. - Administración de Llaves Públicas###

-----
> **ssh -keygen -t isa -b 2048**
> Genera llave de 2048

-----
> **ssh-copy-id -i /home/usuario/.ssh/id-rsa.pub   root@192.168.5.100**
> Copia el id al usuario root

-----
> **nano /etc/ssh/sshd_config**
> Editar archivo sshd_config

-----
> **cambia PubleyAutentication	yes**

---
> **sudo chown root:usuario archivo**
> Cambia de usuarios

---
> **sudo useradd  usuario1**
> Adiciona nuevo usuario1

-----
> **sudo passwd  usuario1**
> Cambia la contraseña del usuario1
