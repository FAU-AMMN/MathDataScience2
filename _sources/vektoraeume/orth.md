(s:orthonormalisierung)=
# Orthogonalisierung und Orthonormalisierung

In vielen Fällen ist es sinnvoll nicht eine beliebige Basis eines endlich-dimensionalen Vektorraums $V$ zu betrachten, sondern eine Familie von Vektoren, die _orthogonal_ oder sogar _orthonormal_ sind.
Dies hat viele Vorteile für die Mathematik, da sich so manche Berechnung durch eine Orthonormalbasis deutlich vereinfachen lässt.
Auch lassen sich durch orthonormale Vektoren längen- und winkelerhaltende Transformationen durchführen.

````{prf:definition} Orthogonalität und Orthonormalität
:label: def:orthonormalisierung
Sei $V$ ein Euklidischer bzw. unitärer Vektorraum.
Dann können wir folgende Begriffe und Notation definieren:

i) Zwei Vektoren $u,v \in V$ heißen _orthogonal_, falls gilt:
\begin{equation*}
\langle v, w \rangle \ = \ 0.
\end{equation*}
Wir notieren in diesem Fall häufig auch $v \perp w$.

ii) Zwei Untervektorräume $U, W \subset V$ heißen _orthogonal_, falls gilt:
\begin{equation*}
u \perp v \quad \text{ für alle } u \in U \text{ und } w \in W.
\end{equation*}
Wir notieren in diesem Fall häufig auch $U \perp W$.

iii) Ist $U \subset V$ ein Untervektorraum, so definieren wir sein _orthogonales Komplement_ als
\begin{equation*}
U^\perp \ \coloneqq \ \lbrace{ v \in V \, | \, v \perp u \text{ für alle } u \in U \rbrace}.
\end{equation*}
Es ist klar, dass $U^\perp$ wieder ein Untervektorraum ist.

iv) Eine Familie von Vektoren $(v_1, \ldots, v_n)$ in $V$ heißt _orthogonal_, wenn gilt
\begin{equation*}
v_i \perp v_j \quad \text{ für alle } i \neq j.
\end{equation*}
Sie heißt _orthonormal_, falls zusätzlich gilt
\begin{equation*}
||v_i|| \ = \ 1 \quad \text{ für alle } 1 \leq i \leq n.
\end{equation*}
In diesem Fall gilt offenbar
\begin{equation*}
\langle v_i, v_j \rangle \ = \ \delta_{ij},
\end{equation*}
wobei $\delta_{ij}$ das Kronecker-Delta bezeichnet (vgl. Definition {prf:ref}`def:normalform_nilpotent`).

v) Wir nennen eine Familie von orthonormalen Vektoren $(v_1, \ldots, v_n)$ in $V$ eine _Orthonormalbasis_, falls die Vektoren eine Basis von $V$ bilden.
\item Ist $V = V_1 \oplus \ldots \oplus V_n$, so heißt die direkte Summe _orthogonal_, falls gilt
\begin{equation*}
V_i \perp V_j \quad \text{ für alle } i \neq j.
\end{equation*}
Wir notieren in diesem Fall häufig auch $V = V_1 \operp \ldots \operp V_n$.
````

````{prf:example}
Betrachten wir $\mathbb{R}^n$ oder $\mathbb{C}^n$ mit dem kanonischen bzw. komplexen Skalarprodukt, so ist die kanonische Basis $B = (e_1, \ldots, e_n)$ eine Orthonormalbasis.
````

````{prf:theorem}
Ist $(v_1, \ldots, v_n)$ eine orthogonale Familie von Vektoren in $V$ mit $v_i \neq 0$ für alle $1 \leq i \leq n$, so gelten die folgenden Aussagen

i) Die Familie $(\alpha_1 v_1, \ldots, \alpha_n v_n)$ von Vektoren mit $\alpha_i \coloneqq ||v_i||^{-1}$ ist orthonormal.
ii) Die Familie $(v_1, \ldots, v_n)$ von Vektoren ist linear unabhängig.
````

