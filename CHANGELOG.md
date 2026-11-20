# Control de cambios

Formato [Keep a Changelog](https://keepachangelog.com/es-ES/1.1.0/). Cada skill lleva su propia versión
[SemVer](https://semver.org/lang/es/), indicada en la tabla del README.

## [Sin publicar]

### docs
- README raíz reescrito: descripción completa de `control-de-cambios` (convenciones, activación y ejemplo de commit), índice, requisitos, instalación y estructura del repositorio.
- Se agrega este control de cambios.

## control-de-cambios [1.2.0] - 2026-11-19

### feat
- El contexto del proyecto ahora se guarda y actualiza en el `CLAUDE.md` de su carpeta (Claude lo carga solo al abrir la sesión ahí, es visible y viaja con el proyecto) en lugar de la memoria oculta de Claude, que queda para preferencias generales.
- Al terminar indica la ruta exacta del archivo actualizado y, si el contexto estaba solo en la memoria oculta, lo pasa al `CLAUDE.md` una vez sin borrar el original.

## control-de-cambios [1.1.0] - 2026-11-19

### feat
- Nueva regla 5: guarda el contexto del proyecto (estado, decisiones, pendientes y preferencias) en la memoria de Claude al cerrar un cambio o cuando se dice "actualiza memoria".

## control-de-cambios [1.0.0] - 2026-11-12

### feat
- Primera versión: `CHANGELOG.md`, tipos `feat`/`fix`, versionamiento SemVer, commits con resumen de lo implementado y uso exclusivo de la cuenta personal de git.
