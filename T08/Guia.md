# REPTE: MALWARE I PROGRAMARI ANTIMALWARE

## Objetivo
Comprobar cómo funciona el malware y el software antimalware en un entorno seguro, realizando pruebas con:
- **EICAR** (archivo de prueba)
- **PSRansom** (simulación de ransomware)
- **WannaCry** (ransomware real en entorno controlado)

---

## FASE 1: Preparación de la máquina virtual

### Objetivo
Crear una instantánea (snapshot) para poder restaurar el estado inicial si algo sale mal.

### Pasos
1. Abre **VirtualBox**.
2. Selecciona la máquina virtual con **Windows 11**.
3. Haz clic en la pestaña **Instantáneas**.
4. Pulsa **Tomar instantánea**.
5. Asigna un nombre:  
   `Abans de proves antimalware`.

**Captura:**  
`[Inserta aquí la captura de la instantánea creada]`

---

## FASE 2: Desactivar SmartScreen y protección en tiempo real

### Objetivo
Permitir la descarga del archivo de prueba EICAR.

### Pasos
1. **Desactivar SmartScreen:**
   - Configuración → Privacidad y seguridad → Control de aplicaciones y navegador.
   - Desactiva:
     - Comprobar aplicaciones y archivos
     - SmartScreen para Microsoft Edge
     - Protección contra descargas

2. **Desactivar protección en tiempo real:**
   - Seguridad de Windows → Protección antivirus y contra amenazas → Configuración.
   - Desactiva **Protección en tiempo real**.

3. **Descargar EICAR:**
   - Accede a [https://www.eicar.org](https://www.eicar.org) y descarga el archivo de prueba.

**Capturas:**  
`[Inserta captura de SmartScreen desactivado]`  
`[Inserta captura de protección en tiempo real desactivada]`  
`[Inserta captura del archivo EICAR descargado]`

---

## FASE 3: Prueba con EICAR y compresión

### Objetivo
Comprobar si el antivirus detecta el archivo EICAR en diferentes formatos.

### Pasos
1. Reactiva la protección en tiempo real.
2. Analiza el archivo EICAR → debería detectarlo.
3. Desactiva la protección en tiempo real.
4. Comprime el archivo en:
   - `.zip`
   - `.tar`
   - `.7z`
5. Reactiva la protección y analiza cada archivo.

**Resultados esperados:**
- ZIP: Detectado
- TAR: Detectado
- 7z: Puede que no detectado

**Capturas:**  
`[Inserta captura de cada prueba con el resultado]`

---

## FASE 4: Protecciones de Windows 11

### Pregunta
**¿Qué protecciones incorpora Windows 11?**

### Respuesta
- **Protección antivirus y contra amenazas:**
  - Protección en tiempo real
  - Protección basada en la nube
  - Protección contra manipulación

- **Control de aplicaciones y navegador:**
  - SmartScreen para aplicaciones y archivos
  - Protección contra descargas

- **Protección contra ransomware:**
  - Acceso controlado a carpetas
  - Copias de seguridad con OneDrive

**Captura:**  
`[Inserta captura de la sección de protección contra ransomware]`

---

## FASE 5: Prueba con PSRansom (simulación ransomware)

### Objetivo
Simular un ataque y comprobar la protección contra ransomware.

### Pasos
1. Crea archivos en **Documentos**.
2. Desactiva la protección contra ransomware.
3. Descarga PSRansom desde [https://github.com/JoelGMSec/PSRansom](https://github.com/JoelGMSec/PSRansom).
4. Permite ejecución de scripts:
   ```powershell
   Set-ExecutionPolicy -ExecutionPolicy unrestricted
  
