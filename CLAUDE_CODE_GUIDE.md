# Guía Completa de Claude Code

## Tabla de Contenidos

1. [Introducción](#introducción)
2. [Conceptos Fundamentales](#conceptos-fundamentales)
3. [Shortcuts de Teclado](#shortcuts-de-teclado)
4. [Comandos Slash](#comandos-slash)
5. [Navegación y Comandos del Sistema](#navegación-y-comandos-del-sistema)
6. [Integración con Neovim](#integración-con-neovim)
7. [Creación de Shortcuts Personalizados](#creación-de-shortcuts-personalizados)
8. [Configuración Avanzada](#configuración-avanzada)
9. [Tips y Mejores Prácticas](#tips-y-mejores-prácticas)

---

## Introducción

**Claude Code** es una herramienta CLI (Command Line Interface) desarrollada por Anthropic que te permite interactuar con Claude AI directamente desde tu terminal. Es un asistente de desarrollo que puede leer, escribir y ejecutar código, gestionar archivos, y ayudarte con tareas de desarrollo complejas.

### ¿Qué hace especial a Claude Code?

- **Interfaz de Terminal Nativa**: Trabaja directamente en tu shell favorito (Fish, Zsh, Nushell, etc.)
- **Acceso Completo al Sistema de Archivos**: Puede leer, escribir y modificar archivos en tu proyecto
- **Ejecución de Comandos**: Ejecuta comandos del sistema directamente
- **Contexto Persistente**: Mantiene conversaciones largas con contexto
- **Extensible**: Soporta comandos personalizados, hooks y MCP servers

---

## Conceptos Fundamentales

### Modos de Operación

Claude Code opera en dos modos principales:

#### 1. **Modo Interactivo (REPL)**
- Iniciado con el comando `claude`
- Sesión de chat continua con Claude
- Ideal para desarrollo iterativo y exploración
- Mantiene contexto entre mensajes

#### 2. **Modo Batch**
- Ejecuta comandos únicos: `claude "tu pregunta"`
- Útil para scripts y automatización
- No mantiene historial de conversación

### Estructura de Directorios

```
tu-proyecto/
├── .claude/                    # Configuración de proyecto
│   ├── commands/              # Comandos slash personalizados
│   │   ├── review.md         # Ejemplo: /review
│   │   └── deploy.md         # Ejemplo: /deploy
│   ├── hooks/                # Hooks de eventos
│   ├── mcp/                  # Servidores MCP
│   └── CLAUDE.md            # Memoria del proyecto
│
~/.claude/                     # Configuración global del usuario
├── commands/                  # Comandos personales
├── config.json               # Configuración principal
└── mcp.json                 # Configuración de MCP servers
```

---

## Shortcuts de Teclado

### Navegación Básica

| Shortcut | Acción | Descripción |
|----------|--------|-------------|
| `?` | Ayuda | Muestra todos los shortcuts disponibles |
| `Tab` | Autocompletar | Completa comandos y rutas |
| `↑` / `↓` | Historial | Navega por el historial de comandos |
| `Ctrl + C` | Cancelar | Cancela la operación actual |
| `Ctrl + D` | Salir | Sale de Claude Code |

### Controles de Conversación

| Shortcut | Acción | Descripción |
|----------|--------|-------------|
| `Esc` | Detener | Detiene a Claude (NO cierra el programa) |
| `Esc` `Esc` | Historial | Muestra lista de mensajes anteriores |
| `Ctrl + B` | Background | Mueve un comando Bash al background |

### Edición y Entrada

| Shortcut | Acción | Descripción |
|----------|--------|-------------|
| `Enter` | Enviar | Envía el mensaje actual |
| `Shift + Enter` | Nueva línea | Añade nueva línea sin enviar |
| `Ctrl + V` | Pegar imagen | Pega imagen desde el portapapeles |
| `Shift + Arrastrar` | Referenciar archivo | Arrastra archivos para referenciarlos |

### Edición de Texto (estilo Emacs)

| Shortcut | Acción | Descripción |
|----------|--------|-------------|
| `Ctrl + A` | Inicio de línea | Mueve cursor al inicio |
| `Ctrl + E` | Fin de línea | Mueve cursor al final |
| `Ctrl + K` | Eliminar hasta el final | Elimina desde cursor hasta fin de línea |
| `Ctrl + U` | Eliminar línea | Elimina la línea completa |
| `Ctrl + W` | Eliminar palabra | Elimina la palabra anterior |
| `Alt + B` | Palabra anterior | Mueve cursor a palabra anterior |
| `Alt + F` | Palabra siguiente | Mueve cursor a palabra siguiente |

---

## Comandos Slash

Los comandos slash (`/comando`) son accesos rápidos para funcionalidades específicas.

### Gestión de Sesión

| Comando | Descripción | Ejemplo |
|---------|-------------|---------|
| `/clear` | Limpia el historial de conversación | `/clear` |
| `/compact [instrucciones]` | Compacta la conversación para liberar contexto | `/compact focus on auth` |
| `/exit` | Sale de la sesión actual | `/exit` |
| `/help` | Muestra todos los comandos disponibles | `/help` |

### Configuración y Estado

| Comando | Descripción | Ejemplo |
|---------|-------------|---------|
| `/config` | Abre el panel de configuración | `/config` |
| `/doctor` | Verifica la salud de la instalación | `/doctor` |
| `/status` | Muestra estado de cuenta y sistema | `/status` |
| `/cost` | Estadísticas de uso de tokens | `/cost` |
| `/model` | Selecciona o cambia el modelo de IA | `/model` |

### Proyecto y Memoria

| Comando | Descripción | Ejemplo |
|---------|-------------|---------|
| `/init` | Inicializa proyecto con guía CLAUDE.md | `/init` |
| `/memory` | Edita archivos de memoria CLAUDE.md | `/memory` |

### Herramientas e Integración

| Comando | Descripción | Ejemplo |
|---------|-------------|---------|
| `/hooks` | Configura hooks de eventos | `/hooks` |
| `/mcp` | Gestiona servidores MCP y OAuth | `/mcp` |
| `/permissions` | Ver/actualizar permisos | `/permissions` |

### Desarrollo

| Comando | Descripción | Ejemplo |
|---------|-------------|---------|
| `/review` | Solicita revisión de código | `/review` |
| `/pr_comments` | Ver comentarios de pull request | `/pr_comments` |

### IDE y Terminal

| Comando | Descripción | Ejemplo |
|---------|-------------|---------|
| `/ide` | Conecta con el IDE | `/ide` |
| `/terminal-setup` | Instala binding Shift+Enter (iTerm2/VSCode) | `/terminal-setup` |
| `/vim` | Activa modo vim (alterna insert/command) | `/vim` |

### Cuenta

| Comando | Descripción | Ejemplo |
|---------|-------------|---------|
| `/login` | Cambia de cuenta de Anthropic | `/login` |
| `/logout` | Cierra sesión | `/logout` |

---

## Navegación y Comandos del Sistema

Claude Code puede ejecutar cualquier comando del sistema y manipular archivos. Aquí están los más útiles:

### Listar Directorios y Archivos

```bash
# En Claude Code, simplemente pregunta:
"Lista los archivos en el directorio actual"
"Muéstrame la estructura del proyecto"
"¿Qué archivos hay en ./src?"

# Claude ejecutará automáticamente:
ls -la
tree
find . -name "*.js"
```

### Navegar por el Sistema de Archivos

```bash
# Cambiar de directorio
"Navega a la carpeta src"

# Ver contenido de archivos
"Muéstrame el contenido de config.json"
"Lee el archivo README.md"

# Buscar archivos
"Encuentra todos los archivos .ts en el proyecto"
"Busca archivos que contengan 'authentication'"
```

### Ejecutar Comandos Personalizados

Claude puede ejecutar cualquier comando que ejecutarías en tu terminal:

```bash
# Git
"¿Cuál es el estado de git?"
"Haz commit de los cambios con el mensaje 'fix: authentication bug'"
"Muéstrame el log de git"

# NPM/Package Managers
"Instala las dependencias"
"Ejecuta npm run build"
"Actualiza los paquetes"

# Docker
"Lista los contenedores en ejecución"
"Construye la imagen de Docker"
"Inicia el contenedor"

# Procesos
"Muéstrame los procesos en ejecución"
"Encuentra el proceso que usa el puerto 3000"

# Redes
"Verifica la conectividad a localhost:8080"
"Muestra las conexiones de red activas"
```

### Manipulación de Archivos

```bash
# Crear archivos
"Crea un nuevo archivo llamado config.yaml con esta configuración..."

# Editar archivos
"Modifica el archivo src/index.js para agregar logging"
"Actualiza el README con las nuevas instrucciones"

# Mover/Renombrar
"Mueve todos los archivos .md a la carpeta docs"
"Renombra config.old a config.backup"

# Eliminar (con precaución)
"Elimina los archivos temporales en /tmp"
"Borra el directorio node_modules"
```

### Comandos Compuestos

Claude puede ejecutar secuencias de comandos:

```bash
"Instala las dependencias, ejecuta el build y luego corre los tests"

# Claude ejecutará:
# npm install && npm run build && npm test

"Crea una rama nueva llamada feature/auth, haz commit y push"

# Claude ejecutará:
# git checkout -b feature/auth
# git add .
# git commit -m "..."
# git push -u origin feature/auth
```

---

## Integración con Neovim

Este proyecto ya tiene Claude Code integrado en Neovim a través del plugin `claudecode.nvim`.

### Shortcuts de Neovim para Claude Code

Los siguientes keybindings están configurados en `GentlemanNvim/nvim/lua/plugins/claude-code.lua`:

| Keybinding | Modo | Acción | Descripción |
|------------|------|--------|-------------|
| `<leader>ac` | Normal | Toggle Claude | Abre/cierra el panel de Claude |
| `<leader>af` | Normal | Focus Claude | Da foco al panel de Claude |
| `<leader>ar` | Normal | Resume | Reanuda la conversación anterior |
| `<leader>aC` | Normal | Continue | Continúa la conversación actual |
| `<leader>am` | Normal | Select Model | Selecciona el modelo de IA |
| `<leader>ab` | Normal | Add Buffer | Añade buffer actual al contexto |
| `<leader>as` | Visual | Send to Claude | Envía selección a Claude |
| `<leader>aa` | Normal | Accept Diff | Acepta los cambios sugeridos |
| `<leader>ad` | Normal | Deny Diff | Rechaza los cambios sugeridos |
| `<leader>at` | Normal | Continue Recent | Continúa conversación reciente |
| `<leader>av` | Normal | Verbose Logging | Activa logging detallado |

### Workflow Típico en Neovim

1. **Abre el archivo que quieres modificar**
2. **Presiona `<leader>ac`** para abrir Claude
3. **Describe tu tarea** o selecciona código con `V` y presiona `<leader>as`
4. **Claude sugerirá cambios**, presiona `<leader>aa` para aceptar o `<leader>ad` para rechazar
5. **Continúa iterando** con `<leader>aC`

### Configuración Actual

```lua
-- Ubicación: GentlemanNvim/nvim/lua/plugins/claude-code.lua
return {
  "coder/claudecode.nvim",
  enabled = true,  -- Claude Code está habilitado por defecto
  -- ... keybindings configurados arriba
}
```

---

## Creación de Shortcuts Personalizados

### Comandos Slash Personalizados

Los comandos slash personalizados son archivos Markdown que contienen prompts predefinidos.

#### Ubicaciones

1. **Comandos de Proyecto** (específicos del repositorio):
   - Ubicación: `.claude/commands/`
   - Visibilidad: Solo en este proyecto
   - Ejemplo: `.claude/commands/deploy.md`

2. **Comandos Personales** (globales):
   - Ubicación: `~/.claude/commands/`
   - Visibilidad: En todos los proyectos
   - Ejemplo: `~/.claude/commands/review-code.md`

#### Crear un Comando Simple

```bash
# Paso 1: Crear la carpeta de comandos
mkdir -p .claude/commands

# Paso 2: Crear el archivo del comando
nano .claude/commands/review.md
```

Contenido de `review.md`:

```markdown
Por favor, revisa el código en este proyecto y proporciona:

1. Análisis de calidad del código
2. Bugs potenciales
3. Mejoras de rendimiento
4. Mejores prácticas no seguidas
5. Vulnerabilidades de seguridad

Sé específico y proporciona ejemplos de código corregido.
```

#### Comandos con Argumentos

Usa `$ARGUMENTS` para aceptar parámetros:

```markdown
# Archivo: .claude/commands/explain.md

Explica en detalle el siguiente concepto o código: $ARGUMENTS

Incluye:
- Descripción general
- Casos de uso
- Ejemplos de código
- Mejores prácticas
```

Uso: `/explain recursion`

#### Comandos con Namespaces

Organiza comandos en subdirectorios:

```bash
.claude/commands/
├── git/
│   ├── review-pr.md
│   └── commit-msg.md
└── docker/
    ├── build.md
    └── deploy.md
```

Uso: `/git:review-pr` o `/docker:build`

### Ejemplos Prácticos de Comandos

#### 1. Comando de Revisión de Código

```markdown
# .claude/commands/code-review.md

Realiza una revisión exhaustiva del código siguiendo estos criterios:

## Aspectos a Revisar:
1. **Legibilidad**: ¿El código es fácil de entender?
2. **Mantenibilidad**: ¿Es fácil de modificar?
3. **Performance**: ¿Hay optimizaciones posibles?
4. **Seguridad**: ¿Hay vulnerabilidades?
5. **Testing**: ¿Tiene cobertura adecuada?
6. **Documentación**: ¿Está bien documentado?

## Formato de Respuesta:
- Lista problemas encontrados
- Proporciona soluciones específicas
- Prioriza por severidad (crítico/alto/medio/bajo)
```

#### 2. Comando de Generación de Tests

```markdown
# .claude/commands/generate-tests.md

Genera tests unitarios completos para: $ARGUMENTS

## Requisitos:
- Framework de testing apropiado al lenguaje
- Casos de prueba positivos y negativos
- Casos edge
- Mocks cuando sea necesario
- Coverage mínimo del 80%

## Formato:
- Código de tests completo y ejecutable
- Comentarios explicativos
- Instrucciones para ejecutar los tests
```

#### 3. Comando de Documentación

```markdown
# .claude/commands/document.md

Genera documentación completa para: $ARGUMENTS

## Incluir:
- Descripción general
- Parámetros y tipos
- Valores de retorno
- Ejemplos de uso
- Posibles errores/excepciones
- Notas adicionales

## Formato:
- JSDoc / TypeDoc para JavaScript/TypeScript
- Docstrings para Python
- XML comments para C#
- Javadoc para Java
```

#### 4. Comando de Refactoring

```markdown
# .claude/commands/refactor.md

Refactoriza el siguiente código aplicando: $ARGUMENTS

## Principios a Aplicar:
- SOLID principles
- DRY (Don't Repeat Yourself)
- Clean Code
- Design Patterns apropiados

## Entregables:
1. Código refactorizado
2. Explicación de cambios
3. Antes vs Después
4. Beneficios obtenidos
```

#### 5. Comando de Debug

```markdown
# .claude/commands/debug.md

Ayuda a debuggear el siguiente problema: $ARGUMENTS

## Proceso:
1. Analiza el código relevante
2. Identifica posibles causas
3. Proporciona soluciones paso a paso
4. Sugiere logging adicional
5. Recomienda prevención futura

## Formato:
- Diagnóstico claro
- Soluciones priorizadas
- Código de ejemplo
```

### Hooks Personalizados

Los hooks se ejecutan en respuesta a eventos específicos.

#### Crear un Hook

```bash
# Crear directorio de hooks
mkdir -p .claude/hooks

# Crear hook pre-commit
nano .claude/hooks/pre-commit.sh
```

Ejemplo de hook:

```bash
#!/bin/bash
# .claude/hooks/pre-commit.sh

# Ejecuta linter antes de cada commit
echo "Ejecutando linter..."
npm run lint

# Ejecuta tests
echo "Ejecutando tests..."
npm test

# Si algo falla, el commit se bloquea
if [ $? -ne 0 ]; then
    echo "Error: Tests o linter fallaron"
    exit 1
fi
```

### Configuración con config.json

```bash
# Editar configuración personal
nano ~/.claude/config.json
```

Ejemplo de configuración:

```json
{
  "model": "claude-sonnet-4",
  "temperature": 0.7,
  "max_tokens": 4096,
  "hooks": {
    "pre_commit": ".claude/hooks/pre-commit.sh",
    "post_command": ".claude/hooks/log.sh"
  },
  "default_commands": [
    "review",
    "test",
    "deploy"
  ]
}
```

---

## Configuración Avanzada

### MCP Servers

MCP (Model Context Protocol) permite extender Claude Code con servidores externos.

#### Configurar un MCP Server

```bash
# Editar configuración MCP
nano ~/.claude/mcp.json
```

Ejemplo de configuración:

```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_TOKEN": "tu_token_aquí"
      }
    },
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem"]
    }
  }
}
```

### CLAUDE.md - Memoria del Proyecto

El archivo `CLAUDE.md` contiene información persistente que Claude siempre recuerda.

```bash
# Crear memoria del proyecto
nano .claude/CLAUDE.md
```

Ejemplo:

```markdown
# Proyecto: Gentleman.Dots

## Descripción
Configuración de dotfiles personalizados para entorno de desarrollo.

## Stack Técnico
- Shell: Fish, Zsh, Nushell
- Editor: Neovim con LazyVim
- Terminal: Alacritty, WezTerm, Kitty
- Multiplexer: Tmux, Zellij

## Convenciones
- Commits en español
- Prefijos: feat, fix, docs, style, refactor, test, chore
- Branches: feature/, bugfix/, hotfix/

## Estructura
- GentlemanNvim/: Configuración de Neovim
- GentlemanFish/: Configuración de Fish shell
- GentlemanZsh/: Configuración de Zsh
- GentlemanTmux/: Configuración de Tmux

## Comandos Comunes
- `./install-linux-mac.sh`: Instalación automática
- Neovim keybindings: leader = space

## Notas Importantes
- Claude Code está integrado en Neovim
- No modificar archivos en .git directamente
- Mantener compatibilidad cross-platform
```

### Permisos y Seguridad

```bash
# Ver permisos actuales
/permissions

# Configurar en config.json
{
  "permissions": {
    "file_operations": true,
    "shell_commands": true,
    "network_access": false,
    "write_to_system": false
  }
}
```

---

## Tips y Mejores Prácticas

### Optimización de Contexto

1. **Usa `/compact` regularmente** cuando la conversación sea muy larga
   ```
   /compact mantén el contexto sobre el sistema de autenticación
   ```

2. **Usa `/clear` para empezar de cero** cuando cambies de tema completamente
   ```
   /clear
   ```

3. **Referencia archivos específicos** en lugar de pedir a Claude que los busque
   ```
   Revisa el archivo ./src/auth.ts y optimízalo
   ```

### Eficiencia en Comandos

1. **Combina operaciones** en una sola pregunta
   ```
   Instala las dependencias, ejecuta el build, corre los tests y muéstrame los resultados
   ```

2. **Sé específico** sobre el resultado esperado
   ```
   Crea un componente React llamado UserCard que muestre nombre, email y avatar
   con props tipadas en TypeScript
   ```

3. **Usa comandos slash personalizados** para tareas repetitivas
   ```
   /deploy production
   /test:unit auth
   ```

### Seguridad

1. **Nunca hagas commit de secretos** a `.claude/`
2. **Revisa los comandos** antes de que Claude los ejecute
3. **Usa `.gitignore`** para excluir archivos sensibles:
   ```gitignore
   .claude/secrets/
   .claude/*.key
   .claude/mcp.json  # si contiene tokens
   ```

### Workflows Eficientes

#### Workflow de Desarrollo

```bash
# 1. Inicia sesión
claude

# 2. Revisa el estado
"Muéstrame el estado de git y los cambios pendientes"

# 3. Implementa la feature
"Agrega autenticación JWT al endpoint /api/login"

# 4. Revisa el código
/review

# 5. Genera tests
/generate-tests src/auth.ts

# 6. Ejecuta tests
"Corre los tests y muéstrame los resultados"

# 7. Commit
"Haz commit con un mensaje descriptivo"
```

#### Workflow de Debugging

```bash
# 1. Describe el problema
"Tengo un error en la función calculateTotal, el resultado es incorrecto"

# 2. Claude analiza
Claude leerá el código y ejecutará tests

# 3. Identifica la causa
Claude te mostrará dónde está el bug

# 4. Aplica la solución
"Aplica el fix sugerido"

# 5. Verifica
"Ejecuta los tests de nuevo"
```

### Integración con Git

```bash
# Claude puede ayudarte con Git automáticamente:

"¿Cuál es el estado de git?"
# -> git status

"Muéstrame los últimos 5 commits"
# -> git log -5 --oneline

"Crea una branch llamada feature/auth"
# -> git checkout -b feature/auth

"Haz commit de todos los cambios con mensaje 'Add authentication'"
# -> git add . && git commit -m "Add authentication"

"Haz push a origin"
# -> git push -u origin feature/auth

"Muéstrame las diferencias con main"
# -> git diff main
```

### Shortcuts de Productividad

#### Atajos de Terminal Útiles

```bash
# Alias útiles (agregar a tu shell config)
alias c="claude"
alias ci="claude /init"
alias cr="claude /review"
alias cc="claude /clear"
alias cd="claude /doctor"

# Con argumentos
alias cq='claude "$@"'  # claude quick

# Uso:
cq "lista archivos en src/"
```

#### Comandos de Proyecto Específicos

Para este proyecto (Gentleman.Dots), comandos útiles:

```bash
# .claude/commands/update-nvim.md
"Actualiza los plugins de Neovim ejecutando Lazy sync"

# .claude/commands/check-config.md
"Verifica que todas las configuraciones estén correctamente instaladas"

# .claude/commands/backup.md
"Crea un backup de todas las configuraciones en ~/dotfiles-backup"
```

### Troubleshooting Común

#### Claude no responde

```bash
# 1. Verifica la instalación
/doctor

# 2. Revisa el status
/status

# 3. Reinicia la sesión
/exit
claude
```

#### Contexto muy grande

```bash
# Compacta la conversación
/compact enfócate en el sistema de auth

# O limpia completamente
/clear
```

#### Comandos no encontrados

```bash
# Verifica que el comando exista
/help

# Revisa la ubicación
ls .claude/commands/
ls ~/.claude/commands/

# Verifica los permisos
chmod +x .claude/commands/*.md
```

---

## Recursos Adicionales

### Documentación Oficial

- [Claude Code Docs](https://docs.claude.com/en/docs/claude-code)
- [Interactive Mode](https://docs.claude.com/en/docs/claude-code/interactive-mode)
- [Slash Commands](https://docs.claude.com/en/docs/claude-code/slash-commands)
- [CLI Reference](https://docs.claude.com/en/docs/claude-code/cli-reference)

### Repositorios Útiles

- [awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) - Lista curada de comandos y workflows
- [claude-code-cheat-sheet](https://github.com/Njengah/claude-code-cheat-sheet) - Cheatsheet completo
- [commands](https://github.com/wshobson/commands) - Comandos slash listos para producción

### Comunidad

- GitHub Issues: Reporta bugs y solicita features
- Discord/Foros: Comparte workflows y aprende de otros usuarios

---

## Resumen de Comandos Rápidos

```bash
# Iniciar Claude Code
claude

# Ayuda
?                    # Shortcuts de teclado
/help               # Lista de comandos slash

# Sesión
/clear              # Limpia historial
/compact            # Compacta conversación
/exit               # Sale de Claude

# Configuración
/config             # Abre configuración
/doctor             # Verifica instalación
/status             # Estado del sistema
/cost               # Uso de tokens

# Proyecto
/init               # Inicializa proyecto
/memory             # Edita CLAUDE.md
/review             # Revisa código

# Navegación
Ctrl+C              # Cancela operación
Ctrl+D              # Sale
Esc                 # Detiene a Claude
Tab                 # Autocompletar
↑/↓                 # Historial
```

---

## Configuración Específica de Gentleman.Dots

### Neovim Shortcuts (ya configurados)

```
<leader>ac - Abre Claude Code
<leader>af - Foco en Claude
<leader>as - Envía selección a Claude
<leader>aa - Acepta cambios
<leader>ad - Rechaza cambios
```

### Estructura del Proyecto

Este proyecto ya tiene la siguiente estructura que puedes aprovechar:

```
Gentleman.Dots/
├── CLAUDE_CODE_GUIDE.md          # Este documento
├── GentlemanNvim/nvim/
│   └── lua/plugins/
│       └── claude-code.lua       # Configuración de Claude Code
└── .claude/                      # (crear si no existe)
    ├── commands/                 # Tus comandos personalizados
    └── CLAUDE.md                 # Memoria del proyecto
```

### Comandos Recomendados para Este Proyecto

1. **Verificar configuraciones**:
   ```bash
   "Verifica que todos los dotfiles estén correctamente configurados"
   ```

2. **Actualizar plugins**:
   ```bash
   "Actualiza todos los plugins de Neovim"
   ```

3. **Sincronizar dotfiles**:
   ```bash
   "Sincroniza las configuraciones con los archivos del sistema"
   ```

---

**Última actualización**: 2025-11-06
**Versión del proyecto**: Gentleman.Dots
**Claude Code**: Compatible con todas las versiones recientes
