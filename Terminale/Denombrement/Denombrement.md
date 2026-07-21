# Dénombrement.
Lycée du Granier: classe Terminale.

Suites et raisonnement par recurrence.

## Rappels cruciaux.

- **Dénombrabilité**, dans un problème **discret**: nous pouvons "compter" les issues, 
  qui sont séparés par des "pas" entiers, à l'opposé de la continuité. 
  _Par exemple_:
	- les nombres réels $\mathbb{R}$ sont un en ensemble continu:
		- nous pouvons toujours trouver un nombre plus petit ou plus grand qu'un autre
			- $2.0 > 1.5 > 1.0$;
			- $1.5 > 1.25 > 1.0$;
			- $1.25 > \frac{\pi}{3} > 1.0$;
			- $...$
	- les nombres entiers $\mathbb{N}$ et les relatifs $\mathbb{Z}$ sont des ensembles dénombrables.


- **Suite numérique**: posons pour tout rang $n \in \mathbb{N}$, une valeur $u_n$ et notons la suite $(u_n)_{n \ge 0}$. 
  Elle est assimilable à un couple antécédent-image, mais _discret_. 
  Nous pouvons la définir de 2 manières:
	- **explicitement**: pour une fonction $f: \mathbb{R} \to \mathbb{R}$ et $\forall n \in \mathbb{N}$: $$
u_n = f(n)
$$
	- par **récurrence**: pour un rang de départ $a$, un valeur initiale $x \in \mathbb{R}$, une fonction $g: \mathbb{R} \to \mathbb{R}$ et $\forall n \in \mathbb{N}$: $$
u_a = x;\; u_{n+1} = g(u_{n})
$$

- **Suites** au lycée; nous n'étudions que 2 types:
	 - **arithmétiques** ($+$):  $\forall n \in \mathbb{N}$, pour une _raison_ $q \in \mathbb{R}$ et un rang de départ $a \in \mathbb{N}$: $$
\begin{aligned}
     &u_{n+1} = q + u_n \\
\iff &u_n     = u_a + q({n - a})
\end{aligned}
$$
	- **géométriques** ($\times$):  $\forall n \in \mathbb{N}$, pour une _raison_ $q \in \mathbb{R}$ et un rang de départ $a \in \mathbb{N}$: $$
\begin{aligned}
     &u_{n+1} = q \times u_n \\
\iff &u_n = u_a \times q^{n - a}
\end{aligned}
$$

- Etude de la **monotonie**, c'est-à-dire si la suite est "tout le temps" croissante ou décroissante. 
  Nous pouvons exprimer la croissance $\forall n \in \mathbb{N};\; u_{n+1} > u_{n}$, car les suites sont un problème _discret_.
	- Principalement pour les arithmétiques (contraposé vraie): $$
\begin{align}
     &u_{n+1} > u_{n} \\
\iff &u_{n+1} - u_{n} > 0 \\
\iff &q > 0 \\
\end{align}
$$
	- Principalement pour les géométriques: $$
\forall n \in \mathbb{N}; \frac{u_{n+1}}{u_{n}} = q
\begin{cases}
u_{n+1} > u_{n}           &\text{si } q > 1 \\
u_{n+1} < u_{n}            &\text{si } 1 > q > 0 \\
(u_n) \text{ non monotone} &\text{si } q < 0
\end{cases}
$$
- Somme de suites, $\forall n \in \mathbb{N}$:
	- **arithmétiques** $u_n = u_a + q \times n$: $$
\sum_{i=a}^{n}{u_i} = \frac{u_a + u_n}{2} 
$$
	- **géométriques $v_n = v_a \times q^n$: $$
\sum_{i=a}^{n}{v_i} = \frac{1 - q^{n - a + 1}}{1 - q}
$$

## Limites de suites.

**Limite** d'une suite:
- c'est la valeur de la suite $(u_n)$ quand le rang $n$, est grand, très grand.
- $n$ _tends_ vers l'infini et notons: $n \to +\infty$.
	- Comme $n \in \mathbb{N}$, nous pouvons raccourcir: $n \to \infty$.
	- Remarquons bien que $n \neq \infty$. Écrire $«n = \infty »$, n'a pas de sens, car $\infty$ n'est pas un nombre.
- Si la valeur de cette limite est finie, la suite _converge_. Appelons-la $l \in \mathbb{R}$ et se note: $$
\lim_{n \to \infty}{u_n} = l \\
\text{ ou } u_n \to l 
$$
- _Si_ la valeur de cette limite est infinie, la suite _diverge_ notons: $$
\lim_{n \to \infty}{u_n} = \pm\infty
$$ _alors_: pour un $N \in \mathbb{N}$ suffisamment grand$$
\nexists n \in \mathbb{N} \text{ tq } u_n > u_N
$$
- _Si_ la suite n'a pas de limite, qu'elle "oscille", elle _diverge_ aussi. Mais nous ne notons pas de limite. 
  _Exemple_: $u_n = sin(n)$

