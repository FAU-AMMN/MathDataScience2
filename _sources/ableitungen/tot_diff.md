# Totale Differenzierbarkeit

Im letzten Abschnitt haben wir gesehen, dass der Begriff der partiellen Ableitung die nächstliegendste  Strategie ist um Ableitungen für Funktionen  mehrerer Veränderlicher zu definieren. Allerdings wurde aus den obigen Beispielen auch klar, dass Definition über Einschränkung auf einzelne Koordinatenachsen, einerseits willkürlich ist, aber insbesondere auch keine befriedigende Verallgemeinerung des Ableitungsbegriffs darstellt. So gilt z.B. die aus dem Eindimensionalen bekannte Implikation für Funktionen $f \colon \R \rightarrow \R$ 
**nicht** für den Begriff der partiellen Differenzierbarkeit.

```{admonition} Eindimensionaler Fall
:class: tip

$f$ ist differenzierbar $\Rightarrow$ $f$ ist stetig
```

Aus diesem Grund, wollen wir nun einen weiteren Ableitungsbegriff kennenlernen, welcher eine tatsächliche Verallgemeinerung dieser Beobachtung darstellt. Insbesondere erlaubt es uns dieser neue Begriff auch Ableitung von vektorwertigen Funktionen $f:U\rightarrow\R^m$ für eine offene Teilmenge $U\subset\R^n$ zu definieren.

````{prf:definition} Totale Differenzierbarkeit
:label: def:totale_differenzierbarkeit

Sei $U\subset\R^n$ eine offene Teilmenge.
Dann heißt eine Funktion $f:U\rightarrow \R^m$ _total differenzierbar_ im Punkt $x\in U$, falls für einen beliebigen Vektor $\xi \in \R^n$ eine lineare Abbildung $L:\R^n\rightarrow\R^m$ existiert, so dass

```{math}
:label: eq:totale_differenzierbarkeit

\lim_{\xi\rightarrow 0} \frac{\norm{f(x+\xi) - f(x) - L\xi}} {\norm{\xi}} \ = \ 0.
```

````

Die folgende Bemerkung beschreibt die Intuition hinter der Definition von totaler Differenzierbarkeit.

````{prf:remark}
:label: bem:fehlerfunktional

Zur totalen Differenzierbarkeit können wir folgende Beobachtungen festhalten.
* In {eq}`eq:totale_differenzierbarkeit` betrachtet man das sogenannte _Fehlerfunktional_

```{math}
:label: eq:fehlerfunktional

r(\xi) \ \coloneqq \ f(x+\xi) - f(x) - L\xi
```

welches die Abweichung zwischen der Linearisierung und der eigentlichen Differenz misst.
Bei der Definition von totaler Differenzierbarkeit fordern wir also, dass diese Diskrepanz schnell genug gegen Null konvergiert.

Zudem erkennen wir, dass Definition {prf:ref}`def:totale_differenzierbarkeit` konsistent mit dem herkömmlichen Begriff der Differenzierbarkeit einer Funktion $f$ im Eindimensionalen ($n=m=1$) ist, da die Funktion $L$ in diesem Fall als 
\begin{equation*}
L(h) \ \coloneqq \ f^\prime(x) \cdot h
\end{equation*}  
gewählt werden kann.
\item%
Die lineare Abbildung $L$ wird typischerweise mit der darstellenden Matrix 
\begin{align*}
L \ = \
\begin{pmatrix}
L_{11}&\ldots &L_{1n}\\
\vdots& &\vdots\\
L_{m1}&\ldots &L_{mn}
\end{pmatrix}
\in\R^{m,n}
\end{align*}
bezüglich der kanonischen Basen von $\R^n$ und $\R^m$ identifiziert. 
Das Fehlerfunktional, hat dann komponentenweise die Form 
\begin{align*}
r_i(\xi) \ = \ f_i(x+\xi) - f_i(x) - \sum_{j=1}^n L_{ij}\xi_j.
\end{align*}
Somit sehen wir, dass $f$ genau dann total differenzierbar ist, falls jede 
Komponente von $f$ im Bildraum total differenzierbar ist.
\end{enumerate}
````