````{prf:proof}
Wir zeigen die beiden Behauptungen für ein allgemeines Skalarprodukt.

i) Da $v_i \perp v_j$ gilt für $i \neq j$ folgt schon, dass gilt
\begin{equation*}
\langle \alpha_i v_i, \alpha_j v_j \rangle \ = \ \alpha_i \overline{\alpha_j} \langle v_i , v_j \rangle \ = \ 0, \quad \text{ für } i \neq j.
\end{equation*}
Die Familie $(\alpha_1 v_1, \ldots, \alpha_n v_n)$ von Vektoren ist also orthogonal.
Da $\alpha_i = ||v_i||^{-1} \in \mathbb{R}$ gilt sehen wir für den Fall $i=j$, dass gilt
\begin{equation*}
\langle \alpha_i v_i, \alpha_i v_i \rangle \ = \ \alpha_i \overline{\alpha_i} \langle v_i , v_i \rangle \ = \ \frac{||v_i||^2}{||v_i||^2} \ = \ 1.
\end{equation*}
Die Familie von Vektoren ist also orthonormal.

ii) Wir müssen für die lineare Unabhängigkeit der Vektoren $v_1, \ldots, v_n \in V$ zeigen, dass aus der Gleichung

```{math}
:label: eq:orthogonal_lu

0 \ = \ \lambda_1v_1 + \ldots + \lambda_n v_n
```

bereits folgt, dass $\lambda_i = 0$ für $1 \leq i \leq n$ gelten muss.
Multiplizieren wir also die Gleichung {eq}`eq:orthogonal_lu` von rechts mit $v_i^T$ so folgt:
\begin{equation*}
0 \ = \ \langle 0, v_i\rangle \ = \ \langle \lambda_1v_1 + \ldots + \lambda_n v_n, v_i \rangle \ = \ \sum_{j=1}^n \lambda_j \langle v_j, v_i \rangle \ = \ \lambda_i \langle v_i, v_i \rangle.
\end{equation*}
Da das Skalarprodukt insbesondere positiv definit ist, muss also schon gelten, dass $\lambda_i = 0$ ist.
Da dies unabhängig von der Wahl des Vektors $v_i$ gilt, müssen schon alle Koeffizienten $\lambda_i = 0$ für $1\leq i \leq n$ gelten.
````

````{prf:theorem}
Sei $(v_1, \ldots, v_n)$ eine Orthonormalbasis von $V$ und $v \in V$ ein beliebiger Vektor.
Setzen wir $\lambda_i \coloneqq \langle v_i, v \rangle$, so gilt:
\begin{equation*}
v \ = \ \lambda_1 v_1 + \ldots + \lambda_n v_n.
\end{equation*}
````

````{prf:proof}
Da $(v_1, \ldots, v_n)$ eine Orthonormalbasis von $V$ ist, existieren eindeutige Koeffizienten $\gamma_i, 1 \leq i \leq n$, so dass sich der beliebige Vektor $v \in V$ schreiben lässt als
\begin{equation*}
v \ = \ \gamma_1 v_1 + \ldots + \gamma_n v_n.
\end{equation*}
Wir multiplizieren obige Gleichung von rechts mit dem Vektor $v_i^T$ und können die Koeffizienten damit eindeutig bestimmen als
\begin{equation*}
\langle v, v_i \rangle \ = \ \langle \gamma_1 v_1 + \ldots + \gamma_n v_n, v_i \rangle \ = \ \gamma_i \langle v_i, v_i \rangle \ = \ \gamma_i.
\end{equation*}
Da dies für alle $1 \leq i \leq n$ gilt, können wir $\lambda_i \coloneqq \gamma_i = \langle v_i, v \rangle$ definieren und es gilt damit offensichtlich
\begin{equation*}
v \ = \ \lambda_1 v_1 + \ldots + \lambda_n v_n.
\end{equation*}
````

