# Singe contre Sanglier

Ébauche de jeu d’action-tactique **3D** : équipes de singes et sangliers, phases d’équipe **simultanées**, déplacement **TPS**, vue **Map** globale, armes façon Worms, résolution par **QTE** individuels ou **couplés** (2v2 → 4v4, humains et/ou bots).

> Statut : **design / GDD** — pas encore de projet Unreal jouable dans ce dépôt.

## Pitch

Map pour décider, TPS pour ressentir, QTE pour trancher. Les alliés jouent **en même temps** pendant la phase d’équipe et peuvent synchroniser des **actions couplées**.

## Contenu du dépôt

| Chemin | Contenu |
|---|---|
| [Docs/GDD.md](Docs/GDD.md) | Game design document (one-pager + systèmes) |
| [Docs/MAPS.md](Docs/MAPS.md) | 5 maps 3D + layouts MVP |
| [Docs/COMBOS.md](Docs/COMBOS.md) | 8 actions couplées + wireflow 3v3 |
| [Docs/UI_KITS.md](Docs/UI_KITS.md) | UI sync + kits de départ 2v2 |
| [Docs/TECH.md](Docs/TECH.md) | Environnement UE5, Ollama, Cursor, pipeline |
| [Docs/prompts/](Docs/prompts/) | Prompts d’itération pour l’IA |

## Modes prévus

- **2v2** (cœur) · **3v3** · **4v4** casual
- Slots **Humain / Bot** librement mixables
- Salon privé + matchmaking (ranked d’abord en 2v2)

## Stack technique cible

- **Unreal Engine 5.5+** (idéalement 5.8 pour MCP)
- Windows, GPU **12 Go** VRAM minimum
- Ollama : `qwen2.5-coder:14b` (context 16k)
- Cursor (Agent cloud) + Continue/aider en local

## Prochaine étape produit

MVP : Cirque des Os · 2v2 H/B · phase simultanée · 2 armes + soin · Tir croisé + Mains vertes · 2 persos.

Voir [Docs/TECH.md](Docs/TECH.md) § checklist Jour 1.
