# StarSectorLocalizer
# Comment traduire les fichiers ?
Actuellement, le patcheur peut traduire automatiquement des fichiers de plusieurs types, à savoir : txt, csv, json, jar. Tous les fichiers de traduction doivent être situés dans le même dossier (hiérarchiquement relatif à la racine du jeu) que le fichier qu'ils traduisent. Selon le type de fichier et de gestionnaire, un postfixe est ajouté à son nom, et le type de postfixe est décrit dans chaque cas individuel ci-dessous. Notez également que toutes les clés de traduction sont sensibles à la casse.

### Traduction de fichiers txt, java
Les fichiers les plus faciles à traduire sont les fichiers txt et java. 
Pour ce faire, vous devez ajouter au fichier original sur une nouvelle ligne `[###StarSectorLocalization###]`, et mettez la traduction sur la ligne suivante. Il est important de conserver le texte original dans l'original, car le patcheur le compare avec ce qu'il trouve dans le fichier du jeu, et en cas de mise à jour du texte dans les nouvelles versions du jeu, vous pouvez notifier la nécessité de corriger la traduction. 
Le séparateur exact entre le texte original et la traduction est une chaîne comme `"\r\n[###StarSectorLocalization###]\r\n"`, le code pour traiter les fichiers txt (et en même temps java) se trouve [lien](/Src/Localizer/Localizers/TxtGeneralLocalizer.cs). 

Postfixe au nom du fichier : `.translation.txt`

Exemple de traduction d'un fichier txt : [lien].(/Translation/Languages/ru/starsector-core/data/missions/afistfulofcredits/mission_text.txt.translation.txt)

### Traduire des fichiers json
Pour traduire un fichier json, vous devrez créer un fichier json - dictionnaire, qui contiendra des paires clé-valeur, où la clé sera le texte original et les valeurs seront la traduction.
Lors de la préparation, il est judicieux de créer une liste complète des phrases à traduire, puis de les traduire. Dans ce cas, vous pouvez spécifier `null` comme traduction, qui sera ignorée pendant la traduction. Vous pouvez également l'utiliser lorsque vous n'êtes pas sûr de savoir comment traduire correctement une phrase.

Postfixe au nom du fichier : `.translation.json`

Exemple de traduction d'un fichier json : [lien](/Translation/Languages/ru/starsector-core/data/missions/afistfulofcredits/descriptor.json.translation.json)

### Traduction des fichiers jar
Pour l'instant, la majeure partie de l'interface utilisateur est contenue dans des fichiers jar. 
La création de traductions pour ces fichiers n'est pas différente des fichiers json, vous devez créer les mêmes paires clé-valeur, mais trouver des phrases pour la traduction est un peu plus difficile. 
C'est pourquoi nous avons préparé à l'avance un fichier modèle pour la traduction (il n'est maintenant nécessaire que pour deux fichiers), où le texte non traduit a une valeur de `null`.

Traductions pour [starfarer.api.jar](/Translation/Languages/ru/starsector-core/starfarer.api.jar.translation.json) и [starfarer_obf.jar](/Translation/Languages/ru/starsector-core/starfarer_obf.jar.translation.json)

Lors de la traduction des fichiers jar, une analyse de base est effectuée pour empêcher le renommage des noms de variables et de paramètres (par exemple, la constante de chaîne "ship" est parfois un paramètre utilisé dans un appel dynamique plutôt que dans le texte de l'interface), mais cela bloque la traduction d'une phrase dans l'ensemble de la classe, ce qui peut laisser des endroits non traduits même si la phrase est spécifiée dans le dictionnaire.

### Traduire des fichiers csv

Lors de la traduction de fichiers csv, un fichier json est créé qui contient la liste des colonnes à traduire (dans l'élément ``TranslatedColumns``) et les traductions clé-valeur (dans l'élément ``Translations``).

Postfixe au nom du fichier : `.translation.json`

Exemple de traduction d'un fichier json : [lien].(/Translation/Languages/ru/starsector-core/data/strings/descriptions.csv.translation.json)

### Autres fichiers

Si le dossier des traductions contient un fichier dont le nom est identique à celui de l'original, il l'écrasera tout simplement. C'est ainsi que fonctionne la localisation des polices.

#### Localisation des polices

Les polices de caractères originales du jeu ne contiennent pas de symboles permettant d'afficher les lettres russes (et pratiquement toutes les lettres sauf l'anglais), vous devez donc les remplacer par vos propres polices de caractères prenant en charge la langue qui vous intéresse. Lors de la localisation, ces fichiers sont simplement remplacés.

Les polices localisées se trouvent dans [ce dossier].(/Translation/Languages/ru/starsector-core/graphics/fonts).

## Traductions personnalisées
1. Traduit par [WhitePulsar](https://github.com/WhitePulsar/StarSectorLocalizer-Machine-MODS)
