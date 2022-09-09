1. Création des modèles et résultats

Le choix des modèles est lié à la variation de jeu de données (Dataset), d’où il est important de visualiser comment les paramètres varient en fonction du temps, les figures 46, 47, 48, 49, 50 et 51 montre la variation des paramètres entre 2012 et 2022 dans notre cas.

D’après le pattern qu’on a obtenu, on a décidé d’implémenter les modèles de régression car ces derniers se basent sur les patterns historiques et ils cherchent à construire un nouveau pattern qui rassemble à celui qu’on a obtenu pour chaque paramètre.

Dans ce qui suit nous allons créer les quatre modèles (**régression linéaire multiple, régression polynomiale, Random Forest Regression, Decision Tree regression**) pour chaque paramètre, chacun d’eux sera entrainé puis tester sur les collections d’entrainement et de test respectivement. Afin d’évaluer la précision des quatre modèles, nous calculerons différentes mesures de performances après l’entrainement pour qu’à la fin nous puissions les comparer. 

*Figure 46:visualisation des données historique de la Température*

*Figure 47:visualisation des données historique du rayonnement solaire*



*Figure 48:visualisation des données historique de la vitesse de vent*

*Figure 49:visualisation des données historique de la précipitation*

*Figure 50:visualisation des données historique de l’humidité*

*Figure 51:visualisation des données historique de la direction de vent*

1. Prévision de la température

La première chose à faire c’est de déterminer les paramètres qui influencent sur la variation de la température ces paramètres ils ont une forte corrélation avec la température (figure 52).


*Figure 52:corrélation de température avec les autres paramètres*

La figure 52 montre que **tempmax, tempmin, temp, humidity, solarradiation, solarenergy, uvindex** sont les paramètres qui ont une relation avec la température.







*Figure 53:: illustration du processus de prédiction de la température*

1. **Multiple Linear Regression**

L'objectif de la régression linéaire multiple est de modéliser la relation linéaire entre les variables explicatives et les variables de réponse.

- **L’entrainement du modèle**

*Figure 54:code l’entrainement du MLR*

Pour entrainer le modèle on importe la bibliothèque **LinearRegression** de **Sklearn**, après on sélectionne l’algorithme (ligne 2 de la figure 54), puis on entraine notre model sur les données d’entrainement qu’on a préparé dans le chapitre précèdent.

- **Résultat du model** 

Pour voir les résultats du modèle, on l’applique sur des données qui n’a pas vu précédemment, ces données sont les données de test qu’on a préparé dans le chapitre précèdent. La fonction **predict()** de notre modèle nous permet de faire ça. 



*Figure 55:code MLR de prédiction*

- **Visualisation de résultat**

*Figure 56:visualisation de résultat de MLR pour T*

- **Evaluation du modèle** 

L’évaluation se faite par le calcul des paramètres suivants :

- **Mean Absolute Error (MAE)** : MAE est la somme des différences absolues entre notre cible et la prévue.

MAE=1n\*i=1nxi-x

- **R-squared** : est une mesure statistique dans un modèle de régression qui détermine la proportion de variance dans la variable dépendante qui peut être expliquée par la variable indépendante. En d'autres termes, le r-squared montre à quel point les données correspondent au modèle de régression

Dans notre cas les résultats de ces deux paramètres sont montrés dans la figure 57

*Figure 57:code d’évaluation du MLR pour T*

1. **Decision Tree Regression**

Ce modèle observe les caractéristiques d'un objet et forme un modèle dans la structure d'un arbre pour prédire les données à l'avenir.

- **L’entrainement du modèle**

*Figure 58:code l’entrainement du DTR*

Pour entrainer le modèle on importe la bibliothèque **DecisionTreeRegressor** de **Sklearn**, après on sélectionne l’algorithme (ligne 2 de la figure 58), puis on entraine notre model

- **Résultat du model** 

Maintenant on applique notre modèle sur les données de test 

