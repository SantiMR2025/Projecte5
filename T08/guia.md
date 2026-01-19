



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
