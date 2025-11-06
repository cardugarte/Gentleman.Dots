# Gentleman.Dots - Memoria del Proyecto

## Descripción General

**Gentleman.Dots** es una colección completa de configuraciones (dotfiles) para un entorno de desarrollo moderno y productivo. El proyecto incluye configuraciones para editores, shells, terminales y multiplexores, con énfasis en la productividad y la personalización.

## Stack Técnico

### Editor Principal
- **Neovim** con LazyVim
- LSP configurado para múltiples lenguajes
- Autocompletado con nvim-cmp
- Integración con AI assistants (Claude Code, Gemini)

### Shells
- **Fish** - Shell interactivo amigable
- **Zsh** - Con Oh My Zsh y Powerlevel10k
- **Nushell** - Shell moderno con tipos de datos estructurados

### Terminal Emulators
- **Alacritty** - GPU-accelerated
- **WezTerm** - GPU-accelerated con Lua config
- **Kitty** - GPU-accelerated
- **Ghostty** - Nueva generación

### Multiplexores
- **Tmux** - Tradicional y robusto
- **Zellij** - Moderno en Rust

### Herramientas Integradas
- **Starship** - Prompt cross-shell
- **FZF** - Fuzzy finder
- **Ripgrep** - Búsqueda rápida
- **Atuin** - Historial inteligente
- **Carapace** - Autocompletado avanzado
- **Obsidian** - Gestión de notas (integrado en Neovim)

## Estructura del Proyecto

```
Gentleman.Dots/
├── GentlemanNvim/          # Configuración de Neovim
│   └── nvim/
│       ├── init.lua        # Punto de entrada
│       └── lua/
│           ├── config/     # Configuraciones base
│           └── plugins/    # 35+ plugins configurados
│
├── GentlemanFish/          # Configuración Fish
├── GentlemanZsh/           # Configuración Zsh
├── GentlemanNushell/       # Configuración Nushell
├── GentlemanTmux/          # Configuración Tmux
├── GentlemanZellij/        # Configuración Zellij
├── GentlemanKitty/         # Configuración Kitty
├── GentlemanGhostty/       # Configuración Ghostty
│
├── alacritty.toml          # Configuración Alacritty
├── .wezterm.lua            # Configuración WezTerm
├── starship.toml           # Configuración Starship
│
├── install-linux-mac.sh    # Script de instalación automática
├── README.md               # Documentación principal
├── CLAUDE_CODE_GUIDE.md    # Guía de Claude Code
│
└── .claude/                # Configuración de Claude Code
    ├── commands/           # Comandos slash personalizados
    └── CLAUDE.md          # Este archivo
```

## Convenciones del Proyecto

### Git Commits
- **Idioma**: Español (commits en español)
- **Formato**: Conventional Commits
- **Prefijos**:
  - `feat:` - Nueva funcionalidad
  - `fix:` - Corrección de bugs
  - `docs:` - Documentación
  - `style:` - Formato, no afecta funcionalidad
  - `refactor:` - Refactorización de código
  - `test:` - Añadir o modificar tests
  - `chore:` - Mantenimiento, actualizaciones

### Estructura de Branches
- `main` - Rama principal estable
- `nix-migration` - Features experimentales (macOS only)
- `feature/*` - Nuevas funcionalidades
- `bugfix/*` - Correcciones de bugs
- `hotfix/*` - Fixes urgentes para producción

### Estilo de Código
- **Lua**: 2 espacios de indentación
- **Shell scripts**: 2 espacios de indentación
- **Markdown**: Líneas máximo 120 caracteres
- **Nombres de archivos**: kebab-case para scripts, PascalCase para documentos principales

## Configuraciones Clave de Neovim

### Leader Key
- **Leader**: `<Space>`
- Ejemplo: `<leader>ac` = `Space + a + c`

### Plugins de IA Integrados
1. **Claude Code** ✅ (ENABLED por defecto)
   - Ubicación: `lua/plugins/claude-code.lua`
   - Keybindings principales: `<leader>a*`

