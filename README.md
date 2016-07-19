# godzilla

godzilla is a mutation testing tool for Go package. 

It is stil very much WIP but if you'd like to try it

    $ go get -u github.com/hydroflame/godzilla/cmd/godzilla
    
then to run it:

    $ godzilla [PACKAGE]

## Mutators

### Swap If Else
The Swap If Else mutator swaps the body of an if/else statement

### Void Call Remover
The void call remover removes all the void function and method call.

### Boolean Operators
The boolean operators mutator swaps boolean operators.

| Original | New |
|----------|-----|
| && | &#124;&#124; |
| &#124;&#124; | && |

### Conditionals Boundary
The conditionals boundary mutator swaps comparison operators to their counterpart that contains, or not, an equality sign.

| Original | New |
|----------|-----|
| >        | >=  |
| <        | <=  |
| >=       | >   |
| <=       | <   |

### Math
The math mutator swaps mathematical operators.

| Original | New |
|----------|-----|
| +	| - |
| -	| + |
| *	| / |
| /	| * |
| %	| * |
| &	| &#124; |
| &#124; | & |
| ^	| & |
| <<	| >> |
| >>	| << |

### Math Assign
The math assign mutator is similar to the Math mutator but for assignements.

| Original | New |
|----------|-----|
| += | -= |
| -= | += |
| *= | /= |
| /= | *= |
| %= | *= |
| &= | &#124;= |
| &#124;= | &= |
| ^= | &= |
| <<= | >>= |
| >>= | <<= |

### Negate Conditionals
The negate conditionals mutator converts boolean checks to their inverse.

| Original | New |
|----------|-----|
| == | != |
| != | == |
| < | >= |
| <= | > |
| > | <= |
| >= | < |

### Float comparison inverter
The float comparison inverter mutator inverts float comparison to their equivalent via De morgan's law. These are actually not equivalent because NaN will return true in one case and false on the other. The main purpose of this mutator is to root out cases where NaN isn't well handled.


| Original | New |
|----------|-----|
| f > g | !(f <= g) |
| f >= g | !(f < g) |
| f < g | !(f >= g) |
| f <= g | !(f > g) |
| !(f <= g) | f > g |
| !(f < g)| f >= g  |
| !(f >= g)| f < g  |
| !(f > g)| f <= g  |