*Figure 59:code DTR de prédiction*

- **Visualisation de résultat**

*Figure 60:visualisation de résultat de DTR pour T*

- **Evaluation du modèle** 

*Figure 61:code d’évaluation du DTR pour T*

1. Random Forest Regression

Est un modèle qui utilise la méthode d'apprentissage d'ensemble pour la régression. La méthode d'apprentissage d'ensemble est une technique qui combine les prédictions de plusieurs algorithmes d'apprentissage automatique pour faire une prédiction plus précise qu'un modèle unique.

- **L’entrainement du modèle**

*Figure 62:code l’entrainement du RFR*

Pour entrainer le modèle on importe la bibliothèque **RandomForestRegressor** de **Sklearn**, après on sélectionne l’algorithme (ligne 2 de la figure 62), puis on entraine notre model.

- **Résultat du model** 

Maintenant on applique notre modèle sur les données de test 

*Figure 63:code RFR de prédiction*

- **Visualisation de résultat**

*Figure 64:: visualisation de résultat de RFR pour T*

- **Evaluation du modèle** 

*Figure 65:code d’évaluation du RFR pour T*

1. Polynomial Regression

Ce modèle utilise une approche statistique qui est employée pour modéliser une relation de forme non-linéaire entre la réponse y et la ou les variables explicatives x.

- **L’entrainement du modèle**

*Figure 66:code l’entrainement du PR*

Pour entrainer le modèle on importe la bibliothèque **PolynomialFeatures** de **Sklearn**, après on sélectionne le degré du polynôme (ligne 2 de la figure 66), puis on transforme les caractéristiques (Features) en une forme polynomiale (ligne 3 de la figure 66) et en fin en entraine notre modèle  

- **Résultat du model** 

*Figure 67:code PR de prédiction*

- **Visualisation de résultat**

*Figure 68:visualisation de résultat de PR pour T*

- **Evaluation du modèle** 

*Figure 69: code d’évaluation du PR pour T*

1. Comparaison des résultats obtenus 

Le tableau suivant représente les résultats d’évaluation des 4 modèles pour la Température :  

|Modèle|R2-Score|MAE|Interprétation|
| :-: | :-: | :-: | :-: |
|MLR|0.98|0.92|<p>- 98 % des prédictions du modèle sont correctes</p><p>- la mesure de l'ampleur moyenne des erreurs dans l’ensemble de prévisions est 0.92</p>|
|DTR|0.96|1.20|<p>- 96 % des prédictions du modèle sont correctes</p><p>- la mesure de l'ampleur moyenne des erreurs dans l’ensemble de prévisions est 1.20</p>|
|RFR|0.98|0.89|<p>- 98 % des prédictions du modèle sont correctes</p><p>- la mesure de l'ampleur moyenne des erreurs dans l’ensemble de prévisions est 0.89</p>|
|**PR**|**0.98**|**0.87**|<p>**- 98 % des prédictions du modèle sont correctes**</p><p>**- la mesure de l'ampleur moyenne des erreurs dans l’ensemble de prévisions est 0.87**</p>|
*Tableau 12:comparaison des 4 modèles pour température*

1. Choix du modèle

Apres le calcul des paramètres d’évaluation (MAE, R2-Score), c’est le temps de prendre une décision à la base des résultats de ces paramètres.

Le bon modèle est celui qui a une petite moyenne des erreurs et un grand pourcentage de prédictions correcte, et d’après le tableau on remarque que le bon modèle pour prédire la température est **Polynomial Regression.**

1. Prévision de l’Humidité

Déterminant les paramètres qui influencent sur la variation de l’humidité c’est-à-dire les paramètres qui ont une forte corrélation avec l’humidité (figure 70).





*Figure 70:corrélation de l’humidité avec les autres paramètres*

