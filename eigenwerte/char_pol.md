# Das charakteristische Polynom

Nachdem wir in Abschnitt {ref}`s:eigenwerte` die grundlegende Begriffe eingeführt haben, wollen wir uns nun damit beschäftigen, wie sich die Eigenwerte eines Endomorphismus bzw. einer darstellenden, quadratischen Matrix berechnen lassen und was wir an ihnen ablesen können.

````{prf:definition} Charakteristisches Polynom
:label: def:char_polynom

Sei $A \in \mathbb{K}^{n \times n}$ eine quadratische Matrix und $I_n \in \mathbb{K}^{n \times n}$ die entsprechende Einheitsmatrix, so bezeichnen wir die Abbildung 
\begin{align}
\begin{split}
P_A \colon \mathbb{K} \ \rightarrow \ & \mathbb{K} \\
t  \ \mapsto \ & \det(A - tI_n)
\end{split}
\end{align}
als charakteristisches Polynom von $A$.
````

Der folgende Satz erlaubt es uns Eigenwerte als Nullstellen des charakteristischen Polynoms zu beschreiben und gibt uns gleichzeitig eine praktische Rechenvorschrift.

````{prf:theorem} Satz zum charakteristischen Polynom
Sei $A \in \mathbb{K}^{n \times n}$ eine quadratische Matrix. 
Dann gilt folgende Äquivalenz:

```{math}
\lambda \in \mathbb{K} \text{ ist Eigenwert von } A \ \Leftrightarrow \ P_A(\lambda) = \det(A - \lambda I_n) \ = \ 0.
```

````

````{prf:proof}
Für einen festen Eigenwert $\lambda \in \mathbb{K}$ von $A$, sei $v \in V, v \neq 0$ der zugehörige Eigenvektor, so dass die Eigenwertgleichung {eq}`eq:eigenwertgleichung_matrix` erfüllt ist.
Dann gilt:

```{math}
& A v - \lambda v \ = \ 0 \\
\overset{(i)}{\Leftrightarrow} \quad & (A - \lambda I_n) v \ = \ 0 \\
\overset{(ii)}\Leftrightarrow \quad & \Kern(A - \lambda I_n) \ \neq \ \vec{0}  \\
\overset{(iii)}\Leftrightarrow \quad & \Bild(A - \lambda I_n) \ \neq \ V  \\
\overset{(iv)}\Leftrightarrow \quad & \Rang(A - \lambda I_n) \ \neq \ \dim(V)  \\
\overset{(v)}\Leftrightarrow \quad & \det(A - \lambda I_n) \ = \ 0
```
Hierbei gilt (i) wegen der Linearität, (ii) wegen {prf:ref}`def:matrix_kern`, (iii) wegen {prf:ref}`def:matrix_bild_rang`, 
(iv) wegen {prf:ref}`def:matrix_bild_rang` und (v) wegen {prf:ref}`lem:rang_determinante`.
````

Die Dimension des $\mathbb{K}$-Vektorraums $V$ gibt den Grad des charakteristischen Polynoms vor, d.h., für $\dim(V) = n$ können wir erwarten, dass das charakteristische Polynom $P_A$ einer Matrix $A \in \mathbb{K}^{n \times n}$ den Grad $n$ hat. Insgesamt ist nun also das geometrische Problem der Bestimmung von Eigenwerten eines Endomorphismus zurückgeführt auf das algebraische Problem der Bestimmung von Nullstellen eines Polynoms.

## Vielfachheiten

Wir können die Nullstellen des charakteristischen Polynoms noch näher charakterisieren durch folgende Definition.

````{prf:definition} Algebraische Vielfachheiten
Wir definieren die Häufigkeit mit der ein Eigenwert $\lambda \in \mathbb{K}$ einer Matrix $\mathbb{K}^{n \times n}$ als Nullstelle des charakteristischen Polynoms $P_A$ auftritt als die \emph{algebraische Vielfachheit} des Eigenwerts $\lambda$.
````

````{prf:theorem} Vielfachheiten
:label: satz:vielfachheiten