````{prf:example}
Sei $C\in\R^{n,n}$ eine symmetrische Funktion und die Funktion 
$f:\R^n\rightarrow\R$ als quadratische Form gegeben durch
\begin{align*}
f(x) \ \coloneqq \ \langle x, C x\rangle.
\end{align*}
Wir berechnen nun für einen beliebigen Punkt $x\in\R^n$ und einen Richtungsvektor $\xi \in \R^n$
\begin{align*}
f(x+\xi) \ &= \ \langle x +\xi, C (x + \xi)\rangle \ = \
\langle x , C x \rangle + 
\underbrace{
\langle x , C \xi\rangle + 
\langle \xi , C x \rangle}_{= \, 2\langle C x, \xi\rangle \, \eqqcolon \, L\xi} \, + \, 
\langle \xi , C \xi\rangle\\
&=
f(x) + L\xi + \langle \xi , C \xi\rangle.
\end{align*}
Das Fehlerfunktional ist also gegeben durch 
\begin{align*}
r(\xi) \ \coloneqq \ f(x+\xi) - f(x) - L\xi \ = \ f(x) + L\xi + \langle \xi , C \xi\rangle - f(x) - L\xi \ = \ \langle \xi , C \xi\rangle.
\end{align*}
Mit Hilfe der Cauchy-Schwarz Ungleichung aus Satz \ref{satz:cauchy-schwarz_r} sehen wir, dass
\begin{align*}
|r(\xi)| \ = \ \langle \xi, C \xi \rangle| \ \leq \ \norm{\xi} \cdot \norm{C\xi} | \ \leq \  \norm{C} \cdot \norm{\xi}^2.
\end{align*}
Damit können wir schließlich folgern
\begin{align*}
\lim_{\xi\rightarrow 0} \frac{\norm{r(\xi)}}{\norm{\xi}} \ \leq \ \lim_{\xi\rightarrow 0} \norm{C}\cdot\norm{\xi} \ = \ 0.
\end{align*}
Wir sehen also, dass die Funktion $f(x) = \langle x, Cx \rangle$ total differenzierbar in allen Punkten $x\in \R^n$ ist.
````

## Stetigkeit total diffbarer Funktionen

Der folgende Satz liefert uns nun die gewünschte Aussage, dass totale Differenzierbarkeit einer Funktion schon Stetigkeit impliziert. Zudem stellt er einen Bezug zum Begriff der partiellen Differenzierbarkeit her.

````{prf:theorem}
:label: thm:totdiff

Sei $U\subset\R^n$ eine offene Teilmenge und sei $f:U\rightarrow \R^m$ eine im Punkt $x\in U$ total differenzierbare Funktion, d.h., es existiert eine Matrix $L\in\R^{m\times n}$, so dass, 
\begin{equation*}
r(\xi) \ = \ f(x+\xi)-f(x)-L\xi
\end{equation*}
die Gleichung {eq}`eq:totale_differenzierbarkeit` erfüllt.
Dann gilt

* f ist stetig im Punkt $x$,
* jede Komponente von $f$ im Bildraum ist partiell differenzierbar in $x$ und die Einträge der Matrix $L$ sind gerade die partiellen Ableitungen von $f$, d.h.,
\begin{align*}
\partial_j f_i \ = \ L_{ij}.
\end{align*}
````

````{prf:proof}
Die Stetigkeit ist eine direkte Folgerung aus der Definition, denn mittels Dreiecksungleichung können wir zeigen, dass gilt 
\begin{align*}
\norm{f(x+\xi) - f(x)} \: = \: \norm{f(x+\xi) - f(x) - L\xi + L\xi} \: \leq \: \norm{f(x+\xi) - f(x) - L\xi} + \norm{L\xi}.
\end{align*}
Da auf Grund der Linearität von $L$ offensichtlich $\lim_{\xi\rightarrow 0}\norm{L\xi} = 0$ gilt und $f$ total differenzierbar ist, d.h.,
\begin{equation*}
\lim_{\xi\rightarrow 0}\norm{f(x+\xi) - f(x) - L\xi} \ = \ 0
\end{equation*}
folgt somit schon
\begin{align*}
\lim_{\xi\rightarrow 0}\norm{f(x+\xi) - f(x)} \ \leq \ \lim_{\xi\rightarrow 0}\norm{f(x+\xi) - f(x) - L\xi} + \norm{L\xi} \ = \ 0.
\end{align*}
Da der obige Grenzwerte beliebige Nullfolgen betrachtet folgt die Stetigkeit von $f$.
\par
Für den Zusammenhang mit der partiellen Differenzierbarkeit in der zweiten Aussage des Satzes betrachten wir eine Komponente $f_i$ von $f$ für $i\in\{1,\ldots,m\}$ und damit gilt nach Bemerkung \ref{bem:fehlerfunktional}
\begin{align*}
r_i(\xi) \ = \ f_i(x+\xi)-f_i(x)-\sum_{j=1}^n L_{ij}\xi_j.
\end{align*}
Treffen wir nun die spezielle Wahl $\xi=h \cdot e_j$ für eine Koordinatenrichtung $e_j, 1 \leq j \leq n$, so sehen wir
\begin{align*}
r_i(h \cdot e_j) \ = \ f_i(x+h \cdot e_j)-f_i(x)- L_{ij} \cdot h.
\end{align*}
Setzen wir nun die Definition der totalen Differenzierbarkeit für die Komponente $r_i$ ein folgt 
\begin{align*}
| \partial_j f_i(x) - L_{ij}| \ &= \ 
\lim_{h\rightarrow 0}
\left|\frac{f_i(x+h\cdot e_j)-f_i(x)}{h} - L_{ij}\right|
= \ \lim_{h\rightarrow 0}\frac{\abs{f_i(x+h\cdot e_j)-f_i(x)- L_{ij} \cdot h}}{h}\\
%
&= \ \lim_{h\rightarrow 0}\frac{\norm{r_i(h\cdot e_j)}}{\norm{h \cdot e_j}} \ = \  \lim_{h\rightarrow 0}\frac{\norm{r_i(\xi)}}{\norm{\xi}} \ = \ 0.
\end{align*}
Damit haben wir gezeigt, dass die Einträge der Matrix $L$ mit den partiellen Ableitungen der Funktion $f$ übereinstimmen.
````

