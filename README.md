## Projet Carte Électronique pour Robot Tondeuse

### Analyse des Composants

#### Moteurs de Propulsion et de Coupe (Motoréducteurs)
- **Choix** : Sélection de motoréducteurs adaptés pour un couple élevé, essentiel pour la propulsion (3600 mA) et la coupe (800 mA) sous une tension de 12V.
- **Justification** : Ces moteurs offrent une mobilité efficace sur l'herbe et une capacité de coupe adéquate, avec une tension compatible avec les batteries standards.

#### Accéléromètre/Gyroscope
- **Choix** : Intégration pour mesurer l'inclinaison et la vitesse du robot, vital pour naviguer sur des terrains variés et prévenir les renversements.
- **Justification** : Un courant de fonctionnement de 100 mA sous 5V permet une bonne autonomie sans compromettre les performances.

#### LED
- **Choix** : Utilisées pour signaler le statut du robot (actif, en panne, etc.).
- **Justification** : Leur consommation modérée de 185 mA sous 5V optimise l'endurance du robot sans sacrifier la visibilité.

#### Capteur Fin de Course
- **Choix** : Déployés pour détecter les collisions et le soulèvement du robot, augmentant ainsi la sécurité et la précision de l'appareil.
- **Justification** : Avec seulement 10 mA sous 5V, ces capteurs fonctionnent efficacement sans épuiser rapidement la batterie.

#### Capteur d'Humidité (Hygromètre)
- **Choix** : Essentiel pour surveiller les conditions météorologiques et déterminer la faisabilité des opérations du robot.
- **Justification** : Consommation quasi nulle de 1 µA sous 5V, parfait pour un monitoring constant sans impacter l'autonomie.

#### LIDAR
- **Choix** : Crucial pour la navigation et l'évitement d'obstacles grâce à une cartographie précise de l'environnement.
- **Justification** : Avec une consommation raisonnable de 180 mA sous 5V, le LIDAR combine performance et efficacité énergétique.

#### Écran LCD 3" & GPS
- **Choix** : L'écran facilite les interactions et les ajustements tandis que le GPS assure une localisation précise pour une gestion optimale de la zone de tonte.
- **Justification** : Consommation réduite (20 mA pour l'écran et 16 mA pour le GPS) adaptée à l'utilisation avec le Raspberry Pi.

### Évaluation et Suggestions

- **Alimentation** : L'adoption d'un régulateur de tension abaisseur (buck converter) comme le TPS564257 est stratégique pour une gestion optimale des différentes tensions nécessaires. Il est crucial de vérifier que la capacité de la batterie peut supporter la consommation élevée des moteurs.
- **Communication et Contrôle** : L'ESP32 pour les tâches en temps réel et le Raspberry Pi pour le traitement complexe et la connectivité forment une combinaison robuste pour la gestion des actionneurs et capteurs.
- **Pont H pour Moteurs** : Indispensable pour contrôler la direction et la vitesse des moteurs. Il est important de sélectionner un modèle qui supporte les courants élevés exigés par les motoréducteurs.
- **Améliorations possibles** :
  - **Gestion de l'Énergie** : Considérer l'intégration d'un système de gestion d'énergie pour maximiser l'autonomie, en mettant certains composants en veille.
  - **Capteurs Supplémentaires** : L'ajout de capteurs de sol pourrait améliorer l'adaptation du robot à des environnements plus complexes.

### Bilan Énergétique

Nous évaluons la consommation énergétique totale des composants pour déterminer la capacité nécessaire de la batterie, visant une autonomie d'une heure.

#### Estimation de la Consommation

- **Moteurs de Propulsion** : \(2 \times 3600 \, \text{mA} = 7200 \, \text{mA}\)
- **Moteur de Coupe** : \(800 \, \text{mA}\)
- **Accéléromètre/Gyroscope** : \(100 \, \text{mA}\)
- **LEDs** : \(2 \times 185 \, \text{mA} = 370 \, \text{mA}\)
- **Capteurs Fin de Course** : \(5 \times 10 \, \text{mA} = 50 \, \text{mA}\)
- **Capteur d'Humidité** : \(1 \, \text{µA} \approx 0 \, \text{mA}\) (négligeable)
- **LIDAR** : \(180 \, \text{mA}\)
- **Écran LCD** : \(20 \, \text{mA}\)
- **GPS** : \(16 \, \text{mA}\)

Le total estimé pour le fonctionnement simultané de tous les composants est de 8736 mA, soit 8.736 A.

#### Calcul de la Capacité de la Batterie Nécessaire

Pour une autonomie d'une heure, la capacité requise serait de 8.736 Ah. Pour assurer une marge de sécurité, une capacité d'au moins 11 Ah est conseillée.

#### Conclusion

La sélection d'une batterie de 12V et d'au moins 11Ah est essentielle pour couvrir les besoins énergétiques tout en assurant la compatibilité avec les composants.

## Compte Rendu de Projet : Conception d'une Carte PCB pour Robot Tondeuse DIY

### Contexte et Objectifs

Ce projet vise à développer une carte PCB modulaire pour un robot tondeuse DIY. L'objectif est de créer une plateforme robuste et adaptable qui facilite l'intégration et le remplacement des modules en cas de défaillance.

### Recherche et Sélection des Composants

La sélection des composants s'est appuyée sur l'analyse de robots similaires et notre expertise. Les moteurs à courant continu et les motoréducteurs codés ont été choisis pour leur performance en coupe et propulsion. L'ESP32 et le Raspberry Pi ont été retenus pour leur compatibilité et facilité d'intégration.

### Justifications Techniques

Les choix de l'ESP32 et du Raspberry Pi se justifient par leur coût, leur efficacité de prototypage et leur facilité de programmation avec divers capteurs et actionneurs.

### Considérations de Conception et d’Intégration

La conception est segmentée pour clarifier les rôles de l'ESP32 et du Raspberry Pi, simplifiant ainsi le développement et le diagnostic.

### Défis et Solutions

Les principaux défis liés à l'utilisation d'outils comme Altium ont été surmontés grâce à l'apprentissage académique, améliorant notre compréhension des composants.

### Résultats et Apprentissages

L'expérience a enrichi nos compétences en conception électronique, préparant le terrain pour la construction effective du robot et renforçant notre capacité à résoudre des problèmes techniques.

### Conclusion

Le projet a souligné l'importance de la sélection appropriée des composants et de la conception modulaire dans le développement de systèmes robotiques, établissant une fondation pour les futures initiatives.
