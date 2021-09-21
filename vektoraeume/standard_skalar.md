(s:skalarprodukt_r)=
# Das kanonische Skalarprodukt in $\mathbb{R}^n$

Sei im Folgenden der zu Grunde liegende Vektorraum gewählt als $V = \mathbb{R}^n$.
Wir definieren zuerst das kanonische Skalarprodukt in $\mathbb{R}^n$.

````{prf:definition} Skalarprodukt in $\mathbb{R}^n$
:label: def:skalarprodukt_r

Seien $x = (x_1,\ldots, x_n) \in \mathbb{R}^n$ und $y = (y_1,\ldots, y_n) \in \mathbb{R}^n$ zwei Vektoren.
Wir bezeichnen die Abbildung
\begin{align*}
\langle \cdot, \cdot \rangle \ \colon \ \mathbb{R}^n \times \mathbb{R}^n \ &\rightarrow \ \mathbb{R}, \\
(x, y) \ &\to \ \langle x, y \rangle \ \coloneqq \ x_1y_1 + \ldots + x_ny_n \ = \ \sum_{i=1}^n x_iy_i
\end{align*}
als _kanonisches Skalarprodukt_ von $x$ und $y$ in $\mathbb{R}^n$.
````

Schreibt man $x, y \in \mathbb{R}^n$ als Spaltenvektoren, so lässt sich das kanonische Skalarprodukt auch schreiben als
\begin{equation*}
\langle x, y \rangle \ = \ x^T \cdot y \ = \ (x_1, \ldots, x_n) \cdot \begin{pmatrix} y_1\\ \vdots \\ v_n \end{pmatrix}.
\end{equation*}
Eine ebenfalls in der Literatur gängige Schreibweise ist ein Skalarprodukt mit runden Klammern, d.h., $(x, y) \coloneqq \langle x,y \rangle$.

Folgende Eigenschaften des Skalarprodukts lassen sich leicht nachrechnen.

````{prf:lemma} Eigenschaften des Skalarprodukts
:label: lem:skalarprodukt_r

Das kanonische Skalarprodukt von $\mathbb{R}^n$ in Definition {prf:ref}`def:skalarprodukt_r` besitzt folgende Eigenschaften für Vektoren $x,x',y,y' \in \mathbb{R}^n$ und Skalare $\lambda \in \mathbb{R}$:

i) Bilinearität:
\begin{equation*}
\begin{split}
&\langle x + x', y \rangle \ = \ \langle x, y \rangle + \langle x', y \rangle, \quad \langle x, y + y' \rangle \ = \ \langle x, y \rangle + \langle x, y' \rangle, \\
&\lambda \langle x, y \rangle \ = \  \langle \lambda x, y \rangle \ = \  \langle x, \lambda y \rangle.
\end{split}
\end{equation*}

ii) Symmetrie:
\begin{equation*}
\langle x, y \rangle \ = \ \langle y, x \rangle.
\end{equation*}

iii) Positive Definitheit:
\begin{equation*}
\langle x, x \rangle \ = \ x_1^2 + \ldots + x_n^2 \ \geq \ 0, \quad \langle x, x \rangle \ = \ 0 \ \Leftrightarrow \ x = \vec{0}.
\end{equation*}
````

Die dritte Eigenschaft von Lemma {prf:ref}`lem:skalarprodukt_r` nutzt bereits eine Eigenschaft des Körpers $\mathbb{R}$ aus, nämlich, dass die Summe von quadratischen Termen nie negativ werden kann.
Das bedeutet, wir können aus dem Skalarprodukt eines Vektors mit sich selbst immer die Wurzel ziehen ohne den Körper $\mathbb{R}$ zu verlassen.
Diese wichtige Beobachtung induziert den Begriff der _Norm_ in folgender Definition, welche wir zur Messung von Längen eines Vektor nutzen können.

````{prf:definition}
:label: def:norm_r

Sei $x \in \mathbb{R}^n$ ein Vektor.
Dann definieren wir die Abbildung
\begin{align*}
||\cdot|| \ \colon \ \mathbb{R}^n \ &\rightarrow \ \mathbb{R}_0^+, \\
x \ &\to \ ||x|| \ \coloneqq \ \sqrt{\langle x, x \rangle} \ = \ \sqrt{x_1^2 + \ldots + x_n^2}
\end{align*}
als _Euklidische Norm_ von $x$ in $\mathbb{R}^n$.
````

