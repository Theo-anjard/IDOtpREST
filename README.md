# TP-REST

## Parie 1 : Utilisé la méthode REST

1. J'ai crée un dépôt GIT avec comme nom IDOtpREST
2. Pour ce connecter à la prise connectée shelly, il faut qu'elle soit en mode AP puis si connecter et rentré l'URL suivante. http://192.168.33.1. La puissance de notre halogène est de 50W.
3. Pour pouvoir récupérer la conso de la prise, on utilise la commande suivante : 
curl http://192.168.33.1/relay/0?turn=off ou on si l'on veut allummer la prise.

Pour voir la conso : 
curl http://192.168.33.1/meter/0

4.
```
test@202-16:~/tp_REST$ curl http://10.202.255.252/meter/0 |jq 
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   118  100   118    0     0   6941      0 --:--:-- --:--:-- --:--:--  6941
{
  "power": 0,
  "overpower": 0,
  "is_valid": true,
  "timestamp": 1606215926,
  "counters": [
    48.663,
    48.776,
    46.173
  ],
  "total": 394
}
```