## Die Jacobi-Matrix

Speziell die besondere Gestalt der Matrix $L$ in der zweiten Aussage des Satzes \ref{thm:totdiff} motiviert die Definition der Jacobi-Matrix einer vektorwertigen, partiell differenzierbaren Funktion.

````{prf:definition} Jacobi-Matrix

Sei $U\subset \R^n$ eine offene Teilmenge und sei $f:U\rightarrow \R^m$ eine partiell differenzierbare Funktion (d.h. jede Komponente $f_i$ ist partiell differenzierbar), dann heißt die Matrix
\begin{align*}
(Df)(x) \ \coloneqq \ J_f(x) \ \coloneqq \
\begin{pmatrix}
\partial_1 f_1(x)&\ldots&\partial_nf_1(x)\\
\vdots& &\vdots\\
\partial_1 f_m(x)&\ldots&\partial_n f_m(x)\\
\end{pmatrix}
\end{align*}
_Jacobi-Matrix_ am Punkt $x\in U$.
````

Im Folgenden wollen wir wichtige Beobachtungen zur Bedeutung der Jacobi-Matrix festhalten.

````{prf:remark}
:label: rem:jacobi_matrix

Sei $U \subset \R^n$ eine offene Teilmenge und sei $f \colon U \rightarrow \R^m$ eine partiell differenzierbare Funktion.
Dann können wir folgendes feststellen.

* Falls $f$ eine reellwertige Funktion ist, d.h., $m=1$, so stimmt die Jacobi-Matrix von $f$ am Punkt $x\in U$ mit dem Gradienten von $f$ in $x$ überein, d.h.
\begin{equation*}
(Df)(x) \ = \ (\nabla f(x))^T.
\end{equation*}
* Aus Satz {prf:ref}`thm:totdiff`, folgt insbesondere, dass die lineare Abbildung $L$ in der Definition der totalen Differenzierbarkeit eindeutig bestimmt ist durch die Jacobi-Matrix.
Das Fehlerfunktional {eq}`eq:fehlerfunktional` ist also gegeben durch
\begin{align*}
r(\xi) = f(x+\xi)-f(x)- J_f(x)\xi.
\end{align*}
````

Wir wissen nun, dass für Funktionen $f \colon U \rightarrow \R^m$ die Implikation

```{admonition} Mehrdimensionaler Fall
:class: tip

$f$ ist total differenzierbar $\Rightarrow$ $f$ ist partiell differenzierbar
```

gilt.
Die Umkehrung gilt offensichtlich nicht, wie wir in Beispiel {prf:ref}`bsp:partiell_diffbar_nicht_stetig` gesehen haben. Nehmen wir jedoch eine zusätzliche zusätzliche Stetigkeitsannahme hinzu, erhalten wir wieder totale Differenzierbarkeit, wie folgender Satz zeigt.

````{prf:theorem}
Sei $U\subset\R^n$ eine offene Teilmenge und sei $f:U\rightarrow\R$ eine in $U$ partiell differenzierbare Funktion für die alle partiellen Ableitungen $\partial_i f$ stetig sind im Punkt $x\in U$.

Dann ist $f$ in $x \in U$ total differenzierbar.
````

````{prf:proof}
Wir wählen $x\in U$ und ein $\delta>0$, so dass $B_\delta(x)\subset U$. 
Wir betrachten nun einen beliebigen Vektor $\xi\in B_\delta(0)$ und definieren basierend auf $\xi$ einen Familie von Vektoren $z_0, \ldots, z_n \in B_\delta(x)$ mit
\begin{align*}
z_k \ \coloneqq \ x + \sum_{i=1}^k \xi_k \ = \ (x_1 + \xi_1,\ldots, x_k + \xi_k, x_{k+1},\ldots, x_n)^T, \qquad \text{ für } \quad k=0,\ldots,n.
\end{align*}
Wir erkennen, dass $z_0=x$ und $z_n = x + \xi$ gilt und die Vektoren $z_k$ dadurch entstehen, dass wir sukzessive weitere Komponenten von $\xi$ hinzunehmen. 
Das bedeutet, dass ich zwei aufeinanderfolgende Vektoren $z_k$ und $z_{k-1}$ nur in der $k$-ten Koordinatenrichtung unterscheiden. 

Im Folgenden beschränken wir die Funktion $f$ auf die $k$-te Komponente, d.h., wir betrachten 
\begin{align*}
\tilde f(\theta) \ \coloneqq \ f(z_{k-1} + \theta \cdot e_k) \ = \ f(x_1 + \xi_1,\ldots, x_{k-1} + \xi_{k-1}, 
x_{k} + \theta, 
x_{k+1},\ldots,x_n)
\end{align*}
Durch diese eindimensionale Beschränkung sehen wir, dass gilt

```{math}
:label: eq:total_diffbar_einschraenkung

f(z_{k}) - f(z_{k-1}) \ = \ \tilde f(\xi_{k}) - \tilde f(0).
```

