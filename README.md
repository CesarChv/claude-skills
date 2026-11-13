# claude-skills

Mis skills personales para [Claude Code](https://claude.com/claude-code): control de cambios,
versionamiento SemVer y commits con Conventional Commits.

## Skills

| Skill | Qué hace |
|---|---|
| [`control-de-cambios`](control-de-cambios/) | Mantiene `CHANGELOG.md`, tipos `feat`/`fix`, versionamiento SemVer y commits con resumen de lo implementado, usando solo la cuenta personal de git. |

## Instalación

Las skills de usuario viven en `~/.claude/skills/`. En una PC nueva:

```powershell
git clone https://github.com/CesarChv/claude-skills.git "$HOME\.claude\skills"
```

Si esa carpeta ya existe y tiene contenido, clona en otro lado y copia dentro las carpetas de cada skill.

Aplican a partir de la siguiente sesión de Claude Code, en cualquier proyecto.

## Agregar una skill

1. Crear una carpeta con el nombre de la skill.
2. Dentro, un `SKILL.md` con cabecera `name` y `description` (la descripción decide cuándo se activa) y las instrucciones.
3. Un `README.md` para personas.
4. Añadirla a la tabla de arriba.

## Nota

`synced/` la gestiona Claude Code y está excluida del repositorio.