Sei $F \colon V \rightarrow V$ ein Endomorphismus von $V$ und sei $\lambda \in \mathbb{K}$ ein Eigenwert von $F$ mit algebraischer Vielfachheit $r \in \mathbb{N}$ und geometrischer Vielfachheit $s \in \mathbb{N}$.
Dann ist die algebraische Vielfachheit von $\lambda$ immer größer oder gleich seiner geometrischen Vielfachheit, d.h., es gilt 
\begin{equation*}
n \geq r \geq s \geq 1.
\end{equation*}
````

````{prf:proof}
Sei $s \in \mathbb{N}$ die geometrische Vielfachheit des Eigenwerts $\lambda$ von $F$, so ist $\Eig(F; \lambda) = \lin(\lbrace{v_1,\ldots, v_s\rbrace}) \subset V$ der zugehörige Eigenraum.
Da $\Eig(F; \lambda)$ ein Untervektorraum von $V$ ist können wir $\lbrace{v_1,\ldots, v_s\rbrace}$ als eine Basis des Eigenraums auffassen.
Mit Hilfe des Basisergänzungssatzes (siehe Lemma 3.24 in {cite:p}`burger_2020`) können wir weitere Vektoren $v_{s+1}, \ldots, v_n \in V$ bestimmen, so dass  $B \coloneqq \lbrace{v_1,\ldots, v_s, v_{s+1}, \ldots v_n\rbrace}$ eine Basis von $V$ ist.
Für die Vektoren $v_j \in V$ muss wegen der Eigenwertgleichung $F(v_j) = \lambda v_j$ gelten für $1\leq j\leq s$.
Gleichzeitig können wir den Endomorphismus $F$ durch die darstellende Matrix $A \coloneqq M_B(F)$ bezüglich der gewählten Basis $B$ ausdrücken.
Die Einträge der Matrix $A$ werden hierbei durch ihre Wirkung auf die Basisvektoren von $B$ eindeutig festgelegt und wir wissen wegen der Eigenwertgleichung, dass gelten muss
\begin{equation*}
F(v_j) \ = \ A v_j \  \overset{!}{=} \ \lambda v_j, \quad 1\leq j \leq s.
\end{equation*}
Da die Basiselemente $v_j, 1\leq j\leq n$ insbesondere linear unabhängig sind, muss zur Erfüllung der rechten Seite der Gleichung für $1\leq j \leq s$ gelten
\begin{equation*}
 A_{i,j} \ = \ \begin{cases} 0, \quad \text{ falls } i \neq j,\\ \lambda, \quad \text{ falls } i = j. \end{cases}
\end{equation*}
Damit ergibt sich, dass die darstellende Matrix $A$ die folgende Gestalt haben muss
\begin{equation*}
A \ = \
\begin{pmatrix}
\lambda I_s & *\\
0 & C\\
\end{pmatrix},
\end{equation*}
wobei für den unteren, rechten Block $C \in \mathbb{K}^{(n-s)\times (n-s)}$ gilt.
Für das charakteristische Polynom können wir also auf Grund der Gestalt von $A$ und der Determinanten-Produktregel für Blockmatrizen in Lemma {prf:ref}`lem:det_blockmatrix` folgern, dass gilt
\begin{equation*}
P_F(t) \ = \ P_{A}(t) \ = \ (\lambda - t)^s \cdot \det(C - tI_{n-s}). 
\end{equation*}
Das zeigt, dass der Eigenwert $\lambda$ von $F$ mindestens die algebraische Vielfachheit $r \geq s$ besitzt.

Abschließend lässt sich festhalten, dass $s \geq 1$ gelten muss, da mindestens ein Eigenvektor zum Eigenwert $\lambda$ von $F$ existieren muss.
Gleichzeitig ist $r \leq n$, da das charakteristische Polynom $P_F$ vom Grad $n$ ist.
````

## Eigenwerte berechnen

Um ein wenig mehr Intuition für den Begriff der Eigenwerte zu bekommen wollen wir zwei konkrete Beispiele durchrechnen.

````{prf:example} Bestimmung von Eigenwerten
:label: bsp:eigenwerte

Wir wollen im Folgenden die Bestimmung von Eigenwerten für $(2 \times 2)$-Matrizen veranschaulichen.

