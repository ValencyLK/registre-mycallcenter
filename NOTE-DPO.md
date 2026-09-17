1\. l’état du registre : combien de traitements recensés, lesquels ? 



Le registre comprend actuellement 3 traitements de données personnelles recensés :  Enregistrement de l'appel téléphonique.  Saisie des réponses et stockage dans la base de données (étude de marché).  Sauvegarde et archivage des enregistrements audio sur le serveur de fichiers.  



2.la durée de conservation retenue pour OP-01, et la source qui la justifie ?



La durée de conservation retenue pour les enregistrements d'appels (DP-01) est de 6 mois maximum.  Source justificative : Cette durée s'appuie sur la fiche pratique de la CNIL intitulée « L'écoute et l'enregistrement des appels sur le lieu de travail ». Elle précise que les enregistrements ne peuvent être conservés au-delà de cette limite, sauf cas particuliers, et que les documents d'analyse ne doivent pas être gardés plus de 3 mois.



3.comment le dépôt permet de prouver qui a déclaré quoi et quand (citez les commandes) ?



L'utilisation de Git garantit le principe d'accountability (article 5.2 du RGPD) en bannissant les fichiers Word statiques échangés par mail. Le dépôt permet de prouver l'historique grâce à deux commandes clés :  git log --oneline --graph : Permet de visualiser l'historique complet des modifications, la chronologie des versions et d'identifier clairement les différents points de fusion (commits) entre collaborateurs.  git blame registre.csv : Permet d'inspecter le fichier ligne par ligne pour attribuer précisément chaque traitement à son auteur exact, avec le hash du commit et la date précise de l'insertion. 



4\. la limite identifiée à l’étape 5, et ce qu’il faudrait pour la lever.



Limite actuelle : La colonne « auteur » de la commande git blame se base uniquement sur l'identité déclarée localement par l'utilisateur via la commande git config user.name. Si un utilisateur malveillant configure son nom en indiquant "le DPO", Git l'enregistrera sous cette fausse identité. Cette preuve n'est donc pas infaillible par défaut.  Solution pour lever cette limite : Pour garantir de manière absolue l'identité de l'auteur, il est nécessaire de mettre en place une signature cryptographique des commits (à l'aide de clés GPG ou de modules RSA), ce qui permettra d'authentifier formellement chaque soumission.





