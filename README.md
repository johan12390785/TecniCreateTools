# 🎈 Plantilla de Evento - TecniLauncher

Este repositorio sirve como base para crear nuevos eventos en el Launcher. Sigue esta guía para configurar tu servidor técnico, modpack o evento especial.

## 📂 Estructura de Archivos
Para que el evento funcione, necesitas obligatoriamente estos 3 archivos en tu repositorio:

1. **eventoinfo.json** (Datos básicos: nombre, versión, loader)
2. **mods.json** (Lista de mods a descargar desde Modrinth)
3. **recursos.json** (Configs, texturas o archivos extra)

---

## 1. Configurar eventoinfo.json
Este archivo define la identidad del evento.

[
  {
    "nombre": "Nombre Del Evento",
    "foto_url": "LINK_DIRECTO_A_TU_IMAGEN_PNG",
    "version_mc": "1.20.1",
    "modloader": "Fabric",
    "version_modloader": "0.14.22",
    "version_evento": "1.0.0" 
  }
]

> **Nota:** El campo "version_evento" sirve para notificar actualizaciones. Si cambias el número, el botón del Launcher cambiará automáticamente a "ACTUALIZAR".

---

## 2. Configurar mods.json
Aquí colocas los IDs de los mods de **Modrinth**. El Launcher los descargará e instalará automáticamente.

{
  "mods": [
    { 
      "id": "P7dR8mSH", 
      "slug": "fabric-api", 
      "version_fija": "" 
    },
    { 
      "id": "AANobbMI", 
      "slug": "sodium", 
      "version_fija": "mc1.20.1-0.5.3" 
    }
  ]
}

### 🕵️ ¿Cómo consigo el ID del mod?
1. Ve a Modrinth.com.
2. Busca el mod que quieres.
3. En la columna de la derecha, baja hasta **"Technical Information"**.
4. Busca el campo **"Project ID"**. Ese código raro es el ID.

> **Tip:** Si dejas la versión fija vacía, el Launcher descargará la última versión compatible. Si necesitas una versión específica, pon el ID de esa versión ahí.

---

## 3. Configurar recursos.json
Usa esto para descargar configuraciones, resourcepacks, mapas o scripts. El archivo debe ser un **.zip** con enlace de descarga directa.

[
  {
    "nombre": "Pack de Texturas",
    "url": "[https://tusitio.com/serverpack.zip](https://tusitio.com/serverpack.zip)",     <------ Tambien puedes subir al github y copiar el raw de descarga
    "destino": "resourcepacks"
  }
]

> **Importante:** El .zip se descomprimirá automáticamente dentro de la carpeta que indiques en "destino".

---

## ⚠️ Errores Comunes (¡LEER!)

1. **La Coma Traicionera:**
   En los archivos JSON, el **último** elemento de una lista NO debe llevar coma al final. Si la pones, el Launcher dará error.

2. **Repositorio Privado:**
   Este repositorio debe estar en **PÚBLICO** para que el Launcher pueda leer los archivos. Ve a la configuración de tu repositorio (Settings) y cambia la visibilidad a Public.

3. **Enlaces RAW:**
   Cuando configures el archivo maestro en tu repositorio principal, asegúrate de usar los enlaces **Raw**. Abre el archivo en GitHub y pulsa el botón que dice "Raw" antes de copiar el link.
