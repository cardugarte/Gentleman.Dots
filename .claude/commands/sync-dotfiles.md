# Sincronizar Dotfiles

Sincroniza las configuraciones de Gentleman.Dots con los archivos del sistema.

## Proceso:

1. **Backup actual**: Crea un backup de las configuraciones actuales del sistema
2. **Verificar symlinks**: Comprueba que todos los enlaces simbólicos estén correctos
3. **Sincronizar cambios**: Copia o actualiza los archivos necesarios
4. **Validar**: Verifica que todo funcione correctamente

## Directorios a sincronizar:

- `~/.config/nvim/` ← `GentlemanNvim/nvim/`
- `~/.config/fish/` ← `GentlemanFish/fish/`
- `~/.zshrc` ← `GentlemanZsh/.zshrc`
- `~/.config/nushell/` ← `GentlemanNushell/`
- `~/.tmux.conf` ← `GentlemanTmux/tmux.conf`
- `~/.config/alacritty/` ← `alacritty.toml`
- `~/.wezterm.lua` ← `.wezterm.lua`
- `~/.config/kitty/` ← `GentlemanKitty/`

## Formato de respuesta:

- Archivos sincronizados correctamente
- Errores encontrados
- Archivos que requieren atención manual
- Siguiente paso recomendado