````{prf:remark}
Im eindimensionalen Fall $V = \mathbb{R}$ reduziert sich die Norm eines Vektors $x \in \mathbb{R}$ auf die Betragsfunktion, d.h., $||x|| = |x|$ für $\dim(V) \eqqcolon n = 1$.
````

Die oben definierte Norm $||x||$ gibt uns den Abstand des Punktes $x \in \mathbb{R}^n$ zum Nullpunkt $\vec{0} \in \mathbb{R}^n$, also gerade die Länge des Vektors $(x - \vec{0}) \in \mathbb{R}^n$.

Folgender wichtiger Satz hilft uns dabei die Eigenschaften der Norm noch besser zu charakterisieren.

````{prf:theorem} Cauchy-Schwarz Ungleichung
:label: satz:cauchy-schwarz_r

Seien $x,y \in \mathbb{R}^n$.
Dann gilt

```{math}
:label: eq:cauchy-schwarz_r

| \langle x, y \rangle | \ \leq \ ||x|| \cdot ||y||.
```

Und es gilt außerdem
\begin{equation*}
| \langle x, y \rangle | \ = \ ||x|| \cdot ||y|| \quad \Leftrightarrow \quad x \text{ und } y \text{ sind linear abhängig}.
\end{equation*}
````

````{prf:proof}
Da die Wurzelfunktion monoton ist, können wir beide Seiten quadrieren, ohne dass sich an der Aussage etwas ändert.
Wir müssen also zeigen, dass gilt

```{math}
:label: eq:cauchy-schwarz_r_beweis

||x||^2 \cdot ||y||^2 - |\langle x, y \rangle|^2 \ = \ \langle x,x \rangle \cdot \langle y, y \rangle - \langle x, y \rangle^2 \ \geq \ 0.
```

Wir bedienen uns des folgenden Tricks.
Wir betrachten eine Matrix $A \in \mathbb{R}^{2 \times n}$ mit
\begin{equation*}
A \ \coloneqq \
\begin{pmatrix}
x_1 & \ldots & x_n\\
y_1 & \ldots & y_n
\end{pmatrix}.
\end{equation*}
Multiplizieren wir nun $A$ von rechts mit $A^T \in \mathbb{R}^{n \times 2}$, so erhalten wir
\begin{equation*}
AA^T \ = \
\begin{pmatrix}
\langle x, x \rangle & \langle x, y \rangle\\
\langle y, x \rangle & \langle y, y \rangle
\end{pmatrix}.
\end{equation*}
Wegen der Symmetrie des Skalarprodukts können wir die linke Seite der Gleichung {eq}`eq:cauchy-schwarz_r_beweis` ersetzen durch den Ausdruck $\det(AA^T)$ und müssen nur zeigen, dass $\det(AA^T) \geq 0$ gilt.
Nach dem Determinanten-Multiplikationstheorem in Satz 3.3.7 {cite:p}`fischer` lässt sich die Determinante von $AA^T$ über die Produkte aller $(2 \times 2)$-Minoren ausrechnen und im vorliegenden Fall gilt
\begin{equation*}
\det(AA^T) \ = \ \sum_{1 \leq k_1 \leq k_2 \leq n} \left(\det(A^{k_1,k_2})\right)^2 \ \geq \ 0.
\end{equation*}
Die Nichtnegativität der Determinante nutzt hier wieder eine Eigenschaft des Körpers $\mathbb{R}$, da die Summe von quadratischen Termen nie negativ werden kann.

Es bleibt nur noch die Gleichheit zu überprüfen.
\begin{equation*}
\begin{split}
& | \langle x, y \rangle | \ = \ ||x|| \cdot ||y|| \\
\Leftrightarrow \ &\det(AA^T) \ = \ \sum_{1 \leq k_1 \leq k_2 \leq n} \left(\det(A^{k_1,k_2})\right)^2 \ = \ 0 \\
\Leftrightarrow \ &\det(A^{k_1,k_2}) \ = \ 0, \quad \text{ für alle } 1 \leq k_1 \leq k_2 \leq n \\
\Leftrightarrow \ &\Rang(A) < 2\\
\Leftrightarrow \ &x \text{ und } y \text{ sind linear abhängig }.
\end{split}
\end{equation*}
````

