Analyse fonctionnelle — US-6 : Effectuer le paiement
Description

Un utilisateur ayant déjà sélectionné et réservé temporairement un siège doit pouvoir effectuer le paiement afin de confirmer définitivement sa réservation.

Le paiement constitue une étape distincte de la réservation du siège. Le paiement doit etre sécurisé, une finalisation du paiement en moins de 5 minutes et l’absence de double vente d’un même siège.

Besoins fonctionnels: 

L’utilisateur doit pouvoir accéder au paiement à partir d’une réservation temporaire valide.

Le système doit afficher le récapitulatif de la réservation avant le paiement : évènement, siège sélectionné et montant à payer.

L’utilisateur doit pouvoir saisir ou sélectionner un moyen de paiement valide.

Le système doit transmettre la demande de paiement au service de paiement externe.

Le système doit recevoir et traiter le résultat de la transaction.

Si le paiement est accepté, le système doit enregistrer la transaction et confirmer définitivement la réservation.

Si le paiement est refusé ou échoue, le système doit informer l’utilisateur et ne doit pas confirmer définitivement la réservation.

Le système doit empêcher qu’une même réservation soit payée plusieurs fois.

Le paiement doit être effectué avant l’expiration de la réservation temporaire.  Dans le parcours déjà défini, le siège passe de verrouillé temporairement à confirmé après un paiement réussi.

Critères d’acceptation:

CA-1 — Paiement réussi

Étant donné qu’un utilisateur possède une réservation temporaire valide,
lorsqu’il fournit des informations de paiement valides et confirme le paiement,
alors le système traite la transaction avec succès, enregistre le paiement et confirme définitivement la réservation.

CA-2 — Paiement refusé

Étant donné qu’un utilisateur tente d’effectuer un paiement,
lorsque le service de paiement refuse la transaction,
alors le système affiche un message d’erreur et la réservation ne doit pas être confirmée comme payée.

CA-3 — Réservation expirée

Étant donné que la réservation temporaire n’est plus valide,
lorsque l’utilisateur tente d’effectuer le paiement,
alors le système doit refuser le paiement associé à cette réservation et informer l’utilisateur que le siège n’est plus réservé.

CA-4 — Double paiement

Étant donné qu’une réservation a déjà été payée avec succès,
lorsqu’une nouvelle tentative de paiement est effectuée pour cette même réservation,
alors le système doit empêcher une seconde transaction.

CA-5 — Délai de paiement

Le processus de paiement doit pouvoir être finalisé dans un délai maximal de : 5 minutes
	​

Exigences non fonctionnelles:

Le paiement doit être réalisé de manière sécurisée.

Le système doit protéger les informations sensibles liées au paiement.

La finalisation du paiement doit être possible en moins de 5 minutes.

Le temps de réponse doit rester inférieur à 2 secondes pour la majorité des requêtes.

Le système doit rester disponible pendant les périodes de forte affluence, pouvant atteindre 250 000 utilisateurs simultanés et 50 000 requêtes par seconde.

Le traitement du paiement doit garantir la cohérence des données : un paiement réussi ne doit correspondre qu’à une seule réservation et un siège ne doit jamais être vendu deux fois.
