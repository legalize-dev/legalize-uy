# Legalize UY

### Legislación uruguaya consolidada en Markdown, versionada con Git.

Cada ley es un fichero. Cada reforma es un commit.

**Fuente oficial:** [IMPO](https://www.impo.com.uy) — Centro de Información Oficial del Uruguay

Forma parte del proyecto [Legalize](https://github.com/legalize-dev/legalize) · [legalize.dev](https://legalize.dev)

> **Fase inicial** — Este repositorio está en desarrollo activo. La estructura de los ficheros, el historial de commits y el contenido pueden cambiar significativamente, incluyendo regeneraciones completas.

## Inicio rápido

```bash
# Clonar la legislación uruguaya
git clone https://github.com/legalize-dev/legalize-uy.git

# Leer la Constitución de la República
less uy/UY-constitucion-1967.md

# Buscar en la Ley de Protección de Datos Personales
grep -A 5 "Artículo 1" uy/UY-ley-18331.md

# Ver el historial de modificaciones de una ley
git log --oneline -- uy/UY-ley-19996.md

# Leer el Código Tributario
less uy/UY-codigo-tributario-14306.md
```

## Estructura

```
uy/
  UY-constitucion-1967.md          — Constitución de la República (1967)
  UY-ley-19996.md                  — Ley Nº 19.996, Rendición de Cuentas
  UY-ley-18331.md                  — Ley Nº 18.331, Protección de Datos Personales
  UY-decreto-ley-14261.md          — Decreto-Ley Nº 14.261
  UY-decreto-122-2021.md           — Decreto Nº 122/2021
  UY-codigo-civil-16603.md         — Código Civil (Ley 16.603)
  UY-codigo-tributario-14306.md    — Código Tributario (DL 14.306)
  ...
```

La estructura del fichero es **plana** — un solo directorio por país, sin subdirectorios por rango. El tipo de norma está en el frontmatter YAML de cada fichero:

| Prefijo | Tipo |
|---|---|
| `UY-constitucion-` | Constitución de la República |
| `UY-ley-{n}` | Ley nacional aprobada por el Parlamento |
| `UY-decreto-ley-{n}` | Decreto-Ley (período 1973–1985) |
| `UY-decreto-{n}-{año}` | Decreto del Poder Ejecutivo (la numeración se reinicia cada año) |
| `UY-codigo-{nombre}-{n}` | Código (Civil, Penal, Tributario, etc.) |

## Formato

Cada fichero es Markdown con frontmatter YAML:

```yaml
---
title: "Ley Nº 18331 - LEY DE PROTECCION DE DATOS PERSONALES"
identifier: "UY-ley-18331"
country: "uy"
rank: "ley"
publication_date: "2008-08-18"
last_updated: "2008-08-18"
status: "in_force"
source: "https://www.impo.com.uy/bases/leyes/18331-2008"
department: "TABARE VAZQUEZ - DAISY TOURNE - GONZALO FERNANDEZ - ..."
official_type: "Ley"
official_number: "18331"
year: "2008"
promulgation_date: "2008-08-11"
gazette_scan_url: "https://www.impo.com.uy/diariooficial/2008/08/18/5"
references_url: "https://www.impo.com.uy/bases/leyes/18331-2008?verreferencias=norma"
rnld_citation: "tomo 1, semestre 2, 2008, p. 378"
signatories: "TABARE VAZQUEZ - DAISY TOURNE - ..."
article_count: "51"
collection: "leyes"
source_encoding: "ISO-8859-1"
images_dropped: "0"
editorial_notes_count: "19"
---
```

El cuerpo del Markdown contiene **únicamente el texto legal** (artículos, tablas, secciones, capítulos, firmantes). Las notas editoriales que IMPO añade a cada artículo (referencias cruzadas internas, decretos reglamentarios, historia de reformas) **no son parte de la ley aprobada por el Parlamento** y se excluyen del cuerpo del fichero. El número de artículos que tenían notas editoriales en IMPO se conserva en `editorial_notes_count` para que cualquier consumidor que las necesite pueda volver a consultar la fuente original.

Los tipos de commit son: `[bootstrap]` (publicación original), `[reforma]` (modificación) y `[correccion]` (corrección de errata).

## Fuente

Los datos provienen de la API pública JSON del [IMPO](https://www.impo.com.uy/) — el Centro de Información Oficial del Uruguay, que es la fuente oficial de la legislación uruguaya. Cualquier URL de norma con el sufijo `?json=true` devuelve el documento estructurado en JSON.

La licencia de los datos es la [**Licencia de Datos Abiertos del Uruguay**](https://www.impo.com.uy/bases/decretos/54-2017) (Decreto 54/2017): atribución únicamente — los datos pueden usarse, modificarse, distribuirse, publicarse, traducirse y adaptarse en cualquier formato citando a IMPO como proveedor.

## Licencia

[MIT](LICENSE) — el contenido de las normas es de dominio público, el código del pipeline es MIT.

---

Generado por el pipeline [legalize-pipeline](https://github.com/legalize-dev/legalize-pipeline).
