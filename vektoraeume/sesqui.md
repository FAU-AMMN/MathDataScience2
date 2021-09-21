# Bilinear- und Sesquilinearformen
Die im vorigen Kapitel besprochenen Werkzeuge zur Messung von Längen, Abständen und Winkeln leiteten sich aus dem Begriff des Skalarprodukts ab. 
Wir werden im Folgenden sehen, dass ein Skalarprodukt nur ein Spezialfall einer ganzen Familie von allgemeineren Abbildungen ist, den sogenannten Bilinear- und Sesquilinearformen.
Zur Untersuchung dieser abstrakteren mathematischen Begriffe sei im Folgenden $\mathbb{K}$ wieder ein beliebiger Körper.

````{prf:definition} Bilinearform
Seien $v,v',w,w' \in V$ und ein Skalar $\lambda \in \mathbb{K}$ gegeben.
Wir nennen eine Abbildung
\begin{align*}
s \ \colon \ V \times V \ &\rightarrow \ \mathbb{K}, \\
(v,w) \ &\to \ s(v,w),
\end{align*}
_Bilinearform} auf $V$, wenn sie _bilinear_ ist, d.h., linear in beiden Argumenten mit
\begin{equation*}
\begin{split}
s(v+v', w) \ = \ s(v,&w) +  s(v',w), \quad s(v, w+w') \ = \ s(v,w) + s(v,w'), \\
&s(\lambda v, w) \ = \ \lambda s(v,w) \ = \ s(v,\lambda w).
\end{split}
\end{equation*}
Die Abbildung $s$ heißt _symmetrisch_, falls gilt
\begin{equation*}
s(v,w) \ = \ s(w,v)
\end{equation*}
und _alternierend_ oder _schiefsymmetrisch_, falls gilt
\begin{equation*}
s(v,w) \ = \ -s(w,v).
\end{equation*}
````

````{prf:example}
:label: bsp:bilinearform
Sei $\mathbb{K} = \mathbb{R}$ und $I = [a,b] \subset \mathbb{R}$ ein Intervall.
Wir betrachten den Vektorrraum der auf dem Intervall $I$ stetigen Funktionen $V = C(I; \mathbb{R})$ und definieren eine Abbildung
\begin{align*}
s  \colon  V \times V \ &\rightarrow \ \mathbb{R}, \\
(f,g) \ &\mapsto \ s(f,g) \ \coloneqq \ \int_a^b f(x) g(x) \, \idx.
\end{align*}
Es folgt aus den Rechenregeln für Integrale, dass die Abbildung $s$ eine symmetrische Bilinearform auf $V$ darstellt.
````

Im obigen Beispiel war der Vektorraum $V$ nicht endlich-dimensional.
Schränken wir uns jedoch auf endlich-dimensionale Vektorräume ein, so lässt sich erkennen, dass sich Bilinearformen durch Matrizen beschreiben lassen.

````{prf:definition} Darstellende Matrix einer Bilinearform
Sei $V$ ein endlich-dimensionaler $\mathbb{K}$-Vektorraum und sei $B \coloneqq (v_1, \ldots, v_n)$ eine Basis von $V$.
Außerdem sei $s$ eine Bilinearform auf $V$.
Dann nennen wir die Matrix $M_B(s) \in \mathbb{K}^{n\times n}$ mit
\begin{equation*}
M_B(s) \ \coloneqq \ (s(v_i, v_j))_{1 \leq i,j \leq n}
\end{equation*}
die _darstellende Matrix_ von $s$ bezüglich $B$.
````