Mit Hilfe der Cauchy-Schwarz Ungleichung können wir die wichtigsten Eigenschaften der Norm zeigen.

````{prf:lemma} Eigenschaften der Norm
:label: lem:norm_eigenschaften

Seien $x, y \in \mathbb{R}^n$ Vektoren und $\lambda \in \mathbb{R}$ ein Skalar, dann gelten für die durch das kanonische Skalarprodukt induzierte Norm folgende Eigenschaften.

i) $||x|| \ = \ 0 \quad \Leftrightarrow \quad x \ = \ 0$,

ii) $||\lambda x|| \ = \ |\lambda| \cdot ||x||$,

iii) $||x + y|| \ \leq \ ||x|| + ||y||$.
````

````{prf:proof}
Die ersten beiden Eigenschaften $i)$ und $ii)$ lassen sich direkt durch Nachrechnen verifizieren.
Die dritte Eigenschaft der Dreiecksungleichung können wir mit Hilfe der Cauchy-Schwarz Ungleichung aus Satz {prf:ref}`satz:cauchy-schwarz_r` zeigen.
Es gilt
\begin{equation*}
\begin{split}
||x + y||^2 \ = \ \langle x+y, x+y \rangle \ &= \ \langle x, x \rangle + 2 \langle x, y \rangle + \langle y, y \rangle \\
&\leq \ \langle x, x \rangle + 2 ||x|| \cdot ||y|| + \langle y, y \rangle \ \leq \ (||x|| + ||y||)^2.
\end{split}
\end{equation*}
Da die Wurzelfunktion monoton ist gilt obige Abschätzung auch ohne die Quadrate auf der linken und rechten Seite der Ungleichung.
````

Dadurch, dass die Norm die Länge eines Vektors beschreibt, können wir sie nutzen um Abstände zu beschreiben.
Um nun den Abstand zwischen zwei Punkten $x, y \in \mathbb{R}^n$ zu messen führt man den Begriff einer durch die Norm induzierten Metrik ein.

````{prf:definition} Metrik
Seien $x,y \in \mathbb{R}^n$ zwei Punkte.
Dann induziert die Norm $||\cdot||$ des Vektorraums eine _Metrik_ genannte Abbildung
\begin{align*}
d \colon \mathbb{R}^n \times \mathbb{R}^n \ &\rightarrow \ \mathbb{R}^+_0, \\
(x,y) \ &\mapsto \ d(x,y) \ \coloneqq \ ||x - y|| \ = \ \sqrt{\sum_{i=1}^n (x_i - y_i)^2},
\end{align*}
mit der man den Abstand (bezüglich der Norm) zwischen $x$ und $y$ messen kann.
````

````{prf:remark}
Wie man im Laufe des Studiums noch lernt, wird je nach Wahl der Norm in Definition {prf:ref}`def:norm_r` eine andere Metrik induziert, die den Abstandsbegriff maßgeblich beeinflusst.
Letzten Endes bestimmt dies auch die sogenannte _Topologie_ eines Vektorraums.
Dies wird durch folgende Relationen dargestellt:

| **Skalarprodukt** (Euklidischer / Unitärer Vektorraum) |
| :----------------------------------------------------- |
| $\quad \downarrow $  induziert                         |
| **Norm** (Normierter Vektorraum)                       |
| $\quad \downarrow $ induziert                          |
| **Metrik** (Metrischer Vektorraum)                     |
| $\quad \downarrow $ induziert                          |
| **Topologie** (Topologischer Vektorraum)               |
````

Wir können nun wesentliche Eigenschaften einer Metrik festhalten.

````{prf:lemma} Eigenschaften einer Metrik
Seien $x,y \in \mathbb{R}^n$, dann gelten für die Metrik $d(x,y) = ||x - y||$ folgende Eigenschaften.

i) $d(x,y) \ = \ 0 \quad \Leftrightarrow \quad x \ = \ y$,

ii) $d(x,y) \  = \ d(y,x)$,

iii) $d(x,z) \ \leq \ d(x,y) + d(y,z)$.
````