In vielen Situationen ist es praktisch eine Orthonormalbasis zu betrachten, da sie viele Berechnungen vereinfacht.
Lässt sich jedoch eine Orthonormalbasis für einen beliebigen Euklidischen bzw. unitären Vektorraum bestimmen?
Darauf gibt glücklicherweise der folgende Satz eine zufriedenstellende Antwort.

````{prf:theorem} Orthonormalisierungssatz
:label: satz:orthonormalisierung

Sei $V$ ein endlich-dimensionaler Euklidischer bzw. unitärer Vektorraum und $W \subset V$ ein Untervektorraum mit Orthonormalbasis $(w_1, \ldots, w_m)$.
Dann existiert eine Ergänzung aus Vektoren $w_{m+1}, \ldots, w_n \in V$, so dass
\begin{equation*}
(w_1, \ldots, w_m, w_{m+1}, \ldots, w_n)
\end{equation*}
eine Orthonormalbasis von $V$ ergibt.
````

````{prf:proof}
Da der Beweis des Satzes in konstruktiver Form erfolgt, formulieren wir diesen im Folgenden als einen konkreten Algorithmus.
````

Da als Unterraum $W = \lbrace{ 0 \rbrace}$ in Satz {prf:ref}`satz:orthonormalisierung` erlaubt ist, erhalten wir direkt  das folgende Korollar.

````{prf:corollary}
Jeder endlichdimensionale Euklidische bzw. unitäre Vektorraum besitzt eine Orthonormalbasis.
````

Außerdem können wir folgendes Korollar aus dem Orthogonalisierungssatz {prf:ref}`satz:orthonormalisierung` ableiten.

````{prf:corollary}
Ist $W \subset V$ Untervektorraum eines Euklidischen bzw. unitären Vektorraums $V$, so gilt
\begin{equation*}
V \ = \ W \operp W^{\perp}, \quad \text{ und } \quad \dim V \ = \ \dim W + \dim W^{\perp}.
\end{equation*}
````

Die Konstruktion einer Orthonormalbasis geht auf die beiden Mathematiker _J. Gram_ und _E. Schmidt_ zurück und wird daher weitläufig auch als **Gram-Schmidtsches Orthogonalisierungsverfahren** bezeichnet.
Bevor wir uns dem Verfahren widmen, wollen wir eine nützliche Abbildung einführen.

````{prf:definition} Orthogonale Projektion
Seien $V$ ein endlich-dimensionaler Euklidischer bzw. unitärer Vektorraum und $v,w \in V$ zwei linear unabhängige Vektoren.
Dann bezeichnen wir die Abbildung
\begin{equation*}
\Pi_v(w) \ \coloneqq \ \frac{\langle w, v \rangle}{\langle v,v \rangle} \cdot v,
\end{equation*}
als _orthogonale Projektion_ von $w$ auf $v$.
Die orthogonale Projektion berechnet den Anteil, den der Vektor $v$ an der Geometrie von $w$ hat.
````

Die Kernidee des Gram-Schmidtschen Orthogonalisierungsverfahren ist es die Vektoren paarweise zueinander orthogonal auszurichten.
Dabei spielt eine Korrektur mit Hilfe der orthogonalen Projektion eine zentrale Rolle, wie das folgende Lemma zeigt.

````{prf:lemma}
Seien $V$ ein endlich-dimensionaler Euklidischer bzw. unitärer Vektorraum und $v,w \in V$ zwei linear unabhängige Vektoren.
Dann können wir einen Vektor $\hat{w} \in V$ berechnen mit
\begin{equation*}
\hat{w} \ \coloneqq \ w - \Pi_v(w) \ = \ w - \frac{\langle w, v \rangle}{\langle v,v \rangle} \cdot v,
\end{equation*}
so dass $\hat{w} \perp v$ gilt.
````