Wenden wir nun den Mittelwertsatz für Funktionen in einer Veränderlichen \cite[Kapitel 6.2]{burger_2020} an, so sehen wir, dass ein $\theta_{k}\in(0,\xi_{k})$ existiert, so dass
\begin{equation*}
\tilde f(\xi_{k}) - \tilde f(0) \ = \ \tilde{f}^\prime(\theta_{k}) \cdot \xi_{k}.
\end{equation*}
Wegen der Identität {eq}`eq:total_diffbar_einschraenkung` folgt damit schon, dass
```{math}
:label: eq:total_diffbar_partielle_ableitung

f(z_{k}) - f(z_{k-1}) \ = \ \partial_k f(z_{k-1} + \theta_{k}e_{k}) \cdot \xi_k.
```

Da {eq}`eq:total_diffbar_partielle_ableitung` für jedes $0 \leq k \leq n$ gilt, können wir über diese Indizes summieren und erhalten damit die folgende Teleskopsumme:
\begin{align*}
f(x+\xi)-f(x) \ &= \ f(z_n) - f(z_0) \ = \ \sum_{k=1}^{n}f(z_{k}) - f(z_{k-1}) \\
&= \ \sum_{k=1}^{n} \partial_k f(z_k + \theta_{k}e_{k}) \cdot \xi_k.
\end{align*}

Wir betrachten nun das folgende Fehlerfunktional für die spezielle Wahl der Linearform $L$ in Definition \ref{def:totale_differenzierbarkeit} als Jacobi-Matrix $J_f$.
In diesem Fall entspricht die Jacobi-Matrix dem transponierten Gradienten von $f$ nach Bemerkung \ref{rem:jacobi_matrix}, d.h., $J_f(x) = (\nabla f(x))^T$.
Man beachte, dass wir nur irgendeine Linearform finden müssen, die die Definition von totaler Differenzierbarkeit erfüllt.
\begin{align*}
r(\xi) &= f(x+\xi)-f(x)-J_f(x)\xi \ = \ \left(\sum_{k=1}^{n}\partial_k f(z_k + \theta_{k}e_{k})\xi_k\right) - \: \langle \nabla F(x), \xi\rangle \\
&=\ \sum_{k=1}^{n} \left(\partial_k f(z_k + \theta_{k}e_{k}) - \partial_k f(x)\right)\xi_k.
\end{align*}
Mittels der Cauchy-Schwarz Ungleichung in Satz \ref{satz:cauchy-schwarz_r} können wir damit sofort folgern , dass
\begin{align*}
\frac{\norm{r(\xi)}}{\norm{\xi}} \ &\leq \ \frac{\norm{\sum_{k=1}^{n} \partial_k f(z_k + \theta_{k}e_{k}) - \partial_k f(x)} \cdot \norm{\xi}} {\norm{\xi}} \\
&= \ \Vert \sum_{k=1}^{n} \partial_k f(z_k + \theta_{k}e_{k}) - \partial_k f(x) \Vert.
\end{align*}

Per Konstruktion gilt stets $\theta_k\leq\xi_k$ für $0 \leq k \leq n$ und somit
\begin{align*}
\lim_{\xi\rightarrow 0} (z_k + \theta_k e_k) \ = \ \lim_{\xi\rightarrow 0}~(x_1 + \xi_1,\ldots, x_{k-1}\xi_{k-1}, x_k + \theta_k,x_{k+1},\ldots,x_n) \ = \ x.
\end{align*}
Benutzen wir nun die Stetigkeit der partiellen Ableitungen folgt damit schon die totale Differenzierbarkeit von $f$ in $x$ durch
\begin{align*}
\lim_{\xi\rightarrow 0}\frac{\norm{r(\xi)}}{\norm{\xi}} \ \leq \ \lim_{\xi\rightarrow 0} \norm{\sum_{k=1}^{n}  \partial_k f(z_k + \theta_{k}e_{k}) - \partial_k f(x)} \ = \ 0.
\end{align*}
````

Insgesamt haben wir nun eine Abstufung der Stärke der verschiedenen Begriffe von Differenzierbarkeit von Funktionen in mehreren Veränderlichen, wie folgende Bemerkung zusammenfasst.

````{prf:remark}
Sei $U \subset \R^n$ eine offene Teilmenge und $f \colon U \rightarrow \R^m$ eine Funktion.
Zusammengefasst habe wir folgende Implikationskette:

$f$ ist stetig partiell differenzierbar $\Rightarrow$ $f$ ist total differenzierbar $\Rightarrow$  $f$ ist partiell differenzierbar. 

Die Umkehrungen obiger Implikationen gelten im Allgemeinen  nicht, wie wir in verschiedenen Beispielen zeigen konnten.
````

## Die Kettenregel

In diesem Abschnitt beweisen wir eine Verallgemeinerung der Kettenregel für Funktionen mehrerer Veränderlicher, welche im nächsten Satz beschrieben ist.

````{prf:theorem} Kettenregel
:label: satz:kettenregel