2. **Otros disponibles** (disabled por defecto):
   - Avante.nvim
   - CopilotChat.nvim
   - CodeCompanion.nvim
   - OpenCode.nvim
   - Gemini.nvim

### Comandos Personalizados de Claude Code

Ubicados en `.claude/commands/`:
- `/check-config` - Verifica todas las configuraciones
- `/update-nvim` - Actualiza plugins de Neovim
- `/sync-dotfiles` - Sincroniza dotfiles con el sistema
- `/review-code` - Revisión exhaustiva de código
- `/explain` - Explica conceptos o código en detalle

## Plataformas Soportadas

- **macOS** ✅ (soporte completo)
- **Linux** ✅ (soporte completo)
- **Arch Linux** ✅ (con script específico)
- **WSL** ✅ (Windows Subsystem for Linux)
- **Windows** ⚠️ (requiere instalación manual + WSL)

## Instalación

### Automática (Recomendada)
```bash
curl -O https://raw.githubusercontent.com/Gentleman-Programming/Gentleman.Dots/refs/heads/main/install-linux-mac.sh
sudo chmod +x install-linux-mac.sh
bash ./install-linux-mac.sh
```

### Manual
Ver README.md para instrucciones detalladas por sistema operativo.

## Dependencias Principales

### Herramientas Esenciales
- Git
- Neovim (>= 0.9)
- Node.js (para LSP servers)
- Python3 (para algunos plugins)
- Rust (para herramientas en Rust)

### Package Managers
- **macOS**: Homebrew
- **Linux**: apt/yum/pacman según distro
- **Arch**: pacman + yay

### Fonts Requeridas
- **Iosevka Term Nerd Font** (obligatorio)

## Notas Importantes

### Para Claude Code
1. **No modificar** archivos en `.git/` directamente
2. **Mantener compatibilidad** cross-platform
3. **Documentar** cambios significativos en commits
4. **Testear** en múltiples plataformas cuando sea posible

### Archivos Sensibles
- No commitear tokens o API keys
- Usar `.gitignore` para archivos locales
- Archivos de configuración con secretos deben ir en `.claude/secrets/` (ignorado por git)

### Workflow de Desarrollo
1. Hacer cambios en los archivos de configuración
2. Testear localmente
3. Documentar si es necesario
4. Commit con mensaje descriptivo en español
5. Push a la rama correspondiente

## Comandos Comunes

### Git
```bash
git status                    # Ver estado
git add .                     # Añadir todo
git commit -m "feat: ..."    # Commit con mensaje
git push origin <branch>     # Push a rama
```

### Neovim
```bash
nvim                         # Abrir Neovim
:Lazy                        # Gestión de plugins
:Mason                       # Gestión de LSP servers
:checkhealth                 # Verificar salud de Neovim
```

### Claude Code
```bash
claude                       # Iniciar Claude Code
/help                        # Ver comandos disponibles
/check-config               # Verificar configuraciones
/update-nvim                # Actualizar plugins
```

## Recursos del Proyecto

- **Repositorio**: https://github.com/Gentleman-Programming/Gentleman.Dots
- **Branch Experimental**: https://github.com/Gentleman-Programming/Gentleman.Dots/tree/nix-migration
- **Documentación de Claude Code**: `CLAUDE_CODE_GUIDE.md`
- **README Principal**: `README.md`

## Filosofía del Proyecto

- **Productividad**: Optimizar el flujo de trabajo
- **Personalización**: Cada herramienta está cuidadosamente configurada
- **Modularidad**: Componentes independientes que trabajan juntos
- **Cross-platform**: Funciona en múltiples sistemas operativos
- **Actualizado**: Mantener al día con las últimas versiones
- **Documentado**: Todo cambio importante debe documentarse

## Contacto y Contribuciones

Este es un proyecto personal pero abierto a contribuciones. Si encuentras problemas o tienes sugerencias, puedes:
1. Abrir un issue en GitHub
2. Hacer un fork y enviar un pull request
3. Documentar el problema claramente

---

**Última actualización**: 2025-11-06
**Versión**: 1.0.0
**Mantenedor**: Gentleman Programming