````{prf:proof}
Wir betrachten folgende Umformungen:
\begin{equation*}
\begin{split}
\langle v, \hat{w} \rangle \ &= \ \langle v, w - \frac{\langle w, v \rangle}{\langle v,v \rangle} \cdot v \rangle \ = \ \langle v, w \rangle - \overline{\left(\frac{\langle w, v \rangle}{\langle v,v \rangle}\right)} \cdot \langle v, v \rangle\\
\ &= \ \langle v, w \rangle - \overline{\langle w, v \rangle} \cdot \frac{1}{\overline{\langle v,v \rangle}} \cdot \langle v, v \rangle \ = \ \langle v, w \rangle - \langle v, w \rangle \cdot \underbrace{\frac{\langle v, v \rangle}{\langle v,v \rangle}}_{=1} \ = \ 0. 
\end{split}
\end{equation*}
Und somit gilt $\hat{w} \perp v$.
Die obigen Umformungen wären einfacher zu zeigen gewesen, wenn man die Gleichung mit $\langle \hat{w}, v \rangle$ begonnen hätte.
So konnte man jedoch sehen, dass die Aussage auch mit dem komplexen Standardskalarprodukt verträglich ist.
````

Der folgende Algorithmus erklärt das Gram-Schmidt-Orthogonalisierungsverfahren zur Konstruktion einer Orthonormalbasis eines endlich-dimensionalen Euklidischen oder unitären Vektorraums.

````{prf:algorithm} Gram-Schmidtsches Orthogonalisierungsverfahren
:label: alg:gram-schmidt

Sei $V$ ein endlich-dimensionaler Euklidischer bzw. unitärer Vektorraum mit $\dim V = n$, dann lässt sich eine Orthonormalbasis $(v_1, \ldots, v_n)$ aus einer Familie von linear unabhängig Vektoren $(w_1, \ldots, w_n)$ von $V$ wie folgt konstruieren.

**1. Schritt:**

Wähle den ersten Vektor $w_1 \in V$ und setze
\begin{equation*}
\tilde{v_1} \ \coloneqq \ w_1.
\end{equation*}
Normiere den ersten Vektor wie folgt:
\begin{equation*}
v_1 \ \coloneqq \ \frac{\tilde{v_1}}{|| \tilde{v_1}||}.
\end{equation*}

**2. Schritt:**

Wähle den zweiten Vektor $w_2 \in V$ und berechne die orthogonale Projektion von $w_2$ auf den normierten Vektor $v_1$ als
\begin{equation*}
\Pi_{v_1}(w_2) \ \coloneqq \ \langle w_2, v_1\rangle v_1.
\end{equation*}
Ziehe die orthogonale Projektion $\Pi_{v_1}(w_2)$ vom ursprünglichen Vektor $w_2$ ab und erhalte damit
\begin{equation*}
\tilde{v_2} \ \coloneqq \ w_2 - \Pi_{v_1}(w_2) \ = \ w_2 - \langle w_2, v_1\rangle v_1.
\end{equation*}
Normiere den zweiten Vektor wie folgt:
\begin{equation*}
v_2 \ \coloneqq \ \frac{\tilde{v_2}}{|| \tilde{v_2}||}.
\end{equation*}

**i. Schritt:**

Wähle den $i$-ten Vektor $w_i \in V$ und berechne die orthogonale Projektion von $w_i$ auf die normierten Vektoren $v_1, \ldots, v_{i-1}$ und ziehe diese Projektionen vom ursprünglichen Vektor $w_i$ ab durch
\begin{equation*}
\tilde{v_i} \ \coloneqq \ w_i  - \sum_{j=1}^{i-1} \langle w_i, v_j \rangle v_j.
\end{equation*}
Normiere den $i$-ten Vektor wie folgt:
\begin{equation*}
v_i \ \coloneqq \ \frac{\tilde{v_i}}{|| \tilde{v_i}||}.
\end{equation*}

**n. Schritt:**