````{prf:theorem}
Sei $s$ eine Bilinearform auf $V$ mit Basis $B = (v_1, \ldots, v_n)$.
Sei außerdem $\Phi_B \colon \mathbb{K}^n \rightarrow V$ das zugehörige Koordinatensystem zur Basis $B$ und $A \coloneqq M_B(s)$ die darstellende Matrix von $s$ bezüglich $B$.
Wenn wir zwei Vektoren $v,w \in V$ betrachten mit den Koordinaten
\begin{equation*}
x \ = \ \Phi_B^{-1}(v), \qquad y \ = \ \Phi_B^{-1}(w),
\end{equation*}
dann gilt
\begin{equation*}
s(v,w) \ = \ (x_1, \ldots, x_n)
\begin{pmatrix}
a_{11} & \cdots & a_{1n}\\
\vdots & & \vdots \\
a_{n1} & \cdots & a_{nn}
\end{pmatrix}
\begin{pmatrix}
y_1\\
\vdots \\
y_n
\end{pmatrix} \ = \ x^T A y.
\end{equation*}
````

````{prf:proof}
Wir können schreiben
\begin{equation*}
s(v,w) \ = \ s(x_1v_1 + \ldots + x_nv_n, y_1v_1 + \ldots + y_nv_n) \ = \ \sum_{i=1}^n \sum_{j=1}^n x_i s(v_i, v_j) y_j.
\end{equation*}
Wir sehen also, dass durch Ausnutzung der Bilinearität von $s$ wir eine Summe aus $n^2$ Summanden erhalten.
Da $A$ die darstellende Matrix von $s$ bezüglich der Basis $B$ ist gilt $s(v_i, v_j) = a_{ij}$, womit schon die Behauptung folgt.
````

Wir wollen die Darstellung einer Bilinearform durch eine Matrix durch folgende zwei Beispiele besser verstehen.

````{prf:example}
Sei $V = \mathbb{R}^2$ ein Euklidischer Vektorraum mit dem kanonischen Skalarprodukt als symmetrischer Bilinearform $s(v,w) \coloneqq \langle v, w\rangle$ auf $V$.
Seien außerdem $v,w \in \mathbb{R}^2$ mit
\begin{equation*}
v \ \coloneqq \
\begin{pmatrix}
2 \\
-1
\end{pmatrix}, \qquad
w \ \coloneqq \
\begin{pmatrix}
0 \\
5
\end{pmatrix}.
\end{equation*}
Wir betrachten die darstellenden Matrix des Skalarprodukts bezüglich zweier unterschiedlicher Basen von $V$ im Folgenden.


i) Wir wählen im ersten Beispiel  die kanonische Standardbasis $B=(e_1, e_2)$ des $\mathbb{R}^2$.
Wir berechnen die darstellende Matrix des Skalarprodukts bezüglich der Basis $B$ als
\begin{equation*}
A \ \coloneqq \ M_B(s) \ = \
\begin{pmatrix}
\langle e_1, e_1 \rangle & \langle e_1, e_2 \rangle\\
\langle e_2, e_1 \rangle & \langle e_2, e_2 \rangle
\end{pmatrix}
\ = \ \begin{pmatrix}
1 &  0 \\
0 & 1
\end{pmatrix}
\ = \ I_2.
\end{equation*}
Bezüglich der Basis $B$ erhalten wir für die Vektoren $v$ und $w$ die folgenden Koordinaten:
\begin{equation*}
x \ = \ \Phi_B(v) \ = \ (2, -1)^T \ = \ v, \qquad y \ = \ \Phi_B(w) \ = \ (0, 5)^T \ = \ w.
\end{equation*}
Damit gilt dann insgesamt:
\begin{equation*}
-5 \ = \ \langle (2,-1)^T, (0,5)^T \rangle \ = \ \langle v, w \rangle \ = \ x^T A y \ = \ v^T I_2 w \ = \ \langle v, w \rangle \ = \ -5.
\end{equation*}