Seien $U\subset\R^n, V\subset\R^k$ zwei offene Teilmengen.
Außerdem sei $g:U\rightarrow V$ eine im Punkt $x\in U$ und $f:V\rightarrow \R^m$ eine im Punkt $g(x) \in V$ total differenzierbare Funktion.
Dann ist die Funktion
\begin{align*}
f\circ g \colon \ U\rightarrow \R^m
\end{align*}
im Punkt $x \in U$ total differenzierbar und für das Differential (d.h. für die Jacobi-Matrix) gilt
\begin{align*}
D(f\circ g)(x) \ = \ Df(g(x))\cdot Dg(x).
\end{align*}
````

````{prf:proof}
Wir wählen einen beliebigen Vektor $\xi\in\R^n$, so dass $x + \xi \in U$ ist und betrachten zunächst das Fehlerfunktional $r_g$ für $g$ bezüglich $\xi$ im Punkt $x \in U$ mit
\begin{align*}
r_g(\xi) \, = \, g(x + \xi) - g(x) - Dg(x)\cdot \xi \quad \Leftrightarrow \quad g(x+\xi) \, = \, g(x) + \underbrace{r_g(\xi) + Dg(x)\cdot \xi}_{:=\eta}.
\end{align*} 
Damit gilt für die Konkatenation der Funktionen
\begin{align*}
(f\circ g)(x + \xi) \ = \ f(g(x + \xi)) \ = \ f(g(x) +\eta).
\end{align*}
Analog sehen wir für das Fehlerfunktional $r_f$ für $f$ bezüglich $\eta$ im Punkt $g(x) \in V$, 
\begin{align*}
r_f(\eta) \ &= \ f(g(x) + \eta) - f(g(x)) - Df(g(x))\cdot \eta\\ 
\Leftrightarrow \quad f(g(x) + \eta) \ &= \ f(g(x)) + r_f(\eta) + Df(g(x))\cdot \eta.
\end{align*}
Insgesamt erhalten wir also den folgenden Zusammenhang

```{math}
:label: eq:kettenregel_f_g

\begin{split}
(f\circ g)(x + \xi) \ &= \ f(g(x) + \eta) \ = \ f(g(x)) + r_f(\eta) + Df(g(x))\cdot \eta\\
\ &= \ f(g(x)) + r_f(\eta) + Df(g(x))\cdot (r_g(\xi) + Dg(x)\cdot \xi).
\end{split}
```

Durch Umstellen von {eq}`eq:kettenregel_f_g` erhalten wir folgende Identität:
\begin{equation*}
\begin{split}
r_{f\circ g}(\xi) \ &\coloneqq \ (f\circ g)(x + \xi) - (f \circ g)(x) - Df(g(x)) \cdot Dg(x) \cdot \xi \\
 &= \ r_f(\eta) + Df(g(x)) \cdot r_g(\xi).
\end{split}
\end{equation*}
Es ist klar, dass der Term $(Df(g(x)) \cdot Dg(x))$ ein linearer Operator ist.
Um zu zeigen, dass es sich auch wirklich um das Differential von $(f \circ g)$ im Punkt $x \in U$ handelt müssen wir zeigen, dass das Fehlerfunktional $r_{f\circ g}(\xi)$ gegen Null konvergiert, wenn $\xi$ gegen Null geht und somit $(f \circ g)$ total differenzierbar in $x \in U$ ist.

Um zeigen, dass die Konkatenation $f\circ g$ total differenzierbar in $x \in U$ ist, wählen wir ein beliebiges $\varepsilon>0$. 
Da $g$ total differenzierbar in $x \in U$ ist nach Voraussetzung, wissen wir, dass ein $\delta_1 > 0$ existiert, so dass für $\norm{\xi}\leq \delta_1$ gilt
\begin{align*}
\norm{r_g(\xi)} \ \leq \ \norm{\xi} \ \leq \ \delta_1.
\end{align*}
Somit gilt insbesondere durch Anwendung der Dreiecksungleichung und der Cauchy-Schwarz-Ungleichung
\begin{align*}
\norm{\eta} \ &= \ \norm{r_g(\xi) + Dg(x)\xi} \ \leq \ \norm{\xi} + \norm{Dg(x)}\cdot\norm{\xi} \ \leq \ \norm{\xi} \cdot (1 + \norm{Dg(x)}).
\end{align*}
Da $f$ total differenzierbar im Punkt $g(x) \in V$ nach Voraussetzung ist, wissen wir, dass ein $\delta_2\leq\delta_1$ 
existiert, so dass für beliebiges $\tilde\eta\in\R^k$, mit $\norm{\tilde\eta} < \delta_2$ gilt, dass
\begin{align*}
\norm{r_f(\tilde\eta)} \ \leq \ \varepsilon \norm{\tilde\eta}.
\end{align*}
Wählen wir nun 
\begin{equation*}
\delta \coloneqq \frac{\delta_2}{\norm{1 + Dg(x)}},
\end{equation*}
so folgt, dass $\norm{\eta}\leq \delta_2$ und somit gilt schon für alle $\xi$ mit $\norm{\xi}\leq \delta$
\begin{align*}
\norm{r_f(\eta)} \ \leq \ \varepsilon \norm{\eta} \ \leq \ \varepsilon \norm{\xi} \cdot (1 + \norm{Dg(x)}) \quad \Leftrightarrow \quad \frac{\norm{r^f(\eta)}}{\norm{\xi}} \  \leq \ \varepsilon (1 + \norm{Dg(x)}).
\end{align*}

