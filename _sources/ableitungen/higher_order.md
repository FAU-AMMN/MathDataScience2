---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

# Differentialoperatoren höherer Ordnung

Analog zum eindimensionalen Fall kann man höhere Ableitungen definieren, d.h., wir wollen die Funktion $f:U\rightarrow \R$ mehrmals ableiten. Induktiv bezeichnet man $f$ als $(k+1)$-mal differenzierbar, falls  $f$ $k$-mal differenzierbar ist und für eine beliebige Kombination von Richtungen $(i_1,\ldots,i_k)$ die Funktion $\partial_{i_1}\ldots \partial_{i_k} f$ wieder partiell differenzierbar ist. Hierbei ist a priori nicht klar, dass die partiellen Ableitungen vertauschbar sind.
Wir stellen uns also die Frage ob für eine zweimal partiell differenzierbare Funktion $f$ die Gleichheit

```{math}
:label: eq:partielle_ableitungen_vertauschbar

\partial_i\partial_j f(x) \ = \ \partial_j \partial_i f(x)
```

für alle $i,j\in\{1,\ldots,n\}$ gilt.

In der Tat reicht die Eigenschaft zweimal partiell differenzierbar zu sein **nicht** für die Gleichheit in 
{eq}`eq:partielle_ableitungen_vertauschbar` aus, wie das folgende Beispiel zeigt.

````{prf:example} Vertauschbarkeit partieller Ableitungen
:label: bsp:partielle_ableitungen_nicht_vertauschbar

Wir betrachten die Funktion 
\begin{align*}
f(x,y) \ \coloneqq \ xy \cdot \frac{x^2-y^2}{x^2+y^2}.
\end{align*}
Wie man nachrechnen kann ist die Funktion $f$ in allen Punkten $(x,y) \in \R^2$ zweimal partiell differenzierbar.
Wir berechnen die ersten partiellen Ableitungen
\begin{align*}
\partial_x f(x,y) \ &= \ \frac{(3x^2y - y^3)(x^2+y^2) - (x^3y -xy^3)\cdot 2x}{(x^2 + y^2)^2} \ = \ y~\frac{x^4 + 4 x^2y^2-y^4}{(x^2 + y^2)^2},\\
\partial_y f(x,y) \ &= \ \frac{(x^3-3xy^2)(x^2+y^2) - (x^3y-xy^3)\cdot 2y}{(x^2 + y^2)^2} \ = \ x~\frac{x^4 - 4 x^2y^2-y^4}{(x^2 + y^2)^2}.
\end{align*}
Wir betrachten nun die \textbf{zweiten} partiellen Ableitungen von $f$ im Punkt $(x,y) = (0,0)$ mit
\begin{equation}\label{eq:bsp_ableitungen_nicht_vertauschbar}
\begin{split}
\partial_y\partial_x f(0,0) \ &= \ \lim_{h\rightarrow 0} \frac{\partial_x f(0, h) - \partial_x f(0,0)}{h} \ = \ 
\lim_{h\rightarrow 0} ~ \frac{h}{h}~\frac{0 + 0-h^4}{(0 + h^2)^2} - 0 \ = \ -1,\\
\partial_x\partial_y f(0,0) \ &= \ \lim_{h\rightarrow 0} \frac{\partial_y f(h, 0) - \partial_y f(0,0)}{h} \ = \ 
\lim_{h\rightarrow 0} ~ \frac{h}{h}~\frac{h^4 - 0 - 0}{(h^2 + 0)^2} - 0 \ = \ +1.
\end{split}
\end{equation}
Wir erkennen, dass die Funktion $f$ zwar zweimal partiell differenzierbar ist im Nullpunkt, jedoch ist die Reihenfolge der partiellen Ableitungen nicht vertauschbar. 
````

## Der Satz von Schwarz

Um eine Bedingung zu erarbeiten, die die Vertauschbarkeit von höheren partiellen Ableitungen versichert, fragt man sich zunächst weshalb die Funktion aus {prf:ref}`bsp:partielle_ableitungen_nicht_vertauschbar` diese Eigenschaft verletzt.
Betrachtet man die zweiten partiellen Ableitungen $\partial_i\partial_j f$ in {prf:ref}`bsp:partielle_ableitungen_nicht_vertauschbar` so fällt auf, dass diese nicht stetig im Punkt $(0,0)$ sind. Die Vermutung liegt also nahe, dass gerade die fehlende Stetigkeit die Vertauschbarkeit verhindert. Diese Vermutung lässt sich tatsächlich auch beweisen, was gemeinhin als der folgende _Satz von Schwarz_ bekannt ist.

