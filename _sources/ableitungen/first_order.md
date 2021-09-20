# Differentialoperatoren erster Ordnung

In diesem Abschnitt wollen wir einige wichtige Operatoren einführen, welche direkt auf dem Konzept der partiellen Differenzierbarkeit von Funktionen basieren. 
Insbesondere werden wir den Gradienten, die Divergenz und die Rotation als Differentialoperatoren erster Ordnung kennenlernen, für deren Definition man nur erste partielle Ableitungen verwendet, und die eine zentrale Rolle in der Mathematik und Physik spielen.

Der erste Operator, den wir diskutieren wollen, ist der sogenannte *Gradient*, der alle partiellen Ableitungen einer Funktionen in einem Vektor sammelt.

````{prf:definition} Gradient
Sei $U \subset \R^n$ eine Teilmenge.
Für eine partiell differenzierbare Funktion $f:U\rightarrow \R$ heißt der Spaltenvektor
\begin{align*}
\nabla f (x) \ \coloneqq \  \left(\frac{\partial f}{\partial x_1} (x),\ldots,\frac{\partial f}{\partial x_n} (x)\right)^T \ = \ \left(\partial_1 f(x),\ldots,\partial_n f(x)\right)^T
\end{align*}
der *Gradient* von $f$ an der Stelle $x\in U$.

Das Symbol $\nabla$ bezeichnet man hierbei häufig als den *Nabla-Operator*.
````

Wir wollen den Gradienten einer Funktion für ein bereits bekanntes Beispiel im Folgenden berechnen.
````{prf:example} Gradient der Euklidischen Norm
Für die Euklidische Norm aus Beispiel \ref{bsp:norm} hat der Gradient für alle $x\neq 0$ die Form
\begin{align*}
\nabla \, \norm{x}{}_2 \ = \ \left( \partial_1 ||x||_2, \ldots, \partial_n ||x||_2 \right)^T \ = \ \left( \frac{x_1}{||x||_2}, \ldots, \frac{x_n}{||x||_2} \right)^T \ = \ \frac{x}{\norm{x}{}_2}.
\end{align*}
Offensichtlich ist der Gradient der Norm selbst normiert, d.h., es gilt $\big\|\nabla \norm{x}{}_2\big\|_2 = 1$.
````

Viele Rechenregeln der Differentiation für Funktionen mit nur einer Veränderlichen lassen sich problemlos auf Funktionen mit mehreren Veränderlichen generalisieren.
Mit den bisherigen Definitionen können wir bereits die Produktregel für die Ableitung auf den Gradienten einer Funktionen verallgemeinern.

````{prf:lemma} Produktregel für den Gradienten
Sei $U \subset \R^n$ eine offene Teilmenge und seien $f,g:U\rightarrow\R$ zwei partiell differenzierbare Funktion.
Dann gilt die folgende Produktregel für den Gradienten des Produkts der Funktionen
\begin{equation*}
\nabla (f\cdot g)(x) \ = \ [f\cdot (\nabla g) + (\nabla f)\cdot g] (x), \quad \text{ für alle } x \in U.
\end{equation*}
````

````{prf:proof}
Aus Gründen der Übersichtlichkeit verzichten wir bei diesem Beweis auf die Angabe des Funktionsarguments $x \in U$, wodurch die Notation zwar unpräzise, jedoch deutlich übersichtlicher wird.
Wir schreiben den Gradienten des Produkts der beiden Funktionen zunächst mittels partiellen Ableitungen, so dass wir komponentenweise die Produktregel für eindimensionale Funktionen anwenden können, d.h.,
\begin{equation*}
\begin{split}
\nabla(f\cdot g) \ &= \ ( \partial_1 (f\cdot g), \ldots, \partial_n (f \cdot g))^T \\
\ &= \ ( \partial_1 f \cdot g + f \cdot \partial_1 g, \ldots, \partial_n f \cdot g + f \cdot \partial_n g)^T 
\end{split}
\end{equation*}
Wir können den entstehenden Vektor nun linear auseinander ziehen und erhalten somit
\begin{equation*}
\begin{split}
\nabla(f\cdot g) \ &= \  ( \partial_1 f \cdot g + f \cdot \partial_1 g, \ldots, \partial_n f \cdot g + f \cdot \partial_n g)^T \\
\ &= \ (\partial_1 f, \ldots, \partial_n f)^T \cdot g \: + \: f \cdot (\partial_1 g, \ldots, \partial_n g)^T\\
\ &= \ \nabla f \cdot g + f \cdot \nabla g. 
\end{split}
\end{equation*}
````

