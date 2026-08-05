Analyse fonctionnelle — Écran de connexion TicketPulse
Description

Un utilisateur possédant déjà un compte TicketPulse doit pouvoir se connecter à la plateforme de billetterie afin d’accéder à son espace personnel, consulter les événements, réserver des sièges et gérer ses billets.

Besoins fonctionnels

L’utilisateur doit pouvoir se connecter en fournissant :

son nom d’utilisateur ou son adresse courrielle;
son mot de passe.

Le système doit :

vérifier que tous les champs obligatoires sont remplis;
vérifier que le compte existe;
vérifier que le mot de passe fourni correspond au compte;
authentifier l’utilisateur lorsque les informations sont valides;
créer une session sécurisée après l’authentification;
rediriger l’utilisateur vers la page principale ou son espace personnel;
refuser la connexion lorsque les informations sont incorrectes;
afficher un message d’erreur sans révéler si le courriel, le nom d’utilisateur ou le mot de passe est incorrect;
permettre à un nouvel utilisateur d’accéder à l’écran d’inscription;
permettre à l’utilisateur d’accéder à la procédure de récupération du mot de passe, lorsque cette fonctionnalité est prévue.

Critères d’acceptation:

CA-1 — Connexion réussie

Étant donné qu’un utilisateur possède un compte actif et fournit un nom d’utilisateur ou un courriel valide ainsi que le bon mot de passe,
lorsque l’utilisateur clique sur « Se connecter »,
alors le système l’authentifie et le redirige vers la plateforme TicketPulse.

CA-2 — Informations incorrectes

Étant donné que le nom d’utilisateur, le courriel ou le mot de passe fourni est incorrect,
lorsque l’utilisateur clique sur « Se connecter »,
alors le système refuse la connexion et affiche un message d’erreur général.

CA-3 — Champs obligatoires manquants

Étant donné qu’un ou plusieurs champs obligatoires sont vides,
lorsque l’utilisateur clique sur « Se connecter »,
alors le système ne soumet pas la demande et indique les champs à remplir.

CA-4 — Accès à l’inscription

Étant donné que l’utilisateur ne possède pas encore de compte,
lorsque celui-ci sélectionne l’action « S’inscrire » ou « Créer un compte »,
alors le système le redirige vers l’écran d’inscription.

CA-5 — Mot de passe oublié

Étant donné que l’utilisateur a oublié son mot de passe,
lorsque celui-ci clique sur « Mot de passe oublié »,
alors le système le redirige vers la procédure de récupération du mot de passe.

CA-6 — Déconnexion ou expiration de session

Étant donné que la session de l’utilisateur est expirée ou qu’il s’est déconnecté,
lorsqu’il tente d’accéder à une page protégée,
alors le système le redirige vers l’écran de connexion.

Exigences non fonctionnelles

Sécurité:
Les données de connexion doivent être transmises au moyen d’une connexion chiffrée.
Le mot de passe ne doit jamais être affiché en clair.
Les mots de passe doivent être conservés sous une forme protégée dans le système.
La session créée après la connexion doit être sécurisée.
Le système doit limiter les tentatives répétées de connexion afin de réduire les risques d’attaque.
Le message d’erreur ne doit pas confirmer l’existence d’un compte précis.

Disponibilité:   le système d’authentification doit être disponible à au moins 99,9 %.

Performance: le système doit traiter une demande de connexion et afficher une réponse en moins de 2 secondes dans les conditions normales d’utilisation.

Utilisabilité:
Les champs doivent être clairement identifiés.
Le bouton « Se connecter » doit être visible.
Les erreurs doivent être compréhensibles.
L’utilisateur doit pouvoir masquer ou afficher temporairement son mot de passe.
L’écran doit être utilisable sur ordinateur, tablette et téléphone.