D’après La figure 70 **tempmax, tempmin, temp, humidity, precipcover, solarradiation, solarenergy, uvindex'**sont les paramètres qui ont une relation avec l’humidité.









*Figure 71:illustration du processus de prédiction de l’humidité*

L’entrainement des modèles est le même que le cas de la température, donc dans ce qui suit on va présenter seulement la visualisation des résultats et l’évaluation des modèles.

1. Multiple Linear Regression
- **Visualisation de résultat**

*Figure 72:visualisation de résultat de MLR pour H*

- **Evaluation du modèle** 

*Figure 73:évaluation du MLR pour H*

1. Decision Tree Regression
- **Visualisation de résultat**

*Figure 74:visualisation de résultat de DTR pour H*

- **Evaluation du modèle** 

*Figure 75:évaluation du DTR pour H*

1. Random Forest Regression
- **Visualisation de résultat**

*Figure 76:visualisation de résultat de RFR pour H*

- **Evaluation du modèle** 

*Figure 77:évaluation du RFR pour H*

1. Polynomial Regression
- **Visualisation de résultat**

*Figure 78:visualisation de résultat de PR pour H*

- **Evaluation du modèle** 

*Figure 79:évaluation du PR pour H*

1. Comparaison des résultats obtenus 

Le tableau suivant représente les résultats d’évaluation des 4 modèles pour la l’humidité

|Modèle|R2-Score|MAE|Interprétation|
| :-: | :-: | :-: | :-: |
|MLR|0.49|4.14|<p>- 49 % des prédictions du modèle sont correctes</p><p>- la mesure de l'ampleur moyenne des erreurs dans l’ensemble de prévisions est 4.14</p>|
|DTR|0.05|5.33|<p>- 5 % des prédictions du modèle sont correctes</p><p>- la mesure de l'ampleur moyenne des erreurs dans l’ensemble de prévisions est 5.33</p>|
|**RFR**|**0.50**|**3.94**|<p>**- 50 % des prédictions du modèle sont correctes**</p><p>**- la mesure de l'ampleur moyenne des erreurs dans l’ensemble de prévisions est 3.94**</p>|
|PR|0.39|4.23|<p>- 39 % des prédictions du modèle sont correctes</p><p>- la mesure de l'ampleur moyenne des erreurs dans l’ensemble de prévisions est 4.23</p>|
*Tableau 13:comparaison des 4 modèles pour l’humidité*

1. Choix du modèle

Apres le calcul des paramètres d’évaluation (MAE, R2-Score), c’est le temps de prendre une décision à la base des résultats de ces paramètres.

Le bon modèle est celui qui a une petite moyenne des erreurs et un grand pourcentage de prédictions correcte, et d’après le tableau on remarque que le bon modèle pour prédire l’humidité est **Random forest Regression.**

1. Prévision de Précipitation
**
` `Déterminant les paramètres qui influencent sur la variation de précipitation c’est-à-dire les paramètres qui ont une forte corrélation avec la précipitation (figure 80).


*Figure 80:corrélation de la précipitation avec les autres paramètres*

D’après la figure 80, **precip et precipcover** sont les paramètres qui ont une relation avec l’humidité.








*Figure 81:illustration du processus de prédiction de l’humidité*

1. Multiple Linear Regression
- **Visualisation de résultat**

*Figure 82:visualisation de résultat de MLR pour P*

- **Evaluation du modèle** 

*Figure 83: évaluation du MLR pour P*

1. Decision Tree Regression
- **Visualisation de résultat**

*Figure 84:visualisation de résultat de DTR pour P*

- **Evaluation du modèle** 

*Figure 85:évaluation du DTR pour P*

1. Random Forest Regression
- **Visualisation de résultat**

*Figure 86:visualisation de résultat de RFR pour P*

- **Evaluation du modèle** 

*Figure 87:évaluation du RFR pour P*

1. Polynomial Regression
- **Visualisation de résultat**

*Figure 88:visualisation de résultat de PR pour P*

