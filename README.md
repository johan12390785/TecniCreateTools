# 🎈 Plantilla de Evento - TecniLauncher

Este repositorio sirve como base para crear nuevos eventos en el Launcher. Sigue esta guía para configurar tu servidor técnico, modpack o evento especial.

## 📂 Estructura de Archivos

Para que el evento funcione, necesitas obligatoriamente estos 3 archivos en tu repositorio:

* **`eventoinfo.json`** (Datos básicos: nombre, versión, loader)
* **`mods.json`** (Lista de mods a descargar desde Modrinth)
* **`recursos.json`** (Configs, texturas o archivos extra)

---

## 1. Configurar `eventoinfo.json`

Este archivo define la identidad del evento.

```json
{
  "nombre": "Nombre Del Evento",
  "foto_url": "LINK_DIRECTO_A_TU_IMAGEN_PNG",
  "version_mc": "1.20.1",
  "modloader": "Fabric",
  "version_modloader": "0.14.22",
  "version_evento": "1.0.0"
}
```

> **Nota:** El campo `version_evento` sirve para notificar actualizaciones. Si cambias el número, el botón del Launcher cambiará automáticamente a "ACTUALIZAR".

---

## 2. Configurar `mods.json`

Aquí colocas los IDs de los mods de **Modrinth**. El Launcher los descargará e instalará automáticamente.

```json
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
```

### 🕵️ ¿Cómo consigo el ID del mod?

1. Ve a [Modrinth.com](https://modrinth.com).
2. Busca el mod que quieres.
3. En la columna de la derecha, ve a los **"..."**.
4. Busca el campo **"Copy ID"**. Ese código raro es el ID.
   ![Mod ID](https://raw.githubusercontent.com/johan12390785/EventoEjemplo/refs/heads/main/ModId.png)

> **Tip:** Si dejas la versión fija vacía, el Launcher descargará la última versión compatible. Si necesitas una versión específica, pon el ID de esa versión ahí.

---

## 3. Configurar `recursos.json`

Usa esto para descargar configuraciones, resourcepacks, mapas o scripts. El archivo debe ser un **.zip** con enlace de descarga directa.

```json
[
  {
    "nombre": "Pack de Texturas",
    "url": "https://tusitio.com/serverpack.zip",
    "destino": "resourcepacks"
  }
]
```

> **Importante:** El `.zip` se descomprimirá automáticamente dentro de la carpeta que indiques en `destino`.

---

## 4. Mods Personalizados (No están en Modrinth)

Si necesitas instalar un mod propio o que no existe en la tienda, tienes dos formas de subirlo dependiendo de su peso:

### Opción A: Si el archivo pesa MENOS de 100MB (Rápido)
Puedes subirlo directamente junto con los archivos de este repositorio.

1. Arrastra tu archivo `.jar` o `.zip` a la lista de archivos en GitHub y dale a "Commit changes".
2. Haz clic en el archivo que acabas de subir.
3. Busca el botón que dice **"Raw"** (o "Download") a la derecha.
4. Haz **Click Derecho** > **Copiar dirección del enlace**.

### Opción B: Si el archivo pesa MÁS de 100MB (GitHub Releases)
GitHub no permite subir archivos gigantes directamente. Debes usar **Releases** (Soporta hasta 2GB):

1. En tu repositorio, mira a la derecha donde dice **"Releases"** y haz clic en "Create a new release".
2. Ponle un título (ej: "Mods Pesados") y **arrastra tu archivo** a la zona de subida.
3. Publica la release.
4. En la sección "Assets" de la release publicada, haz **Click Derecho** sobre tu archivo y **Copiar dirección del enlace**.

---

### 📝 Cómo agregarlo al `recursos.json`
Independientemente de la opción que uses, pega el enlace que copiaste en tu archivo `recursos.json` apuntando a la carpeta de mods:

**Agrégalo a `recursos.json` así:**

```json
[
  {
    "nombre": "Mod Custom Gigante",
    "url": "PEGAR_LINK_DE_LA_RELEASE_AQUI.zip",
    "destino": "mods"
  }
]
```

---

## ⚠️ Errores Comunes (¡LEER!)

1. **La Coma Traicionera:** En los archivos JSON, el **último** elemento de una lista NO debe llevar coma al final. Si la pones, el Launcher dará error.

2. **Repositorio Privado:** Este repositorio debe estar en **PÚBLICO** para que el Launcher pueda leer los archivos. Ve a la configuración de tu repositorio (Settings) y cambia la visibilidad a Public.

3. **Enlaces RAW:** Cuando configures el archivo maestro en tu repositorio principal, asegúrate de usar los enlaces **Raw**. Abre el archivo en GitHub y pulsa el botón que dice "Raw" antes de copiar el link.
