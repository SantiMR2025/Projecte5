Aquí tens la guia tècnica en **format Markdown** per publicar a GitHub:

***

# **Activitat A i B: Configuració de Servidor FTP i SFTP**

## **Objectiu**

Aprendre a configurar:

*   **Servidor FTP estàndard** (vsftpd): creació d’usuaris, engabialament (chroot) i permisos.
*   **Servidor SFTP** (sobre SSH): transferència segura, engabialament i seguretat.

Entendre la diferència entre FTP (sense xifrat) i SFTP (xifrat sobre SSH).

***

## **Fase 1: Preparació de l’entorn**

1.  Crear una **màquina virtual** amb Linux (Ubuntu Server recomanat).
2.  Assegurar que tens accés com a usuari amb privilegis `sudo`.
3.  Connexió a xarxa per provar transferències.

***

## **Fase 2: Configuració del servidor FTP (vsftpd)**

### **Instal·lació**

```bash
sudo apt update
sudo apt install vsftpd -y
```

### **Creació d’usuari FTP**

```bash
sudo adduser ftpuser
sudo passwd ftpuser
```

### **Configuració d’engabialament (chroot)**

Edita el fitxer `/etc/vsftpd.conf`:

```bash
sudo nano /etc/vsftpd.conf
```

Activa les línies:

    chroot_local_user=YES
    allow_writeable_chroot=YES

### **Permisos de lectura/escriptura**

```bash
sudo chmod 755 /home/ftpuser
```

### **Reiniciar el servei**

```bash
sudo systemctl restart vsftpd
```

**Nota:** FTP envia dades **en clar**, per tant és insegur en xarxes públiques.

***

## **Fase 3: Configuració del servidor SFTP (sobre SSH)**

### **Instal·lació del servidor SSH**

```bash
sudo apt install openssh-server -y
```

### **Creació d’usuari SFTP**

```bash
sudo adduser sftpuser
```

### **Configuració d’engabialament**

Edita `/etc/ssh/sshd_config`:

    Subsystem sftp internal-sftp
    Match User sftpuser
        ChrootDirectory /home/sftpuser
        ForceCommand internal-sftp
        AllowTcpForwarding no
        X11Forwarding no

### **Permisos**

```bash
sudo chown root:root /home/sftpuser
sudo mkdir /home/sftpuser/upload
sudo chown sftpuser:sftpuser /home/sftpuser/upload
```

### **Reiniciar SSH**

```bash
sudo systemctl restart ssh
```

***

## **Diferències clau**

*   **FTP**: Dades en clar, insegur.
*   **SFTP**: Comunicació xifrada sobre SSH, segur.

***

## **Proves**

*   **FTP**: Connecta amb `ftp ftpuser@IP` i observa que les credencials viatgen sense xifrat.
*   **SFTP**: Connecta amb `sftp sftpuser@IP` i comprova que la connexió és segura.

***

### **Seguretat**

Com a administradors, la seguretat **no és opcional**, és una obligació.  
Sempre prioritza protocols segurs com SFTP en entorns reals.

***

Vols que ara **afegeixi una secció amb comandes per verificar la connexió i capturar paquets amb Wireshark** per demostrar que FTP és en clar i SFTP és xifrat?  
O prefereixes que et prepari **la versió final amb apartat per afegir captures**?
