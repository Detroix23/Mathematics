# Coefficients binomiaux.
Lycée du Granier: classe Terminale.

## Définition.
Soit $n \in \mathbb{N}^*, k \in \mathbb{N}, n \geq k$.

Notons la **factorielle** de $n$:
$$
n! = \prod_{i=1}^{n} {i} = 1 \times 2 \; \times \; ... \times \; n 
$$
Par définition:
$$
0! = 1
$$

Nous avons $k$ parmi $n$:
$$
\binom{n}{k} = \frac{n!}{(n-k!)\; k!}
$$
_Conseil pour la compréhension de la formule_: développer les factorielles et remarquer les parties qui s'annulent.

**Propriétés**:
- $\binom{n}{0} = \binom{n}{n} = 1$
- $\binom{n}{1} = \binom{n}{n-1} = n$
- Symétrie: $\binom{n}{k} = \binom{n}{n - k}$ 
## Combinaisons et point de vue plus concret.
D'une manière plus pratique, $\binom{n}{k}$, lu $k$ _parmi_ $n$, compte le nombre de _combinaisons_ de $k$ éléments dans un ensemble de $n$ éléments. Dans une combinaison:
- l'ordre n'importe pas;
- les répétitions non plus.

_Exemples_:
Comprendre les contraintes. Posons $E = \set{a, b, c, d}$. 

Ses combinaisons de cardinal 3 sont égales:
$$
\set{a, b, c} = \set{a, c, b} = \set{b, c, a} = \set{b, a, c} = \set{c, b, a} = \set{c, a, b} = \set{a, a, a, b, b, c,c}
$$

Comprendre ce que nous cherchons:
Prenons un set de 4 "billes". "Choisir $n$ billes" ici veux dire choisir strictement $n$ billes. 

| ①   | ②   | ③   | ④   |
| --- | --- | --- | --- |
- $\binom{4}{0} = 1$: nous choisissons 0 billes parmi 4. Combien il y a-t-il de set possibles ? 1, celui vide:

| ◯   | ◯   | ◯   | ◯   |
| --- | --- | --- | --- |

- $\binom{4}{1} = 4$: nous choisissons 1 bille parmi 4. Il y a 4 sets:

| ①   | ◯   | ◯   | ◯   |
| --- | --- | --- | --- |
| ◯   | ②   | ◯   | ◯   |
| ◯   | ◯   | ③   | ◯   |
| ◯   | ◯   | ◯   | ④   |
- $\binom{4}{2} = 6$: nous choisissons 2 bille parmi 4. Il y a 6 sets:

| ①   | ②   | ◯   | ◯   |
| --- | --- | --- | --- |
| ①   | ◯   | ③   | ◯   |
| ①   | ◯   | ◯   | ④   |
| ◯   | ②   | ③   | ◯   |
| ◯   | ②   | ◯   | ④   |
| ◯   | ◯   | ③   | ④   |
- $\binom{4}{3} = 4$:

| ①   | ②   | ③   | ◯   |
| --- | --- | --- | --- |
| ①   | ②   | ◯   | ④   |
| ①   | ◯   | ③   | ④   |
| ◯   | ②   | ③   | ④   |

- $\binom{4}{4} = 1$: nous choisissons 4 bille parmi 4. Il y a 1 set, toute les billes:

| ①   | ②   | ③   | ④   |
| --- | --- | --- | --- |

Ainsi, nous pouvons bien comprendre les propriétés:
- $\binom{n}{0} = \binom{n}{n} = 1$
- $\binom{n}{1} = \binom{n}{n-1} = n$
- Symétrie: $\binom{n}{k} = \binom{n}{n - k}$ 


**Graphiques**.
Nous pouvons décrire ce nombre de combinaison pour $n$ élément en fonction de $k$. Pour cela traçons tout les points $(k, \binom{n}{k})$ pour $k \in [[1; n]]$, et observons la "cloche":

![[IMAGE_BinomialCoefficients-Bell1.png]]
