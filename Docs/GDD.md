# GDD — Singe contre Sanglier

## One-pager

### Pitch
Jeu d’action-tactique **3D** où des équipes de singes et sangliers s’affrontent en **phases d’équipe simultanées**. Chacun bouge en **TPS**, lit le champ en **vue Map**, vise avec des armes absurdes façon Worms, puis tranche le combat dans des **QTE** — individuels ou **couplés** (duo / salve / ulti d’escouade). Humains et **bots** mixables en **2v2, 3v3, 4v4**.

### Piliers
1. Map pour décider, TPS pour ressentir, QTE pour trancher  
2. Jouer ensemble dans la même phase, pas seulement chacun son tour  
3. Armes lisibles + combos d’équipe comme signature fun  

### Boucle d’un round
Phase équipe A (timer, actions //) → Résolution lockstep → Phase équipe B → Environnement (marée, etc.) → repeat jusqu’à KO équipe adverse.

### Ressources
PV · budget move / phase · munitions · **Adrénaline d’équipe (0–100)**

### Combat
- Visée : directe / balistique / lob  
- QTE templates : séquence, rythme, mash zone, hold, trace souris, cibles, équilibre, parade, cocktail  
- Escalade si critique / grosse arme  
- Soft fail > hard fail  

### Combos MVP
Liane-Bélier · Tir croisé · Salve d’ananas · Mains vertes · Banane d’Or (ulti 100)

### Modes
Salon privé & matchmaking : slots Humain/Bot · 2v2 (cœur) · 3v3 · 4v4 casual · vs bots · ranked d’abord en 2v2  

### Maps MVP
1. **Canopée Fêlée** — verticalité lianes  
2. **Cirque des Os** — PvP symétrique  
3. **Marée des Coques** — timer d’eau  

### Fantasy / art
Cartoon violent, cel-shade, VFX comiques, UI QTE à identité forte par template, musique qui accélère avec l’intensité.

### Scope MVP produit
1 arène (Cirque) · 2v2 H/B · phase simultanée · 4 armes + 1 soin · 3 QTE · 2 combos duo · 2 persos (1 singe, 1 sanglier) · kits α/β  

### Non-goals MVP
Open world · 5v5 ranked · destruction voxel totale · vocal natif · crafting profond  

### Risques
QTE fatigants → variété + durée courte · chaos 4v4 → limiter combos/phase · netcode sync → timer lockstep simple  

### Critère de fun (playtest)
« Est-ce qu’un duo a crié après un Tir croisé ou une Liane-Bélier ? » Si non, itérer le combo avant d’ajouter du contenu.

---

## Caméras

| Phase | Caméra |
|---|---|
| Positionnement | TPS |
| Lecture tactique | Map (¾ / demi-dessus) |
| Visée | TPS épaule |
| QTE | Overlay TPS ou ciné combo |
| Résolution | Courte cinématique skipable |

Toggle Map ↔ TPS pendant sa phase d’équipe (pas pendant le QTE ranked).

---

## Factions

| | Singes | Sangliers |
|---|---|---|
| Bonus | Mobilité, arcs, pièges, soins | PV, knockback, charges |
| Malus | Moins de PV | Move cost ↑ |
| Archétypes | Voltigeur, Lanceur, Chaman, Sniper | Bélier, Artilleur, Fouisseur, Chef |

Mixte OK dans une même équipe.

---

## Architecture systèmes MVP (UE5)

| Module | Responsabilité |
|---|---|
| SSCore | Phases, timer, adrénaline, GameMode/State |
| SSCombat | Armes, visée, QTE, projectiles |
| SSTeam | Combos, invites, pings |
| SSAI | Bots (tactique + score QTE) |
| SSUI | HUD, Map, overlays QTE, lobby |

### Jalons proto
1. TPS + Map toggle blockout  
2. Phase timer 2v2  
3. Fusil + QTE séquence  
4. Grenade + QTE mash  
5. Soin + QTE hold  
6. Tir croisé  
7. Mains vertes + jauge ADR  
8. 2 bots Soldat + lobby slots  

---

## DataAssets

- `HeroData` — move, PV, faction  
- `WeaponData` — trajectoire, dégâts, munitions, template QTE  
- `ComboData` — joueurs min/max, coût ADR, rôles, effets  
- `KitData` — α Pression / β Roc  
