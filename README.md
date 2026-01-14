# 🎈 Plantilla de Evento - TecniLauncher

Este repositorio sirve como base para crear nuevos eventos. Sigue esta guía para que los jugadores puedan entrar a tu servidor de una froma mas facil.

## 📂 Archivos Necesarios

Para que el evento funcione, necesitas obligatoriamente estos 3 archivos:

* **`eventoinfo.json`** (Nombre, versión del juego, foto)
* **`mods.json`** (Lista de mods de Modrinth)
* **`recursos.json`** (Configs, ResourcePacks, Mapas o Mods externos)

---

## 1. Configurar `eventoinfo.json`

Define la identidad de tu evento aquí.

```json
{
  "nombre": "Gran Evento",
  "foto_url": "LINK_DIRECTO_IMAGEN.png",
  "version_mc": "1.20.1",
  "modloader": "Fabric",
  "version_modloader": "0.14.22",
  "version_evento": "1.0.0"
}
```
> **🔄 Actualizaciones:** Cada vez que hagas un cambio en los mods o configs, **aumenta el número** de `version_evento` (ej: de `1.0.0` a `1.0.1`). Esto avisará a los jugadores que deben actualizar.

---

## 2. Configurar `mods.json` (Modrinth)

Aquí van los mods oficiales de la tienda Modrinth.

```json
{
  "mods": [
    { 
      "id": "P7dR8mSH", 
      "version_fija": "0.92.0+1.20.1" 
    },
    { 
      "id": "AANobbMI", 
      "version_fija": "" 
    },
    { 
      "id": "Wq5SjeWM", 
      "version_fija": "" 
    },
    { 
      "id": "J81TRJWm", 
      "version_fija": "" 
    },
    { 
      "id": "CVT4pFB2", 
      "version_fija": "" 
    }
  ]
}

```

### 🛑 Reglas de Oro para Mods:
1. **ID:**
   * **`id`**: Es el código raro (ej: `P7dR8mSH`). **Es obligatorio** para descargar.
2. **Version Fija:**
   * Déjalo siempre en `""` (vacío). El launcher buscará automáticamente la última versión compatible.
   * **Solo** pon un número si el mod está roto y necesitas una versión antigua específica.

---

## 3. Configurar `recursos.json` (Configs y Packs)

Aquí descargas todo lo que NO sea un mod de Modrinth (ResourcePacks, Menús, Configs, Scripts).
**¡OJO!** Ahora puedes decidir si el archivo se descomprime o no.

### Opción A: Configs, Mapas o Menús (`descomprimir: true`)
Usa esto si subes un `.zip` que contiene carpetas dentro (ej: carpeta `fancymenu`).

```json
{
  "nombre": "Menu Personalizado",
  "url": "LINK_DE_TU_CONFIG.zip",
  "destino": "config",
  "descomprimir": true
}
```
*El launcher bajará el zip, sacará los archivos y borrará el zip.*

### Opción B: Resource Packs y Shaders (`descomprimir: false`)
Usa esto para archivos que Minecraft necesita leer cerrados (sin descomprimir).

```json
{
  "nombre": "Pack Texturas Realistas",
  "url": "LINK_DEL_PACK.zip",
  "destino": "resourcepacks",
  "descomprimir": false
}
```
*El launcher bajará el archivo y lo dejará guardado tal cual.*

---

## 4. Mods Personalizados (GitHub Releases)

Si tienes un mod propio o muy pesado (>100MB) que no está en la tienda:

1. Ve a la sección **Releases** de este repositorio (a la derecha).
2. Crea una "New Release" y sube tu archivo `.jar` o `.zip`.
3. Copia el link de descarga del archivo subido (Click derecho en Assets -> Copiar enlace).
4. Agrégalo a `recursos.json`:

```json
{
  "nombre": "Mi Mod Propio",
  "url": "PEGAR_LINK_DE_RELEASE.jar",
  "destino": "mods",
  "descomprimir": false
}
```

---

## ⚠️ Errores Frecuentes

1. **La Coma Final:** En los archivos JSON, el **último** elemento de la lista NO lleva coma.
   * ✅ `... }, { ... }`
   * ❌ `... }, { ... },`
2. **Repositorio Privado:** Asegúrate de que este repositorio esté en **Public** en los Settings.
3. **Enlaces RAW:** Si subes archivos pequeños directamente al código, usa siempre el botón **"Raw"** antes de copiar el link.