````{prf:theorem} Satz von Schwarz
:label: satz:schwarz
Sei $U \subset \R^n$ eine offene Teilmenge und $f:U\rightarrow \R$ eine zweimal stetig partiell differenzierbare Funktion.
Dann gilt 
\begin{align*}
\partial_i \partial_j f \: = \: \partial_j \partial_i f
\end{align*}
für alle Ableitungsrichtungen $i,j\in\{1,\ldots,n\}$.
````

````{prf:proof}
Wir können o.B.d.A. annehmen, dass $U\subset\R^2$ eine offene Teilmenge ist. 
Wir betrachten einen beliebigen Punkt $(\bar x,\bar y)\in U$.
Da $U$ offen ist existiert ein $\delta>0$, so dass ein Quadrat $B^\infty_\delta$ mit Seitenlänge $\delta$ noch in $U$ liegt, d.h.,
\begin{align*}
B^\infty_\delta(\bar x,\bar y) \ \coloneqq \ \{(x,y)\in\R^2: \abs{x-\bar x} < \delta \wedge \abs{y-\bar y} < \delta\} \ \subset \ U.
\end{align*}

Für ein festes $y\in (\bar y -\delta, \bar y + \delta)$ betrachten wir nun die eindimensionale Funktion 
\begin{align*}
R_y:[-\delta,\delta] \ &\rightarrow \ \R\\
x \ &\mapsto \ R_y(x) \ \coloneqq \ f(x+\bar x, y + \bar y) - f(x+\bar x, \bar y).
\end{align*}
Wir bemerken zunächst, dass für $y=0$ gilt
\begin{equation*}
R_0(x) \ = \ f(x+\bar x, \bar y) - f(x+\bar x, \bar y) \ = \ 0, \quad \text{ für alle } x\in [-\delta, \delta].
\end{equation*}
Da $R_y$ als Einschränkung von $f$ in eine Koordinatenrichtung stetig ist können wir für ein beliebiges $x\in[-\delta,\delta]$ mit Hilfe des Mittelwertsatzes \cite[Kapitel 6.2]{burger_2020} einen Punkt $\xi_x\in[-\delta,\delta]$ finden mit $\abs{\xi_x}\leq\abs{x}$, so dass
\begin{align*}
R^\prime_y(\xi_x)\cdot x \ = \ R_y(x) - R_y(0).
\end{align*}
Hierbei ist die Ableitung der Funktion $R_y$ gegeben durch
\begin{align*}
R^\prime_y(\xi_x) \ = \ \partial_1 R_y(\xi_x) \ = \ \partial_1 f (\xi_x + \bar x, y + \bar y) \, - \, \partial_1 f(\xi_x + \bar x, \bar y) .
\end{align*}
Wir können nun basierend auf dem obigen Ausdruck erneut eine stetige eindimensionale Funktion $r:[-\delta,\delta]\to\R$ definieren mit $r(y) \coloneqq R^\prime_y(\xi_x)$. 
Auf diese Funktion wenden wir erneut den Mittelwertsatz an und finden analog für jedes beliebige $y\in [-\delta,\delta]$ einen Punkt $\eta_y\in [-\delta,\delta]$ mit $\abs{\eta_y}\leq\abs{y}$, so dass
\begin{align*}
r^\prime(\eta_y) \cdot y \ = \ r(y) - r(0).
\end{align*}
Hierbei ist die Ableitung der Funktion $r$ gegeben durch
\begin{align*}
r^\prime(\eta_y) \ = \ \partial_2\partial_1 f(\xi_x + \bar x, \eta_y + \bar y).
\end{align*}

