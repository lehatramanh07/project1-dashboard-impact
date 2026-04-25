# 🏥 Analyse de Performance : Équipements d'Imagerie Médicale

![Visualisation](https://img.shields.io/badge/Visualisation-Power_BI-yellow) ![Calcul](https://img.shields.io/badge/Calcul-DAX_Avancé-blue) ![Secteur](https://img.shields.io/badge/Secteur-Imagerie_Médicale-red) ![Expertise](https://img.shields.io/badge/Expertise-Analyse_de_Risque-green)

## 📌 Présentation du Projet

Ce projet consiste en une analyse trimestrielle des performances opérationnelles et économiques du parc d'imagerie médicale d'un centre hospitalier. L'objectif est de transformer des données de maintenance et d'utilisation brutes en levier de décision stratégique.

**Résultat clé :** Identification d'une vulnérabilité systémique majeure sur l'unité **IRM-01**, permettant une réduction potentielle de **85% des erreurs critiques** sur les protocoles AVC.

---

## 🚀 Objectifs Métier

* **Optimisation budgétaire :** Réduire de 20% les coûts de maintenance superflus.
* **Fiabilité clinique :** Identifier les équipements à haut risque (taux d'erreur > 15%).
* **Aide à la décision :** Passer d'une gestion par les coûts à une gestion par la **valeur clinique**.

---

## 🛠️ Stack Technique

* **Outils :** Microsoft Power BI — Power Query (nettoyage, transformation des données) et Data Modeling.
* **Langage :** DAX (Data Analysis Expressions) pour la création de KPIs dynamiques.
* **Données :** 940 enregistrements fictifs couvrant 3 équipements majeurs sur 3 mois.

---

## 📊 Analyses Clés & Insights

### 1. Performance Économique (ROI vs Risque)

* **Radiographie (XRAY-01) :** Le "Cheval de Trait" — 37% des patients pour un coût quasi nul.
* **Scanner (CT-01) :** Coûts élevés mais justifiés par des protocoles critiques et urgents (Stroke Protocol, Brain Trauma, Thorax PE).
* 👉 **Conclusion :** Le coût seul est un mauvais indicateur ; il faut mesurer la criticité des actes médicaux réalisés.

### 2. Risque Clinique : Le Maillon Faible

L'analyse croisée a révélé que l'**IRM-01** présente un taux d'erreur global de **33%**.

* **Alerte Rouge :** 100% des erreurs sur le "Stroke Protocol" (AVC) proviennent de cette seule machine.
* **Plan d'action en 3 étapes :**
  * **J+1 :** Suspension immédiate des protocoles AVC sur l'IRM-01.
  * **J+15 :** Audit technique complet par les ingénieurs du fabricant (coût estimé : 7 000 €).
  * **J+30 :** Workshop de remise à niveau pour les techniciens opérant sur l'IRM-01.

---

## 📂 Structure du Repository

* `data/` : Jeu de données (CSV).
* `Script/` : Contient les mesures DAX et le rapport détaillé.
* `README.md` : Présentation synthétique (ce fichier).

---

## 💡 Apprentissages

Ce projet démontre l'importance du **Data Storytelling** en milieu hospitalier : ne pas se contenter de chiffres financiers, mais remonter jusqu'à la sécurité du patient.

---

*Réalisé par **Lê, H. T. A** — Juillet 2025*