````{prf:remark}
Sei $U \subset \R^n$ eine offene Teilmenge.
Folgende Interpretationen des Gradienten-Operators sind ebenfalls geläufig.
* Mit etwas missbräuchlicher Notation kann man den Gradienten auch als mehrdimensionale Abbildung interpretieren mit
\begin{align*}
\nabla \colon U \ &\rightarrow \ \R^n\\
x \ &\mapsto \ \nabla(x).
\end{align*}
* Funktionen $v: U\rightarrow \R^n$ werden auch \emph{Vektorfelder} genannt. 
In diesem Sinne kann der Gradient als Vektorfeld auf $U$ interpretiert werden.
````

Für partiell differenzierbare Vektorfelder $v \colon U \rightarrow \R^n$ (d.h. jede Komponente $v_i$ von $v$ ist partiell differenzierbar) gibt es weitere Differentialoperatoren erster Ordnung.
Im Folgenden führen wir den Begriff der Divergenz eines Vektorfelds $v$ ein.
\begin{definition}[Divergenz eines Vektorfelds]
Sei $U \subset \R^n$ eine offene Teilmenge. 
Für ein partiell differenzierbares Vektorfeld $v:U\rightarrow \R^n$ nennt man
\begin{equation*}
\dv v(x) \ \coloneqq \  \sum_{i=1}^{n} \frac{\partial v_i}{ \partial x_i} (x)  \ = \ \sum_{i=1}^{n} \partial_i v_i(x)
\end{equation*}
die *Divergenz* von $v$ an der Stelle $x\in U$.

Oft wird die Divergenz auch als Skalarprodukt des Nabla-Operators $\nabla$ mit einen Vektorfeld $v$ notiert, d.h., 
\begin{equation*}
\dv v \ = \ \langle \nabla, v \rangle.
\end{equation*}
\end{definition}

````{prf:remark}
Die Divergenz eines Vektorfeldes $v \colon U \rightarrow \R^n$ besitzt eine einfache physikalische Interpretation.
Es misst anschaulich den Fluss des Vektorfeldes im Punkt $x$.
Man kann also an Hand der Divergenz entscheiden ob mehr Fluss in den Punkt $x\in U$ hinein- als hinausfließt oder anders herum.
* Ist die Divergenz in einem Punkt $x\in U$ *positiv* d.h., gilt $\dv v(x) > 0$ so spricht man davon, dass das der Punkt eine **Quelle** des Vektorfelds darstellt.
Anschaulich könnte man den Punkt $x$ mit einem $n$-dimensionalen Würfel umschließen und die Menge an Fluss, die aus dem Würfel austritt wäre größer als die Menge an Fluss die hineinfließt.
* Ist die Divergenz in einem Punkt $x\in U$ *negativ* d.h., gilt $\dv v(x) < 0$ so spricht man davon, dass das der Punkt eine **Senke** des Vektorfelds darstellt.
Die Menge an Fluss, die in den umschließenden $n$-dimensionalen Würfel hineinfließt wäre größer als die Menge an Fluss die austritt.
* Ist die Divergenz in einem Punkt $x\in U$ *Null*, d.h., gilt $\dv v(x) = 0$, so nennen wir das Vektorfeld *divergenzfrei* im Punkt $x$.
Die Menge an Fluss, die in den umschließenden $n$-dimensionalen Würfel hineinfließt entspricht in diesem Fall der Menge an Fluss die austritt.
````

Im Folgenden wollen wir die Divergenz für ein dreidimensionales Vektorfeld konkret ausrechnen und bezüglich ihres Vorzeichens das Vektorfeld charakterisieren.

