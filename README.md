<img src="Data/Images/Avion2.png" width="400" style="display: block; margin: 0 auto;">
<p style='text-align: center; font-style: italic; color: #7f8c8d;'>
    Source : Données NTSB 1962-2023
</p>

# Évaluation des Risques Aériens pour l’Acquisition d’Avions
Ce projet analyse les données d’accidents aériens de 1962 à 2023 fournies par le National Transportation Safety Board (NTSB), afin d’aider notre entreprise à entrer en toute sécurité dans le secteur de l’aviation.

À travers des techniques de nettoyage, d’analyse et de visualisation des données, nous identifions les types d’avions les moins risqués et formulons des recommandations concrètes pour leur acquisition.

L’objectif final est de permettre à l’entreprise de prendre des décisions éclairées et basées sur les données pour minimiser les risques.

## Compréhension des affaires

Contexte :
Notre entreprise cherche à élargir son portefeuille en entrant dans le secteur de l’aviation commerciale et privée.

Objectif stratégique :
Identifier les types d’avions les plus sûrs à acquérir, en se basant sur les données d’accidents historiques, pour minimiser les risques opérationnels et financiers.

Défis clés :

L'aviation est un secteur à haut risque, avec des implications humaines, économiques et juridiques importantes en cas d'incident.

L'entreprise n’a pas encore de connaissances spécifiques sur les modèles d’avions ni sur les facteurs de risque associés.

Notre mission :
Fournir à la direction des recommandations basées sur des données pour orienter les décisions d’investissement dans l’achat d’avions, en mettant l’accent sur la sécurité, la fiabilité et les tendances d’accidents par modèle d’appareil.

## Data Understanding
Source des données :
National Transportation Safety Board (NTSB)
Période couverte : 1962 à 2023
Portée : Accidents d’aviation civile aux États-Unis et dans les eaux internationales

Volume de données :
+ Plus de 80 000 enregistrements
Chaque ligne représente un incident ou accident d’aviation

Variables clés analysées :

Date de l’événement

Modèle de l’avion

Gravité des blessures (aucune, mineures, graves, mortelles)

Phase du vol (décollage, croisière, atterrissage, etc.)

Conditions météorologiques

Cause probable

Type d’exploitation (commerciale, privée, militaire, etc.)

Objectif de l’analyse :
Comprendre les tendances, facteurs de risque, et déterminer quels types d’avions sont les plus sûrs pour guider les décisions d’investissement.

## Data Preparation
 Analyse des données manquantes
 
Nettoyage des données manquantes :

Détection et suppression des doublons

Priorité donnée aux colonnes critiques pour l’analyse (modèle, sévérité, date)

Conversion de la colonne de dates

Transformation des colonnes de dates au bon format (datetime)

Regroupement par type météo avec moyenne de la gravité

Uniformisation des champs numériques (nombre de blessés, morts, etc.)

Agrégation des données :

Par modèle d’avion pour comparer la fréquence et la gravité des incidents

Par type de vol (commercial, privé, formation, etc.)

## Analysis and Results

Taux d’accidents par type d’avion :

Calcul du nombre d’accidents par modèle, normalisé si possible par l’usage (si données disponibles)

Identification des modèles présentant le moins d’accidents ou de blessures graves

📈 Visualisation : Nombre d'accidents par mois
```python
# Extraire le mois
df['Month'] = df['Event.Date'].dt.month

# Visualisation
plt.figure(figsize=(7,3))
df['Month'].value_counts().sort_index().plot(kind='bar', color='skyblue')
plt.title("Nombre d'accidents par mois")
plt.xticks(range(12), ['Jan', 'Fév', 'Mar', 'Avr', 'Mai', 'Juin', 'Juil', 'Août', 'Sep', 'Oct', 'Nov', 'Déc'])
plt.show()
```

<img src="Data/Images/Screenshot 2025-06-07 183539.png" width="400" style="display: block; margin: 0 auto;">
<p style='text-align: center; font-style: italic; color: #7f8c8d;'>
</p>

Impact des conditions météorologiques :
```python
taux_mortalite = (df['Total.Fatal.Injuries'] > 0).mean() * 100
print(f" {taux_mortalite:.1f}% des accidents ont causé au moins un décès")

# Visualisation
plt.figure(figsize=(6,6))
plt.pie([taux_mortalite, 100-taux_mortalite], 
        labels=['Accidents mortels', 'Autres'], 
        colors=['#e74c3c', '#3498db'], 
        autopct='%1.1f%%')
plt.title("Proportion d'accidents mortels")
plt.show()

```

<img src="Data/Images/Screenshot 2025-06-07 182936.png" width="400" style="display: block; margin: 0 auto;">
<p style='text-align: center; font-style: italic; color: #7f8c8d;'>
</p>
Répartition géographique des accidents :

<img src="Data/Images/Screenshot 2025-06-07 183010.png" width="400" style="display: block; margin: 0 auto;">
<p style='text-align: center; font-style: italic; color: #7f8c8d;'>
</p>

## Utilisation Power  BI  Pour la Visualisation des donnees :

Nombre de personnes impliquées dans des accidents par année

<img src="Data/Images/Screenshot 2025-06-13 115253.png" width="400" style="display: block; margin: 0 auto;">
<p style='text-align: center; font-style: italic; color: #7f8c8d;'>
</p>

.Nombre d'accidents par mois

.Impact des conditions météorologiques :

.Répartition géographique des accidents :

<img src="Data/Images/Screenshot 2025-06-13 115740.png" width="400" style="display: block; margin: 0 auto;">
<p style='text-align: center; font-style: italic; color: #7f8c8d;'>
</p>

### Business Recommendation 1
investir dans les modèles les plus fiables

Acheter les modèles d’avions ayant un historique sans accident mortel depuis plus de 10 ans

Données historiques fiables = risque opérationnel réduit

Exemples (si disponibles) : Boeing 737 NextGen, Airbus A320neo...

### Business Recommendation 2
Éviter les modèles sensibles à la météo

Certains modèles sont statistiquement plus impliqués dans des accidents par mauvais temps

Prioriser les avions avec meilleure performance en conditions météorologiques défavorables

Important pour les opérations en zones à climat instable

## Conclusion
Les modèles les plus sûrs ont été identifiés à partir d’une analyse rigoureuse des données NTSB

Des facteurs clés comme la météo et le type de vol influencent significativement le risque

Cette analyse offre une base solide pour une entrée maîtrisée dans le secteur aéronautique

### 
Aller plus loin dans la décision d’investissement

Intégrer des données sur la maintenance, l’âge des avions, la formation des pilotes

Consulter des experts du secteur pour valider les choix techniques et stratégiques

Simuler des scénarios d’achat selon différents modèles économiques

##
Merci pour votre attention !
Des questions ?

Nom :Septama Louison  
Email :septamalouison634@gmail.com

LinkedIn :https://www.linkedin.com/in/septama-louison-03335a31a/
