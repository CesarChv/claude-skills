# claude-skills

![Claude Code](https://img.shields.io/badge/Claude%20Code-skills-d97757)
![Skills](https://img.shields.io/badge/skills-1-blue)
![Convención](https://img.shields.io/badge/commits-Conventional%20Commits-fe5196)
![Versionado](https://img.shields.io/badge/versionado-SemVer-3f4551)

Colección de skills para [Claude Code](https://claude.com/claude-code) orientadas a mantener un flujo de
trabajo consistente entre proyectos.

Una *skill* es un paquete de instrucciones que Claude carga automáticamente cuando la tarea lo requiere.
Permite definir una sola vez las convenciones de trabajo y aplicarlas en cualquier repositorio, sin
repetirlas en cada sesión.

## Contenido

- [Skills](#skills)
  - [control-de-cambios](#control-de-cambios)
- [Requisitos](#requisitos)
- [Instalación](#instalación)
- [Estructura del repositorio](#estructura-del-repositorio)
- [Agregar una skill](#agregar-una-skill)
- [Control de cambios](#control-de-cambios-del-repositorio)
- [Autor](#autor)

## Skills

| Skill | Versión | Para qué sirve |
|---|---|---|
| [`control-de-cambios`](#control-de-cambios) | 1.0.0 | Changelog, versionamiento y commits ordenados en cualquier proyecto. |

---

### control-de-cambios

Estandariza la gestión del historial de un proyecto: cada cambio queda documentado, la versión se
incrementa según el tipo de cambio y cada commit describe lo implementado. Es independiente del lenguaje
y del gestor de paquetes.

**Convenciones que aplica**

| Regla | Detalle |
|---|---|
| **Control de cambios** | Mantiene un `CHANGELOG.md` en la raíz (formato [Keep a Changelog](https://keepachangelog.com/es-ES/1.1.0/)). Si no existe, lo crea. Cada cambio terminado se anota bajo `[Sin publicar]`, agrupado por tipo y descrito para quien usa el proyecto, no como lista de archivos. |
| **Tipos de cambio** | `feat` (función nueva), `fix` (corrección), `docs`, `test`, `refactor` y `chore`. |
| **Versionamiento** | [SemVer](https://semver.org/lang/es/) en el manifiesto del proyecto (`package.json`, `pyproject.toml`, `Cargo.toml`…). `feat` sube la versión menor, `fix` sube el parche y un cambio incompatible sube la mayor. `docs`, `test`, `chore` y `refactor` no suben versión. El manifiesto y el changelog siempre coinciden. |
| **Commits con resumen** | Título en [Conventional Commits](https://www.conventionalcommits.org/es/v1.0.0/) (`feat(ámbito): qué hace`) y un cuerpo con viñetas de lo implementado, sacadas del diff real. |
| **Solo cuenta personal** | Los commits, push y pull requests salen únicamente con la identidad configurada en git. Nunca se añade `Co-Authored-By: Claude` ni "Generated with Claude Code". Si la identidad de git no es la esperada, Claude se detiene y pregunta. |
| **Nada sin pedirlo** | Terminar un cambio no autoriza un commit, y un commit no autoriza un push. Tampoco se hace `--force` ni se crean etiquetas sin pedirlo. |

**Activación**

- Automática, al terminar un cambio, al tocar un changelog o una versión, y antes de cualquier commit, push, etiqueta o pull request.
- Con frases como "haz el commit", "sube los cambios", "versiona esto" o "actualiza el changelog".
- Manual, con el comando `/control-de-cambios`.

**Ejemplo de commit generado**

```
feat(minijuegos): agrega Número único y Flechas locas

- Número único: elección secreta del 1 al 5; gana el más alto sin repetir.
- Flechas locas: secuencia de flechas con congelamiento al fallar.
- Los minijuegos ya no se repiten hasta haber jugado los cinco.

Versión 0.2.0
```

**Personalización:** la skill declara la identidad de git esperada. Para reutilizarla con otra cuenta,
modifica esa línea en [`control-de-cambios/SKILL.md`](control-de-cambios/SKILL.md).

Documentación completa en el [README de la skill](control-de-cambios/README.md).

---

## Requisitos

- [Claude Code](https://claude.com/claude-code) (CLI, aplicación de escritorio o extensión de IDE).
- Git, con `user.name` y `user.email` configurados.

## Instalación

**Para todos los proyectos de la máquina.** Las skills de usuario residen en `~/.claude/skills/`:

```powershell
git clone https://github.com/CesarChv/claude-skills.git "$HOME\.claude\skills"
```

Si el directorio ya existe y tiene contenido, clona el repositorio en otra ubicación y copia la carpeta de
cada skill dentro de `~/.claude/skills/`.

**Para un único proyecto.** Copia la carpeta de la skill en `.claude/skills/` dentro del repositorio;
quedará disponible para cualquiera que lo clone.

Las skills se cargan al iniciar la siguiente sesión de Claude Code.

## Estructura del repositorio

```
claude-skills/
├── README.md                 Índice y documentación general
├── CHANGELOG.md              Historial de cambios del repositorio
└── control-de-cambios/
    ├── SKILL.md              Instrucciones que lee Claude
    └── README.md             Documentación de la skill
```

## Agregar una skill

1. Crear una carpeta con el nombre de la skill.
2. Añadir un `SKILL.md` con la cabecera `name` y `description` (la descripción determina cuándo se activa) y las instrucciones.
3. Añadir un `README.md` con la documentación para personas.
4. Registrarla en la tabla de [Skills](#skills), con su propia sección.
5. Anotar el cambio en [`CHANGELOG.md`](CHANGELOG.md).

## Control de cambios del repositorio

El historial se documenta en [`CHANGELOG.md`](CHANGELOG.md). Cada skill mantiene su propia versión
SemVer, indicada en la tabla de [Skills](#skills).

## Autor

[@CesarChv](https://github.com/CesarChv)