ii) Wir wählen im zweiten Beispiel die Basis $B=(v_1, v_2)$ des $\mathbb{R}^2$ mit
\begin{equation*}
v_1 \ \coloneqq \
\begin{pmatrix}
1\\
2
\end{pmatrix}, \qquad
v_2 \ \coloneqq \
\begin{pmatrix}
2\\
-1
\end{pmatrix}
\end{equation*}
Wir berechnen die darstellende Matrix des Skalarprodukts bezüglich der Basis $B$ als
\begin{equation*}
A \ \coloneqq \ M_B(s) \ = \
\begin{pmatrix}
\langle v_1, v_1 \rangle & \langle v_1, v_2 \rangle\\
\langle v_2, v_1 \rangle & \langle v_2, v_2 \rangle
\end{pmatrix}
\ = \ \begin{pmatrix}
5 &  0 \\
0 & 5
\end{pmatrix}.
\end{equation*}
Bezüglich der Basis $B$ erhalten wir für die Vektoren $v$ und $w$ die folgenden Koordinaten:
\begin{equation*}
x \ = \ \Phi_B(v) \ = \ (0,1)^T, \qquad y \ = \ \Phi_B(w) \ = \ (2,-1)^T.
\end{equation*}
Damit gilt dann insgesamt:
\begin{equation*}
\begin{split}
-5 \ &= \ \langle (2,-1)^T, (0,5)^T \rangle \ = \ \langle v, w \rangle \ = \ x^T A y \\
 &= \
(0,1)^T \cdot
\begin{pmatrix}
5 & 0\\
0 & 5
\end{pmatrix}
\cdot
\begin{pmatrix}
2 \\
-1
\end{pmatrix}
\ = \ (0,1)^T
\begin{pmatrix}
10 \\
-5
\end{pmatrix} \ = \ -5.
\end{split}
\end{equation*}
````

Zwischen Matrizen und Bilinearformen existiert ein starker Zusammenhang, wie wir im Folgenden feststellen.

````{prf:remark} Bijektivität und Symmetrie von Bilinearformen
Sei $V$ ein endlich-dimensionaler $\mathbb{K}$-Vektorraum und $B$ eine zugehörige Basis von $V$.
Dann ist die Abbildung
\begin{equation*}
s \ \mapsto \ M_B(s)
\end{equation*}
von den Bilinearformen auf $V$ nach $\mathbb{K}^{n \times n}$ _bijektiv_.
Außerdem ist $s$ genau dann _symmetrisch_, wenn $M_B(s)$ symmetrisch ist.
````

````{prf:lemma}
:label: lem:transformationsformel
Seien $A,B \in \mathbb{K}^{n \times n}$ gegeben mit
\begin{equation*}
x^T A y \ = \ x^T B y,
\end{equation*}
für alle $x,y \in \mathbb{K}^n$.
Dann gilt schon $A = B$.
````

````{prf:proof}
Da die Gleichung $x^TAy = x^TBy$ für alle Vektoren in $\mathbb{K}^n$ gilt, muss sie insbesondere auch für die Einheitsvektoren gelten und damit folgt für alle Indizes $1 \leq i,j \leq n$:
\begin{equation*}
a_{i,j} \ = \ e_i^T A e_j \ = \ e_i^T B e_j \ = \ b_{i,j}.
\end{equation*}
Damit folgt also direkt, dass $A=B$ ist.
````

````{prf:theorem} Transformationsformel
:label: satz:transformationsformel

Sei $V$ ein endlich-dimensionaler Vektorraum mit zwei Basen $A,B$.
Sei außerdem $T^B_A$ die entsprechende Transformationsmatrix von Basis $B$ zu Basis $A$.
Für jede Bilinearform $s$ auf $V$ gilt dann die folgende Transformationsformel:

```{math}
:label: eq:transformationsformel
M_B(s) \ = \ (T^B_A)^T \cdot M_A(s) \cdot T^B_A.
```

````