Wähle den $n$-ten Vektor $w_n \in V$ und berechne die orthogonale Projektion von $w_n$ auf die normierten Vektoren $v_1, \ldots, v_{n-1}$ und ziehe diese Projektionen vom ursprünglichen Vektor $w_n$ ab durch
\begin{equation*}
\tilde{v_n} \ \coloneqq \ w_n  - \sum_{j=1}^{n-1} \langle w_n, v_j \rangle v_j.
\end{equation*}
Normiere den $n$-ten Vektor wie folgt:
\begin{equation*}
v_n \ \coloneqq \ \frac{\tilde{v_n}}{|| \tilde{v_n}||}.
\end{equation*}

Die Familie $(v_1, \ldots, v_n)$ bilden nach Konstruktion nun eine Orthonormalbasis von $V$.
````

Wir wollen das Gram-Schmidtsche Orthogonalisierungsverfahren mit einem kurzen Rechenbeispiel veranschaulichen.

````{prf:example}
Sei $V = \mathbb{R}^2$ der Euklidische Vektorraum und wir betrachten zwei linear unabhängige Vektoren $w_1, w_2 \in V$, die wir orthonormalisieren wollen mit
\begin{equation*}
w_1 \ \coloneqq \begin{pmatrix} 3 \\ 1 \end{pmatrix}, \quad w_2 \ \coloneqq \begin{pmatrix} 2 \\ 2 \end{pmatrix}.
\end{equation*}
Wir nutzen Algorithmus {prf:ref}`alg:gram-schmidt` zur Konstruktion einer Orthonormalbasis aus $w_1$ und $w_2$.

**1. Schritt:**

Wir setzen $\tilde{v_1} = w_1$ und normieren den Vektor wie folgt:
\begin{equation*}
v_1 \ = \ \frac{\tilde{v_1}}{||\tilde{v_1}||} \ = \ \frac{1}{\sqrt{10}} \cdot \begin{pmatrix} 3 \\ 1 \end{pmatrix}.
\end{equation*}

**2. Schritt:**

Wir berechnen die orthogonale Projektion von $w_2$ auf $v_1$ wie folgt:
\begin{equation*}
\Pi_{v_1}(w_2) \ = \ \langle w_2, v_1\rangle \cdot  v_1 \ = \ \frac{1}{\sqrt{10}} \cdot \langle (2,2)^T, (3,1)^T \rangle \cdot \frac{(3,1)^T}{\sqrt{10}} \ = \ \frac{8}{10} \cdot \begin{pmatrix} 3 \\ 1 \end{pmatrix}.
\end{equation*}
Damit können wir nun den Vektor $w_2$ orthogonalisieren mit
\begin{equation*}
\tilde{v_2} \ = \ w_2 - \Pi_{v_1}(w_2) \ = \ \begin{pmatrix} 2 \\ 2 \end{pmatrix} - \frac{8}{10} \cdot \begin{pmatrix} 3 \\ 1 \end{pmatrix} \ = \ \frac{1}{5} \cdot \begin{pmatrix} -2 \\ 6 \end{pmatrix}.
\end{equation*}
Durch Normierung erhalten wir den zweiten Vektor der Orthonormalbasis:
\begin{equation*}
v_2 \ = \ \frac{\tilde{v_2}}{||\tilde{v_2}||} \ = \ \sqrt{\frac{25}{40}}\cdot \frac{1}{5}\cdot \begin{pmatrix} -2 \\ 6 \end{pmatrix} \ = \ \frac{1}{\sqrt{10}} \cdot \begin{pmatrix} -1 \\ 3 \end{pmatrix} .
\end{equation*}
Damit haben wir eine Orthonormalbasis von $V$ konstruiert, da offensichtlich gilt:
\begin{equation*}
\begin{split}
\langle v_1, v_2 \rangle \ &= \ \frac{1}{10} \cdot \langle (3,1)^T, (-1,3)^T \rangle \ = \ 0,\\
\langle v_1, v_1 \rangle \ &= \ \frac{1}{10} \cdot \langle (3,1)^T, (3,1)^T \rangle \ = \ 1,\\
\langle v_2, v_2 \rangle \ &= \ \frac{1}{10} \cdot \langle (-1,3)^T, (-1,3)^T \rangle \ = \ 1.\\
\end{split}
\end{equation*}
````