````{prf:example}
:label: bsp:divergenz
Sei $v \colon \R^3 \rightarrow \R^3$ ein Vektorfeld mit
\begin{equation*}
v(x,y,z) \ \coloneqq \ 
\frac{1}{2}
\begin{pmatrix}
x^2\\
-4xz\\
6z
\end{pmatrix}, \quad \text{ für alle } (x,y,z)^T \in \R^3.
\end{equation*}
Wir berechnen die Divergenz des Vektorfelds für allgemeine Punkte $(x,y,z)^T \in \R^3$ als
\begin{equation*}
\begin{split}
\dv v(x,y,z) \ &= \ \partial_x v_1 (x,y,z) + \partial_y v_2 (x,y,z) + \partial_z v_3 (x,y,z) \ = \ \frac{1}{2} \cdot (\partial_x  x^2 - \partial_y 4xz + \partial_z 6z)\\
&= \ x - 0 + 3 \ = \ x + 3.
\end{split}
\end{equation*}
Wir erkennen also, dass die Divergenz des Vektorfelds $v$ maßgeblich von der $x$-Koordinate abhängt.
Für $x > -3$ ist jeder Punkt $(x,y,z) \in \R^3$ *Quelle* des Vektorfelds, für $x < -3$ ist jeder Punkt $(x,y,z) \in \R^3$ *Senke* des Vektorfelds und nur bei $x=-3$ ist jeder Punkt $(x,y,z) \in \R^3$ des Vektorfelds *divergenzfrei*.
````

Auch für die Divergenz lässt sich eine Produktregel für das Produkt einer reellwertigen Funktion und eines Vektorfeldes herleiten.

````{prf:lemma} Produktregel für die Divergenz
Sei $U \subset \R^n$ eine offene Teilmenge und es sei $v:U\rightarrow \R^n$ ein partiell differenzierbares Vektorfeld (d.h. jede Komponente $v_i$ von $v$ ist partiell differenzierbar) und $f:U\rightarrow \R$ eine partiell differenzierbare Funktion.
Dann gilt die folgende Produktregel für die Divergenz:
\begin{equation*}
\dv (f\cdot v)(x) \ = \ \langle \nabla f(x), v(x)\rangle + f(x) \cdot \dv v(x), \quad \text{ für alle } x\in U.
\end{equation*}
````

````{prf:proof}
In der Hausaufgabe zu zeigen.
````

Der letzte Differentialoperator erster Ordnung, den wir einführen wollen, ist a priori nur im Fall $U\subset\R^3$ definiert ist und spielt insbesondere in physikalischen Anwendungen eine wichtige Rolle. 
Der sogenannte Rotations-Operator hat seinen Namen dadurch erhalten, dass er bei Anwendung auf ein Strömungsfeld für jeden Ort das Doppelte der Winkelgeschwindigkeit angibt, mit der sich ein mitschwimmender Körper dreht.

````{prf:definition} Rotation
Sei $U\subset\R^3$ eine offene Teilmenge und $v:U\rightarrow\R^3$ ein partiell differenzierbares Vektorfeld (d.h. jede Komponente $v_i$ von $v$ ist partiell differenzierbar).
Dann heißt  der folgende Operator
\begin{align*}
\rot v \coloneqq \ 
\left(\partial_2 v_3 - \partial_3 v_2, 
\partial_3 v_1 - \partial_1 v_3,
\partial_1 v_2 - \partial_2 v_1\right)
\end{align*}
*Rotation* von $v$.
Er bildet also ein Vektorfeld wieder auf ein Vektorfeld ab.

Oft wird die Rotation als auch Vektorprodukt (vgl. Definition \ref{def:vektorprodukt}) des Nabla-Operators $\nabla$ mit einen Vektorfeld $v$ notiert, d.h., 
\begin{align*}
\rot v \ = \ \nabla \times v.
\end{align*}
````

Wir wollen die Rotation für das Vektorfeld aus Beispiel {prf:ref}`bsp:divergenz` nachrechnen.

````{prf:example}
Sei $v \colon \R^3 \rightarrow \R^3$ ein Vektorfeld mit
\begin{equation*}
v(x,y,z) \ \coloneqq \ 
\frac{1}{2}
\begin{pmatrix}
x^2\\
-4xz\\
6z
\end{pmatrix}, \quad \text{ für alle } (x,y,z)^T \in \R^3.
\end{equation*}
Wir berechnen die Rotation des Vektorfelds für allgemeine Punkte $(x,y,z)^T \in \R^3$ als
\begin{equation*}
\begin{split}
\rot v(x,y,z) \ &= \ \left(\partial_y v_3 - \partial_z v_2, 
\partial_z v_1 - \partial_x v_3,
\partial_x v_2 - \partial_y v_1\right)(x,y,z) \\
\ &= \ \left(\partial_y 6z + \partial_z 4xz, 
\partial_z x^2 - \partial_x 6z,
- \partial_x 4xz - \partial_y x^2\right) \\
\ &= \ (4x, 0, -4z).
\end{split}
\end{equation*}
Wir erkennen also, dass die Rotation des Vektorfelds nicht von der $y$-Koordinate abhängt.
````
