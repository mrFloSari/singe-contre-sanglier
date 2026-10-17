# Prompt — Nouvelle arme

Ajoute une arme data-driven sans hardcoder les dégâts dans le gameplay.

## Contexte
Projet Singe contre Sanglier (UE5). Lire `Docs/GDD.md` et `Docs/COMBOS.md`.

## Entrée
- Nom :
- Type trajectoire : Direct | Ballistic | Lob | Heal | Utility
- Dégâts base / munitions / coût éventuel
- Template QTE : Sequence | Mash | Hold | …
- Faction hint (singe / sanglier / neutre)

## Tâches
1. Créer/mettre à jour `DA_Weapon_<Name>` (ou DataTable row)
2. Brancher le template QTE existant (ne pas en inventer un nouveau sans demander)
3. Ajouter l’entrée inventaire kit si demandé
4. Logs `LogSSCombat` sur tir / hit
5. Ne pas modifier le design des combos sans validation

## Done when
PIE : équiper → viser → QTE → dégâts cohérents avec le DA.
