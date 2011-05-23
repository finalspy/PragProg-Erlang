# Modules

## Definition

Unité de basique de code.
Contient les fonctions.
Est sotcké sous la forme d'un fichier .erl.

## Exemple

### Code source

	-module(geometry).
	-export([area/1]).
	area({rectangle, Width, Height}) -> Width * Height;
	area({circle, R})-> 3.14159 * R * R.

### Compilation

	1> c(geometry).
	{ok,geometry}

### Utilisation

	2> geometry:area({rectangle, 10, 5}).
	50
	3> geometry:area({circle, 1.4}).
	6.15752


