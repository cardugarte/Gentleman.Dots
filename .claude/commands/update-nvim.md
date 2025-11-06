# Actualizar Plugins de Neovim

Actualiza todos los plugins de Neovim usando el gestor de plugins LazyVim.

## Pasos a realizar:

1. Navega al directorio de Neovim
2. Verifica el estado actual de los plugins
3. Ejecuta el comando de actualización de Lazy
4. Muestra un resumen de los plugins actualizados
5. Verifica si hay errores durante la actualización

## Comandos a ejecutar:

```bash
# Actualizar plugins con Lazy
nvim --headless "+Lazy! sync" +qa

# O si es necesario, muestra la interfaz interactiva
nvim +Lazy
```

## Respuesta esperada:

- Lista de plugins actualizados
- Nuevas versiones instaladas
- Errores encontrados (si los hay)
- Recomendaciones post-actualización
