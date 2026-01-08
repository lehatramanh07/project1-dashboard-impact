# **Analyse de Performance des Équipements d'Imagerie Médicale**

tags: [PowerBI, Healthcare, DataViz, DAX, Data Analysis] 

date: 2025-07-26

## **1. Introduction / Résumé Exécutif**

- **Contexte :** Analyse trimestrielle des équipements médicaux d'un centre hospitalier, motivée par des coûts de maintenance élevés et des doutes sur l'efficacité opérationnelle.
- **Solution :** Développement d'un tableau de bord interactif sur Power BI pour transformer les données brutes en insights exploitables.
- **Découvertes Clés :** L'analyse a révélé la nécessité d'une évaluation basée sur la **valeur clinique** (plutôt que le coût seul) et a identifié un **risque systémique majeur** sur l'équipement IRM-01 (taux d'erreur global de 33%).
- **Objectif Quantitatif :** Réduire de 20% les coûts de maintenance superflus et identifier les équipements à haut risque (taux d'erreur >15%) d'ici fin 2025.

## **2. Problématique / Objectif Métier**

**La Grande Question :** Comment un hôpital peut-il savoir si ses équipements à plusieurs millions d'euros sont réellement performants ?

L'objectif de ce projet est de répondre à cette question en identifiant les appareils les plus performants, en détectant les processus à risque et en fournissant des recommandations basées sur les données pour faciliter une prise de décision rapide et éclairée.

## **3. Méthodologie & Outils Utilisés**

### **Outils :**

- **Microsoft Power BI :** Utilisé pour l'ensemble du processus, de la connexion aux données à la création du tableau de bord final.
- **DAX (Data Analysis Expressions) :** Langage de calcul utilisé pour créer des métriques dynamiques (KPIs) dans Power BI.
  
### **Méthodologie :**
1. **Nettoyage et Transformation des Données :**  
   Correction des types de données via Power Query, notamment :
   - Conversion du champ `Date` au format date
   - Vérification des valeurs numériques (`Duree_Heures`, `Cout_Maintenance_EUR`)
   - Standardisation des valeurs `Erreur_Positionnement` (Oui/Non)

2. Création de Mesures (Ingénierie des Caractéristiques)

Développement de KPIs en DAX avec logique de calcul :

```dax
// 1. Taux d'erreur de positionnement (basé sur les enregistrements)
Taux d'Erreur = 
VAR NombreErreurs = 
    CALCULATE(
        COUNTROWS('DonneesEquipements'),
        'DonneesEquipements'[Erreur_Positionnement] = "Oui"
    )
VAR TotalCas = COUNTROWS('DonneesEquipements')
RETURN
    DIVIDE(NombreErreurs, TotalCas, 0)


// 2. Durée moyenne par patient (basée sur la somme agrégée)
Durée Moyenne par Patient =
    DIVIDE(
        SUM('DonneesEquipements'[Duree_Heures]),
        SUM('DonneesEquipements'[Nb_Patients]),
        0
    )
```

3. **Analyse Exploratoire :** L'exploration initiale, guidée par les coûts, a rapidement évolué pour inclure la fiabilité opérationnelle afin d'obtenir une vision complète de la performance.

## **4. Source des Données**

Les données utilisées pour ce projet sont des **données fictives**, créées spécifiquement pour les besoins de cette analyse. Elles simulent les données d'activité des équipements d'imagerie médicale d'un hôpital sur une période de trois mois.
*→ **Volume traité :** 940 enregistrements patients couvrant 3 équipements (juillet-septembre 2025).*

## **5. Analyses Clés & Recommandations**

Cette section présente les deux analyses principales qui ont émergé des données, ainsi que les recommandations associées.

### Analyse Clé n°1 : Performance Économique - ROI vs Risque

La première question que tout manager se pose est : "Quel appareil est le plus efficace ?". En combinant deux indicateurs clés, le **Nombre de Patients** et le **Coût de Maintenance**, le graphique ci-dessous raconte une histoire très claire.

<img width="347" height="308" alt="Capture d’écran 2025-07-26 à 15 58 39" src="https://github.com/user-attachments/assets/bc6f0501-c942-49e3-ba0f-587c9df3c985" />

**Analyse & Découverte Initiale :**

En un seul coup d'œil, le graphique révèle la performance de chaque dispositif sur les trois derniers mois :

- **Le "Cheval de Trait" :** L'appareil de **Radiographie Mobile (XRAY-01)** est le héros discret. Il a pris en charge près de 37% du total des patients (349/940) pour un coût de maintenance quasi nul de seulement 50 euros.
- **L'"Enfant Terrible" :** Le **Scanner CT-01 (CT Philips)** présente une tout autre histoire. Non seulement il est le dispositif le plus **coûteux** en maintenance (avec un incident majeur en août coûtant 5000 euros), mais il n'a servi que 189 patients.

**Analyse Approfondie : Un coût élevé est-il justifié ?**

Une question importante se pose : Le coût de maintenance élevé du scanner CT est-il un réel problème, ou simplement le reflet de missions plus critiques ? Pour vérifier cette hypothèse, j'ai analysé le nombre de **protocoles médicaux** réalisés par chaque machine.

<img width="332" height="296" alt="Capture d’écran 2025-07-26 à 15 59 55" src="https://github.com/user-attachments/assets/6a59d1a6-3c4b-431f-ac24-c7ca56fbcae4" />

Les résultats montrent que le **CT et l'IRM** sont principalement dédiés aux protocoles spécialisés et urgents (Stroke Protocol, Brain Trauma, Thorax PE), tandis que la **Radiographie** se concentre sur les examens standards.

**Conclusion & Recommandation Stratégique (Récit n°1) :** Plutôt que de voir le CT-01 comme un appareil "coûteux", il incarne un rôle clé dans la prise en charge des cas critiques. Une évaluation basée sur la **valeur (Valeur)** qu'il apporte, et non plus seulement sur son **coût (Coût)**, est recommandée.

### Analyse Clé n°2 : Identification d'un Risque Clinique Majeur

Après avoir clarifié la performance économique, une question plus profonde émerge : **une défaillance opérationnelle silencieuse pourrait-elle compromettre la sécurité de nos patients ?**

**L'Hypothèse de Départ : La Complexité Engendre l'Erreur**

Notre intuition première était que les protocoles plus complexes (et donc plus longs) génèrent plus d'erreurs. Le graphique de corrélation ci-dessous semble confirmer cette tendance, mais révèle surtout des anomalies.

<img width="756" height="238" alt="Capture d’écran 2025-07-26 à 16 00 37" src="https://github.com/user-attachments/assets/9b5c4de2-d851-4eb6-9c8f-da3f9f0285ef" />

**Zoom sur le "Point Chaud" : Le Protocole AVC sous haute surveillance**

L'analyse par protocole révèle une situation alarmante et désigne un coupable évident.

<img width="415" height="164" alt="Capture d’écran 2025-07-26 à 16 01 04" src="https://github.com/user-attachments/assets/c872cd95-94c3-40ec-8d98-2a028505ea0e" />

Le **Protocole AVC (Stroke Protocol)** affiche un taux d'erreur stupéfiant de **85,7%**.

**La Découverte du "Maillon Faible" : La Machine, pas le Protocole**

L'analyse croisée nous offre une révélation sans équivoque.

<img width="340" height="141" alt="Capture d’écran 2025-07-26 à 16 01 36" src="https://github.com/user-attachments/assets/d8530ac0-e6a4-4e1c-ada2-a914286554cb" />

**100% des 6 erreurs** sur le Protocole AVC proviennent d'une seule machine : **l'IRM-01**. De plus, son taux d'erreur global (33%) est trois fois plus élevé que celui des autres appareils. Il s'agit d'une **vulnérabilité systémique**.

**Conclusion & Plan d'Action (Récit n°2) :** Le problème est la performance dangereusement faible de l'équipement **IRM-01**. Un plan d'action en 3 étapes est recommandé pour neutraliser ce risque.

> Plan d'Action :
> 
> 1. **Immédiat (J+1) :** **Suspendre immédiatement** l'assignation de tous les Protocoles AVC à l'IRM-01.
> 2. **Technique (J+15) :** **Diligenter un audit technique complet** de l'IRM-01 par les ingénieurs du fabricant (coût estimé : 7 000 €).
> 3. **Opérationnel (J+30) :** **Organiser un workshop de remise à niveau** pour les techniciens opérant sur l'IRM-01.

## **6. Synthèse & Impact**

Ce tableau de bord fournit un double levier de décision : il oriente la stratégie d'investissement vers la valeur clinique et permet de quantifier et neutraliser les risques opérationnels, avec une **réduction potentielle de 85% des erreurs critiques** sur les protocoles d'AVC.

## **7. Apprentissages & Pistes d'Amélioration**

- **Apprentissages :** L'importance de ne pas s'arrêter à la première conclusion et de toujours chercher le "pourquoi" derrière les chiffres.
- **Pistes d'Amélioration :** Enrichir l'analyse avec des données sur le type de pathologie, le niveau d'urgence, et la valeur diagnostique par examen.
