# Prompt — Session MCP blockout Cirque des Os

## Prérequis
- Commit propre avant toute écriture MCP
- Map `L_Cirque_Blockout` ouverte
- Une seule action par message agent

## Tâches atomiques (une par une)
1. Vérifier connexion MCP (read-only)
2. Placer 4 PlayerStart : Duo Ouest / Duo Est (tags TeamA/TeamB)
3. Volumes : MapCameraBounds, KillZ
4. Markers POI : PontVertèbre, Brasero, Tambour (empty actors nommés)
5. 4 cubes cover G1 ouest + 4 est

## Après chaque tâche
Output Log · diff Git · PIE spawn check · commit si OK

## Interdit
« Finish the level » · supprimer des actors non listés · exposer MCP hors localhost
