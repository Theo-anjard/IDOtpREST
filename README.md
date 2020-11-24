# TP-REST

## Parie 1 : Utilisé la méthode REST

1. J'ai crée un dépôt GIT avec comme nom IDOtpREST
2. Pour ce connecter à la prise connectée shelly, il faut qu'elle soit en mode AP puis si connecter et rentré l'URL suivante. http://192.168.33.1. La puissance de notre halogène est de 50W.
3. Pour pouvoir récupérer la conso de la prise, on utilise la commande suivante : 
curl http://192.168.33.1/relay/0?turn=off ou on si l'on veut allummer la prise.

Pour voir la conso : 
curl http://192.168.33.1/meter/0

4. Grâce à jq, le tout est lisible
```bash=
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
5. Les scrips ont été crée et son disponible dans ce reposiroty.

6. Les trames suivantes montrent les intéractions entre la prise et notre pc.

Si l'on veut allumer la prise : 
La trame 409 un une requête du pc à la prise en HTTP, on le voit dans les infos et celle-ci fait 147 octets
```
No.     Time           Source                Destination           Protocol Length Info
    409 66.005511322   10.202.16.1           10.202.255.252        HTTP     147    GET /relay/0?turn=on HTTP/1.1 

Frame 409: 147 bytes on wire (1176 bits), 147 bytes captured (1176 bits) on interface 0
Internet Protocol Version 4, Src: 10.202.16.1, Dst: 10.202.255.252
```
La 411 est une réponse de la prise nous disant qu'elle a bien reçu notre demande la trame fait 290 octets.
```
No.     Time           Source                Destination           Protocol Length Info
    411 66.024851318   10.202.255.252        10.202.16.1           HTTP     290    HTTP/1.1 200 OK  (application/json)

Frame 411: 290 bytes on wire (2320 bits), 290 bytes captured (2320 bits) on interface 0
Internet Protocol Version 4, Src: 10.202.255.252, Dst: 10.202.16.1
``` 
Si l'on veut l'éteindre les trames sont les suivantes :
La trame est plus importante en terme d'octet ici 148 pour l'envoie et 291 pour la réponse à la requête.
```
No.     Time           Source                Destination           Protocol Length Info
     37 6.610185078    10.202.16.1           10.202.255.252        HTTP     148    GET /relay/0?turn=off HTTP/1.1 

Frame 37: 148 bytes on wire (1184 bits), 148 bytes captured (1184 bits) on interface 0
Internet Protocol Version 4, Src: 10.202.16.1, Dst: 10.202.255.252
```
```
No.     Time           Source                Destination           Protocol Length Info
     38 6.624583160    10.202.255.252        10.202.16.1           HTTP     291    HTTP/1.1 200 OK  (application/json)

Frame 38: 291 bytes on wire (2328 bits), 291 bytes captured (2328 bits) on interface 0
Internet Protocol Version 4, Src: 10.202.255.252, Dst: 10.202.16.1
```
Il ne faut pas oublié qu'ici nous ne regardons que les trames HTTP, alors que en amont et en aval un dialogue TCP est en cours entre nos deux machines.
Les octets pour la totalité d'une communication sont donc beaucoup plus important.

## Parie 2 : MQTT

Les scripts serons à voir dans le tag partie 2.