Insgesamt erhalten wir für alle $(x,y)\in B^\infty_\delta(0,0)$ die folgende Identität
\begin{equation*}
\begin{split}
\partial_2\partial_1 f(\xi_x + \bar x, \eta_y + \bar y) \ &= \ r'(\eta_y) \ = \ \frac{r(y) - r(0)}{y} \ = \ \frac{R'_y(\xi_x) - R'_0(\xi_x)}{y}\\
\ &= \  \frac{\frac{R_y(x) - R_y(0)}{x} - \frac{R_0(x) - R_0(0)}{x}}{y} \ = \  \frac{R_y(x) - R_y(0)}{xy}   \\
\ &= \ \frac{f(x+\bar x, y + \bar y) - f(x + \bar x, \bar y)  - f(\bar x, y+\bar y) - f(\bar x, \bar y)}{xy}.
\end{split}
\end{equation*}
Insgesamt gilt also für alle $(x,y)\in B^\infty_\delta(0,0)$ die folgende Gleichung
\begin{equation}\label{eq:schwarz_1}
\partial_2\partial_1 f(\xi_x + \bar x, \eta_y + \bar y) \cdot xy \ = \ f(x+\bar x, y + \bar y) - f(x + \bar x, \bar y)  - f(\bar x, y+\bar y) - f(\bar x, \bar y).
\end{equation}

Mit vertauschten Rollen wenden wir die Argumente für ein festes $x\in (\bar x -\delta, \bar x + \delta)$ analog auf die eindimensionale Funktion 
\begin{align*}
T_x \colon [-\delta,\delta]\ &\rightarrow \ \R\\
y \ &\mapsto\ T_x(y) \ \coloneqq \ f(x+\bar x, y + \bar y) - f(\bar x, y+\bar y)
\end{align*}
an. 
Für $(x,y)\in B^\infty_\delta(0,0)$ liefert das jeweils Skalare $\hat \xi_x, \hat \eta_y \in [-\delta, \delta]$ mit $\abs{\hat \xi_x}\leq\abs{x}, \abs{\hat \eta_y}\leq\abs{y}$, so dass
\begin{equation*}
\begin{split}
\partial_1\partial_2 f(\hat \xi_x + \bar x, \hat \eta_y + \bar y) \cdot yx \ &= \ T_x(y) - T_x(0) \\
\ &= \ f(x+\bar x, y + \bar y) - f(x + \bar x, \bar y) 
- f(\bar x, y+\bar y) - f(\bar x, \bar y) .
\end{split}
\end{equation*}
Zusammen mit \eqref{eq:schwarz_1} können wir für $xy\neq 0$ schlussfolgern, 
dass
\begin{equation*}
(\partial_2\partial_1 f)(\xi_x + \bar x, \eta_y + \bar y) \ = \
(\partial_1\partial_2 f)(\hat\xi_x + \bar x, \hat\eta_y + \bar y).
\end{equation*}

Es folgt nun der entscheidende Schritt. 
Wir betrachten im Folgenden eine Nullfolge $(x_n,y_n)_{n\in\N} \subset B^\infty_\delta(0,0)$ mit $(x_n,y_n)_{n\in\N} \rightarrow (0,0)$ und $x_ny_n\neq 0$ für alle $n\in\N$. 
Diese Folge induziert mit den obigen Argumenten zwei weitere Nullfolgen $(\xi_n,\eta_n)_{n\in\N}$ und $(\hat \xi_n, \hat\eta_n)_{n\in\N}$, so dass
\begin{equation*}
(\partial_2\partial_1 f)(\xi_n + \bar x, \eta_n + \bar n) \ = \
(\partial_1\partial_2 f)(\hat\xi_n + \bar x, \hat\eta_n + \bar y).
\end{equation*}
Um zu sehen, dass diese beiden Folgen wieder Nullfolgen sind nutzen wir die Beschränktheit der Folgeglieder aus, d.h., dass $\abs{\xi_x}, \abs{\hat \xi_x}\leq\abs{x}$ und $\abs{\eta_y}, \abs{\hat \eta_y}\leq\abs{y}$ gilt. 

Schließlich benutzen wir die Stetigkeit der zweiten partiellen Ableitungen und sehen damit ein, dass
\begin{align*}
\partial_2\partial_1 f(\bar x, \bar y)  \ &= \ 
\lim_{n\rightarrow \infty} 
\partial_2\partial_1 f (\xi_n + \bar x, \eta_n + \bar y)\\ 
&= \ \lim_{n\rightarrow \infty} 
\partial_1\partial_2 f(\hat \xi_n + \bar x, \hat \eta_n + \bar y) \ = \  \partial_1\partial_2 f(\bar x, \bar y).
\end{align*}
````