* Sei $A \in \mathbb{R}^{2 \times 2}$ eine Matrix deren Eigenwerte wir bestimmen wollen mit
\begin{equation*}
A \ \coloneqq \
\begin{pmatrix}
-9 & -3 \\
16 & 5
\end{pmatrix}
\end{equation*}
Zur Berechnung der Eigenwerte stellen wir das charakteristische Polynom aus Definition {prf:ref}`def:char_polynom` auf und setzen es gleich Null.
\begin{equation*}
P_A(t) \ = \ \det(A - tI_2) \ = \
\det
\begin{pmatrix}
-9 - t & -3 \\
16 & 5 - t
\end{pmatrix}
\ \overset{!}{=} \ 0.
\end{equation*}
Für das einfache Beispiel einer $(2 \times 2)$-Matrix können wir die Determinante der obigen Matrix in geschlossener Form angeben als
\begin{equation*}
\det
\begin{pmatrix}
-9 - t & -3 \\
16 & 5 - t
\end{pmatrix}
\ = \ (-9 - t) \cdot (5 -t) - (-3) \cdot 16 \ = \ t^2 + 4t + 3.
\end{equation*}
Da das charakteristische Polynom bereits in Normalform vorliegt, lassen sich die Nullstellen von $P_A$, die die Eigenwerte von $A$ darstellen, mittels der $p$-$q$-Formel für $p=4$ und $q=3$ angeben:
\begin{equation*}
\lambda_{1/2} \ = \ - \frac{p}{2} \pm \sqrt{\left( \frac{p}{2} \right)^2 - q} \ = \ -2 \pm \sqrt{4 - 3} \ = \ -2 \pm 1.
\end{equation*}
Wir erhalten also die Eigenwerte $\lambda_1 = -3$ und $\lambda_2 = -1$ der Matrix $A$.

* Für den einfachen Fall von $2 \times 2$-Matrizen lässt sich das charakteristische Polynom in allgemeiner Form angeben.
Sei $A = \begin{pmatrix}a & b\\ c & d\end{pmatrix} \in \mathbb{K}^{2\times 2}$, so lässt sich das charakteristische Polynom $P_A$ von $A$ schreiben als:
\begin{equation*}
\begin{split}
P_A(t) \ &= \ \det \begin{pmatrix}a-t & b\\ c & d-t\end{pmatrix} \ = \ (a - t) \cdot (d - t)  - b \cdot c \\
\ &= \ t^2 - (a + d) \cdot t + (ad - bc) \ = \ t^2 - \tr(A) \cdot t + \det(A).
\end{split}
\end{equation*}
Durch Anwendung der $p$-$q$-Formel wie in Beispiel {prf:ref}`bsp:eigenwerte` lassen sich die Eigenwerte $\lambda_1, \lambda_2 \in \mathbb{K}$ als Nullstellen von $P_A$ auch in allgemeiner Form angeben als:

```{math}
:label: eq:eigenwerte_2x2_allgemein

\lambda_{1/2} \ = \ \frac{\tr(A)}{2} \pm \sqrt{\left( \frac{\tr(A)}{2} \right)^2 - \det(A)}.
```

Aus Gleichung {eq}`eq:eigenwerte_2x2_allgemein` können wir die folgenden interessanten mathematischen Zusammenhänge ablesen:

```{math}
:label: eq:summe_prod_ew

\begin{split}
\lambda_1 + \lambda_2 \ &= \  \frac{\tr(A)}{2} + \frac{\tr(A)}{2} \ = \ \tr(A), \\
\lambda_1 \cdot \lambda_2 \ &= \ \left(  \frac{\tr(A)}{2} \right)^2 -  \left( \frac{\tr(A)}{2} \right)^2 + \det(A) \ = \ \det(A).
\end{split}
```

````

````{prf:remark}
Wir wollen folgende Beobachtungen  zur Berechnung  von Eigenwerten festhalten.

* Wie man anhand der Berechnungsformel {eq}`eq:eigenwerte_2x2_allgemein` sieht, kann das charakteristische Polynom $P_A$ komplexe Nullstellen besitzen, sogar wenn die Matrix nur reelle Einträge hat, d.h., $A \in \mathbb{R}^{2 \times 2}$.
Wir erinnern daran, dass wir eine Nullstelle des charakteristischen Polynoms nur dann Eigenwert nennen, wenn sie aus dem zu Grunde liegenden Körper $\mathbb{K}$ des Vektorraums $V$ stammt.
Bettet man jedoch beispielsweise $\mathbb{R}$ in seinen algebraischen Abschluss $\mathbb{C}$ ein, so dass $V$ zu einem komplex-wertigen Vektorraum wird, dann lassen sich alle Nullstellen des charakteristischen Polynoms als Eigenwerte in $\mathbb{C}$ auffassen.

