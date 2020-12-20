# cloud-competition-solution
 Solution de la competition Understanding clouds par Chris Deotte

# Description de la compétition
https://www.kaggle.com/c/understanding_cloud_organization

# Objectif
Le but ici est de créer un algorithme de classification des modèles(patterns) d'organisation des nuages à partir d'images satellites. Cela aidera les scientifiques à mieux comprendre comment les nuages influencent le climat futur. Cette recherche guidera le développement de modèles de nouvelle génération qui pourraient réduire les incertitudes dans les projections climatiques.

https://www.github.com/asseridos/cloud-competition-solution/images/Teaser_AnimationwLabels.gif

# Données
Comme dit ci-desssus, il s'agit d'un problème de classification. Il faut identifier les régions des images satellites fournies qui correspondent aux types de nuages définis dont les labels sont : 'Fish', 'Flower', 'Gravel', 'Sugar'. Pour être plus clair, il faudra segmenter chaque image de l'ensemble de test en différentes régions (suites de pixels) correspondant à des types de nuages. Ainsi, chaque image contient au moins un type de nuage et peut contenir tous les 4 types de nuages.

Le segment (la région) correspondant à chaque label de type de nuage pour une image est codé sur une seule ligne, même s'il existe plusieurs zones non contiguës du même type dans une image. S'il n'y a pas de zone d'un certain type de nuage pour une image, la prédiction EncodedPixels correspondante doit être laissée vide.

# Liste des fichiers
- train.csv - les segmentations pour chaque paire image-label dans les images d'entraînement. Ces segmentations sont au format RLE(Run Length Encoded)

- train_images.zip - dossier contenant les images d'entraînement

- test_images.zip - dossier contenant les images de test; la tâche est de prédire les masques de segmentation de chacun des 4 types de nuages (labels) pour chaque image. Il est important de noter également que les masques de prédiction doivent être réduits à 350 x 525 px.

- sample_submission.csv - un exemple de fichier de soumission au format correct

# Métriques
## Coefficient de similarité de Dice
Cette compétition est évaluée sur la base du coefficient de Dice.
Le coefficient encore connu sous le nom d'indice de Sorensen-Dice est un indicateur statistique qui mesure la similarité de deux échantillons. Cet indice a pour formule générale :

'images/dice-coef.png'
où |X| est le nombre d'éléments de X et |Y| le nombre d'éléments de Y. L'indice peut varier de 0 (quand X et Y sont disjoints) à 1 (quand X et Y sont égaux).
Dans le cas de cette compétition, ces opérations peuvent être exprimées en terme d'opérations vectorielles sur les vecteurs X et Y. Le coefficient de Dice est donc utilisé ici pour comparer la similarité pixel-pixel entre une segmentation prédite et la vérité.

'images/dice-coef-2.png'
où X est l'ensemble de pixels prédits et Y l'ensemble de pixels correspondant à la vérité. Lorsque X et Y sont vides, il n'est pas possible de calculer cette formule  puisqu'on se retrouve face à une indétermination. Dans ce cas spécifique, le coefficient prend automatiquement la valeur 1. Le score correspond en fin de compte à la moyenne des coefficients de Dice pour chaque paire <Image, Label> de l'ensemble de test.

## Encodage des pixels
