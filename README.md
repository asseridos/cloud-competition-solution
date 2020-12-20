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