- **Evaluation du modèle** 

*Figure 89:évaluation du PR pour P*

1. Comparaison des résultats obtenus 

Le tableau suivant représente les résultats d’évaluation des 4 modèles pour la précipitation :

|Modèle|R2-Score|MAE|Interprétation|
| :-: | :-: | :-: | :-: |
|MLR|0.42|0.31|<p>- 42 % des prédictions du modèle sont correctes</p><p>- la mesure de l'ampleur moyenne des erreurs dans l’ensemble de prévisions est 0.31</p>|
|DTR|-0.94|0.47|- la mesure de l'ampleur moyenne des erreurs dans l’ensemble de prévisions est 0.73|
|RFR|-0.17|0.40|- la mesure de l'ampleur moyenne des erreurs dans l’ensemble de prévisions est 0.40|
|PR|0.47|0.33|<p>- 47 % des prédictions du modèle sont correctes</p><p>- la mesure de l'ampleur moyenne des erreurs dans l’ensemble de prévisions est 0.33</p>|
*Tableau 14: : comparaison des 4 modèles pour précipitation*

1. Choix du modèle

Apres le calcul des paramètres d’évaluation (MAE, R2-Score), c’est le temps de prendre une décision à la base des résultats de ces paramètres.

Le bon modèle est celui qui a une petite moyenne des erreurs et un grand pourcentage de prédictions correcte, et d’après le tableau on remarque que le bon modèle pour prédire la précipitation est **Polynomial Regression.**

1. Prévision de rayonnement solaire

Déterminant les paramètres qui influencent sur la variation du rayonnement solaire c’est-à-dire les paramètres qui ont une forte corrélation avec le rayonnement solaire (figure 90).


*Figure 90:corrélation du rayonnement solaire avec les autres paramètres*

D’après la figure 90 **tempmax, humidity, solarradiation, solarenergy, uvindex** sont les paramètres qui ont une relation avec rayonnement solaire.







*Figure 91:illustration du processus de prédiction du rayonnement solaire*

1. Multiple Linear Regression
- **Visualisation de résultat**

*Figure 92:visualisation de résultat de MLR pour SR*

- **Evaluation du modèle** 

*Figure 93:évaluation du MLR pour SR*

1. Decision Tree Regression
- **Visualisation de résultat**

*Figure 94:visualisation de résultat de DTR pour SR*

- **Evaluation du modèle** 

*Figure 95:évaluation du DTR pour SR*

1. Random Forest Regression
- **Visualisation de résultat**

*Figure 96:visualisation de résultat de RFR pour SR*

- **Evaluation du modèle** 

*Figure 97:évaluation du RFR pour SR*

1. Polynomial Regression
- **Visualisation de résultat**

*Figure 98:visualisation de résultat de PR pour SR*

- **Evaluation du modèle** 

*Figure 99: évaluation du PR pour SR*

1. Comparaison des résultats obtenus 

Le tableau suivant représente les résultats d’évaluation des 4 modèles pour le rayonnement solaire :

|Modèle|R2-Score|MAE|Interprétation|
| :-: | :-: | :-: | :-: |
|**MLR**|**0.69**|**239.02**|<p>**- 69 % des prédictions du modèle sont correctes**</p><p>**- la mesure de l'ampleur moyenne des erreurs dans l’ensemble de prévisions est 239.02**</p>|
|DTR|0.49|259.91|<p>-0.49 % des prédictions du modèle sont correctes</p><p>- la mesure de l'ampleur moyenne des erreurs dans l’ensemble de prévisions est 259.91</p>|
|RFR|0.68|234.07|<p>-68 % des prédictions du modèle sont correctes</p><p>- la mesure de l'ampleur moyenne des erreurs dans l’ensemble de prévisions est 234.07</p>|
|PR|0.48|283.03|<p>- 48 % des prédictions du modèle sont correctes</p><p>- la mesure de l'ampleur moyenne des erreurs dans l’ensemble de prévisions est 283.03</p>|
*Tableau 15:comparaison des 4 modèles pour rayonnement solaire*

