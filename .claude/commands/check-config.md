# Verificar Configuración

Por favor, verifica que todas las configuraciones de Gentleman.Dots estén correctamente instaladas y funcionando.

## Aspectos a revisar:

1. **Neovim**:
   - Verifica que Neovim esté instalado
   - Comprueba que los plugins estén correctamente instalados
   - Verifica la configuración de Claude Code en `GentlemanNvim/nvim/lua/plugins/claude-code.lua`

2. **Shells**:
   - Fish: Comprueba `GentlemanFish/fish/config.fish`
   - Zsh: Comprueba `GentlemanZsh/.zshrc`
   - Nushell: Comprueba `GentlemanNushell/config.nu`

3. **Terminal Emulators**:
   - Alacritty: Verifica `alacritty.toml`
   - WezTerm: Verifica `.wezterm.lua`
   - Kitty: Verifica `GentlemanKitty/kitty.conf`

4. **Multiplexers**:
   - Tmux: Verifica `GentlemanTmux/tmux.conf`
   - Zellij: Verifica `GentlemanZellij/zellij/`

5. **Dependencias**:
   - Verifica que todas las herramientas necesarias estén instaladas (ripgrep, fzf, etc.)

## Formato de respuesta:

- ✅ Elementos correctamente configurados
- ⚠️  Elementos con advertencias
- ❌ Elementos faltantes o incorrectos
- 📝 Recomendaciones de mejora
