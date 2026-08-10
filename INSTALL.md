# Guía de instalación rápida

## Windows (PowerShell)

```powershell
# Skills
npx skills add TabooHarmony/roblox-brain
npx skills add dillydog580/animate-roblox-characters
irm https://raw.githubusercontent.com/andrian-syh/roblox-best-practices-skill/main/install.ps1 | iex

# RBSmithy
git clone https://github.com/gogolumo/rbsmithy-roblox-claude-skill.git
mkdir $env:USERPROFILE\.claude\skills -Force
Copy-Item -Recurse rbsmithy-roblox-claude-skill\skills\rbsmithy $env:USERPROFILE\.claude\skills\
```

## macOS / Linux

```bash
npx skills add TabooHarmony/roblox-brain
npx skills add dillydog580/animate-roblox-characters
curl -fsSL https://raw.githubusercontent.com/andrian-syh/roblox-best-practices-skill/main/install.sh | bash

git clone https://github.com/gogolumo/rbsmithy-roblox-claude-skill.git
mkdir -p ~/.claude/skills
cp -R rbsmithy-roblox-claude-skill/skills/rbsmithy ~/.claude/skills/
```

Luego configura Blender MCP y Roblox Studio MCP según el README principal.
