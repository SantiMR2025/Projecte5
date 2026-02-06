# Introducció

Un cop tenim ja el nostre domini creat, el següent pas és **desplegar el domini**, és a dir, crear els diferents objectes que el formen: grups, usuaris i màquines. Aquí veurem la utilitat d’organitzar els objectes amb **unitats organitzatives (OU)**.

***

# Procediment pràctic

*   Crear una **estructura d’unitats organitzatives (OU)** que sigui coherent i justificar la decisió.

*   Definir la següent estructura de grups:
    *   **gestio**
    *   **magatzem**
    *   **gerencia**
    *   **personal**  
        *(tots els grups anteriors han de ser membres d’aquest grup)*

*   Crear una **plantilla d’usuari** per cadascun dels grups:

    *   Gestio
    *   Magatzem
    *   Gerencia

    Cada plantilla ha de tenir definida:

    *   la **pertinença al grup**
    *   la **creació de la carpeta personal**

*   Definir **un usuari de prova** per cadascuna de les plantilles.

*   Aprovisionar un equip anomenat **PC1** dins la OU **equips**.

*   Crear una màquina virtual amb **Windows 11**, amb:

    *   **4 GB de RAM**
    *   **disc suficient**
    *   xarxa en mode **NAT**

    Un cop creat l’equip, **agregeu-lo al domini**.

*   Comprovar el correcte funcionament iniciant sessió a l’equip client amb **els tres usuaris de prova**.

***

# Materials i links de suport

*   **UD6.AA3 Desplegament** — *\[Moodle 0224 SOX]*
