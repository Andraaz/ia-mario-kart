# ia-mario-kart

#Description du projet 

Projet personnel qui a pour but d'utiliser l'apprentissage renforcé sur le jeu mario kart (DS). Étant en plein 
apprentissage dans le domaine(l'IA), il y a de forte chance que je me mange des murs...Je les noterais tout au 
long de ce readme.

## Premier test. 08/04/2023 -- 22h40

1- J'ai téléchargé l'émulateur Desmume et la ROM mario Kart 
2- J'ai crée du code Lua : 
```lua
x = memory.readbyte(0x02066A18)
y = memory.readbyte(0x02066A1C)
speed = memory.readbyte(0x02066A20)
print("Position: (" .. x .. ", " .. y .. ")")
print("Vitesse: " .. speed)
```
    2.1- Problème ? Le code en hexa ne fonctionne pas...Et
    d'après ce que j'ai compris. Il peut changer à chaque fois que l'on relance le jeu. Pour la prochaine fois, je chercherais donc à trouver le code hexa soit à l'aide de forum, soit à l'aide d'un logiciel type "cheatEngine" et tricher un peu...