````{prf:proof}
Die ersten beiden Eigenschaften $i)$ und $ii)$ sind klar und lassen sich direkt durch Nachrechnen verifizieren.
Die dritte Eigenschaft $iii)$ folgt direkt aus der Dreiecksungleichung der Norm in Lemma {prf:ref}`lem:norm_eigenschaften`, da
\begin{equation*}
d(x,z) \ = \ ||x -z|| \ = \ ||x - y + y - z|| \ \leq \ ||x -y|| + ||y - z|| \ = \ d(x,y) + d(y,z).
\end{equation*}
````

````{prf:example} Manhattan Metrik
Eine interessante Metrik, die nicht durch die Euklidische Norm induziert wird, ist die sogenannte _Manhattan Metrik_, die für zwei Vektoren $x, y \in \mathbb{R}^n$ wie folgt definiert ist:
\begin{equation*}
d(x,y) \ \coloneqq \ \sum_{i=1}^n|x_i - y_i| \ \eqqcolon \ ||x - y||_1.
\end{equation*}
Der Name lehnt sich an die orthogonalen Straßengitter Manhattans an, die dazu führen, dass man zum Erreichen eines Ziels nur durch Aneinanderreihung vertikaler und horizontaler Wegstücke zu überwinden. Hierbei weisen alle Wege, die einen näher zum Ziel bringen, immer die gleiche Entfernung auf.
````

Die Cauchy-Schwarz Ungleichung in Satz {prf:ref}`satz:cauchy-schwarz_r` liefert uns nicht nur nützliche Aussagen bei der Längenmessung (wie die Dreiecksungleichung für die Norm), sondern liefert zudem eine Methode zur _Winkelmessung_ im $\mathbb{R}^n$.
Betrachtet man nämlich den Quotienten der linken und rechten Seite in der Cauchy-Schwarz Ungleichung {eq}`eq:cauchy-schwarz_r`, so erhält man für zwei Vektoren $x,y \in \mathbb{R}^n$ mit $x,y \neq \vec{0}$ folgende Abschätzung

```{math}
:label: eq:angle_quotient

-1 \ \leq \frac{\langle x, y \rangle}{||x|| \cdot ||y||} \ \leq 1.
```

Der Quotient ist also ähnlich beschränkt wie die Kosinusfunktion $\cos \colon [0, \pi] \rightarrow [-1, 1]$ und es wird klar, dass es für fixe Vektoren $x$ und $y$ genau ein Winkel $\alpha \in [0, \pi]$  existiert, so dass
\begin{equation*}
\cos \alpha \ = \ \frac{\langle x, y \rangle}{||x|| \cdot ||y||}.
\end{equation*}
Dies macht auch geometrisch Sinn, da das Skalarprodukt $\langle x, y \rangle$ von $x$ und $y$ als Maß für den Anteil des einen Vektors, der in Richtung des anderen Vektors zeigt interpretiert werden kann.
Je größer dieser Anteil ist, desto kleiner ist der Winkel $\alpha$ zwischen den beiden Vektoren $x$ und $y$.

Dies motiviert die folgende Definition zur Winkelmessung in $\mathbb{R}^n$.

````{prf:definition}
:label: def:winkelmessung

Seien $x,y \in \mathbb{R}^n$ zwei Vektoren mit $x,y \neq \vec{0}$.
Dann definieren wir den Winkel $\measuredangle(x,y)$ zwischen $x$ und $y$ als den Arkuskosinus des Quotienten in {eq}`eq:angle_quotient`, d.h.

```{math}
:label: eq:winkelberechnung

\measuredangle(x,y) \ \coloneqq \ \arccos \frac{\langle x, y \rangle}{||x|| \cdot ||y||} .
```

````

````{prf:remark}
:label: bem:winkelmessung

Aus den Eigenschaften des Skalarprodukts in Lemma {prf:ref}`lem:skalarprodukt_r` folgen direkt folgende sinnvolle Beobachtungen für Vektoren $x,y \in \mathbb{R}^n$ mit $x,y \neq \vec{0}$ und positive Skalare $\lambda > 0$:

i) $\measuredangle(x,y) \ = \ \measuredangle(y,x)$,

ii) $\measuredangle(\lambda x,y) \ = \ \measuredangle(x,\lambda y) \ = \  \measuredangle(x, y)$.
````

Zur Veranschaulichung dieser wichtigen geometrischen Erkenntnisse soll das folgende Beispiel dienen.