1. Choix du modèle

Apres le calcul des paramètres d’évaluation (MAE, R2-Score), c’est le temps de prendre une décision à la base des résultats de ces paramètres.

Le bon modèle est celui qui a une petite moyenne des erreurs et un grand pourcentage de prédictions correcte, et d’après le tableau on remarque que le bon modèle pour prédire le rayonnement solaire est **Multiple linear regression**

1. Prévision de vitesse de vent

Déterminant les paramètres qui influencent sur la variation de la vitesse de vent c’est-à-dire les paramètres qui ont une forte corrélation avec la vitesse de vent.




*Figure 100:corrélation de la vitesse de vent avec les autres paramètres*

D’après la figure 100 **windspeed, winddir, solarradiation, solarenergy, uvindex** sont les paramètres qui ont une relation avec la vitesse de vent.

Le problème pour ce paramètre c’est que sa corrélation avec les autres paramètres n’est forte, il ne dépasse pas 0.27 ce qui va influencer négativement sur nos modèles.









*Figure 101:illustration du processus de prédiction de la vitesse de vent*

1. Multiple Linear Regression
- **Visualisation de résultat**

*Figure 102:visualisation de résultat de MLR pour VV*

- **Evaluation du modèle** 

*Figure 103:évaluation de MLR pour VV*

1. Decision Tree Regression
- **Visualisation de résultat**

*Figure 104:visualisation de résultat de DTR pour VV*

- **Evaluation du modèle** 

*Figure 105:évaluation de DTR pour VV*

1. Random Forest Regression
- **Visualisation de résultat**

*Figure 106:visualisation de résultat de RFR pour VV*

- **Evaluation du modèle** 

*Figure 107: évaluation de RFR pour VV*

1. Polynomial Regression
- **Visualisation de résultat**

*Figure 108:visualisation de résultat de PR pour VV*

- **Evaluation du modèle** 

*Figure 109:évaluation de PR pour VV*

1. Comparaison des résultats obtenus 

Le tableau suivant représente les résultats d’évaluation des 4 modèles pour la vitesse de vent

|Modèle|R2-Score|MAE|Interprétation|
| :-: | :-: | :-: | :-: |
|MLR|0.52|3.07|<p>- 52 % des prédictions du modèle sont correctes</p><p>- la mesure de l'ampleur moyenne des erreurs dans l’ensemble de prévisions est 3.07</p>|
|DTR|0.06|4.21|<p>- 6 % des prédictions du modèle sont correctes</p><p>- la mesure de l'ampleur moyenne des erreurs dans l’ensemble de prévisions est 4.21</p>|
|RFR|0.56|2.92|<p>- 56 % des prédictions du modèle sont correctes</p><p>- la mesure de l'ampleur moyenne des erreurs dans l’ensemble de prévisions est 2.92</p>|
|PR|0.54|2.98|<p>-54 % des prédictions du modèle sont correctes</p><p>- la mesure de l'ampleur moyenne des erreurs dans l’ensemble de prévisions est 2.98</p>|
*Tableau 16:comparaison des 4 modèles pour vitesse de vent*

1. Choix du modèle

Apres le calcul des paramètres d’évaluation (MAE, R2-Score), c’est le temps de prendre une décision à la base des résultats de ces paramètres.

Le bon modèle est celui qui a une petite moyenne des erreurs et un grand pourcentage de prédictions correcte, et d’après le tableau on remarque que le bon modèle pour prédire la vitesse de vent est **Random forest Regression**

1. Prévision de la direction de vent

Déterminant les paramètres qui influencent sur la variation de la direction de vent c’est-à-dire les paramètres qui ont une forte corrélation avec la direction de vent (figure 110).


*Figure 110:corrélation de la direction de vent avec les autres paramètres*

