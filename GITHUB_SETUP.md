# GitHub MCP — Setup paso a paso

El servidor MCP `github` ya está instalado y configurado en Kimi CLI y OpenClaw. Solo falta crear la cuenta dedicada de GitHub y generar el token.

## Lo que ya está listo (hecho por Kimi)

- ✅ Paquete `@modelcontextprotocol/server-github` instalado globalmente
- ✅ Config de Kimi CLI (`~/.kimi/mcp.json`) con placeholder
- ✅ Config de OpenClaw (`~/.openclaw/openclaw.json`) con placeholder
- ✅ Documentación en `MCP.md` actualizada

## Lo que tenés que hacer vos

### 1. Crear la cuenta dedicada de GitHub

1. Andá a [github.com/signup](https://github.com/signup).
2. Usá el **email de DataMaq** (no el personal).
3. Elegí un username tipo `datamaq-automation` o `openclaw-bot`.
4. Completá el CAPTCHA y verificá el email.

### 2. Crear el token de acceso

1. En la cuenta nueva, andá a **Settings → Developer settings → Personal access tokens → Fine-grained tokens**.
2. Clic en **Generate new token**.
3. Configuración:
   - **Token name**: `openclaw-mcp`
   - **Expiration**: 90 días (o el máximo que permita; podés regenerarlo después).
   - **Repository access**: **Only select repositories**
   - Seleccioná el/los repos de DataMaq y/o el repo de KimiClaw.
   - **Permissions**:
     - Contents: **Read and write**
     - Issues: **Read and write**
     - Pull requests: **Read and write**
     - Metadata: **Read** (se selecciona automáticamente)
4. Clic en **Generate token** y **copiá el token** (aparece solo una vez).

### 3. Reemplazar el placeholder en la VM

El token placeholder actual es `ghp_REEMPLAZAR_CON_TOKEN_DEDICADO`. Tenés que reemplazarlo en dos archivos:

```bash
# Editar ~/.kimi/mcp.json
nano ~/.kimi/mcp.json

# Editar ~/.openclaw/openclaw.json
nano ~/.openclaw/openclaw.json
```

Reemplazá `ghp_REEMPLAZAR_CON_TOKEN_DEDICADO` por el token real en ambos archivos.

### 4. Reiniciar servicios

```bash
systemctl --user restart openclaw-gateway.service
```

Después, verificá:

```bash
kimi mcp list
openclaw mcp list
```

Ambos deberían mostrar `filesystem` y `github`.

## Seguridad

- El token solo existe en estos dos archivos locales de la VM.
- Nunca lo commitees al repo (están en `~/.kimi/` y `~/.openclaw/`, fuera del workspace).
- Si sospechás que se filtró: revocalo desde GitHub y generá uno nuevo.
- La cuenta dedicada aísla 100% tu GitHub personal de cualquier acción del agente.

## Herramientas que expondrá el MCP GitHub

- `create_issue`, `update_issue`, `list_issues`
- `create_pull_request`, `update_pull_request`, `list_pull_requests`
- `get_file_contents`, `create_or_update_file`
- `list_commits`, `get_commit`
- `search_code`, `search_issues`, `search_repositories`
- `create_branch`, `list_branches`
- `fork_repository`, `create_repository`

Todo limitado a los repos que le diste acceso.
