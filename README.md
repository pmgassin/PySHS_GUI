# PySHS – Interface graphique Tkinter

Interface utilisateur pour les programmes **HRS** et **SHS** de PySHS V3.2.x.

## Prérequis

- Python 3.8+
- `tkinter` (généralement inclus, sinon `sudo apt install python3-tk`)
- `matplotlib` (`pip install matplotlib` ou `python3-matplotlib`)
- Compilateur C : `gcc` ou `clang` (`sudo apt install build-essential`)

## Lancement

```bash
cd PySHS_GUI
python3 pyshs_gui.py
```

## Fonctionnalités

1. **Choix du module** : HRS (molécules incohérentes) ou SHS (structures corrélées)
2. **Type de calcul** :
   - `polarplot_single` – diagramme de polarisation à un angle fixe
   - `polarplot_integrate` – intégration sur une plage d’angles
   - `angle_scattering` – intensité en fonction de l’angle de diffusion
3. **Paramètres** adaptés automatiquement selon le module et le type de calcul
4. **Fichiers d’entrée** :
   - Tenseur d’hyperpolarisabilité (format texte avec labels `xxx`, `xxy`…)
   - Positions / orientations (SHS uniquement) – génération automatique d’une sphère possible
5. **Compilation automatique** des sources C (`HRS.c`, `SHS.c`)
6. **Affichage des résultats** + graphiques matplotlib intégrés
7. Sauvegarde des résultats et des figures

## Structure

```
PySHS_GUI/
├── pyshs_gui.py          ← programme principal (interface)
├── HRS.c / SHS.c         ← sources C
├── graph_*.py            ← scripts de tracé originaux (référence)
├── script_sphere*.py     ← scripts de génération de sphère
└── work/                 ← dossiers temporaires de calcul
```

## Notes

- Les programmes C sont interactifs (`scanf`). L’interface leur fournit automatiquement les réponses via stdin.
- Le fichier `out_plot` généré par les binaires C est parsé pour produire les graphiques.
- Sur Windows, les exécutables s’appellent `HRS.exe` / `SHS.exe`.
