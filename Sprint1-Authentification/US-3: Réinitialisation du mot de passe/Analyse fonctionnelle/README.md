ANALYSE FONCTIONNELE

DESCRIPTION

Lorsqu'un utilisateur inscrit oublie son mot de passe, il doit pouvoir réinitialiser ses paramètres de connexion en créant un nouveau mot de passe afin d'accéder à la plateforme.

EXIGENCES FONCTIONNELLES
- L'utilisateur doit pouvoir cliquer sur "Mot de passe oublié".
- L'utilisateur doit fournir une adresse courriel valide.
- Le système doit vérifier que le compte existe.
- Le système doit envoyer un code de réinitialisation d'une durée de 5 minutes
- L'utilisateur doit pouvoir créer un nouveau mot de passe en respectant les mêmes exigences qu'à la création du compte et confirmer ce mot de passe en l'entrant de nouveau, identiquement au précédent.
- Le système doit mettre à jour le mot de passe dans la base de données.

CRITÈRES D'ACCEPTATION

CA-1

Après avoir cliqué sur mot de passe oublié, l'utilisateur doit entrer son adresse courriel. Le système envoie à cet adresse un code de validation d'une durée de 5 minutes pour réinitialiser son mot de passe.

CA-2

Après avoir valider le lien en entrant le code, l'utilisateur doit saisir dans un nouvel interface son nouveau mot de passe en respectant les exigences de création de mot de passe. Le système met à jour le mot de passe. L'interface de connexion s'affiche.

CA-3

Si le courriel n'existe pas, alors un message d'erreur est affiché.

CA-4

Message d'erreur si l'utilisateur valide le lien après expiration.

CA-5

Message d'erreur lorsque le nouveau mot de passe ne respecte pas les exigences de création de mot de passe ou que les deux mots de passe à la création ne correspondent pas.

EXIGENCES NON FONCTIONNELLES
- Temps de réponse inférieur à 2 secondes.
- hachage et sécurisation maximale du mot de passe.
- Journalisation des demandes de réinitialisation.

