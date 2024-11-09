---
layout: post
title: 'La topologie'
date: 2024-11-05 19:00:00 +0200
tags: Modélisation Théorique
featured_image: /images/topology-hero.jpg
---

Étude de la topologie polygonale. Et de pourquoi dans chaque les sous domaines de la 3D, une compréhension même basique de la topologie est essentielle.

<p class="hero-image">
<img src="/images/topology-hero.jpg" alt="Deux feuilles ornementales représentées en 3D">
</p>

## La topologie polygonale

Ok, aujourd'hui on parle de topologie. Si vous avez déjà joué à un jeu vidéo en 3D, regardé un pixar, ou même juste ouvert un logiciel de modélisation 3D, vous y avez été exposé.  
Selon [wikipedia](https://fr.wikipedia.org/wiki/Topologie) :

_La topologie est la branche de la géométrie qui étudie les propriétés d'objets géométriques préservées par déformation continue sans arrachage ni recollement, comme un élastique que l'on peut tendre sans le rompre._

Cet article est orienté vers la topologie dans le monde de la 3D en général, avec un petit accent sur la modélisation polygonale. Le but est de démystifier tout ça, en partant des bases pour essayer de perdre personne en chemin.

### Qu'est ce qu'un polygone ?

Pour pouvoir ensuite parler de flow, de subdivisions, patati patata, il va falloir commencer par expliquer comment un ordinateur voit et calcul un model 3D, pour ensuite l'afficher. Oui même les logiciels de CAD (Solidworks, Catia, etc) utilisent des polygones pour afficher les modèles. C'est dans le fonctionnement même des cartes graphiques (on pourra parler dans un autre article du fonctionnement d'une carte graphique tiens, je note).

En gros, pour un ordinateur, tout n'est qu'un gros tas de sommets (**vertex**), placés dans l'espace.
_Important parce que ça me gonfle; on dit UN vertex et DES vertices. Merci._
Ces sommets sont ensuite reliés entre eux par des segments, les **edges**.
Lorsque trois sommets sont reliés entre eux par des segments, on obtient un **triangle**, une **face**. C'est la forme géométrique plane qui contient le moins de vertices, la forme parfaite par excellence. Un tabouret à quatre pieds, c'est bancal, alors qu'un tabouret à trois pieds sera toujours stable.

Tout ce que calcul et affiche un ordinateur en 3D est en réalité composé d'une multitude de triangles, qui côte à côte permettent de représenter n'importe quelle forme.

![Visuel de trois cubes](/images/cube.jpg)
_Vertice, edges, faces. Un cube, c'est 8 vertices, 12 edges et 6 faces._

La c'est le moment ou vous m'enguelez parce que "gnagnagni, Gaëtan tu nous parles de triangles depuis tout à l'heure, et la tu nous montre un cube avec que des face à 4 sommets". Oui, c'est vrai, mais un carré (ou n'importe quel un quadrilatère), ce n'est au final que deux triangles qui s'aiment tellement qu'ils ont fusionnés. C'est ce qu'on appelle un **quad**. Gardez bien ce terme en tête, on va pas mal en reparler.

Maintenant les plus brillants d'entre vous se posent la question suivante "ce qu'il se passe si on a plus de 4 sommets sur une face". Paf, entre le **n-gone**. Et alors les n-gones c'est controversé, certains vous diront qu'il faut les fuir comme la peste, d'autres qu'il faut pas se prendre la tête, si ça marche ça marche.  
Il est pas forcément mauvais, mais il est pas forcément bon non plus. Il est juste là, à te regarder, et il va falloir faire avec.

_Pour résumer; quelque soit l'objet, l'ordinateur va tout réduire sous forme de triangles pour l'afficher. C'est pour ça que la topologie est importante, car elle va déterminer comment l'objet va être **subdivisé** en triangles par la suite._

### Les différents workflows

Avant de commencer la création il faut savoir, en fonction de ce que l'on veut faire, quel workflow est le plus adapté. Modélisation low poly, hard surface, assets pour du jeu vidéo, rendu d'architecture... Chaque domaine à des contraintes propres, et donc des workflows très différents.  
Sans rentrer dans trop de détails, voici quatre grandes familles (il y en a d'autres) de comment qu'on fait pour avoir un model 3D:

- **Modélisation polygonale**
- **Sculpture digitale**
- **NURBS**

Je vais pas m'atarder sur les NURBS et la sculpture digitale
