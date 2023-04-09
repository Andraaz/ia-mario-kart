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
2.1- Problème ? Le code en hexa ne fonctionne pas...Et d'après ce que j'ai compris. Il peut changer à chaque fois que l'on relance le jeu. Pour la prochaine fois, je chercherais donc à trouver le code hexa soit à l'aide de forum, soit à l'aide d'un logiciel type "cheatEngine" et tricher un peu...

# Deuxième test. À la recherche des adresses ! 09/04/2023 - 9h45

Bon. ça n'a pas été facile, surtout que pour le coup, même chatGpt me disait de la merde et me demandait de fouiller là où ça n'avait pas trop de sens...Il me demendait de passer par cheatEngine pour trouver les adresses, alors que Desmume a un outil pour rechercher les adresses en temps réel (comme cheatEngine quoi. Mais en mieux pour notre partie). Étant donné que je recherchais juste la vitesse pour ce matin (histoire de faire le test), je me suis amusé à rester sur place, cherchais la valeur par 0, avancer, rechercher une valeur supérieur à 0. Bref, en boucle histoire qu'il nous reste 20 adresses. Puis...J'ai procéddé par élimination. Le résultat est concluant et j'ai trouvé ma bonne adresse. Le "hic", c'est que dans mon script LUA, qui devrait m'afficher la vitesse entre -40(marche arrière) et 120 ? (marche avant), il considère la marche arrière comme étant entre 200 et 240. Mais bon, avec une bonne condition dans notre futur code, j'imagine que cela ne sera pas un problème. Reste plus qu'à faire pour nos autres paramètres de "bases" (tourner, et...Sans objets de bases.)


![RAM WATCH](https://user-images.githubusercontent.com/68385783/230762836-9716b773-988e-44a3-917d-85f460431ad2.png)