D’après la figure 110 **windspeed, winddir** sont les paramètres qui ont une relation avec la direction de vent.	








*Figure 111:illustration du processus de prédiction de la direction de vent*

1. Multiple Linear Regression
- **Visualisation de résultat**

*Figure 112:visualisation de résultat de MLR pour DV*

- **Evaluation du modèle** 

*Figure 113:évaluation de MLR pour VV*

1. Decision Tree Regression
- **Visualisation de résultat**

*Figure 114:visualisation de résultat de DTR pour DV*

- **Evaluation du modèle** 

*Figure 115:évaluation de DTR pour DV*

1. Random Forest Regression
- **Visualisation de résultat**

*Figure 116:visualisation de résultat de RFR pour DV*

- **Evaluation du modèle** 

*Figure 117:évaluation de RFR pour DV*

1. Polynomial Regression
- **Visualisation de résultat**

*Figure 118:visualisation de résultat de PR pour DV*

- **Evaluation du modèle** 

*Figure 119:évaluation de PR pour DV*

1. Comparaison des résultats obtenus 

Le tableau suivant représente les résultats d’évaluation des 4 modèles pour la direction de vent :

|Modèle|R2-Score|MAE|Interprétation|
| :-: | :-: | :-: | :-: |
|MLR|0.35|24.17|<p>- 35% des prédictions du modèle sont correctes</p><p>- la mesure de l'ampleur moyenne des erreurs dans l’ensemble de prévisions est 24.17</p>|
|DTR|0.38|32.43|<p>- 38 % des prédictions du modèle sont correctes</p><p>- la mesure de l'ampleur moyenne des erreurs dans l’ensemble de prévisions est 32.43</p>|
|RFR|0.23|25.37|<p>- 23 % des prédictions du modèle sont correctes</p><p>- la mesure de l'ampleur moyenne des erreurs dans l’ensemble de prévisions est 25.37</p>|
|**PR**|**0.40**|**23.04**|<p>**-40 % des prédictions du modèle sont correctes**</p><p>**- la mesure de l'ampleur moyenne des erreurs dans l’ensemble de prévisions est 23.04**</p>|
*Tableau 17:comparaison des 4 modèles pour direction de vente*

1. Choix du modèle

Apres le calcul des paramètres d’évaluation (MAE, R2-Score), c’est le temps de prendre une décision à la base des résultats de ces paramètres.

Le bon modèle est celui qui a une petite moyenne des erreurs et un grand pourcentage de prédictions correcte, et d’après le tableau on remarque que le bon modèle pour prédire la vitesse de vent est **Polynomial Regression**

1. Résultats finaux

Le tableau suivant représente les résultats finaux des modèles les plus performants pour la prévision de chaque paramètre météorologique :   

|**Paramètre**|**Model choisi**|**Observation**|
| :-: | :-: | :-: |
|**Température**|**PR**|Le pourcentage de prédictions correcte est 98%|
|**Humidité** |**RFR**|Le pourcentage de prédictions correcte est 50%|
|**Précipitation**|**PR**|Le pourcentage de prédictions correcte est 47%|
|**Rayonnement solaire**|**MLR**|Le pourcentage de prédictions correcte est 69%|
|**Direction de vent**|**PR**|Le pourcentage de prédictions correcte est 40%|
|**Vitesse de vent**|**RFR** |Le pourcentage de prédictions correcte est 56%|
*Tableau 18:modèle choisi pour chaque paramètre*
## Conclusion
##
Au cours de ce sprint, nous avons appliqué et évalué les modèles proposés de l’apprentissage automatique supervisé pour prédire un ensemble de paramètres météorologiques (Température, Humidité, Précipitation, Rayonnement solaire, Direction de vent, vitesse de vent).

Dans le sprint suivant on va mettre en place une API pour fournir ces prévisions aux différentes applications de l’entreprise.  

