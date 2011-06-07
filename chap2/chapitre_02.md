# Installation Erlang

## Linux

### Installation
La façon la plus simple d'installer erlang sous linux est de manière classique via aptitude :

	> apt-get install erlang
	
Il est également possible de le construire depuis les sources.

Par ailleurs Erlang s'installe aussi sous Windows ou MacOS.

### Vérification
Il suffit alors de démarrer un "shell" Erlang en tapant "erl" en ligne de commande :

	> erl
		Erlang R13B03 (erts-5.7.4) [source] [64-bit] [smp:4:4] [rq:4] [async-threads:0] [hipe] [kernel-poll:false]
		
		Eshell V5.7.4  (abort with ^G)
		1> 



# Notions de Base

## Les variables 

### Notation

Les variables en Erlang portent un nom commençant par une majuscule.
Exemple :

	1> MaVariable = 123.
	123
	2> pasVariable = 456.
	** exception error: no match of right hand side value 456

Dans le second cas nous ne commençons pas par une majuscule ce qui entraine une erreur que nous expliciterons plus tard.

### Assignation simple

En Erlang les variables ... ne varient pas ! 
En effet les variables en Erlang sont assignées une fois pour toutes. 

Ainsi le code suivant produira une erreur lorsque nous tenterons de réaffecter une nouvelle valeur à la "variable" : AutreVariable.

	3> AutreVariable = 789.
	789
	4> AutreVariable = 246.
	** exception error: no match of right hand side value 246

Enfin si l'on utilise une variable sans lui avoir assigné une valeur alors une erreur est également levée : 

	5> VariableNonAssignee.
	* 1: variable 'VariableNonAssignee' is unbound

### Explications

En fait l'opérateur = n'est pas un opérateur d'assignation mais un opérateur de "filtrage par motif" (pattern matching), qui agit comme une assignation si la variable à gauche n'a pas de valeur liée.

Ainsi la partie droite (Right Hand Side - RHS) est évaluée et comparée à la partie gauche (LHS - Left Hand Side).

Dans le cas d'une variable sans assignation, Erlang ne peut comparer et rendre son verdict, ainsi pour satisfaire à la demande il lie la variable de gauche à l'expression évaluée de droite et ainsi l'affirmation devient valide.

Un peu déroutant quand on vient d'un autre langage comme Java, mais soit admettons :) 

### Exemples 

	6> Soixante = 12 * 5.
	60	
	7> Trente = 27 + 3.
	30
	8> Trente = 30.
	30
	9> Soixante = Trente.
	** exception error: no match of right hand side value 30
	10> Trente = 60.
	** exception error: no match of right hand side value 60
	11> Soixante = Trente * 2.
	60

### Conclusion 

En Erlang si une variable n'a pas la valeur attendue, on sait immédiatement d'où provient l'erreur puisque l'assignation est unique.
Pas d'effets de bord => parallèlisation des programmes simplifiée.


## Atoms

### Définition

Les "atoms" sont utilisés en Erlang pour représenter des valeurs constantes non numériques.
Les "atoms" sont assez similaires aux Enums en Java.

### Notation

Les "atoms" commencent par une lettre minuscule.
Ceci permet donc de différencier "atoms" et variables.

Les atoms sont alors constitués d'une suite de caractères alphanumériques ainsi que des caractères "@" ou "_" .

### Exemples 

	12> monAtom.
	monAtom
	13> MonAutreAtom.
	* 1: variable 'MonAutreAtom' is unbound



## Tuples

### Définition 

Un "tuple" est un regroupement d'éléments en une seule entité.
Un "tuple" est assez similaire à un "struct" C, à la différence qu'un "tuple est anonyme.

### Notation

Un "tuple" se note avec des accolades pour encadrer ses éléments et des virgules pour les séparer.

### Exemples

L'exemple ci-dessous est un tuple {yann,33} représentant mon prénom et mon age.
Formé d'un "atom" : yann.
Et d'un nombre : 33.
Et l'on peut l'affecter a une variable : Moi.

	1> {yann,33}.
	{yann,33}
	2> Moi = {yann,33}.
	{yann,33}
	3> Moi.
	{yann,33}

Il est possible de combiner des tuples pour arriver a des structures plus complexes.

	4> Famille = {{pere,Moi},{mere,{carine,31}},{fils,{evan,6}}}.
	{{pere,{yann,33}},{mere,{carine,31}},{fils,{evan,6}}}

### Extraction

Les "tuples" ça a l'air sympa... mais comment les exploiter ?
Comment récupérer les valeurs ?

Et bien il faut utiliser l'opérateur =, puisqu'on a déjà dit qu'il agit comme un opérateur de pattern matching et que Erlang tenterait de rendre un égalité vrai.

Ainsi dans les exempls ci-dessous nous affectons a des variables les valeurs des éléments des tuples :

	5> {Papa,Maman,Enfant} = Famille.
	{{pere,{yann,33}},{mere,{carine,31}},{fils,{evan,6}}}
	6> Maman.
	{mere,{carine,31}}
	7> Enfant.
	{fils,{evan,6}}
	8> {_,{Prenom,Age}} = Enfant.
	{fils,{evan,6}}
	9> Age.
	6
	10> Prenom.
	evan


## Listes

## Strings

## Pattern Matching

... A Suivre ...



