# Cyber Kali — site de téléchargement

Le site est une page statique hébergée sur GitHub Pages. Le bouton APK et le compteur utilisent l'API publique des releases de `Abdoul273/cyber-kali-site`. Le compteur additionne les téléchargements des fichiers `cyber-kali.apk` des releases publiques (jusqu'aux 100 dernières) et se rafraîchit toutes les 90 secondes quand la page est visible. Les chiffres viennent de GitHub, pas des clics sur le bouton.

Les avis et les notes utilisent `https://abdoul.pythonanywhere.com/api/site/reviews`, implémenté dans `../flutter_kali_cours/server/app.py`. Cette route doit être déployée sur PythonAnywhere **avant** la publication du site : les avis ne fonctionneront pas sur le serveur distant tant que son code n'aura pas été mis à jour et l'application rechargée. Conserver le même fichier SQLite (`LICENSE_DB_PATH`) pour préserver les avis. Configurer un `SECRET_KEY` privé et stable.

Vérification après déploiement :

1. `GET https://abdoul.pythonanywhere.com/api/site/reviews` doit renvoyer `count`, `average` et `reviews`.
2. Publier une release contenant `cyber-kali.apk` pour activer le bouton et alimenter le compteur GitHub.
3. Ouvrir le site dans deux navigateurs : publier un avis dans le premier et vérifier son apparition dans l'autre dans les 15 secondes.

Si l'URL de l'API change, modifier la constante `API` en bas de `index.html`.
