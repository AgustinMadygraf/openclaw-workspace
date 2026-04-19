# TOOLS.md

## SSH / Infra

- GCE instance principal: `openclaw-server`
- Zona GCE: `southamerica-west1-b`
- Comando preferido para acceso SSH:
  - `gcloud compute ssh openclaw-server --zone=southamerica-west1-b`

## Workspace del agente principal

- Workspace agente `main`: `~/openclaw-workspace/agents/main/`
- Archivos base del agente viven en la raíz de ese directorio
- Carpeta de avatar: `~/openclaw-workspace/agents/main/avatars/`

## Identidad visual

- Avatar principal: `avatars/tenazas.svg`
- Avatar alternativo: `avatars/tenazas.jpg`
- Nombre público del bot: `Tenazas`
- Referencia visual: Tenazas, la langosta de Homero

## Rutas útiles

- `AGENTS.md`
- `SOUL.md`
- `IDENTITY.md`
- `USER.md`
- `TOOLS.md`
- `avatars/tenazas.svg`
- `avatars/tenazas.jpg`

## Convenciones locales

- Preferir rutas relativas al workspace cuando sea posible
- Mantener los assets del agente dentro del workspace
- No guardar secretos ni credenciales en este repositorio
- Usar este archivo para notas del entorno, no para reglas operativas

## Git

- Repo del agente inicializado dentro de:
  - `~/openclaw-workspace/agents/main/`
- Antes de commit:
  - revisar archivos nuevos con `git status`
  - evitar duplicados por mayúsculas/minúsculas
