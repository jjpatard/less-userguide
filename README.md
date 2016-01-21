#LESS

##Introduction

LESS est un langage dynamique de génération de feuilles de style [...]. 
LESS est implémenté en open source. [...] Une particularité de LESS par rapport aux autres préprocesseurs CSS est qu'il peut être compilé à la volée, soit lors du rendu par le navigateur, soit côté serveur. Il peut également être compilé à l'avance en un simple fichier CSS. 
[source : wikipedia](https://fr.wikipedia.org/wiki/LESS_(langage))

##Préprocesseur CSS

LESS est un préprocesseur CSS, c'est à dire un outil qui compile une syntaxe spécifique afin de générer du CSS. Et, comme tout préprocesseur, quelques mises en garde doivent être faites :

* LESS n'ajoute pas de fonctionnalités CSS
* LESS ne masque pas la complexité des CSS
* LESS ne remplace pas les bonnes pratiques de codage CSS
* LESS n'est pas systématiquement à mettre en oeuvre sur un projet Web

Mais, alors, que permet LESS ? LESS introduit des fonctionnalités proches d'un langage de programmation. Ces fonctionnalités vont permettre de réaliser des feuilles de styles plus maintenables, extensibles et évolutives.

##Fonctionnalités principales

Les fonctionnalités les plus couramment utilisées sont abordées dans cet article. Ne sera pas vu la notion d'import puisqu'elle est, à peu de chose près, identique à celle rencontrée en CSS. 

Si vous souhaitez approfondir ces notions, vous pourrez consulter [la liste complète des fonctionnalités](http://lesscss.org/features/) et [la liste des fonctions intégrées au langage LESS (Math, Color...)](http://lesscss.org/functions/).

###Variables

Les variables LESS évitent la duplication d'information et permettent uné réutilisation de la feuille de style sur d'autres projets :

	// Variables
	@link-color:        #FF6600; // Orange
	@link-color-hover:  darken(@link-color, 10%);

	//utilisation
	a{
		color: @link-color;
		&:hover{
			color: @link-color-hover;
		}
	}

###Mixins

Les mixins sont en quelque sorte des fonctions. Ils possèdent une syntaxe, soit proche d'une fonction (avec parenthèses et paramètres), soit proche d'un sélecteur CSS (sans parenthèses). Les mixins permettent de mutualiser des règles de styles (et ainsi obtenir un code DRY) :

	.orange{
		color: #FF6600;
	}

	p{
		.orange;//utilisation d'un mixin sans parenthèses
	}

###Sélecteurs LESS

En étendant la notion de sélecteurs CSS, LESS proposent d'une part de rédiger les styles par imbrication de sélecteurs, d'autre part d'utiliser un sélecteur dit "parent" pour ajouter des règles spécifiques (par  héritage).

	//Exemple de sélecteur imbriqué
	.mod{
		color: #FF6600;
		.inner{
			margin: 10px;
		}
	}
	
	//Exemple de sélecteur parent (identifiable par un '&')
	.message{
		font-family: Arial;
		&.error{
			color: #C00;
		}
		&.warn{
			color: #FC0;
		}
	}
	
##Outils

###Utiliser un soft pour éditer du LESS

Les éditeurs et IDEs les plus connus supporte LESS, nativement ou sous forme de plugins, proposant une coloration syntaxique du code. Vous pouvez consulter la liste [ici](http://lesscss.org/usage/#editors-and-plugins).

###Utiliser less.js pour tester la transformation en CSS

Il s'agit d'un Javascript très utile dont le rôle est d'ajouter dynamiquement des balises HTML de type  &lt;link rel="stylesheet"&gt; et d'y inclure le code CSS compilé à partir de LESS.

1- Ajouter la ligne suivante dans l'entête de la page HTML :

    <link href="app.less" type="text/css" rel="stylesheet/less">
2- Ajouter la ligne suivante dans une page HTML (head ou body) : 

    <script src="https://cdnjs.cloudflare.com/ajax/libs/less.js/2.5.3/less.min.js"></script>
    
###Utiliser un task runner pour compiler du LESS

La génération CSS à partir de LESS peut être réalisée à partir d'un "task runner". [Grunt](http://gruntjs.com/) et [Gulp](http://gulpjs.com/) sont les plus connus. [Grunt LESS](https://github.com/gruntjs/grunt-contrib-less) et [Gulp LESS](https://github.com/plus3network/gulp-less) sont des extensions embarquant un compilateur LESS et sont exécutables via un éditeur ou en ligne de commande.

###Utiliser un soft pour compiler du LESS
Ce n'est pas l'approche à priviligier pour un développeur (voir les task runners). De nombreux utilitaires LESS sont disponibles pour Windows, Linux et Mac. Vous pouvez consulter la liste [ici](http://lesscss.org/usage/#guis-for-less).

##Ressources

* [LESS](http://lesscss.org/)
* [Grunt LESS](https://github.com/gruntjs/grunt-contrib-less)
* [Gulp LESS](https://github.com/plus3network/gulp-less)
* [Bootstrap en version LESS](https://github.com/twbs/bootstrap/tree/master/less)

##Historique

* 2016-01-21 : versionné sous GIT