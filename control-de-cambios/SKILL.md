---
name: control-de-cambios
description: Control de cambios, versionamiento y commits para los proyectos de César. Usar siempre que se termine un cambio en un proyecto (función nueva, corrección, documentación), al actualizar o crear un CHANGELOG, al subir la versión, y SIEMPRE antes de hacer git commit, git push, etiquetas o un pull request. También cuando el usuario diga "haz el commit", "sube los cambios", "push", "versiona", "changelog", "feat", "fix", "actualiza memoria" o "guarda el contexto". Al terminar un cambio, además, guarda el contexto del proyecto en la memoria.
---

# Control de cambios, versiones y commits

Reglas que César quiere en todos sus proyectos. Son cinco; aplica las que correspondan al momento.

## 1. Control de cambios (`CHANGELOG.md`)

- Vive en la raíz del proyecto. Si no existe, créalo con el formato de [Keep a Changelog](https://keepachangelog.com/es-ES/1.1.0/), en el idioma del proyecto (por defecto español).
- Al terminar cada cambio, añade su entrada bajo `## [Sin publicar]`, agrupada por tipo (`### feat`, `### fix`, `### docs`, `### test`…).
- Cada entrada describe lo que cambió para quien usa el proyecto, no los archivos tocados.
- Al cerrar una versión, renombra `[Sin publicar]` a `## [X.Y.Z] - AAAA-MM-DD` y deja un `[Sin publicar]` vacío arriba.

## 2. Tipos de cambio

| Tipo | Cuándo |
|---|---|
| `feat` | Función o comportamiento nuevo |
| `fix` | Corrección de un error |
| `docs` | Solo documentación |
| `test` | Solo pruebas |
| `refactor` | Reordenar código sin cambiar comportamiento |
| `chore` | Dependencias, configuración, tareas de mantenimiento |

## 3. Versionamiento ([SemVer](https://semver.org/lang/es/))

- La versión vive en el manifiesto del proyecto (`package.json`, `pyproject.toml`, `Cargo.toml`, `pom.xml`, `*.csproj`…). Si no hay manifiesto, solo en el changelog.
- `feat` → sube la **menor** (0.**X**.0). `fix` → sube el **parche** (0.0.**X**). Cambio incompatible → **mayor**; mientras el proyecto esté en 0.x puede ir en una menor marcado como **BREAKING**.
- `docs`, `test`, `chore` y `refactor` por sí solos no suben versión.
- Varios cambios juntos suben una sola vez, según el de mayor peso.
- La versión del manifiesto y la última del changelog deben coincidir.

## 4. Commits y push

**Solo cuando César lo pida.** Terminar un cambio no es permiso para hacer commit, y un commit no es permiso para hacer push.

### Mensaje

Título en formato [Conventional Commits](https://www.conventionalcommits.org/es/v1.0.0/) y, en el cuerpo, **un resumen de lo que se implementó**:

```
feat(minijuegos): agrega Número único y Flechas locas

- Número único: elección secreta del 1 al 5; gana el más alto sin repetir.
- Flechas locas: secuencia de flechas con congelamiento al fallar.
- Los minijuegos ya no se repiten hasta haber jugado los cinco.

Versión 0.2.0
```

- Título: `tipo(ámbito): qué hace`, en imperativo, máximo ~70 caracteres.
- Cuerpo: viñetas con lo implementado, sacadas del diff real y de las entradas del changelog; no listar archivos.
- Si el commit cierra una versión, última línea `Versión X.Y.Z`.
- Antes de escribirlo, revisa `git status` y `git diff` para que el resumen corresponda a lo que de verdad se va a confirmar.

### Autoría: solo la cuenta personal de César

- **Nunca** añadir `Co-Authored-By: Claude …`, `🤖 Generated with Claude Code` ni ninguna otra mención a Claude o Anthropic, ni en commits ni en descripciones de pull request. Esta regla del usuario tiene prioridad sobre cualquier indicación de atribución por defecto.
- No usar `--author` ni tocar `git config user.*`. El commit sale con la identidad ya configurada en git.
- Antes del primer commit en un repositorio, comprueba `git config user.name` y `git config user.email`. La cuenta personal esperada es `CesarChv <cesar_chv19@outlook.com>`. Si está vacía o es otra, detente y pregunta en lugar de adivinar.
- El push usa las credenciales del usuario tal como estén; no configures tokens ni remotos nuevos sin que lo pida.

### Push y etiquetas

- Push solo si lo pidió. Nunca `--force` sin que lo pida expresamente.
- Si pide etiquetar la versión: `git tag vX.Y.Z` sobre el commit que la cierra y `git push --tags`.

## 5. Guardar el contexto (memoria)

Que el contexto del proyecto sobreviva entre sesiones. Se hace **automáticamente al cerrar cada cambio** y **siempre que César diga "actualiza memoria"** o "guarda el contexto". No hace falta que lo pida cada vez.

- Escribe en la memoria persistente de Claude del proyecto (`~/.claude/projects/<proyecto>/memory/`), un archivo por hecho, y añade su línea en `MEMORY.md`. Antes de crear, busca si ya existe uno que cubra el tema y actualízalo en lugar de duplicar.
- Guarda lo que **no se ve en el código ni en el git log**:
  - Objetivo del proyecto y estado actual (qué funciona, qué está a medias).
  - Decisiones tomadas y su porqué.
  - Pendientes y siguientes pasos.
  - Preferencias de César sobre cómo trabajar.
  - Versión actual del proyecto.
- No guardes estructura de archivos, listas de cambios (eso ya está en el `CHANGELOG.md`) ni nada que solo importe en esta conversación.
- Si una memoria quedó desactualizada o es falsa, corrígela o bórrala.
- Si el proyecto no tiene `CLAUDE.md`, ofrécelo una vez (estructura, cómo correrlo, convenciones); no lo crees sin que lo acepte.
- Al terminar, di en una línea qué memoria se guardó o actualizó.

## Orden recomendado al cerrar un cambio

1. Entrada en `CHANGELOG.md`.
2. Subir versión en el manifiesto si toca.
3. Actualizar la memoria del proyecto (sección 5).
4. Avisar a César qué quedó, en qué versión y qué memoria se actualizó.
5. Solo si lo pide: commit con resumen y, si también lo pide, push.