Wir haben insgesamt also 
\begin{align*}
\lim_{\xi\rightarrow 0} \frac{\norm{r^f(\eta)}}{\norm{\xi}} \ = \ 0
\end{align*}
gezeigt und somit gilt wegen der totalen Differenzierbarkeit von $g$ in $x \in U$ für die Konkatenation
\begin{align*}
\lim_{\xi\rightarrow 0} \frac{\norm{r_{f\circ g}(\xi)}}{\norm{\xi}} \ \leq \
\lim_{\xi\rightarrow 0} 
\frac{\norm{r_f(\eta)}}{\norm{\xi}} + 
\norm{Df(g(x))} \cdot \frac{\norm{r_g(\xi)}}{\norm{\xi}} \ = \ 0.
\end{align*}
````

Im Folgenden wollen wir die Anwendung der mehrdimensionalen Kettenregel an Hand eines einfachen Beispiels illustrieren

````{prf:example}
Wir betrachten zwei total differenzierbare Funktionen $f,g \colon \R^2 \rightarrow \R^2$ mit
\begin{equation*}
f(x,y) \ \coloneqq \
\begin{pmatrix}
x - y \\ x y^2
\end{pmatrix}, \qquad
g(x,y) \ \coloneqq \
\begin{pmatrix}
\sin(x) \\ \cos(y)
\end{pmatrix}.
\end{equation*}
Wir betrachten die Konkatenation $h \coloneqq f \circ g \colon \R^2 \rightarrow \R^2$ der beiden Funktionen mit
\begin{equation*}
h(x,y) \ \coloneqq \ (f \circ g)(x,y) \ = \ f (g (x,y) ) \ = \
\begin{pmatrix}
\sin(x) - \cos(y) \\ \sin(x) \cdot \cos^2(y)
\end{pmatrix}.
\end{equation*}
Wir können die Jacobi-Matrix $J_h$ direkt berechnen als
\begin{equation*}
J_h(x,y) \ = \
\begin{pmatrix}
\partial_x h_1(x,y) & \partial_y h_1(x,y) \\
\partial_x h_2(x,y) & \partial_y h_2(x,y)
\end{pmatrix}
\ = \ 
\begin{pmatrix}
\cos(x) & \sin(y) \\
\cos(x) \cdot \cos^2(y) & -2 \sin(x)\cdot \sin(y) \cdot \cos(y)
\end{pmatrix}.
\end{equation*}

