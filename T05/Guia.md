
# **Desplegament d’Active Directory com a prova de concepte (PoC)**

## **Introducció**
Com a continuació de la tasca anterior, desplegarem **Active Directory Domain Services (AD DS)** sobre una màquina virtual Windows Server. L’objectiu és practicar el procediment per al posterior desplegament en el client i generar una prova de concepte (PoC) per mostrar als responsables de **TransLògic**, ajustant les configuracions a les necessitats reals.

---

## **Objectius**
- Instal·lar els rols necessaris al servidor.
- Crear un domini nou en un bosc nou anomenat `translogicXX.test` (on **XX** és el vostre número de llista).
- Establir el nivell funcional a **Windows Server 2025**.
- Promocionar el servidor com a controlador de domini.
- Documentar la pantalla resum.
- Generar i desar l’script PowerShell que automatitza el procés.
- Copiar l’script al repositori utilitzat.

---

## **Requisits previs**
- Màquina virtual amb **Windows Server 2022 o superior**.
- Connexió a Internet.
- Nom d’equip definit (exemple: `SRV-AD`).
- IP fixa configurada (recomanat per a entorns AD).
- Accés d’administrador al servidor.

---

## **Procediment**

### **Fase 1: Instal·lació dels rols necessaris**
1. Obre **Server Manager**.
2. Ves a **Add Roles and Features**.
3. Selecciona:
   - **Active Directory Domain Services (AD DS)**.
   - **DNS Server** (recomanat per a AD).
4. Completa l’assistent i reinicia si ho demana.

**Captura requerida:**  
![Captura del rol AD DS instal·lat](ruta/captura1.png)

---

### **Fase 2: Creació del domini i promoció del servidor**
1. A **Server Manager**, fes clic a la notificació **Promote this server to a domain controller**.
2. Selecciona:
   - **Add a new forest**.
   - Nom del domini: `translogicXX.test`.
3. Nivell funcional:
   - Escull **Windows Server 2025** (si apareix com a opció).
4. Defineix la contrasenya per al **Directory Services Restore Mode (DSRM)**.
5. Accepta la configuració DNS i camins per defecte.
6. Revisa la **pantalla resum** i fes una captura per documentar.
7. Fes clic a **Install** i espera el reinici.

**Captura requerida:**  
![Pantalla resum abans de la instal·lació](ruta/captura2.png)

---

### **Fase 3: Generar l’script PowerShell**
Quan completes la promoció, Windows et permet generar l’script PowerShell equivalent:
- A la pantalla final, fes clic a **View Script**.
- Desa’l com `ADDS_Install.ps1`.

**Exemple d’script PowerShell:**
```powershell
#
# Windows PowerShell script for AD DS Deployment
#

Import-Module ADDSDeployment
Install-ADDSForest `
-CreateDnsDelegation:$false `
-DatabasePath "C:\WINDOWS\NTDS" `
-DomainMode "Win2025" `
-DomainName "translogic17.test" `
-DomainNetbiosName "TRANSLOGIC17" `
-ForestMode "Win2025" `
-InstallDns:$true `
-LogPath "C:\WINDOWS\NTDS" `
-NoRebootOnCompletion:$false `
-SysvolPath "C:\WINDOWS\SYSVOL" `
-Force:$true
``
