# Moteur-Simulation-ALM
Moteur de projection ALM en Python et SQL

Projet d'analyse ALM basé sur une banque systémique européenne. L'objectif est de tester la robustesse des indicateurs réglementaires (**LCR**) et de rentabilité (**MNI**) via un moteur de calcul Python.

> **Données sources :** Inspirées du Document d'Enregistrement Universel 2025 de la **Société Générale**.

##  Architecture du Projet
* **Base de données :** SQL (Structure du bilan, taux, maturités, lois d'écoulement).
* **Moteur de calcul :** Python (Pandas) pour la projection des flux à 120 mois.
* **Visualisation :** Matplotlib (Génération automatique des graphiques de gap).

---

##  Analyse de la Liquidité (LCR)
Analyse en **Run-off** (extinction de bilan) pour identifier les points de rupture sans biais de modélisation.

| Scénario | Hypothèse | Résultat & Observation |
| :--- | :--- | :--- |
| **Référence** | 20% de fuite (part volatile) | Solvabilité CT maintenue ; risque de refinancement identifié au mois 72. |
| **Stress-Test** | 40% de fuite (Bank Run) | **Rupture :** LCR à **42,19%** (seuil reg. 100%). Position nette à -93 Md€. |

Le modèle démontre une incapacité de couverture par les HQLA (90 Md€ vs 192 Md€ de sorties stressées), rendant une intervention externe indispensable en cas de crise systémique.

---

##  Risque de Taux (MNI)
Mesure de l'impact d'un choc de taux sur la **Marge Nette d'Intérêt** (MNI de base : 27,04 Md€) sans stratégie de couverture (hors-bilan).

### Choc de taux : +200 bps
* **Scénario "Standard" :** Profit supplémentaire de **+8,8 Md€**.
* **Scénario "Beta 60%" :** Profit réduit à **+3 Md€** si 60% de la hausse est reversée aux clients.

**Conclusion de l'analyse :**
Le bilan est structurellement **"Asset-Sensitive"**. La banque bénéficie mécaniquement d'une hausse des taux, ses actifs se réévaluant plus vite que ses passifs.

>  Point d'attention : Cette structure expose l'établissement à une contraction majeure de la marge en cas de baisse des taux, soulignant l'importance de mettre en place des couvertures (Swaps) pour stabiliser le P&L.
