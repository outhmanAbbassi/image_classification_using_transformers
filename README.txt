Code implementation:
le model met en œuvre un modèle Swin Transformer, qui est un type d'architecture de réseau neuronal, pour la classification d'images sur l'ensemble de données CIFAR-100. Il utilise la bibliothèque Keras, qui est une API de haut niveau pour la construction et la formation de modèles d'apprentissage automatique dans TensorFlow.

Voici un résumé de ce que le code fait:

La première section du code importe les bibliothèques et modules nécessaires, tels que matplotlib pour le dessin et TensorFlow/Keras pour la construction du modèle.
Ensuite, les hyperparametres et les dimensions de l'image sont définis. Ce sont des valeurs qui seront utilisées dans tout le code pour configurer le modèle et le chargement des données.
L'ensemble de données CIFAR-100 est chargé à l'aide de la fonction keras.datasets.cifar100.load_data() et est divisé en ensembles de formation, de validation et de test. Les images sont normalisées entre 0 et 1 et les étiquettes sont encodées en un seul coup.
Une série de fonctions d'utilité sont définies pour travailler avec des correctifs d'image, comme l'extraction de correctifs à partir d'une image et leur fusion.
La classe WindowAttention est définie, qui est une couche personnalisée qui applique l'auto-attention à plusieurs têtes à une fenêtre de correctifs à l'intérieur d'une image. Il utilise des embeddings de position relative pour capturer les relations spatiales entre les patches.
La classe SwinTransformer est définie, qui est une couche personnalisée qui applique une série de blocs Swin Transformer aux données d'image. Chaque bloc se compose d'une couche de normalisation, une couche d'auto-attention à plusieurs têtes et d'un réseau de transmission. Les blocs sont appliqués de manière hiérarchique, la taille de la fenêtre des couches d'attention augmentant à chaque étape.
La fonction patch_extract est définie, qui extrait des patches d'une image et leur applique une projection linéaire.
La classe PatchEmbedding est définie, qui applique la fonction patch_extract et ajoute une position appréhensible d'incorporation aux correctifs.
La classe PatchMerging est définie, qui fusionne les patches en prenant leur concatenation et en appliquant une transformation linéaire.
Les variables dataset, dataset_val et dataaset_test sont définies, qui sont tf.data.Ensemble d'objets de données qui contiennent les ensembles de formation, de validation et de test, respectivement. Ils sont créés en appliquant une série d'augmentations de données et de transformations de pré-traitement aux données chargées.
Le modèle est défini comme une série de couches, y compris les couches PatchEmbedding, SwinTransformer, PatchMerging et Dense.
Le modèle est compilé avec une fonction de perte, un optimisateur et des mesures.
Le modèle est entraîné à l'aide de la fonction fit(), qui prend en charge l'ensemble de données de formation et exécute le modèle pour un nombre spécifié d'époques. L'ensemble de données de validation est utilisé pour calculer la perte et l'exactitude de la validation à la fin de chaque époque.
Le progrès de la formation est visualisé en utilisant un plan des pertes de formation et de validation au fil des époques.
Les résultats finaux de la formation sur CIFAR-100 sont affichés en évaluant le modèle sur l'ensemble de données d'essai et en imprimant la perte et l'exactitude des tests.
En résumé, ce code met en œuvre un modèle Swin Transformer pour la classification de l'image et l'entraîne sur l'ensemble de données CIFAR-100. Il comprend le chargement des données, le pré-traitement, la construction de modèles et les étapes d'évaluation.