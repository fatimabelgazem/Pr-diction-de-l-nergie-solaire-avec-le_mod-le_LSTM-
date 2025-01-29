# Prédiction de la Production Photovoltaïque

 Ce projet utilise un modèle de prévision basé sur des données historiques de la production photovoltaïque pour prédire la consommation d'énergie (en MW) sur une période donnée. Le modèle utilise une approche de Machine Learning en utilisant des réseaux de neurones LSTM (Long Short-Term Memory).
 
 --- 
 
 ## Contenu

1. [Description](#description)
2. [Préparation des Données](#Préparation-des-Données)
3. [Entraînement du Modèle](#Entraînement-du-Modèle)
4. [Évaluation du Modèle](#Évaluation-du-Modèle)
5. [Résultats](#Résultats)

---

## Description 
Le but de ce projet est de prédire la production d'énergie photovoltaïque (MW) à partir de données historiques. Les données contiennent des informations sur la production d'énergie photovoltaïque pour chaque jour de l'année sur plusieurs années. Le modèle LSTM est utilisé pour prédire les valeurs futures de la production énergétique.

Les étapes du projet incluent la préparation des données, la création du modèle de réseau neuronal LSTM, l'entraînement du modèle, et l'évaluation des performances du modèle en utilisant l'erreur quadratique moyenne (MSE).

---

## Préparation des Données
Les données sont téléchargées directement depuis une API externe contenant des fichiers CSV pour chaque année de production photovoltaïque. Ces fichiers sont ensuite nettoyés et prétraités pour retirer les lignes inutiles, et les valeurs sont transformées à l'aide d'un MinMaxScaler pour être utilisées dans le modèle.

---

## Entraînement du Modèle
Le modèle utilisé dans ce projet est un modèle LSTM, spécialement conçu pour traiter des séries temporelles. Le modèle est constitué de plusieurs couches LSTM, avec un taux de régularisation Dropout pour éviter le surapprentissage.

```bash
model = Sequential()
model.add(LSTM(units=8, input_shape=(Xtrain.shape[1], 1), return_sequences=True))
model.add(Dropout(0.2))
model.add(LSTM(units=16))
model.add(Dropout(0.2))
model.add(Dense(1, activation='sigmoid'))
model.compile(optimizer=ops.Nadam(lr=1e-3), loss='mse')

``` 

Le modèle est entraîné pendant 50 epochs avec un batch size de 8, et la fonction de perte utilisée est l'erreur quadratique moyenne (mse).

---

## Évaluation du Modèle

Après l'entraînement du modèle, les résultats sont évalués sur un ensemble de données de test. L'erreur quadratique moyenne (MSE) est calculée pour déterminer la performance du modèle sur des données qu'il n'a pas encore vues.

```bash
mean_squared_error(Ytestp[0], testPredict[:,0])
```
---

## Résultats

Une fois l'entraînement terminé, vous pouvez visualiser l'évolution de la perte du modèle au fil des epochs à l'aide du graphique généré par la fonction ploter_Erreur().

---

## Auteurs
Ce projet a été développé par :

  -Fatima Belgazem : fatimabelgazem1@gmail.com
