Diagramme architecture système et choix de technologie
1. Choix de l'architecture
L'architecture retenu pour notre projet est l’architecture microservices, combinée à une architecture distribuée pour répondre au profil de charge (250 000 utilisateurs simultanés, 50 000 req/s).
Justification en s'appuyant uniquement sur les concepts vus au cours :
- Scalabilité horizontale : on ajoute des instances du service Réservation et Recherche pendant les ventes flash, plutôt que de renforcer une seule machine (scale up), qui est limité et présente un risque de point unique de panne.
- Load balancer : répartit les 50 000 req/s entrantes entre plusieurs instances du service concerné et évite la surcharge d'un seul serveur.
- Cache (Redis) : les recherches d'événements et la consultation des sièges disponibles sont les requêtes les plus fréquentes, les mettre en cache réduit la charge sur la base de données et respecte l'exigence de moins de 2 secondes de réponse.
- Files d'attente (message queue) : l'envoi du courriel de confirmation et la génération du billet QR n'ont pas besoin d'être synchrones, ils sont placés en file d'attente pour renvoyer une réponse immédiate à l'utilisateur.
- Sharding et réplication : la base de données des billets et des sièges est partitionnée par événement, avec réplication pour éviter la perte de données et améliorer la disponibilité.
- CDN : les images d'événements et le contenu statique du site sont livrés depuis un serveur proche de l'utilisateur, réduisant la charge sur les serveurs applicatifs.
- Architecture en couches : reste appliquée à l'intérieur de chaque microservice (présentation, métier, accès aux données)

Compromis : la complexité opérationnelle (surveillance, débogage, cohérence des données) est plus élevée qu'avec un monolithique, mais nécessaire pour respecter la haute disponibilité exigée durant les ventes flash. Un monolithique présenterait un point unique de défaillance inacceptable pour ce scénario critique du sujet.

2. Architecture globale : schéma des composants
Le schéma illustre le flux de requêtes de bout en bout : le client passe par le CDN pour le contenu statique, et par le load balancer puis l'API Gateway pour les requêtes dynamiques, dispatchées vers les quatre microservices. Ceux-ci s'appuient sur le cache et la file d'attente asynchrone avant d'atteindre la base de données partitionnée et répliquée.
 
<img width="975" height="875" alt="image" src="https://github.com/user-attachments/assets/db7a1f80-5acd-4ea0-8e02-6446dc807eb3" />

