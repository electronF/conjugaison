# Conjugaison
Ce dépot contient un algorithme d'apprentissage automatique de Neural Machine Translation construit grace à un encodeur decodeur avec mechanisme d'attention. 

## Grattage de données
Le repos contient déjà une base de données au nom 'verbes_conjuges_avec_groupe' il faut extraire l'archive pour l'obtenir en .csv et en .json. Dans sa version actuelle l'algorithme n'utilise que le .csv.

Mais pour obtenir une base de données à jour, il y a quelques etapes à suivre.

Note: Remercions **Le conjuguer** du **Le Figaro** qui possède une grande base de données de verbes à gratter.

### Grattage de verbe
Pour obtenir la base de données finale il faut commencer par obtenir la liste des verbes et les liens vers les pages contenant les conjugaisons des verbes. 

Pour ce faire il faut executer le code dans le notebook *'grattage_verbes.ipynb'* Ce code contient une version lente et une version rapide pour effectuer le grattage. La version rapide utilise le multhreading pour effectuer simultannement plusieurs requetes vers le serveur. Rassurer vous que votre ordinateur supporte le multithreading. 

Cette version permet de reduire le temps d'attente d'un facteur d'aumoins 10. Vous pouvez modifier la taille de la trame pour ameliorer la vitesse au detriment du nombre de thread.

Si votre ordinateur ne supporte pas le multithreading, alors  utiliser la version normale.


### Grattage de verbes conjugués
Executer le code contenu dans le notebook *'grattage_des_conjuguaisons_des_verbes.ipynb'* pour avoir la base de donnée finale. Parreillement à la section precedente ce notebook contient deux versions de code une plus lente qui n'exploite pas le multithreading et une plus rapide. Les instructions sont les memes que celles de la partie grattage de verbes.

## Traitement de données et entrainement du modèle
Le notebook *'conjuguaison_francais_tensorflow.ipynb'* contient le code qui permet de traiter les données et d'entrainer le modele. 
Le modele est un encodeur decodeur avec mecanisme d'attention. Il contient le modele l'entrainement et le code necessaire pour sauvegarder, valider et tester le modèle. Il y a egalement une fonction qui peut etre utile pour l'utilisation du modele. 


## Perspectives
* Ajouter des callback pour sauvegarder automatiquement le meilleurs modele.
* Ajouter un callback pour arreter l'apprentissage quand un bon modele est trouvé grace à l'approche *early stopping*
* Tester l'apprentissage sans mechanisme d'attention (Voir *'future_conjuguaison_francais_tensorflow.ipynb'*)
* Refaire creer de nouveaux modeles avec et sans mechanisme d'attention et les entrainer avec pytorch.
