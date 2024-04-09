## Projet Carte Électronique Robot Tondeuse

### Analyse des Composants

#### Moteurs de Propulsion et de Coupe (Motoréducteurs)
- **Choix** : Les motoréducteurs sont choisis pour leur capacité à fournir un couple élevé nécessaire pour la propulsion et la coupe, avec une consommation de 3600 mA et 800 mA respectivement sous 12V.
- **Justification** : Ces moteurs permettent au robot de se déplacer efficacement sur l'herbe et de couper l'herbe avec la force nécessaire. La tension de 12V est standard et facilite l'intégration avec des batteries couramment disponibles.

#### Accéléromètre/Gyroscope
- **Choix** : Utilisé pour mesurer l'inclinaison et la vitesse du robot, crucial pour naviguer sur des terrains inégaux et éviter le basculement.
- **Justification** : Un courant de fonctionnement de 100 mA sous 5V est raisonnable pour les capacités qu'il offre, aidant à maintenir une bonne autonomie du robot.

#### LED
- **Choix** : Les LED servent d'indicateurs visuels pour le statut du robot (en fonction, en erreur, etc.).
- **Justification** : Leur faible consommation (185 mA sous 5V) les rend idéales pour une utilisation prolongée sans impacter significativement l'autonomie de la batterie.

#### Capteur Fin de Course
- **Choix** : Utilisés pour détecter la collision et le levage, ils jouent un rôle crucial dans la sécurité et la précision du robot.
- **Justification** : Très faible consommation (10 mA sous 5V), ce qui est excellent pour des capteurs qui seront fréquemment activés.

#### Capteur d'Humidité (Hygromètre)
- **Choix** : Important pour déterminer les conditions météorologiques et si le robot peut fonctionner ou doit se mettre en pause.
- **Justification** : Extrêmement faible consommation (1 µA sous 5V), idéale pour une surveillance continue sans affecter l'autonomie.

#### LIDAR
- **Choix** : Essentiel pour la navigation et l'évitement d'obstacles, offrant une cartographie précise de l'environnement.
- **Justification** : Consommation de 180 mA sous 5V, raisonnable pour les capacités avancées de cartographie et de navigation qu'il offre.

#### Ecran LCD 3" & GPS
- **Choix** : L'écran permet une interaction utilisateur pour le paramétrage ou l'affichage de données. Le GPS permet une localisation précise pour le suivi et le traçage de la zone de tonte.
- **Justification** : Faible consommation (20 mA pour l'écran et 16 mA pour le GPS) et tension adaptée à leur usage avec le Raspberry Pi.

### Évaluation et Suggestions

- **Alimentation** : Le choix d'un régulateur abaisseur de tension (buck converter) comme le TPS564257 est judicieux pour gérer efficacement les différentes tensions requises. Assurez-vous que la capacité de la batterie est suffisante pour gérer la consommation globale, surtout des moteurs.
- **Communication et Contrôle** : L'utilisation de l'ESP32 et du Raspberry Pi permet une gestion flexible et puissante des capteurs et des actionneurs. L'ESP32 est idéal pour les tâches en temps réel et le Raspberry Pi pour le traitement complexe et la connectivité.
- **Pont H pour Moteurs** : Nécessaire pour la gestion de la direction et de la vitesse des moteurs. Assurez-vous de choisir un modèle capable de supporter les courants maximaux des motoréducteurs.
- **Améliorations possibles** :
  - **Gestion de l'Énergie** : Envisagez d'ajouter un système de gestion de l'énergie pour optimiser l'autonomie, notamment en mettant en veille certains composants non utilisés.
  - **Capteurs Supplémentaires** : Pour une meilleure adaptation aux environnements complexes, envisagez d'ajouter des capteurs supplémentaires (par exemple, capteurs de sol pour détecter différents types de terrains).

### Bilan Énergétique

Pour évaluer le bilan énergétique du robot tondeuse, nous allons estimer la consommation totale d'énergie basée sur les composants énumérés et calculer la capacité de batterie nécessaire pour une autonomie souhaitée.

#### Estimation de la Consommation

- **Moteurs de Propulsion** : \(2 \times 3600 \, \text{mA} = 7200 \, \text{mA}\)
- **Moteur de Coupe** : \(800 \, \text{mA}\)
- **Accéléromètre/Gyroscope** : \(100 \, \text{mA}\)
- **LEDs** : \(2 \times 185 \, \text{mA} = 370 \, \text{mA}\)
- **Capteurs Fin de Course** : \(5 \times 10 \, \text{mA} = 50 \, \text{mA}\)
- **Capteur d'Humidité** : \(1 \, \text{µA} \approx 0 \, \text{mA}\) (négligeable)
- **LIDAR** : \(180 \, \text{mA}\)
- **Ecran LCD** : \(20 \, \text{mA}\)
- **GPS** : \(16 \, \text{mA}\)

Le courant total estimé pour le fonctionnement simultané de tous les composants est donc :

\[
7200 \, \text{mA} + 800 \, \text{mA} + 100 \, \text{mA} + 370 \, \text{mA} + 50 \, \text{mA} + 180 \, \text{mA} + 20 \, \text{mA} + 16 \, \text{mA} = 8736 \, \text{mA} \, (ou \, 8.736 \, \text{A})
\]

#### Calcul de la Capacité de la Batterie Nécessaire

Pour une autonomie souhaitée de, disons, 1 heure (60 minutes), la capacité de la batterie nécessaire peut être calculée comme suit :

\[
\text{Capacité} = \text{Courant Total} \times \text{Durée} = 8.736 \, \text{A} \times 1 \, \text{heure} = 8.736 \, \text{Ah}
\]

Pour garantir une marge de sécurité et prendre en compte les inefficacités et les variations de consommation, il est conseillé d'augmenter cette valeur de 20% à 30%. Ainsi, une capacité de batterie d'au moins :

\[
8.736 \, \text{Ah} \times 1.25 \approx 11 \, \text{Ah}
\]

serait recommandée pour une autonomie d'une heure.

#### Conclusion

Il est crucial de choisir une batterie avec une capacité suffisante pour répondre à la demande énergétique du robot, tout en prenant en compte la tension requise par les composants. Une batterie de 12V, 11Ah ou plus, serait idéale pour ce projet.