````{prf:proof}
Seien $\Phi_A, \Phi_B \colon \mathbb{K}^n \rightarrow V$ Koordinatensysteme von $V$ bezüglich der Basen $A$ und $B$.
Seien außerdem $v, v' \in V$ mit 
\begin{equation*}
v \, = \, \Phi_A(x) \, = \, \Phi_B(y), \qquad v' \, = \, \Phi_A(x') \, = \, \Phi_B(y').
\end{equation*}
Sei weiterhin $T \coloneqq T^B_A$, so sehen wir ein, dass gilt
\begin{equation*}
x \, = \, Ty, \qquad x' \, = \, Ty'.
\end{equation*}
Damit können wir folgern, dass gilt
\begin{equation*}
y^T M_B(s) y' \ = \ s(v,v') \ = \ x^T M_A(s) x' \ = \ (Ty)^T M_A(s) (Ty') \ = \ y^T (T^eqrefT M_A(s) T) y'.
\end{equation*}
Mit Lemma {prf:ref}`lem:transformationsformel` folgt dann schon, dass gelten muss:
\begin{equation*}
M_B(s) \ = \ (T^B_A)^T \cdot M_A(s) \cdot T^B_A.
\end{equation*}
````

````{prf:remark}
Das Transformationsverhalten bei Endomorphismen in Kapitel {ref}`ch:eigenwerttheorie` unterscheidet sich von der Transformationsformel {eq}`eq:transformationsformel`, da für einen Endomorphismus $F \colon V \rightarrow V$ galt:
\begin{equation*}
M_B(F) \ = \ \underbrace{(T^B_A)^{-1}}_{= T^A_B} \cdot M_A(F) \cdot T^B_A.
\end{equation*}
````

````{prf:definition} [Quadratische Form]
Sei $s$ eine symmetrische Bilinearform auf $V$ und $v \in V$.
Dann definieren wir die Abbildung
\begin{align*}
q \colon V \ &\rightarrow \ \mathbb{K},\\
v \ &\mapsto \ q(v) \ \coloneqq \ s(v,v),
\end{align*}
die zugehörige _quadratische Form_ von $s$.
Aus der Bilinearität von $s$ folgt für alle Skalare $\lambda \in \mathbb{K}$ direkt, dass gilt
\begin{equation*}
q(\lambda v) \ = \ \lambda^2 q(v).
\end{equation*}
````

Wir wollen die quadratische Form zu der wohl naheliegensten Bilinearform betrachten - dem kanonischen Skalarprodukt in $\mathbb{R}^n$.

````{prf:example}
Sei $V = \mathbb{R}^n$ ein Euklidischer Vektorraum.
Sei außerdem $v \in V$ und ein Skalar $\lambda \in \mathbb{R}$ gegeben.
Wir betrachten das kanonische Skalarprodukt aus Definition {prf:ref}`def:skalarprodukt_r` und bestimmen die zugehörige quadratische Form als
\begin{equation*}
q(v) \ = \ \langle v, v \rangle \ = \ v_1^2 + \ldots v_n^2 \ = \ ||v||^2.
\end{equation*}
Wir sehen also ein, dass die quadratische Norm die quadratische Form des kanonischen Skalarprodukts darstellt und in der Tat gilt auch:
\begin{equation*}
q(\lambda v) \ = \ ||\lambda v||^2 \ = \ \lambda^2 ||v||^2 \ = \ \lambda^2 q(v).
\end{equation*}
````

````{prf:definition} Sesquilinearform
Sei $V$ ein komplexer Vektorraum und seien $v,v',w,w' \in V$ und ein Skalar $\lambda \in \mathbb{C}$ gegeben.
Wir nennen eine Abbildung
\begin{align*}
s \ \colon \ V \times V \ &\rightarrow \ \mathbb{C}, \\
(v,w) \ &\to \ s(v,w),
\end{align*}
_Sesquilinearform_ auf $V$, wenn sie linear im ersten Argument und semilinear im zweiten Argument ist, d.h.
\begin{equation*}
\begin{split}
s(v+v', w) \ &= \ s(v,w) +  s(v',w), \quad s(v, w+w') \ = \ s(v,w) + s(v,w'), \\
&s(\lambda v, w) \ = \ \lambda s(v,w), \quad s(v, \lambda w)  \ = \ \overline{\lambda}s(v,w).
\end{split}
\end{equation*}
Die Abbildung $s$ heißt _hermitesch_, falls zusätzlich gilt
\begin{equation*}
s(v,w) \ = \ \overline{s(w,v)}.
\end{equation*}
Zu einer Sesquilinearform $s$ auf $V$ definieren wir eine zugehörige _quadratische Form_
\begin{align*}
q \ \colon \ V  \ &\rightarrow \ \mathbb{C}, \\
v \ &\to \ q(v) \ \coloneqq \ s(v,v).
\end{align*}
````