````{prf:example}
Um zu verstehen, dass die Definition {prf:ref}`def:winkelmessung` für die Winkelmessung sich mit unserer Vorstellung eines unorientierten Winkels deckt, betrachten wir zwei Beispiele:

* Es seien zwei Vektoren $x,y \in \mathbb{R}^3$ gegeben mit:
\begin{equation*}
x \ \coloneqq \ 
\begin{pmatrix}
1 \\ 2 \\ 3
\end{pmatrix}, \quad
y \ \coloneqq \ 
\begin{pmatrix}
4 \\ 5 \\ 6
\end{pmatrix}.
\end{equation*}
Um den Winkel $\alpha \in [0, \pi]$ zwischen $x$ und $y$ mittels der Formel {eq}`eq:winkelberechnung` zu berechnen, sehen wir uns zunächst die einzelnen Terme an:
\begin{equation*}
\begin{split}
\langle x, y \rangle \ &= \ \langle (1, 2, 3)^T, (4, 5, 6)^T \rangle \ = \ 4 + 10 + 18 \ = \ 32,\\
||x|| \ &= \ \sqrt{1 + 4 + 9} \ = \ \sqrt{14}, \qquad ||y|| \ = \ \sqrt{16 + 25 + 36} \ = \ \sqrt{77}.
\end{split}
\end{equation*}
Damit können wir den Winkel $\alpha$ wie folgt bestimmen:
\begin{equation*}
\alpha \ \coloneqq \ \measuredangle(x,y) \ = \ \arccos \frac{\langle x, y \rangle}{||x|| \cdot ||y||}  \ = \ \arccos \frac{32}{\sqrt{14\cdot77}} \ \approx \ 13^\circ.
\end{equation*}

* Für zwei allgemeine Vektoren $x,y \in \mathbb{R}^2$ führen wir normierte Varianten $x',y' \in \mathbb{R}^n$ mit
\begin{equation*}
x' \ \coloneqq \ \frac{x}{||x||}, \quad y' \ \coloneqq \ \frac{y}{||y||}.
\end{equation*}
Aus der Normierung wird klar, dass $||x|| = ||y|| = 1$ gilt und auf Grund von Bemerkung {prf:ref}`bem:winkelmessung` sehen wir ein, dass $\measuredangle(x,y) = \measuredangle(x',y')$.

Da $x'$ und $y'$ auf dem Einheitskreis $\mathbb{S}^1$ liegen, wissen wir aus der Analysis, dass eine Parametrisierung mit Winkeln $\alpha, \beta \in [0, 2\pi [$ gibt, so dass
\begin{equation*}
x' \ = \ (\cos \alpha, \sin \alpha), \quad y' \ = \ (\cos \beta, \sin \beta).
\end{equation*}
Mit den Additionsregeln für den Kosinus in \cite[Kapitel 5.5]{burger_2020} können wir also schreiben
\begin{equation*}
\langle x', y' \rangle \ = \ \cos \alpha \cos \beta + \sin \alpha \sin \beta \ = \ \cos(\beta - \alpha),
\end{equation*}
%wobei wir \warn{$\beta - \alpha \in [0, \pi]$} annehmen können.
wobei wir $\beta - \alpha \in [0, \pi]$ annehmen können.

Insgesamt folgt also, dass
\begin{equation*}
\measuredangle(x,y) \ = \ \beta - \alpha .%,
\end{equation*}
````

Für zwei Vektoren $x,y \in \mathbb{R}^n$ mit $x,y \neq \vec{0}$ wird klar, dass der Winkel zwischen den beiden genau $\frac{\pi}{2}$ (oder $90^{\circ}$) entspricht, wenn das Skalarprodukt $\langle x, y\rangle = 0$ ist.
Das motiviert die folgende Definition.

````{prf:definition} Orthogonalität von Vektoren
Zwei Vektoren $x,y \in \mathbb{R}^n$ heißen _senkrecht_ oder _orthogonal_, wenn für sie gilt
\begin{equation*}
\langle x, y \rangle \ = \ 0.
\end{equation*}
Diese Definition gilt auch, wenn einer der beiden Vektoren der Nullvektor ist.
Sind die Vektoren $x$ und $y$ orthogonal, so schreiben wir auch häufig $x \perp y$.
````
