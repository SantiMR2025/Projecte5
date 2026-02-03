# **Plantilla GitHub – Pràctica: Anàlisi de vulnerabilitats amb OpenVAS i Metasploitable-2**

## 1. Objectiu de l’activitat

Aquesta pràctica té com a objectiu:

*   Configurar un entorn de proves amb dues màquines virtuals.
*   Executar un escaneig de vulnerabilitats amb OpenVAS.
*   Identificar punts febles reals en un sistema vulnerable (Metasploitable-2).
*   Documentar quatre vulnerabilitats i proposar mesures de mitigació.

***

## 2. Entorn de treball

### Màquines utilitzades

*   **Metasploitable-2** (màquina vulnerable)
*   **OpenVAS / Greenbone Vulnerability Manager** (eina d’escaneig)

***

# 3. Configuració de l’entorn

## 3.1. Configuració de la màquina Metasploitable-2

### 1. Importar la màquina a VirtualBox

captures/import-metasp.png

### 2. Configuració de xarxa (NAT)

captures/metasp-network.png

### 3. Inici de sessió i obtenció de la IP

Credencials:

*   Usuari: `msfadmin`
*   Contrasenya: `msfadmin`

Executar:

    ip a

captures/metasp-ip.png

***

## 3.2. Configuració de la màquina OpenVAS

### 1. Importació de la màquina

captures/openvas-import.png

### 2. Configuració de les dues interfícies de xarxa

*   NAT
*   Host-Only

captures/openvas-network.png

### 3. Inicialització i configuració

*   Saltar llicència
*   Crear usuari `admin / admin`
*   Configurar amb DHCP

captures/openvas-setup.png

### 4. IP d’accés a la interfície web

captures/openvas-ip.png

***

# 4. Procediment pràctic d’anàlisi

## 4.1. Accedir a OpenVAS via web

Entrar al navegador:

    https://IP_Host_Only:9392

Ignorar l'avís del certificat.

captures/openvas-cert.png

Iniciar sessió:

captures/openvas-login.png

***

## 4.2. Crear Host

### 1. Afegir la IP de Metasploitable

captures/openvas-new-host.png

***

## 4.3. Crear Target

### 1. Associar el Host i afegir credencials SSH

Credencials SSH:

*   Usuari: `msfadmin`
*   Contrasenya: `msfadmin`

captures/openvas-target.png

***

## 4.4. Crear i engegar l’escaneig

captures/openvas-new-task.png

### Execució de l’escaneig

captures/openvas-scan-running.png

***

# 5. Resultats de l’anàlisi

Quan finalitza:

*   Resum de vulnerabilitats
*   Classificació per severitat
*   Serveis afectats
*   Informes detallats

### Resum general

captures/openvas-results-overview\.png

### Vista detallada d’una vulnerabilitat

captures/openvas-vuln-detail.png

***

# 6. Anàlisi de 4 vulnerabilitats

Completa cada secció amb la informació obtinguda.

***

## Vulnerabilitat 1: **Nom de la vulnerabilitat**

**CVE:**  
**Severitat:**  
**Descripció:**  
**Possible explotació:**  
**Mesures de mitigació:**

captures/vuln1.png

***

## Vulnerabilitat 2: **Nom de la vulnerabilitat**

**CVE:**  
**Severitat:**  
**Descripció:**  
**Possible explotació:**  
**Mesures de mitigació:**

captures/vuln2.png

***

## Vulnerabilitat 3: **Nom de la vulnerabilitat**

**CVE:**  
**Severitat:**  
**Descripció:**  
**Possible explotació:**  
**Mesures de mitigació:**

captures/vuln3.png

***

## Vulnerabilitat 4: **Nom de la vulnerabilitat**

**CVE:**  
**Severitat:**  
**Descripció:**  
**Possible explotació:**  
**Mesures de mitigació:**

captures/vuln4.png

***

# 7. Conclusions

Reflexiona sobre:

*   Quines vulnerabilitats han estat més crítiques i per què.
*   Com OpenVAS facilita la detecció de fallades.
*   La importància de les actualitzacions i la seguretat activa.

***

# 8. Annex (opcional)

*   Informes exportats
*   Fitxers de configuració
*   Notes tècniques

***

Si vols, puc generar-te aquesta plantilla:

*   amb **carpetes precreades** (`captures/`, `docs/`, etc.)
*   adaptada al teu **estil de repositori**
*   o amb un **fitxer zip descarregable** amb tota l’estructura preparada.

Vols que t’ho organitzi en un format encara més complet?