Calculer les limites grace aux **raisons**:
- Suite **arithmétique** $u_n = u_a + q \times n$: $$
\begin{cases}
u_n \to +\infty &\text{si } q > 0 \\
u_n \to -\infty &\text{si } q < 0 \\
u_n = u_a     &\text{si } q = 0   \\
\end{cases}
$$
- Suite **géométrique** $u_n = u_a \times q^n$: $$
\begin{cases}
(1) \quad u_n \to +\infty \times u_a &\text{si } 1 < q  \\
(2) \quad u_n \to 0 &\text{si } -1 < q < 1              \\
\quad \quad \; u_n \to u_a &\text{si } q = 1            \\
(3) \quad (u_n) \text{ diverge} &\text{si } q < -1      \\
\end{cases}
$$
- _Exemple_ graphique (retrouvable sur [Desmos](https://www.desmos.com/calculator/txzpkgbbdm)): ![Limites de suites géométriques.|400](resources/IMAGE_SequencesGeometricLimits.png)

Calculer la limite d'un suite définie **explicitement**: 
- Notons: $$
\begin{aligned}
u_n &= f(n)                                          \\
\lim_{n \to \infty}{u_n} &= \lim_{n \to \infty}{f(n)} \\
\end{aligned}
$$
- "Appliquer" la limite $n \to \infty$ dans l'experssion de $f$.
- Utiliser les règles de calcul avec des limites pour $x \in \mathbb{R}$ et les infinités $\pm \infty$":
	- les opérations négatives suivent la même logique;
	- ici, 2 signes $\pm$ sont de même signe;

| $a$        | $\star$  | $b$          | $a \star b$  |
| ---------- | -------- | ------------ | ------------ |
| $+ \infty$ | $+$      | $\pm x$      | $+ \infty$   |
| $+\infty$  | $+$      | $+\infty$    | $+\infty$    |
| $+\infty$  | $\times$ | $\pm x$      | $\pm \infty$ |
| $+\infty$  | $\times$ | $\pm \infty$ | $\pm \infty$ |
| $+\infty$  | $\div$   | $\pm x$      | $\pm \infty$ |
| $\pm x$    | $\div$   | $+\infty$    | $0^{\star}$  |
| $\pm x$    | $\div$   | $0$          | $\pm \infty$ |

$^{\star}$ _plus de details dans le chapitre sur les limites de fonctions_

- Faire attentions aux formes indéterminées, qui n'ont pas de résultat ni de sens. Par abus de language: $$
	«+\infty - \infty \, » \quad 
	«0 \times \pm \infty» \quad
	«\frac{\pm\infty}{\pm\infty}» \quad
	«\frac{0}{0}» \quad
$$
- *Exemple*: $$
\begin{aligned}
	 &\text{Cherchons: } \lim_{n \to \infty}{u_n}  \\
	 &\text{Posons: }                              \\
	 &u_n = 5 + \frac{5n}{n^2} \quad \text{
		 Simplifions car forme indeterminée 
		 avec la fraction.
	 }                                             \\
\iff &u_n = 5 + \frac{5}{n}                        \\
	 &\text{Ainsi: }                               \\
	 &\lim_{n \to \infty}{u_n} = 5 + \frac{5}{n}
		 = 5 + 0
		 = 5                                       \\
\end{aligned} $$


Théorèmes de **comparaison**.
- Théorème de comparaison des suites monotones (contraposée vraie): $$
\forall n \in \mathbb{N}, u_n \geq v_n
\begin{cases}
	\lim_{n \to \infty}{u_n} = +\infty 
	&\text{si } \lim_{n \to \infty}{v_n} = +\infty \\
	\lim_{n \to \infty}{v_n} = -\infty 
	&\text{si } \lim_{n \to \infty}{u_n} = -\infty \\
\end{cases}
$$
- Théorème des gendarmes ou du « sandwitch »: $$
\begin{aligned}
	&\forall n \in \mathbb{N}, \quad a_n \leq u_n \leq b_n \\
	\text{Si } &\lim_{n \to \infty}{a_n} = \lim_{n \to \infty}{b_n} = l \\
	\text{Alors } &\lim_{n \to \infty}{u_n} = l
\end{aligned}
$$

## Raisonnement par récurrence.
_A voir en cour, avec des exemples_.

Structure d'une **hypothèse de récurrence**, où nous notons $\mathcal{P}(n)$ notre propriété pour $n$ dans un sous-ensemble de $\mathbb{N}$:
- $\underline{Initialisation}$: nous validons notre propriété $\mathcal{P}(n_0)$ à un rang de départ $n_0$
  ($0$ pour $\mathbb{N}$, $1$ pour $\mathbb{N}^{\star}$, $\dots$)
- $\underline{Hérédité}$: nous supposons $\mathcal{P}(n)$ vraie, pour un $n$ ***quelconque***
  (non pas *pour tout* $\forall n$, sinon nous supposons qu'elle est déjà tout vraie, et il ne reste plus rien à prouver).
  La récurrence consiste à faire «tomber les dominos» et à prouver que, grace à notre supposition,  $\mathcal{P}(n+1)$ est vrai aussi.
- $\underline{Conclusion}: \mathcal{P(n)} \text{ est initialisée en } n = n_0 \text{ et héreditaire, } \underline{ ainsi } \; \mathcal{P(n)} \text{ est vraie } \forall n$