Neben dem komplexen Skalarprodukt $\langle \cdot, \cdot \rangle_c$ aus Definition {prf:ref}`def:skalarprodukt_c` gibt es noch weitere Sesquilinearformen, wie das folgende Beispiel zeigt.

````{prf:example}
Sei $\mathbb{K} = \mathbb{C}$ und $I = [a,b] \subset \mathbb{R}$ ein Intervall.
Wir betrachten den Vektorrraum der auf dem Intervall $I$ stetigen, komplex-wertigen Funktionen $V = C(I; \mathbb{C})$ und definieren eine Abbildung
\begin{align*}
s  \colon  V \times V \ &\rightarrow \ \mathbb{C}, \\
(f,g) \ &\mapsto \ s(f,g) \ \coloneqq \ \int_a^b f(x) \overline{g}(x) \, \idx.
\end{align*}
Es folgt aus den Rechenregeln für Integrale, dass die Abbildung $s$ eine Sesquilinearform auf $V$ darstellt.
````

````{prf:remark}
Ähnlich wie bei Bilinearformen können wir folgende Charakteristiken feststellen.

i) Eine Sesquilinearform kann auch durch eine Matrix beschrieben werden.
Hierzu müssen wir allerdings die komplexe Konjugation berücksichtigen.
Sei $B = (v_1, \ldots, v_n)$ eine Basis eines komplexen Vektorraums $V$ und $s$ eine Sesquilinearform auf $V$.
Die darstellende Matrix $M_B(s)$ von $s$ bezüglich der Basis $B$ ist gegeben durch:
\begin{equation*}
A \ \coloneqq \ (M_B(s))_{ij} \ = \ s(v_i, v_j), \qquad \text{ für alle } 1 \leq i,j \leq n.
\end{equation*}
Die Matrix $A$ ist genau dann hermitesch, d.h., $A^T = \overline{A}$, falls die Sesquilinearform $s$ hermitesch ist.
Für zwei Vektoren $v,w \in V$ mit Koordinaten
\begin{equation*}
x \ = \ \Phi_B(v), \qquad y \ = \ \Phi_B(w),
\end{equation*}
lässt sich die Sesquilinearform $s$ ausdrücken durch
\begin{equation*}
s(v,w) \ = \  (x_1, \ldots, x_n)
\begin{pmatrix}
a_{11} & \cdots & a_{1n}\\
\vdots & & \vdots \\
a_{n1} & \cdots & a_{nn}
\end{pmatrix}
\begin{pmatrix}
\overline{y_1}\\
\vdots \\
\overline{y_n}
\end{pmatrix} \ = \ x^T A \overline{y}.
\end{equation*}

ii) Sei $C$ eine weitere Basis von $V$ und sei $T \coloneqq T^C_B$ die Transformationsmatrix von Basis $C$ zu Basis $B$.
Dann erhalten wir folgendes Transformationsverhalten für die darstellende Matrix $M_C(s)$ von $s$ bezüglich $C$:
\begin{equation*}
M_C(s) \ = \ T^T \cdot M_B(s) \cdot \overline{T}.
\end{equation*}
````

