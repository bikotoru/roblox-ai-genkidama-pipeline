# Roblox AI Genkidama / Animation + VFX Pipeline

Setup completo para que un **agente de IA** (Claude Code o Cursor) cree animaciones R6 + efectos VFX complejos (ej: Genkidama de Goku) de forma casi autónoma.

El agente controla Blender + Roblox Studio a través de MCPs y skills especializados.

## ¿Qué puedes lograr?

- Animación R6 de levantar brazos estilo Goku
- Energías que llegan de todas partes
- Formación de la Genkidama (bola de energía)
- ParticleEmitters, Beams, Animation Events y scripts listos
- Todo generado e integrado por el agente con mínima intervención tuya

## Requisitos previos

- **Claude Code** (recomendado) o **Cursor**
- **Blender 4.5 LTS o superior**
- **Roblox Studio** (última versión)
- Python 3.10+
- Node.js (para algunos installs)
- `uv` (recomendado para MCPs): `curl -LsSf https://astral.sh/uv/install.sh | sh`

---

## 1. Instalar los Skills (lo más importante)

### Opción rápida con `npx skills` (Claude Code / agentes compatibles)

```bash
# Skills principales de Roblox
npx skills add TabooHarmony/roblox-brain
npx skills add dillydog580/animate-roblox-characters
npx --allow-git=all github:andrian-syh/roblox-best-practices-skill

# Si tienes el CLI de skills de Claude
# (o copia manualmente a ~/.claude/skills/)
```

### RBSmithy (el más completo para assets + VFX + best practices)

```bash
git clone https://github.com/gogolumo/rbsmithy-roblox-claude-skill.git
mkdir -p ~/.claude/skills
cp -R rbsmithy-roblox-claude-skill/skills/rbsmithy ~/.claude/skills/
```

### blender-skills (VFX, export, animación en Blender)

```bash
git clone https://github.com/arjun988/blender-skills.git
# Copia las carpetas relevantes a ~/.claude/skills/ o ~/.cursor/skills/
# Especialmente: vfx-fx, export-pipeline, animation, asset-optimization
```

### Para Cursor

Los skills se pueden poner en `.cursor/skills/` del proyecto o globalmente en `~/.cursor/skills/`.

---

## 2. Instalar Blender MCP

1. Instala el servidor:
```bash
uvx blender-mcp
# o sigue las instrucciones oficiales de https://github.com/ahujasid/blender-mcp
# o el MCP oficial de blender.org
```

2. En Blender:
   - Ve a Edit → Preferences → Add-ons
   - Instala el addon de Blender MCP
   - Actívalo y haz clic en "Connect to Claude" / Start Server

3. En Claude Code / Cursor añade el MCP server correspondiente.

---

## 3. Roblox Studio MCP

### Oficial (recomendado)
1. Abre Roblox Studio
2. Ve a **Assistant Settings** → **MCP Servers**
3. Usa **Quick Connect** para Claude Code o Cursor
4. O habilita el servidor built-in

Documentación oficial: https://create.roblox.com/docs/en-us/studio/mcp

### Alternativas community
- ZeroScript (extensión de navegador con multi-MCP)
- WEPPY, BloxBot, etc.

---

## 4. Plugins útiles de Roblox (recomendados)

- **Blender Animations (ultimate edition)** — Creator Store
- **Moon Animator 2**
- **RBX Toolbox** (addon de Blender para Roblox)

---

## 5. Prompt ejemplo para Genkidama full IA

Copia y pega esto en Claude Code / Cursor (con los skills y MCPs activos):

```
Usa RBSmithy + animate-roblox-characters + blender-skills (vfx-fx).

Crea una secuencia completa de Genkidama estilo Goku en un personaje R6:

1. Animación R6 de 5-7 segundos:
   - El personaje levanta ambos brazos hacia el cielo (pose de carga de Goku).
   - Mantén la pose de concentración.
   - Añade ligeramente el cuerpo inclinándose hacia atrás.

2. VFX en Blender:
   - Energías (pequeñas esferas / orbes brillantes) que llegan desde el entorno hacia las manos.
   - Una gran bola de energía (Genkidama) que se forma y crece encima de las manos.
   - Glow, rays y swirls.

3. Exporta todo correctamente (FBX / .rbxanim + texturas/flipbooks).

4. En Roblox Studio (usa el MCP):
   - Importa la animación y los assets.
   - Crea ParticleEmitters para las energías que llegan.
   - Crea el MeshPart/Part de la Genkidama con material Neon + emitters internos.
   - Añade Animation Events en los frames correctos.
   - Escribe un LocalScript + ServerScript seguro (server-authoritative) para reproducir la secuencia.
   - Incluye rate limiting y validación básica.

Hazlo paso a paso, muestra previews cuando puedas, y corrige errores automáticamente.
```

---

## 6. Orden recomendado de uso

1. Instala todo lo de arriba una sola vez.
2. Abre Blender + Roblox Studio.
3. Abre Claude Code / Cursor en la carpeta de tu proyecto.
4. Pega el prompt de arriba.
5. Deja que el agente itere (normalmente 2-5 rondas de feedback).
6. Prueba en Studio y pide ajustes (“haz la bola más grande”, “las partículas más lentas”, etc.).

---

## Notas importantes

- **No es 100% one-shot perfecto**. El agente hace el 85-95% del trabajo. Tú das feedback artístico.
- R6 es más limitado que R15. El skill `animate-roblox-characters` maneja ambos.
- Para video reference: puedes describir el video o extraer frames y pedir al agente que analice.
- Siempre revisa seguridad (server authority) — los skills de best practices ayudan mucho.

## Links útiles

- RBSmithy: https://github.com/gogolumo/rbsmithy-roblox-claude-skill
- animate-roblox-characters: https://github.com/dillydog580/animate-roblox-characters
- roblox-brain: https://github.com/TabooHarmony/roblox-brain
- roblox-best-practices-skill: https://github.com/andrian-syh/roblox-best-practices-skill
- Blender MCP: https://github.com/ahujasid/blender-mcp
- Roblox Studio MCP docs: https://create.roblox.com/docs/en-us/studio/mcp

---

Hecho para la comunidad. Si mejoras el setup, abre un PR.