* Die Beobachtungen in Gleichung {eq}`eq:summe_prod_ew` lassen sich erstaunlicherweise auch auf beliebige Matrizen $A \in \mathbb{K}^{n \times n}$ verallgemeinern und man kann zeigen, dass gilt:
\begin{equation*}
\sum_{i=1}^n \lambda_i \ = \ \tr(A), \qquad \prod_{i=1}^n \lambda_i \ = \ \det(A).
\end{equation*}

* Für beliebige quadratische Matrizen $A \in \mathbb{K}^{n \times n}$ gibt es für $n > 3$ im Allgemeinen keine einfache Form zur Berechnung der Determinante. Hier nutzt man typischerweise das Gaußsche Eliminationsverfahren aus Kapitel 3.2 in {cite:p}`burger_2020` um die Matrix $A - \lambda I_n$ in eine obere, rechte Dreiecksmatrix zu überführen,  deren Determinante man dann an der Hauptdiagonale ablesen kann.
Es sei jedoch Vorsicht geboten: Die Determinante dieser oberen, rechten Dreiecksform ist im Allgemeinen verschieden von der ursprünglichen Determinante.
Das folgende Beispiel erklärt welche Schritte man zusätzlich berücksichtigen muss, um das korrekte charakteristische Polynom zu erhalten.
````

````{prf:example}
Sei $A \in \mathbb{R}^{2 \times 2}$ eine quadratische Matrix deren Determinante wir bestimmen wollen mit 
\begin{equation*}
A \ = \ 
\begin{pmatrix}
6 & 1 \\
3 & 2
\end{pmatrix}.
\end{equation*}
Obwohl man in diesem einfachen Fall direkt die Determinante bestimmen kann als
\begin{equation*}
\det(A) \ = \ 6 \cdot 2 - 1 \cdot 3 \ = \ 9
\end{equation*}
verwenden wir zunächst das Gaußsche Eliminationsverfahren, um  die Matrix $A$ in einer obere, rechte Dreiecksform zu bringen.
\begin{equation*}
\begin{pmatrix}
6 & 1 \\
3 & 2
\end{pmatrix}
\ \overset{2 \cdot II.}{\rightarrow} \
\begin{pmatrix}
6 & 1 \\
6 & 4
\end{pmatrix}
\ \overset{II. -I.}{\rightarrow} \
\begin{pmatrix}
6 & 1 \\
0 & 3
\end{pmatrix}
\ \eqqcolon \ \tilde{A}.
\end{equation*}
Man ist schnell versucht anzunehmen, dass die Determinante dieser oberen, rechten Dreiecksmatrix $\tilde{A}$ der Determinante von $A$ entspricht, jedoch zeigt sich, dass
\begin{equation*}
\det(A) \ = \ 6 \cdot 3 \ = \ 18 \ \neq \ 9 \ = \det(A).
\end{equation*}
Um die korrekte Determinante von $A$ aus der Form von $\tilde{A}$ zu bestimmen, müssen wir die elementaren Zeilenoperationen des Gaußschen Eliminationsverfahrens mit Hilfe der entsprechenden Elementarmatrizen schreiben.
Wir können schreiben:
\begin{equation*}
\tilde{A} \ = \ 
\begin{pmatrix}
6 & 1 \\
0 & 3
\end{pmatrix}
\ = \
\begin{pmatrix}
1 & 0 \\
-1 & 1
\end{pmatrix}
\cdot
\begin{pmatrix}
1 & 0 \\
0 & 2
\end{pmatrix}
\cdot
\underbrace{
\begin{pmatrix}
6 & 1 \\
3 & 2
\end{pmatrix}
}_{= A}
\end{equation*}
Mit der Produktregel für Determinanten aus \cite[Satz 3.1.3, D11]{fischer} können wir obige Gleichung schreiben als:
\begin{equation*}
\underbrace{
\det \begin{pmatrix}
6 & 1 \\
0 & 3
\end{pmatrix}
}_{= 18}
\ = \
\underbrace{
\det \begin{pmatrix}
1 & 0 \\
-1 & 1
\end{pmatrix}
}_{= 1}
\cdot
\underbrace{
\det \begin{pmatrix}
1 & 0 \\
0 & 2
\end{pmatrix}
}_{=2}
\cdot
\det (A).
\end{equation*}
Durch Umstellen erhalten wir dann die richtige Determinante mit $\det(A) = \frac{18}{1\cdot 2} = 9$.
````