Andererseits können wir über die mehrdimensionale Kettenregel in Satz {prf:ref}`satz:kettenregel` das Differential berechnen als
\begin{equation*}
D(f \circ g) (x) \ = \ D(f(g(x)) \cdot Dg(x).
\end{equation*}
Wir berechnen also zunächst die Jacobi-Matrizen $Df = J_f$ von $f$ und $Dg = J_g$ von $g$:
\begin{equation*}
J_f(x,y) \ = \ 
\begin{pmatrix}
1 & -1 \\
y^2 & 2xy
\end{pmatrix}, \qquad
J_g(x,y) \ = \ 
\begin{pmatrix}
\cos(x) & 0 \\
0 & -\sin(y)
\end{pmatrix}.
\end{equation*}
Durch Einsetzen erhalten wir also insgesamt
\begin{align*}
D(f \circ g)(x) \ &= \ J_f(g(x,y)) \cdot J_g(x,y) \ = \ 
\begin{pmatrix}
1 & -1 \\
\cos^2(y) & 2\sin(x)\cos(y)
\end{pmatrix}
\cdot
\begin{pmatrix}
\cos(x) & 0 \\
0 & -\sin(y)
\end{pmatrix}\\
&= \ 
\begin{pmatrix}
\cos(x) & \sin(y) \\
\cos(x) \cdot \cos^2(y) & -2 \sin(x)\cdot \sin(y) \cdot \cos(y)
\end{pmatrix} \ = \ J_h(x,y).
\end{align*}
Die mehrdimensionale Kettenregel liefert also das gleiche Ergebnis für das Differential der Konkatenation von $f$ und $g$.
````

## Richtungsableitung

Wir führen nun zusätzlich noch das Konzept der Richtungsableitung ein, welches analog zur partiellen Ableitung in Kapitel \ref{s:partielle_ableitungen} Differenzen entlang eindimensionaler Linien betrachtet, mit dem wichtigen Unterschied, dass wir nun beliebige Richtungen im $\R^n$ zulassen werden.

````{prf:definiton}
Sei $U\subset\R^n$ eine offene Teilmenge und sei $f\colon U\rightarrow\R$ eine Funktion. 
Für einen Punkt $x\in U$ und einen normierten Richtungsvektor $v\in\R^n$ mit $\norm{v} = 1$ heißt der Grenzwert (sofern er existiert)
\begin{align*}
D_vf(x) \ \coloneqq \ \frac{d}{dt} f(x + tv)\Big|_{t=0} \ = \ \lim_{t\rightarrow 0}\frac{f(x+ tv)-f(x)}{t}
\end{align*}
\emph{Richtungsableitung} von $f$ am Punkt $x$ in Richtung $v$.
````

Für stetig partiell differenzierbare Funktionen lassen sich Richtungsableitungen leicht über den Gradienten darstellen, wie der folgende Satz aussagt.

````{prf:theorem}
:label: thm:dirder

Sei $U\subset\R^n$ eine offene Teilmenge und sei $f:U\rightarrow\R$ eine stetig partiell differenzierbare Funktion.
Dann gilt für jeden Richtungsvektor $v\in\R^n$ mit $\norm{v}=1$, dass gilt
\begin{align*}
D_vf(x) \ = \ \langle \nabla f(x), v  \rangle
\end{align*}
für alle $x\in U$.
````

````{prf:proof}
In der Hausaufgabe zu zeigen.
````

Die folgende Bemerkung motiviert die Betrachtung der speziellen Richtung des stärksten Gradientenanstiegs bzw. -abstiegs in numerischen Methoden der Optimierung.

````{prf:remark}
Sofern $\nabla f(x) \neq 0$ können wir den Winkel $\theta \coloneqq \sphericalangle(\nabla f(x), v)$  zwischen $\nabla f(x)$ und $v$ definieren. 
In diesem Fall gilt nach Definition \ref{def:winkelmessung} die Identität
\begin{align*}
\langle \nabla f(x), v \rangle \ = \ \norm{v}\cdot\norm{\nabla f(x)}\cdot\cos(\theta) \ = \ \norm{\nabla f(x)}\cdot\cos(\theta).
\end{align*}
Dieser Ausdruck wird maximal bzw. minimal wenn für den Winkel $\theta$ gilt
\begin{align*}
\cos(\theta) \, = \, 1 \quad &\Leftrightarrow \quad \theta \, = \, 0 \quad \Leftrightarrow \quad v \, = \, \nabla f(x)\\
\cos(\theta) \, = \, -1\quad & \Leftrightarrow \quad \theta \, = \, \pi \quad \Leftrightarrow \quad v \, = \, -\nabla f(x).
\end{align*}
Anschaulich bedeutet diese Beobachtung, dass am Punkt $x$ der steilste Aufstieg bzw. Abstieg in Richtung des (negativen) Gradienten erfolgt. 
Diese Überlegung bildet die Grundlagen vieler numerischer Optimierungsverfahren, da diese Richtung offensichtlich die Funktionswerte am stärksten verändert.
````

## Der Mittelwertsatz

Für Funktionen mehrerer Veränderlicher haben wir bisher häufig alle Koordinatenrichtungen bis auf eine fixiert haben, so dass wir effektiv den Mittelwertsatz für Funktionen in einer Veränderlichen benutzen konnten. 
Analog können wir reellwertige Funktionen in mehreren Veränderlichen auch entlang beliebiger Richtungen betrachten was zu folgender Aussage führt.

````{prf:theorem} Mittelwertsatz für reellwertige Funktionen
:label: satz:mittelwertsatz_reellwertig

Sei $U\subset\R^n$ eine offene Teilmenge und $f:U\rightarrow\R$ eine stetig partiell differenzierbare Funktion. 
Für einen Punkt $x\in U$ und einem Richtungsvektor $\xi\in\R^n$ mit $(x+t\xi) \in U$ für alle $t\in[0,1]$ existiert ein $\theta\in[0,1]$, so dass
\begin{align*}
f(x+\xi) - f(x) \ = \ \langle\nabla f(x + \theta\xi),\xi\rangle.
\end{align*}
````

````{prf:proof}
Wir betrachten die eindimensionale Einschränkung $g(t):=f(x+t\xi)$ von $f$ und sehen mit Hilfe des Mittelwertsatzes für Funktionen in einer Veränderlichen (\citep{burger_2020}, Kapitel 6.2), dass ein $\theta\in[0,1]$ existiert, so dass wir mit der Kettenregel aus Satz {prf:ref}`satz:kettenregel` erhalten
\begin{align*}
f(x+\xi) - f(x) \ &= \ g(1)- g(0) \ = \ g^\prime(\theta) \cdot 1 \\ 
&= \ \nabla f(g(\theta)) \cdot g'(\theta) \ = \ \langle\nabla f(x+\theta\xi), \xi\rangle.
\end{align*}
````

Die obige Darstellung des Mittelwertsatzes funktioniert leider nur für reellwertige Funktionen, wie die folgende Bemerkung feststellt.

````{prf:remark}
:label: bem:mittelwertsatz

Für vektorwertige Funktionen $f:U\rightarrow\R^m$ scheitert die Überlegung aus Satz {prf:ref}`satz:mittelwertsatz_reellwertig` leider, da wir hier verschiedene unabhängige Komponenten im Bildbereich haben. 
Wir müssten also den Mittelwertsatz für reellwertige Funktionen auf jede Komponente $f_i$ von $f$ einzeln anwenden und erhalten in obiger Notation $m$ verschiedene Zwischenstellen $x + \theta_i\xi \in \R^n$. 
Da diese Zwischenstellen im Allgemeinen verschieden sind scheitert das Argument.

Das Konzept lässt sich allerdings durch folgende Überlegungen verallgemeinern.
Für eine stetig differenzierbare Funktion $f:I\rightarrow\R$, wobei $I\subset\R$ eine offene Teilmenge sei, folgt aus dem Hauptsatz der Differential- und Integralrechnung \cite[Kapitel 7.2]{burger_2020}, dass
\begin{align*}
f(x+\xi)-f(x) \ = \ \left(\int_0^{1} f^\prime(x+t\xi)\, \mathrm{d}t\right)\cdot\xi.
\end{align*}
Diese Integralform lässt sich nun auch auf Funktionen mit mehreren Komponenten übertragen. 
Dazu bemerken wir kurz, dass das Integral einer matrixwertigen Funktion $A:\R\rightarrow\R^{n\times m}$ durch das Integral der einzelnen Matrix-Einträge gegeben ist, das heißt es gilt
\begin{align*}
\left(\int_{t_0}^{t_1} A(t)\, \mathrm{d}t\right)_{i,j} \ = \ \int_{t_0}^{t_1} A_{i,j}(t)\, \mathrm{d}t
\end{align*}
für $1\leq i \leq n,  1 \leq j \leq m$.
````

Basierend auf der Beobachtung in Bemerkung {prf:ref}`bem:mittelwertsatz` können wir im Folgenden den Mittelwertsatz für vektorwertige Funktionen in mehreren Veränderlichen formulieren.

````{prf:theorem} Mittelwertsatz
:label: satz:mittelwertsatz_vektorwertig

Sei $U\subset\R^n$ eine offene Teilmenge und  sei $f:U\rightarrow\R^m$ eine stetig partiell differenzierbare, vektorwertige Funktion.
Für einen beliebigen Punkt $x\in U$ und einen Richtungsvektor $\xi\in\R^n$ mit $x+t\xi\in U$ für alle $t\in[0,1]$ gilt
\begin{align*}
f(x+\xi) - f(x) \ = \ \left(\int_0^1 Df (x+t\xi)\, \mathrm{d}t\right) \cdot \xi.
\end{align*}
\end{satz}
\begin{proof}
Für jede Komponente $f_i$ im Bild von $f$ betrachten wir eine eindimensionale Funktion $g_i:[0,1]\rightarrow\R$ mit
\begin{align*}
g_i(t)\ \coloneqq \ f_i(x+t \xi).
\end{align*}
Wenden wir auf diese Funktionen den Hauptsatz der Differential- und Integralrechnung \cite[Kapitel 7.2]{burger_2020} an und benutzen die Darstellung der Richtungsableitung aus Satz {prf:ref}`thm:dirder`, so sehen wir, dass für jede Komponente $i \in \lbrace 1, \ldots, m \rbrace$ gilt
\begin{align*}
f_i(x+\xi)-f_i(x) \ &= \ g_i(1)-g_i(0) \ = \ \int_0^1 g_i^\prime(t) \, \mathrm{d}t \\
&= \ \int_0^1 \langle \nabla f_i(x + t\xi),\xi\rangle \, \mathrm{d}t \ = \ \langle \int_0^1\nabla f_i(x + t\xi)\, \mathrm{d}t, \xi\rangle.
\end{align*}
````

Der allgemeine Mittelwertsatz {prf:ref}`satz:mittelwertsatz_vektorwertig` erlaubt es uns zusätzlich eine sehr praktische Norm-Abschätzung herzuleiten.
Dafür benötigen wir jedoch zunächst folgendes Hilfslemma.

````{prf:lemma}
:label: lem:norm_integral_abschaetzung

Sei $f:[t_0,t_1]\rightarrow\R^m$ eine stetige Funktion, dann gilt 
\begin{align*}
\left\Vert\int_{t_0}^{t_1} f(t)\, \mathrm{d}t\right\Vert \ \leq \ \int_{t_0}^{t_1} \norm{f(t)}\, \mathrm{d}t.
\end{align*}
````

````{prf:proof}
In der Hausaufgabe zu zeigen.
````


Mit Hilfe des Lemmas {prf:ref}`lem:norm_integral_abschaetzung` können wir nun ein nützliche Abschätzung für die Abstand zweier Funktionswerte in Abhängigkeit des Differentials zeigen.

````{prf:theorem}
:label: thm:meanest

Sei $U\subset\R^n$ eine offene Teilmenge und  sei $f:U\rightarrow\R^m$ eine stetig partiell differenzierbare, vektorwertige Funktion.
Für einen Punkt $x\in U$ und einem Richtungsvektor $\xi\in\R^n$ mit $(x+t\xi) \in U$ für alle $t\in[0,1]$ sei außerdem
\begin{align*}
M \ \coloneqq \ \sup_{t\in[0,1]} \norm{Df(x+t\xi)}.
\end{align*}
Dann gilt die folgende Abschätzung
\begin{align*}
\norm{f(x+\xi) - f(x)} \ \leq \ M \cdot \norm{\xi}.
\end{align*}
````

````{prf:proof}
In der Hausaufgabe zu zeigen.
````
