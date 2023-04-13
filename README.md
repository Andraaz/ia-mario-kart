# ia-mario-kart

#Description du projet 

Projet personnel qui a pour but d'utiliser l'apprentissage renforcé sur le jeu mario kart (DS). Étant en plein 
apprentissage dans le domaine(l'IA), il y a de fortes chances que je me mange des murs...Je les noterais tout au 
long de ce readme tel un petit journal de bord. À la fin de mon projet je ferais bien entendu un fichier "conclusion.md" qui a pour but d'expliquer le procéder, mais également la "logique" de manière rapide, simple, concis. Pour ce qui est de ce readme...Il faut plus le voir comme un défouloir pour ma pensée, à défaut d'avoir quelqu'un à qui partager l'un de mes loisirs.

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

Bon. ça n'a pas été facile, surtout que pour le coup, même chatGpt me disait de la merde et me demandait de fouiller là où ça n'avait pas trop de sens...Il me demendait de passer par cheatEngine pour trouver les adresses, alors que Desmume a un outil pour rechercher les adresses en temps réel (comme cheatEngine quoi. Mais en mieux pour notre partie). Étant donné que je recherchais juste la vitesse pour ce matin (histoire de faire le test), je me suis amusé à rester sur place, cherchais la valeur par 0, avancer, rechercher une valeur supérieur à 0. Bref, en boucle histoire qu'il nous reste 20 adresses. Puis...J'ai procéddé par élimination. Le résultat est concluant et j'ai trouvé ma bonne adresse. Le "hic", c'est que dans mon script LUA, qui devrait m'afficher la vitesse entre -40(marche arrière) et 120 ? (marche avant), il considère la marche arrière comme étant entre 200 et 240. Mais bon, avec une bonne condition dans notre futur code, j'imagine que cela ne sera pas un problème. Reste plus qu'à faire pour nos autres variables d'environement (tourner, et...Sans objets de bases.)


![RAM WATCH](https://user-images.githubusercontent.com/68385783/230762836-9716b773-988e-44a3-917d-85f460431ad2.png)

Je me suis fait un tableau de ce que je devais rechercher en plus des contrôles de base du véhicule. 

| Environnement     | Type  | Description                                   |
|-------------------|-------|-----------------------------------------------|
| Vitesse           | int   | Avancer, reculer                              |
| Tourner à droite  | int   | Angle                                         |
| Tourner à gauche  | int   | Angle                                         |
| Carte ?           | List  | ??? Comment indiquer les obstacles ?          |
| Position          | List  | Position du joueur sur la carte ? sur X,Y,Z ? |
| Ligne d'arrivée   | List  | Position de la ligne d'arrivée                |

  
# Troisième test. Position X,Y introuvable ! 10/04/2023 - 11h05 

Je dois avouer que je bloque. À la base, je cherchais à coordonner la première map du jeu...Mais ce fut bien trop difficile. Alors je me suis dit que juste la position du joueur serait suffisant. Après tout, si dans mes récompenses j'indique que baisser de vitesse fait perdre des points, alors à force de se manger des murs, il "s'inventera" sa propre carte, non ? 
Quoi qu'il en soit, je n'arrive pas à trouver la position X et Y du joueur quelque soit la map.

# Quatrième test. On a l'environnement ! Enfin...Le strict minimum ! 13/04/2023 - 22h27

Bon, je pensais que cela allait être impossible, mais en regardant de plus près, j'ai réussi ce que je pensais être l'axe Y. L'axe X de son côté, me semble peu cohérent...(Valeur à environ 200 sur la ligne de départ ?). D'ailleurs, en prime j'ai par hasard trouvé le pourcentage de la course (plus vous vous rapproché de la ligne d'arrivé, plus la valeur augmente, et inversement). Autant dire que c'est une adresse en or pour calculer les récompenses ! Voilà le fichier LUA que j'ai rédigé. Comme je l'ai écrit, c'est le strict minimum. Pas d'item, de dérapage, etc...Pour la prochaine fois, je chercherais comment relier ce LUA à un fichier python pour commencer le gros du code.

![Capture d'écran 2023-04-13 224032](https://user-images.githubusercontent.com/68385783/231878252-7daf1288-dd88-4067-989d-fd00c962941b.png)

