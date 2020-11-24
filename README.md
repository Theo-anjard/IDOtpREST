# TP-REST

## Parie 1 : Utilisé la méthode REST

1. J'ai crée un dépôt GIT avec comme nom IDOtpREST
2. Pour ce connecter à la prise connectée shelly, il faut qu'elle soit en mode AP puis si connecter et rentré l'URL suivante. http://192.168.33.1. La puissance de notre halogène est de 50W.
3. Pour pouvoir récupérer la conso de la prise, on utilise la commande suivante : 
curl http://192.168.33.1/relay/0?turn=off ou on si l'on veut allummer la prise.

Pour voir la conso : 
curl http://192.168.33.1/meter/0

4.


