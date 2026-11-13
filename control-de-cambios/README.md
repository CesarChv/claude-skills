# Skill: control-de-cambios

Skill personal de Claude Code que aplica las mismas reglas de control de cambios,
versionamiento y commits en **cualquier proyecto**.

## Qué hace

| # | Regla | Resumen |
|---|---|---|
| 1 | Control de cambios | Mantiene `CHANGELOG.md` en la raíz, con entradas por tipo. |
| 2 | Tipos de cambio | `feat`, `fix`, `docs`, `test`, `refactor`, `chore`. |
| 3 | Versionamiento | SemVer: `feat` sube la menor, `fix` sube el parche. |
| 4 | Commits y push | Solo cuando se piden; el commit lleva un resumen de lo implementado y sale únicamente con la cuenta personal, sin menciones a Claude. |

Las reglas completas están en [`SKILL.md`](SKILL.md); ese es el archivo que Claude lee.
Este README es solo para personas.

## Cómo se usa

- **Automático:** Claude la carga cuando termina un cambio, toca un changelog o una versión, o cuando le pides commit/push.
- **A mano:** escribe `/control-de-cambios` en Claude Code.

Ejemplos de lo que la activa: "haz el commit", "sube los cambios", "versiona esto", "actualiza el changelog".

## Cuenta de git esperada

`CesarChv <cesar_chv19@outlook.com>`. Si un repositorio tiene otra identidad configurada,
Claude debe detenerse y preguntar. Si cambias de cuenta, actualiza esa línea en `SKILL.md`.

## Cómo modificarla

Edita `SKILL.md`. Los cambios aplican en la siguiente sesión de Claude Code.

- La `description` de la cabecera decide **cuándo** se activa: si no se dispara cuando esperas, añade ahí las palabras que usas.
- El cuerpo decide **qué hace**.

## Ubicación

`C:\Users\cesar\.claude\skills\control-de-cambios\` — es una skill de usuario: funciona en todos
tus proyectos de esta PC, pero no viaja con los repositorios. Para llevarla a otra máquina, copia la carpeta.

## Historial

- **1.0.0** (2026-11-12): primera versión — changelog, tipos feat/fix, SemVer, commits con resumen y sin atribución a Claude.
