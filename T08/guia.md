


# Fase 2 — Verificació d’antimalware amb EICAR i arxius comprimits

> **Objectiu.** Comprovar el comportament del navegador (**SmartScreen**) i de l’antivirus (Microsoft Defender o el que utilitzis) amb el fitxer de prova **EICAR** i veure què passa quan l’“amaguem” dins **ZIP / TAR / 7Z**. El fitxer **EICAR** és una mostra **segura** creada per provar antivirus —no és malware real. [1](https://www.ninjaone.com/blog/windows-defender-exploit-protection-settings/)

---

## 1) Preparació i seguretat

- Realitza les **proves en una màquina virtual** i amb **snapshot** previ.  
- Desactiva proteccions **només el temps imprescindible** i torna‑les a activar tot seguit.  
- Documenta cada pas amb **captures** (estat de Windows Security, alertes, quarantena, etc.).

---

## 2) Desactivar **SmartScreen** temporalment (per permetre la baixada de prova)

1. Obre **Windows Security** → **App & browser control** → **Reputation‑based protection settings**.  
2. Posa **Off**:  
   - **Check apps and files**  
   - **SmartScreen for Microsoft Edge**  
   - (Opcional) **Potentially unwanted app blocking**  
3. Recorda **reactivar** SmartScreen en acabar de descarregar la mostra. [2](https://geekchamp.com/enable-or-disable-windows-defender-real-time-protection-in-windows-11/)[3](https://www.solveyourtech.com/how-to-turn-off-windows-defender-in-windows-11-a-step-by-step-guide-4/)

---

## 3) Desactivar **protecció en temps real** temporalment (si cal per a la baixada)

1. **Windows Security** → **Virus & threat protection** → **Manage settings**.  
2. Canvia **Real‑time protection** a **Off** (confirma el prompt d’UAC).  
> Aquesta desactivació és **temporal** i Windows pot tornar‑la a activar automàticament; re‑activa‑la manualment quan acabis. [4](https://www.facebook.com/DDHS.TW/posts/httpsgithubcomjoelgmsecpsransom/1547140832333576/)[5](https://github.com/JoelGMsec)

---

## 4) Obtenir el fitxer de prova **EICAR**

- **Opció A (recomanada)**: descarrega’l des del web oficial d’**EICAR** i tria una variant com *eicar.com.txt*. [1](https://www.ninjaone.com/blog/windows-defender-exploit-protection-settings/)  
- **Opció B (alternativa)**: crea’l tu mateix amb l’string oficial (guarda’l com **EICAR.txt**):

X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*

*(És el patró que els antivirus identifiquen com a prova.)* [6](https://www.thewindowsclub.com/ransomware-protection-in-windows-defender)

---

## 5) Prova 1 — Validar detecció amb proteccions **activades**

1. Activa **SmartScreen** (secció 2) i la **protecció en temps real** (secció 3). [2](https://geekchamp.com/enable-or-disable-windows-defender-real-time-protection-in-windows-11/)[5](https://github.com/JoelGMsec)  
2. Intenta descarregar **eicar.com.txt** i guarda’l a **Descàrregues**.  
3. Observa i captura si:  
 - El navegador (**Edge/SmartScreen**) **avisa o bloqueja** la baixada. [2](https://geekchamp.com/enable-or-disable-windows-defender-real-time-protection-in-windows-11/)  
 - **Defender** el **detecta/quarantena** automàticament. [6](https://www.thewindowsclub.com/ransomware-protection-in-windows-defender)

---

## 6) Prova 2 — Forçar la baixada i després comprovar la detecció

1. Torna a **desactivar temporalment** SmartScreen i la **Real‑time protection** per permetre la baixada. [2](https://geekchamp.com/enable-or-disable-windows-defender-real-time-protection-in-windows-11/)[4](https://www.facebook.com/DDHS.TW/posts/httpsgithubcomjoelgmsecpsransom/1547140832333576/)  
2. Descarrega **eicar.com.txt**.  
3. **Re‑activa immediatament** la protecció en temps real. [5](https://github.com/JoelGMsec)  
4. Obre l’Explorador → **clic dret** sobre el fitxer → **Scan with Microsoft Defender** (o l’AV que facis servir).  
 - **Esperable:** detecció i **quarantena** de la mostra EICAR. [6](https://www.thewindowsclub.com/ransomware-protection-in-windows-defender)

---

## 7) Prova 3 — “Amagar” EICAR dins **ZIP / TAR / 7Z**

> Molts antivirus detecten el patró EICAR **fins i tot dins d’arxius comprimits**, però el **moment de detecció** (a la baixada, a l’escaneig sota demanda o en **extraure**) pot variar segons producte i configuració. [7](https://pureinfotech.com/enable-smart-app-control-windows-11/)

**Procediment:**
1. Desactiva **temporalment** la **Real‑time protection** per poder crear els arxius sense que es bloquegin. [4](https://www.facebook.com/DDHS.TW/posts/httpsgithubcomjoelgmsecpsransom/1547140832333576/)  
2. Crea, a partir d’**EICAR.txt**, aquests arxius: **EICAR.zip**, **EICAR.tar**, **EICAR.7z**.  
3. Re‑activa la **Real‑time protection**. [5](https://github.com/JoelGMsec)  
4. Per a **cada** format:  
 - Fes **escaneig sota demanda** (clic dret → escanejar).  
 - Prova d’**extraure** el contingut a una carpeta de proves.  
5. Anota **si detecta** i **quan** (a l’escaneig de l’arxiu, en extraure, etc.). [7](https://pureinfotech.com/enable-smart-app-control-windows-11/)

---

## 8) Tornar a l’estat segur (OBLIGATORI)

- Deixa **SmartScreen** i la **protecció en temps real** **activats**. [2](https://geekchamp.com/enable-or-disable-windows-defender-real-time-protection-in-windows-11/)[5](https://github.com/JoelGMsec)  
- Elimina la mostra EICAR i **buida la quarantena** si escau (els productes solen gestionar‑ho automàticament). [6](https://www.thewindowsclub.com/ransomware-protection-in-windows-defender)

---

## 9) Lliurable (estructura recomanada)

- **A) Desactivar SmartScreen —** Passos (captures de *App & browser control → Reputation-based protection settings*). [2](https://geekchamp.com/enable-or-disable-windows-defender-real-time-protection-in-windows-11/)  
- **B) Desactivar/activar protecció en temps real —** Passos i temps de desactivació. [4](https://www.facebook.com/DDHS.TW/posts/httpsgithubcomjoelgmsecpsransom/1547140832333576/)  
- **C) Detecció amb l’antimalware —** Resultat (alerta/quarantena) amb la mostra EICAR. [6](https://www.thewindowsclub.com/ransomware-protection-in-windows-defender)  
- **D) Resultats amb arxius comprimits** — Taula:

| Format | Detecta a l’escaneig de l’arxiu? | Detecta en extraure? | Notes |
|---|---|---|---|
| ZIP |  |  |  |
| TAR |  |  |  |
| 7Z  |  |  |  |

> *(Justifica els resultats: la detecció en comprimits pot variar per format i moment.)* [7](https://pureinfotech.com/enable-smart-app-control-windows-11/)

---

## 10) Resolució d’incidències

- **No em deixa baixar EICAR ni amb SmartScreen desactivat.**  
→ Crea el fitxer amb l’**string oficial** (Opció B) i continua igual les proves. [6](https://www.thewindowsclub.com/ransomware-protection-in-windows-defender)  
- **No detecta fins que intento extraure TAR/7Z.**  
→ És un resultat vàlid; documenta **quan** es produeix la detecció. [7](https://pureinfotech.com/enable-smart-app-control-windows-11/)

---

## 11) Referències
- EICAR — definició i descàrregues del **fitxer de prova**. [1](https://www.ninjaone.com/blog/windows-defender-exploit-protection-settings/)  
- Microsoft Learn — ús d’**EICAR** per validar Defender/Endpoint. [6](https://www.thewindowsclub.com/ransomware-protection-in-windows-defender)  
- **SmartScreen** (on activar/desactivar temporalment a Windows 11). [2](https://geekchamp.com/enable-or-disable-windows-defender-real-time-protection-in-windows-11/)[3](https://www.solveyourtech.com/how-to-turn-off-windows-defender-in-windows-11-a-step-by-step-guide-4/)  
- **Detecció** d’EICAR dins **arxius comprimits** (comportament i consideracions). [7](https://pureinfotech.com/enable-smart-app-control-windows-11/)

-----

# Fase 3 — Sistemes de protecció de Windows 11

> **Objectius**
> - Identificar les proteccions de **“Protección antivirus y contra amenazas”**.
> - Enumerar opcions de **“Control de aplicaciones y navegador”**.
> - Activar i validar la **protecció contra ransomware** (Controlled Folder Access).

## 3.1. Protección antivirus y contra amenazas

- **Current threats**: estat d’amenaces, darrera execució i botó **Quick scan**. [MS Support](https://support.microsoft.com/en-us/windows/virus-and-threat-protection-in-the-windows-security-app-1362f4cd-d71a-b52a-0b66-c2820032b65e)
- **Scan options**: Quick / Full / Custom / **Microsoft Defender Offline**. [MS Support](https://support.microsoft.com/en-us/windows/virus-and-threat-protection-in-the-windows-security-app-1362f4cd-d71a-b52a-0b66-c2820032b65e)
- **Settings**:
  - **Real‑time protection** (On) — vigilància contínua. [TenForums doc](https://www.tenforums.com/tutorials/3569-turn-off-real-time-protection-microsoft-defender-antivirus.html)
  - **Cloud‑delivered protection** — detecció quasi immediata. [DigitalCitizen](https://www.digitalcitizen.life/windows-defender-gets-cloud-protection-windows-10-how-turn-it/)
  - **Automatic sample submission** — enviament per a veredict ràpid. [Windows11 Forum tut.](https://www.elevenforum.com/t/enable-or-disable-automatic-sample-submission-for-microsoft-defender-antivirus-in-windows-11.4010/)
  - **Tamper Protection** — evita canvis no autoritzats. [TenForums / MS docs](https://www.tenforums.com/tutorials/3569-turn-off-real-time-protection-microsoft-defender-antivirus.html)
- **Updates** (Security intelligence). [MS Support](https://support.microsoft.com/en-us/windows/virus-and-threat-protection-in-the-windows-security-app-1362f4cd-d71a-b52a-0b66-c2820032b65e)
- **Ransomware protection** (enllaç a CFA/OneDrive). [MS Support](https://support.microsoft.com/en-us/windows/virus-and-threat-protection-in-the-windows-security-app-1362f4cd-d71a-b52a-0b66-c2820032b65e)

> **Evidències**: captura de *Current threats*, *Scan options*, *Settings* i *Updates*.

## 3.2. Control de aplicaciones y navegador

- **Smart App Control (SAC)** — només en instal·lacions netes; bloqueig d’apps no fiables. [MS Support / Pureinfotech](https://support.microsoft.com/en-us/windows/app-browser-control-in-the-windows-security-app-8f68fb65-ebb4-3cfb-4bd7-ef0f376f3dc3)
- **Reputation‑based protection (SmartScreen)**:
  - Check apps and files, SmartScreen per Edge/Store, PUA blocking. [MS Support](https://support.microsoft.com/en-us/windows/app-browser-control-in-the-windows-security-app-8f68fb65-ebb4-3cfb-4bd7-ef0f376f3dc3)
- **Exploit protection** — mitigacions sistema/app (DEP, CFG, ASLR…). [MS Support / NinjaOne](https://support.microsoft.com/en-us/windows/app-browser-control-in-the-windows-security-app-8f68fb65-ebb4-3cfb-4bd7-ef0f376f3dc3)

> **Evidències**: captura de la pàgina de **SAC**, llistat de **Reputation-based protection** i **Exploit protection settings**.

## 3.3. Protecció contra ransomware (Controlled Folder Access)

- **Què és**: només apps de confiança poden canviar fitxers en carpetes protegides. [MS Learn](https://learn.microsoft.com/en-us/defender-endpoint/controlled-folders)
- **Activació**: `Windows Security → Virus & threat protection → Manage ransomware protection → Controlled folder access = On`. [Pureinfotech](https://pureinfotech.com/enable-ransomware-protection-windows-11/)
- **Configura**:
  - **Protected folders**: afegeix *Documents de prova*.
  - **Allow an app**: permet apps legítimes si cal.
  - **Block history**: consulta intents bloquejats. [How‑To Geek](https://www.howtogeek.com/controlled-folder-access-windows-11/)
- **Requisits**: Defender actiu i **Real‑time protection On**. [MS Learn](https://learn.microsoft.com/en-us/defender-endpoint/controlled-folders)
- **Gestió avançada**: Intune/MDM/GPO/PowerShell; començar en **Audit mode**. [MS Learn](https://learn.microsoft.com/en-us/defender-endpoint/enable-controlled-folders)
- **Limitació**: CFA no evita lectura/exfiltració; protegeix contra canvis/supressions. [How‑To Geek](https://www.howtogeek.com/controlled-folder-access-windows-11/)

> **Evidències**: captura del toggle de **CFA**, de **Protected folders**, d’un **bloqueig** al *Block history*.

---