````{prf:remark}
Bei einem genaueren Studium der Elementarmatrizen im Gaußschen Eliminationsverfahren fällt auf, dass 

* **skalare Multiplikation einer Zeile** mit Faktor $a \in \mathbb{K}$ immer durch eine Elementarmatrix mit Determinante $a$ ausgedrückt wird.

* **Subtraktion zweier Zeilen** immer durch eine Elementarmatrix mit Determinante $1$ ausgedrückt wird.

* **Zeilenvertauschungen** immer durch eine Elementarmatrix mit Determinante $1$ oder $-1$ ausgedrückt wird, in Abhängigkeit der ensprechenden Zeilenindizes.
````

Da wir nun wissen, dass wir die Eigenwerte einer Matrix als Nullstellen des charakteristischen Polynoms berechnen können, wollen wir uns mit der Bestimmung der zugehörigen Eigenvektoren beschäftigen.
Wir werden im folgenden Beispiel sehen, dass sich der Eigenraum zu einem Eigenwert einer Matrix als Lösungsraum des homogenen linearen Gleichungssystems $(A - \lambda I_n) v = 0$ bestimmen lässt.

````{prf:example} Eigenraumbestimmung
Sei $A \in \mathbb{R}^{3 \times 3}$ eine reellwertige, quadratische Matrix mit
\begin{equation*}
A \ = \
\begin{pmatrix}
1 & 2 & 0\\
-1 & 0 & 1\\
1 & 0 & 0
\end{pmatrix}.
\end{equation*}
Wie man mit der Determinantenregel von Sarrus aus Lemma {ref}{lem:sarrus} nachrechnen kann, sind die Nullstellen des charakteristischen Polynoms $P_A(t)$ gegeben durch $t_1 = 1$, $t_2 = i\sqrt{2}$ und $t_3 = -i \sqrt{2}$.
Somit hat die Matrix $A$ als lineare Abbildung auf den $\mathbb{R}^3$ lediglich den reellen Eigenwert $\lambda_1 = 1$.

Zur Bestimmung eines Eigenvektors $v \in \mathbb{R}^3$ zum Eigenwert $\lambda_1 = 1$, der die Eigenwertgleichung {eq}`eq:eigenwertgleichung` erfüllt, müssen wir das folgende lineare Gleichungssystem lösen:
\begin{equation*}
(A - \lambda_1\cdot I_3) v \ = \ 
\begin{pmatrix}
1 - 1 & 2 & 0\\
-1 & 0 - 1 & 1\\
1 & 0 & 0 - 1
\end{pmatrix}
\begin{pmatrix}
v_1\\
v_2\\
v_3
\end{pmatrix} \ = \ 
\begin{pmatrix}
0 & 2 & 0\\
-1 & - 1 & 1\\
1 & 0 & - 1
\end{pmatrix}
\begin{pmatrix}
v_1\\
v_2\\
v_3
\end{pmatrix}
\ = \ 0.
\end{equation*}
Um den gesuchten Eigenvektor $v = (v_1, v_2, v_3)^T \in \mathbb{R}^3$ zu bestimmen, verwenden wir das Gaußsche-Eliminationsverfahren zum Lösen linearer Gleichungssysteme (siehe Kapitel 3.2 {cite:p}`burger_2020`).
Hierzu betrachten wir die folgende Sequenz  von Zeilenoperationen:
\begin{equation*}
\begin{split}
(A  - \lambda_1 I_3 \ | \ y ) \ &= \
\begin{bmatrix}[ccc|c]
0 & 2 & 0 & 0\\
-1 & - 1 & 1 & 0\\
1 & 0 & - 1 & 0
\end{bmatrix}
\rightarrow
\begin{bmatrix}[ccc|c]
-1 & - 1 & 1 & 0\\
0 & 2 & 0 & 0\\
1 & 0 & - 1 & 0
\end{bmatrix}
\rightarrow
\begin{bmatrix}[ccc|c]
-1 & - 1 & 1 & 0\\
0 & 2 & 0 & 0\\
0 & -1 & 0 & 0
\end{bmatrix}\\
& \rightarrow \,
\begin{bmatrix}[ccc|c]
-1 & - 1 & 1 & 0\\
0 & 2 & 0 & 0\\
0 & 0 & 0 & 0
\end{bmatrix}
\end{split}
\end{equation*}
Durch Rückwärtseinsetzen erhalten wir, dass $v_2 = 0$ gelten muss. Aus der ersten Zeile folgert man nun, dass $-v_1 + v_3 = 0$ und somit $v_1 = v_3$ gelten muss.

