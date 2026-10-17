# Playbook technique — environnement & pipeline

Contrainte : **GPU 12 Go VRAM**, Windows, UE5.

## Stack

```
Cursor (cloud Agent + Tab)
  └─ option Ollama via tunnel HTTPS
Repo + GDD + .cursor/rules + Docs/prompts
Unreal 5.5–5.8 (MCP :8000/mcp en 5.8)
Ollama :11434 → ss-coder16k (Qwen2.5-Coder-14B, ctx 16k)
Continue / Cline / aider en local
```

## Machine

| | Mini | Recommandé |
|---|---|---|
| GPU | 12 Go | RTX 3060/4070 12G |
| RAM | 32 Go | 64 Go |
| Disque | 200 Go SSD | 1 To NVMe |

Install : VS 2022 (Game C++) · UE 5.5+ · Git LFS · Ollama · Cursor · Python 3.11+ · Blender · ngrok/cloudflared (opt.)

**VRAM :** ne pas lancer Ollama 14B + PIE lourd en même temps.

## Projet UE5

- Template **Third Person C++**
- Plugins : Enhanced Input · OSS · **Unreal MCP** (5.8) · Editor Scripting · Modeling Tools · Chaos light  
- Live Coding on · PIE Listen Server 2–4 players · startup `L_Cirque_Blockout`  
- Modules : SSCore · SSCombat · SSTeam · SSAI · SSUI  

### Dossiers Content
Maps · Characters · Weapons · UI · VFX · Audio · Data · Dev/Blockout

## Assets

Personnages (SKM/AnimBP) · armes + Niagara + DA_Weapon · maps blockout + volumes · WBP · MetaSounds · **DataAssets prioritaires pour l’IA**.

## Ollama (12 Go)

```bat
ollama pull qwen2.5-coder:14b
ollama pull qwen2.5-coder:7b
```

Modelfile → `ss-coder16k` :
```
FROM qwen2.5-coder:14b
PARAMETER num_ctx 16384
PARAMETER temperature 0.25
```

| Modèle | Usage |
|---|---|
| ss-coder16k (14B) | Défaut code |
| 7B | Hotfix pendant UE ouvert |
| ue-expert-v2 | API UE (opt.) |

Clients locaux : Continue / Cline / aider → `http://127.0.0.1:11434/v1`

## Cursor + Ollama

Cursor **ne joint pas localhost**. BYOK = tunnel HTTPS + Override OpenAI Base URL `https://…/v1`.  
Tab reste sur modèles Cursor.  
**Reco :** Agent cloud pour gros travaux · Ollama via Continue pour le quotidien.

## UE MCP (5.8)

1. Enable plugins MCP + toolsets  
2. Auto Start Server  
3. `ModelContextProtocol.GenerateClientConfig Cursor`  
4. Endpoint `http://127.0.0.1:8000/mcp` (loopback only)  

Règles : commit avant write · 1 action vérifiable · log + diff + PIE · rollback · petit surface d’outils.

## Pipeline itération (&lt; 15–20 min / bug)

1. Repro → 2. Issue template → 3. Agent/aider → 4. Live Coding → 5. PIE multi → 6. Test → 7. Commit  

Automations J1 : clang-format · Automation QTE/ADR · validate_data.py · SS.SmokeTest · LogSS*  

Prompts versionnés : voir `Docs/prompts/`.

## Checklist Jour 1

1. VS 2022 C++  
2. Projet UE Third Person C++  
3. Git + LFS  
4. Ollama ss-coder16k  
5. Continue → Ollama  
6. Cursor rules + Docs  
7. MCP read-only (5.8)  
8. L_Cirque_Blockout + 4 spawns  
9. Premier DA arme + logs  
10. validate_data + Automation vide  

## MVP terminé quand

2v2 (humain + bots) sur Cirque : phases simultanées · 2 armes + soin · 1 combo offensif · 1 combo soin · UI timer/pings/ADR · 3 playtests fun OK.