Das folgende Korollar sagt aus, dass die Vertauschbarkeit nicht nur für zwei Ableitungsrichtungen gilt, sondern für eine beliebige Permutation von partiellen Ableitungen gegeben ist.

````{prf:corollary}
Sei $U\subset\R^n$ eine offene Teilmenge und $f:U\rightarrow \R$ eine $k$-mal stetig partiell differenzierbare Funktion.
Dann gilt für jede bijektive Abbildung $\pi:\{1,\ldots,k\}\rightarrow \{1,\ldots,k\}$ (auch \emph{Permutation} genannt) 
\begin{align*}
\partial_{i_1}\ldots\partial_{i_k} f \ = \ \partial_{i_{\pi(1)}}\ldots\partial_{i_{\pi(k)}} f
\end{align*}
für beliebige Indizes $i_1,\ldots,i_k\in\{1,\ldots,n\}$.
````

````{prf:proof}
In der Hausaufgabe zu zeigen.
````

````{prf:remark}
* Für mehrfache partielle Ableitung in die gleiche Koordinatenrichtung schreibt man häufig kurz
\begin{align*}
\partial_i\partial_i f \ \eqqcolon \ \partial_i^2 f.
\end{align*}
Dies lässt sich analog für höhere Ableitungen durch höhere Potenzen ausdrücken.

* Insbesondere folgt aus  dem Satz \ref{satz:schwarz} von Schwarz, dass für eine zweimal stetig partiell differenzierbare Funktion $f$ die folgende Beobachtung für die Rotation gilt
\begin{equation*}
\rot\nabla f \: = \:  0.
\end{equation*}
Dies folgt aus der Beobachtung, dass $x\times x = 0$ gilt für alle $x \in \R^3$ (vgl. Lemma \ref{lem:vektorprodukt}) und der Notation
\begin{align*}
\rot \nabla f \: = \: \nabla\times\nabla f \: = \: 0.
\end{align*}
Diese Erkenntnis wird im allgemeinen Sprachgebrauch häufig mit dem Ausspruch _Gradientenfelder sind Rotationsfrei_ gemeint.
````

## Die Hesse-Matrix

Analog zur zweiten Ableitung von Funktionen in einer Veränderlichen kann man für mehrdimensionale Funktionen einen Operator definieren, der alle zweiten Ableitungen sammelt - die sogenannte _Hesse-Matrix_.

````{prf:definition} Hesse-Matrix
Sei $U \subset \R^n$ eine offene Teilmenge und $f : U \rightarrow R$ eine zweimal stetig partiell differenzierbare Funktion. Dann ist die _Hesse-Matrix_ von $f$ im Punkt $x \in U$ definiert als
\begin{equation*}
H_f(x) \ \coloneqq \ \left( \frac{\partial^2 f}{\partial x_i \partial x_j}(x) \right)_{1 \leq i,j \leq n} \ = \ \left( \partial_i\partial_j f (x) \right)_{1 \leq i,j \leq n} \ = \ 
\begin{pmatrix}
\partial_1 \partial_1 f(x) & \cdots & \partial_1 \partial_n f(x)\\
\vdots & \ddots & \vdots \\
\partial_n \partial_1 f(x) & \cdots & \partial_n \partial_n f(x)\\
\end{pmatrix}.
\end{equation*}
````

````{prf:remark}
Die Hesse-Matrix $H_f$ einer zweimal stetig partiell differenzierbaren Funktion $f$ ist symmetrisch, da die Reihenfolge der partiellen Ableitungen vertauscht werden kann und somit gilt $H_f = H_f^T$.
````

Wir wollen im folgenden Beispiel die Hesse-Matrix einer zweidimensionalen Funktion berechnen.

