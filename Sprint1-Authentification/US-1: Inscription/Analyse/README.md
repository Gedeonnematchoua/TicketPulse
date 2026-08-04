
# Analyse Fonctionnelle - US1 Inscription

## Description

En tant que nouvel utilisateur,
je souhaite créer un compte TicketPulse
afin d'accéder à la plateforme de billetterie.

## Besoins fonctionnels

- L'utilisateur doit pouvoir s'inscrire.
- L'utilisateur doit fournir un courriel valide.
- L'utilisateur doit créer un mot de passe.
- Le système doit enregistrer le compte.
- Le système doit empêcher les doublons de courriel.

## Critères d'acceptation

### CA-1
Étant donné qu'un utilisateur fournit un courriel valide
et un mot de passe valide,

Lorsque l'utilisateur clique sur "S'inscrire",

Alors le compte est créé avec succès.

### CA-2
Si le courriel existe déjà,

Alors le système affiche un message d'erreur.

### CA-3
Le délai de réponse doit être inférieur à 2 secondes.

## Exigences non fonctionnelles

- Sécurité des données.
- Disponibilité élevée.
- Temps de réponse inférieur à 2 secondes.