Der zum Eigenwert $\lambda_1 = 1$ von $A$ zugehörige Eigenvektor $v \in \mathbb{R}^3$ ist also ein Vektor der Form $v = \alpha (1, 0, 1)^T$ für $\alpha \neq 0$.
Der durch den Kern von $A - \lambda_1 I_3$ beschriebene Unterraum von $\mathbb{R}^3$ ist somit gegeben durch die lineare Hülle bzw. den Spann $\Kern(A - \lambda_1 I_3) = \lin(\lbrace v\rbrace)$.
````

## Eigenschaften von Eigenwerten und Eigenvektoren

````{prf:theorem}
:label: satz:eigenwert_komplex_konjugiert

Sei $A \in \mathbb{R}^{n \times n}$ eine reellwertige Matrix aufgefasst als Abbildung auf $\mathbb{C}^n$. Wenn $\lambda \in \mathbb{C}$ Eigenwert von $A$ ist, so ist auch sein komplex konjugiertes Element $\overline{\lambda} \in \mathbb{C}$ Eigenwert von $A$. Außerdem sind die zugehörigen Eigenvektoren komplex konjugiert zueinander.
````

````{prf:proof}
Aus den Rechenregeln für komplexe Zahlen in Kapitel 2.2.7 {cite:p}`burger_2020` können wir für zwei komplexe Zahlen $v,w \in \mathbb{C}$ mit $v \coloneqq a + b\cdot i$ und $w \coloneqq c + d\cdot i$ für $a,b,c,d \in \mathbb{R}$ folgern, dass $\overline{v w} = \overline{v}\:\overline{w}$ gilt, da
\begin{equation*}
\begin{split}
\overline{vw} \ &= \ \overline{(a+b\cdot i)(c+d\cdot i)} \ = \ \overline{(ac-bd) + (ad+bc)\cdot i} \ = \ (ac-bd) - (ad+bc)\cdot i \\
&= \  (ac-bd) + (-ad-bc)\cdot i \ = \ (a-b\cdot i)(c-d\cdot i) \ = \ \overline{v}\:\overline{w}.
\end{split}
\end{equation*} 

Außerdem kann man leicht für endliche Summen komplexer Zahlen $v_1,\ldots,v_n \in \mathbb{C}$ zeigen, dass gilt
\begin{equation*}
\overline{\sum_{i=1}^n v_i} \ = \ \sum_{i=1}^n \overline{v_i}.
\end{equation*}
Mit den beiden hergeleiteten Eigenschaften kann man nun direkt folgern, dass ein ähnlicher Zusammenhang für die Matrix-Vektor Multiplikation gilt, nämlich $\overline{Av} = \overline{A}\overline{v}$ für eine quadratische Matrix $A \in \mathbb{C}^{n \times n}$ und einen Vektor $v \in \mathbb{C}^n$.

Sei nun $\lambda \in \mathbb{C}$ ein Eigenwert der reellen Matrix $A \in \mathbb{R}^{n \times n}$ zum Eigenvektor $v \in \mathbb{C}^n$.
Dann gilt offensichtlich die Eigenwertgleichung $Av = \lambda v$. Durch komplexe Konjugation beider Seiten der Gleichung wissen wir dann, dass folgende Gleichung erfüllt ist

```{math}
:label: eq:eigenwertgleichung_komplex

\overline{Av} \ = \ \overline{\lambda v}.
```