````{prf:example}
:label: bsp:hesse_matrix
Sei $f \colon \R^2 \rightarrow \R$ eine zweimal stetig partiell differenzierbare Funktion mit
\begin{equation*}
f(x,y) \ \coloneqq \ x^2y - \sin(x).
\end{equation*}
Um die Hesse-Matrix $H_f$ von $f$ zu berechnen geben wir zuerst die ersten partiellen Ableitungen von $f$ an mit
\begin{equation*}
\begin{split}
\partial_x f(x,y) \ &= \ \partial_x (x^2y - \sin(x)) \ = \ 2xy - \cos(x),\\
\partial_y f(x,y) \ &= \ \partial_y (x^2y - \sin(x)) \ = \ x^2.
\end{split}
\end{equation*}
Nun betrachten wir die zweiten partiellen Ableitungen von $f$ mit
\begin{equation*}
\begin{split}
\partial_x \partial_x f(x,y) \ &= \ \partial_x (2xy - \cos(x)) \ = \ 2y + \sin(x),\\
\partial_y \partial_x f(x,y) \ &= \ \partial_y (2xy - \cos(x)) \ = \ 2x,\\
\partial_x \partial_y f(x,y) \ &= \ \partial_x (x^2) \ = \ 2x,\\
\partial_y \partial_y f(x,y) \ &= \ \partial_y (x^2) \ = \ 0,\\
\end{split}
\end{equation*}
Daraus ergibt sich für die Hesse-Matrix von $f$ die folgende Gestalt:
\begin{equation*}
H_f(x) \ = \ 
\begin{pmatrix}
\partial_x \partial_x f(x,y) & \partial_x \partial_y f(x,y)\\
\partial_y \partial_x f(x,y) & \partial_y \partial_y f(x,y)\\
\end{pmatrix}
\ = \ 
\begin{pmatrix}
2x + \sin(x) & 2x\\
2x & 0\\
\end{pmatrix}.
\end{equation*}
````

## Der Laplace-Operator

Den letzten Operator den wir in diesem Abschnitt kennenlernen wollen ist der sogenannte Laplace-Operator.

```{note}
Der Operator ist nach dem französischen Mathematiker 
[Pierre-Simon Laplace](https://en.wikipedia.org/wiki/Pierre-Simon_Laplace) (1749-1827) benannt.
```

````{prf:definition} Laplace-Operator
Sei $U\subset\R^n$ offen und $f:U\rightarrow\R$ eine zweimal stetig differenzierbare Funktion, dann heißt
\begin{equation*}
\Delta f(x) \ \coloneqq \ \dv \nabla f(x) \ = \ \sum_{i=1}^n \frac{\partial^2f}{\partial x_i^2}(x) \ = \ \sum_{i=1}^n \partial_i^2 f(x). 
\end{equation*}
Laplace-Operator.
Analog zu den vorherigen Überlegungen kann auch der Laplace-Operator 
als Differtialoperator geschrieben werden,
\begin{align*}
\Delta f \ \eqqcolon \ \langle \nabla, \nabla f\rangle \ \eqqcolon \ \nabla^2 f.
\end{align*} 
````

Wir wollen den Laplace Operator für die Funktion aus Beispiel {prf:ref}`bsp:hesse_matrix` im Folgenden berechnen.

````{prf:example}
Sei $f \colon \R^2 \rightarrow \R$ eine zweimal stetig partiell differenzierbare Funktion mit
\begin{equation*}
f(x,y) \ \coloneqq \ x^2y - \sin(x).
\end{equation*}
Um den Laplace-Operator $\Delta f$ von $f$ zu berechnen geben wir zunächst die relevanten zweiten partiellen Ableitungen von $f$ an mit
\begin{equation*}
\begin{split}
\partial^2_x f(x,y) \ &= \ \partial^2_x (x^2y - \sin(x)) \ = \ 2x + \sin(x),\\
\partial^2_y f(x,y) \ &= \ \partial^2_y (x^2y - \sin(x)) \ = \ 0.
\end{split}
\end{equation*}
Nun können wir den Laplace Operator $\Delta f$ von $f$ angeben als
\begin{equation*}
\Delta f(x,y) \ \coloneqq \ \partial^2_x f(x,y) + \partial^2_y f(x,y) \ = \ 2x + \sin(x) + 0 \ = \ 2x + \sin(x).
\end{equation*}
````

````{prf:remark}
Der Laplace Operator $\Delta f$ einer zweimal stetig partiell differenzierbaren Funktion $f$ lässt sich ebenfalls als Spur der Hesse-Matrix $H_f$ von $f$ darstellen durch:
\begin{equation*}
\Delta f(x) \ = \ \tr(H_f(x)).
\end{equation*}
````
