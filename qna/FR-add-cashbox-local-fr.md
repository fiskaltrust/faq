## Question
Comment créer une CashBox (local) ?

## Metadata tags
lang-fr, market-fr, middleware, PosCreator, PosDealer, PosOperator, Consultant

## Answer
Pour créer une CashBox, certaines conditions doivent être remplies au préalable : 

Un numéro de SIREN valide doit être saisi et contrôlé dans les données de base de l’entreprise.
Un Etablissement valide doit être enregistré. Pour cela, l’adresse de l’établissement et son numéro de SIRET doivent être saisis et vérifiés. 
Une fois ces deux conditions remplies, une Cashbox peut être créée en 5 étapes. 

**1ère étape :**<br>Créez une unité de création de signature (Signature creation unit, SCU) dans le menu Configuration. Lors de la création, vous devez sélectionner le bon établissement. 

**2ème étape :**<br>Allez dans le menu de configuration et ouvrez la commande “Queue”. En cliquant sur le bouton “Créer”, vous débutez la création. Acceptez le SQLite-Package présélectionné. La version du package doit être celle du dernier package 1.2 (sans le suffixe “-dev”). La localisation doit être la même que celle sélectionnée lors de l’étape précédente. Ajoutez une CashBoxId unique. 

Enregistrez cette configuration et ajoutez dans la fenêtre suivante une URL http, sans modifier aucune des autres valeurs. Enregistrez la configuration. 

**3ème étape :**<br>Recherchez la queue récemment créée dans la liste. Sur le côté droit se trouve quatre boutons de configuration, cliquez sur le premier (le rectangle avec la flèche). Choisissez ensuite le SCU que vous avez créé lors de la première étape et cliquez sur Enregistrer et fermer. 

Soyez extrêmement prudent lors de cette étape, en effet il sera impossible de modifier la SCU de cette queue à l’avenir. 

**4ème étape :**<br>
Dans la commande CashBox du menu de configuration, vous devez cliquer sur le bouton “+ Ajouter“. Saisissez une description et choisissez à nouveau la même prise que dans les étapes précédentes. Après avoir cliqué sur enregistrer, vous trouverez une nouvelle CashBox dans la liste. Cliquez sur le bouton avec la main dessus. Faites maintenant glisser la file d’attente récemment créée de gauche à droite. Vérifiez si la prise correcte est sélectionnée et cliquez sur enregistrer. 

**5ème et dernière étape :**<br>
Cliquez sur le bouton rebuild configuration (flèches circulaires) à droite dans la ligne de la CashBox. 

Vous pouvez maintenant télécharger l’un des trois “Launcher” et installer fiskaltrust.Middleware sur votre machine locale. 