Damit können wir den Beweis nun direkt hinschreiben. 
\begin{equation*}
A\overline{v} \ \overset{A \text{ reell}}{=} \ \overline{A}\overline{v} \ = \ \overline{Av} \ \overset{\eqref{eq:eigenwertgleichung_komplex}}{=} \ \overline{\lambda v} \ = \ \overline{\lambda}\:\overline{v}.
\end{equation*}
Es gilt also $A\overline{v} = \overline{\lambda}\:\overline{v}$ und wir haben damit gezeigt, dass $\overline{\lambda} \in \mathbb{C}$ auch Eigenwert von $A$ zum Eigenvektor $\overline{v} \in \mathbb{C}^n$ ist.
````

Der folgende Satz macht eine entscheidende Beobachung, die es uns in Kapitel {ref}`s:diagonalisierbarkeit` erlauben wird, den Vektorraum $V$ als direkte Summe der Eigenräume einer quadratischen Matrix $A$ zu zerlegen, falls $A$ gewisse Eigenschaften erfüllt.

````{prf:theorem}
:label: satz:eigenvektoren_lu

Sei $A \in \mathbb{K}^{n \times n}$ eine Matrix und seien $\lambda_1, \ldots, \lambda_k \in \mathbb{K}, k \leq n$, Eigenwerte von $A$. 
Außerdem seien $v_1, \ldots, v_k \in V$ Eigenvektoren von $A$ zu den Eigenwerten $\lambda_1, \ldots, \lambda_k$.
Sind die Eigenwerte von $A$ paarweise verschieden, d.h., $\lambda_i \neq \lambda_j$ für alle $i\neq j$, so sind die Eigenvektoren linear unabhängig.
````

````{prf:proof}
Wir führen den Beweis dieser Aussage durch vollständige Induktion über $k \in \mathbb{N}$.

\textbf{Induktionsanfang: $k=1$}\\
Die Aussage ist trivialerweise erfüllt, da für den Eigenvektor $v_1 \in V$ gelten muss $v_1 \neq \vec{0}$.

\textbf{Induktionsschritt: $k-1 \rightarrow k$}\\
Die Induktionsannahme ist, dass die Aussage bereits für den Fall $k-1$ gezeigt wurde.
Seien $\alpha_1, \ldots, \alpha_k \in \mathbb{K}$ so gewählt, dass gilt

```{math}
:label:{eq:induktion_lin_abh}

\sum_{i=1}^k \alpha_i v_i \ = \ \vec{0}.
```

Sei nun $\lambda_k \in \mathbb{C}$ ein Eigenwert von $A$, der paarweise verschieden ist zu $\lambda_1, \ldots, \lambda_{k-1} \in \mathbb{C}$.
Wir multiplizieren die Gleichung {eq}`eq:induktion_lin_abh` mit dem Eigenwert $\lambda_k$ und erhalten

```{math}
:label:{eq:induktion_mult_lambda}
\sum_{i=1}^k \alpha_i \lambda_k v_i \ = \ \vec{0}.
```

Außerdem erhalten wir aus Gleichung {eq}`eq:induktion_lin_abh` durch Multiplikation von links mit der Matrix $A$ aus der Linearität folgenden Zusammenhang:

```{math}
:label: eq:induktion_mult_A

A \cdot \sum_{i=1}^k  \alpha_i v_i \ = \ \sum_{i=1}^k  \alpha_i A v_i \ = \ \sum_{i=1}^k  \alpha_i \lambda_i v_i \ = \ \vec{0}.
```
Wenn wir nun die rechte Seite von {eq}`eq:induktion_mult_A` von Gleichung {eq}`eq:induktion_mult_lambda` subtrahieren erhalten wir
\begin{equation*}
\sum_{i=1}^k \alpha_i (\lambda_k - \lambda_i) v_i \ = \ \sum_{i=1}^{k-1} \alpha_i (\lambda_k - \lambda_i) v_i \ = \ \vec{0}.
\end{equation*}
Da wir $\lambda_k$ als paarweise verschieden zu $\lambda_1, \ldots, \lambda_{k-1}$ angenommen haben wissen wir, dass $\alpha_i = 0$ für $i=1,\ldots,k-1$ gelten muss, damit obige Gleichung gilt.
Setzen wir dies in Gleichung {eq}`eq:induktion_lin_abh` ein, so folgt direkt, dass auch $\alpha_k = 0$ gelten muss, da für den Eigenvektor $v_k \neq \vec{0}$ gilt.
Dies beweist also die lineare Unabhängigkeit der Eigenvektoren von $A$ für paarweise verschiedene Eigenwerte.
````
