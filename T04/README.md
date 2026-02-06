# Introducció al cas

Després del nostre assessorament, TransLògic S.A. ens encarrega el desplegament dels seus servidors Windows Servers 2025.

Per aquest motiu, haurem de desplegar diverses màquines virtuals i, amb l’objectiu de ser eficients i seguir bones pràctiques, realitzarem **una instal·lació de prova** que servirà tant per aprendre els procediments com per elaborar **una guia d’instal·lació**, que ha de proporcionar una documentació de base a la posterior implantació als sistemes del client.

***

# Procediment

*   Crea una màquina virtual amb **8 GB de RAM** i **dos processadors**.  
    La VM disposarà de **dos discos**:
    *   un de **32 GB** com a disc principal (on instal·lareu el SO)
    *   un de **10 GB** com a disc secundari  
        La màquina haurà de tenir **dues interfícies de xarxa**:
    *   una en **xarxa NAT (no NAT)**
    *   una en **host-only**

*   Instal·la **Windows Server 2025 en mode GUI**, idioma **US** però configuració i teclat en **espanyol**.

*   Canvia el nom de l’equip a **DCxx** (xx és el vostre número de llista).

*   Actualitza la màquina virtual (un cop fet, **pausa les actualitzacions** tot el temps que sigui possible).

***

# Contingut de la guia

*   Compara la configuració de la màquina virtual definida a l’apartat anterior amb els requisits indicats per Microsoft.  
    **Són coherents?**

*   Documenta els diversos procediments de la instal·lació amb **captures de pantalla** i observacions.  
    Recorda que el format a utilitzar és **Markdown**.

***

# Materials i links de suport

*   **UD.6. AA2. Instal·lació Window Server 2025** — *\[Moodle 0224 Sist. Operatius en Xarxa]*
*   **Requisitos de hardware para Windows Server** — *Microsoft Learn (enllaç)*

