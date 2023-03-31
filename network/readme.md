# Transfert DNS

Le but ici est de trouver une balise cachée dans un DNS.

## plusieurs façons existent, la première en utilisant la commande DIG : 

```
dig [adress] [server] -p [PORT] any 
```
Cette commande retourne les informations relatives au DNS tel que : 
```bash
;; global options: +cmd
[server] 604800 IN SOA     ......................
[server] 604800 IN TXT     "DNS transfer secret key : xxxx"
[server] 604800 IN NS      ......................
[server] 604800 IN A       127.0.0.1
[server] 604800 IN A 192.168.27.101
[server] 604800 IN SOA     ......................
;; Query time: 33 msec
;; SERVER:......................(188.165.33.26)
;; WHEN: Mon May 20 19:31:28 2013
;; XFR size: 6 records (messages 1, bytes 235)
```
## Seconde méthode : 

Avec la commande nslookup de cette manière :

```
#nslookup
>set port=[port]
>set type=any
>server [server]
```
et on retrouve également le flag : `...............    text = "DNS transfer secret key : CBkFRwfNMMtRjHY"`