Es ist in der Tat möglich symmetrische Bilinearformen und Sesquilinearformen nur an Hand ihrer quadratischen Formen zu rekonstruieren.
Diesen mathematischen Zusammenhang nennt man Polarisierung und wird durch folgenden Satz beschrieben.

````{prf:theorem} Polarisierung
:label: satz:polarisierung

Sei $V$ ein $\mathbb{R}$-Vektorraum und $W$ ein $\mathbb{C}$-Vektorraum.
Sei außerdem $b$ eine symmetrische Bilinearform auf $V$ mit zugehöriger quadratischer Form $q(v) = b(v,v)$ und $s$ eine Sesquilinearform auf $W$ mit zugehöriger quadratischer Form $p(v) = s(v,v)$.
Dann gelten die folgenden, _Polarisierung_ genannten, Zusammenhänge:

i) $b(v,w) \ = \ \frac{1}{4} [q(v+w) - q(v - w)]$, \quad für alle $v,w \in V$,

ii) $s(v,w) \ = \ \frac{1}{4} [p(v+w) - p(v - w) + i \cdot p(v + iw) - i \cdot p(v - iw)]$, \quad für alle $v,w \in W$.
````

````{prf:proof}
In der Hausaufgabe zu zeigen.
````

Im reellen Fall ist es entscheidend, dass man in Satz {prf:ref}`satz:polarisierung` eine symmetrische Bilinearform annimmt, da die Polarisierungsformel nicht für beliebige Bilinearformen gilt, wie das folgende Beispiel zeigt:

````{prf:example}
Sei $V = \mathbb{R}^2$ und wir betrachten die folgende Bilinearform
\begin{equation*}
s(x,y) \ \coloneqq \ x^T 
\begin{pmatrix}
0 & -1\\
1 & 0
\end{pmatrix}
y
\ = \ -x_1y_2 + x_2y_1.
\end{equation*}
Es gilt offensichtlich für alle $x \in \mathbb{R}^2$
\begin{equation*}
s(x,x) \ = \ -x_1x_2 + x_1x_2 \ = \ 0.
\end{equation*}
Andererseits gilt jedoch nicht die Polarisierungsformel, wie man im folgenden sieht
\begin{equation*}
1 \ = \ s((1,0)^T, (0,1)^T) \ \neq \ \frac{1}{4}[\underbrace{s((1,1)^T, (1,1)^T)}_{=0} - \underbrace{s((1,-1)^T, (1,-1)^T)}_{=0}] \ = \ 0.
\end{equation*}
````

````{prf:definition} Positive Definitheit
Wir wollen im folgenden den Begriff der positiven Definitheit für Matrizen und symmetrische Bilinearformen bzw. hermitesche Sesquilinearformen einführen.
Sei $V$ ein $\mathbb{K}$-Vektorraum.

i) Eine symmetrische Bilinearform bzw. hermitesche Sesquilinearform $s \colon V \times V \rightarrow \mathbb{K}$ heißt _positiv definit} falls für alle $v \in V$ mit $v \neq 0$ gilt:
\begin{equation*}
s(v,v) \ > \ 0.
\end{equation*}

ii) Eine symmetrische bzw. hermitesche Matrix $A \in \mathbb{K}^{n \times n}$ heißt _positiv definit} falls für alle $x \in \mathbb{K}^n$ mit $x \neq 0$ gilt:
\begin{equation*}
x^T A \overline{x} \ > \ 0.
\end{equation*}
````

Schlussendlich sind wir in der Lage den Begriff eines Euklidischen und unitären Vektorraums mit Hilfe von Bilinear- und Sesquilinearformen zu definieren.

````{prf:definition} Euklidischer und unitärer Vektorraum
Wir nennen eine positiv definite symmetrische Bilinearform bzw. eine positiv definite hermitesche Sesquilinearform ein _Skalarprodukt}.
Einen reellen bzw. komplexen Vektorraum zusammen mit einem Skalarprodukt nennen wir _Euklidischen} bzw. _unitären Vektorraum}.
````
