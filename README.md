# 🏥 Analyse de Performance : Équipements d'Imagerie Médicale

![Power BI](https://img.shields.io/badge/Data_Viz-Power_BI-yellow) ![DAX](https://img.shields.io/badge/Analysis-DAX-blue) ![Healthcare](https://img.shields.io/badge/Industry-Healthcare-red)

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
* **Outils :** Microsoft Power BI (Power Query, Data Modeling).
* **Langage :** DAX (Data Analysis Expressions) pour la création de KPIs dynamiques.
* **Données :** 940 enregistrements (Fictifs) couvrant 3 équipements majeurs.

---

## 📊 Analyses Clés & Insights

### 1. Performance Économique (ROI vs Risque)
* **Radiographie (XRAY-01) :** Le "Cheval de Trait" — 37% des patients pour un coût quasi nul.
* **Scanner (CT-01) :** Coûts élevés mais justifiés par des protocoles critiques et urgents. 
* 👉 **Conclusion :** Le coût seul est un mauvais indicateur ; il faut mesurer la criticité des actes.

### 2. Risque Clinique : Le Maillon Faible
L'analyse croisée a révélé que l'**IRM-01** présente un taux d'erreur global de **33%**.
* **Alerte Rouge :** 100% des erreurs sur le "Stroke Protocol" (AVC) proviennent de cette machine.
* **Action immédiate :** Suspension des protocoles AVC sur cet équipement et audit technique complet.

---

## 📂 Structure du Repository
* `data/` : Jeu de données (CSV).
* `Script/` : Contient les mesures DAX et le rapport détaillé.
* `README.md` : Présentation synthétique (ce fichier).

---

## 💡 Apprentissages
Ce projet démontre l'importance du **Data Storytelling** en milieu hospitalier : ne pas se contenter de chiffres financiers, mais remonter jusqu'à la sécurité du patient.

---
*Réalisé par [Tên của bạn] - Juillet 2025*