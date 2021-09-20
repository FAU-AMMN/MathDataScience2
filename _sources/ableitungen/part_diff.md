# Partielle Differenzierbarkeit

Um den Begriff der Ableitung auf Funktionen mehrerer Variablen zu übertragen, betrachtet man zunächst deren Änderungsverhalten entlang einzelner Koordinatenrichtungen.
Wir fixieren also einen Punkt $x\in U$ und betrachten die Funktion 

\begin{equation*}
\tilde{f}(\xi) \ \coloneqq \ f(x_1,\ldots,x_{i-1},\xi,x_{i+1},\ldots,x_n).
\end{equation*}

Anschaulich gesprochen halten wir alle Variablen, bis auf die $i$-te fest und erhalten somit eine eindimensionale Funktion. 
Dies erlaubt es uns den Ableitungsbegriff auf die schon bekannte Definition für Funktionen in einer Veränderlichen herunterzubrechen, was zum Begriff der partiellen Differenzierbarkeit führt.

````{prf:definition} Partielle Differnzierbarkeit
:label: def:partielle_diffbarkeit

Sei $U\subset \R^n$ eine offene Teilmenge und $f:U\rightarrow \R$ eine Funktion.

_i)_ Wir nennen die Funktion $f$ *(lokal) partiell differenzierbar* im Punkt $x\in U$ in die $i$-te Koordinatenrichtung falls folgender Grenzwert existiert, 
    
```{math}
\frac{\partial f}{\partial x_i} (x) \ \coloneqq \ \partial_i f(x) \      \coloneqq \ \lim_{h\rightarrow 0} \frac{f(x + h\cdot e_i) - f(x)}{h}.
```

_ii)_ Wir nennen die Funktion $f$ *(global) partiell differenzierbar* falls sie für jedes $x\in U$ und jede Koordinatenrichtung $i\in\{1,\ldots,n\}$ partiell differenzierbar ist. 

_iii)_ Ist die Funktion $\partial_i f:U\rightarrow \R$ partiell differenzierbar und zudem stetig für jedes $i\in\{1,\ldots,n\}$, so nennen wir $f$ *stetig partiell differenzierbar*.
````

In der obigen Definition bezeichnet
\begin{equation*}
e_i \ \coloneqq \ (0,\ldots,0,\underbrace{1}_{i\text{-te Stelle}},0,\ldots,0)\in\R^n
\end{equation*}
den $i$-ten Einheitsvektor des $\R^n$. 
Im Grenzwert für $h\rightarrow 0$ sind nur Nullfolgen $(h_k)_{k\in\N}$ erlaubt, welche die Bedingung 
\begin{equation*}
(x+h_k\cdot e_i) \in U \quad \text{ mit } \quad h_k \neq 0, \ \forall k\in \N
\end{equation*}
erfüllen. 
Das Symbol $\partial$ ist hierbei eine stilisierte Version des Buchstaben d (manchmal auch del ausgesprochen).

Im folgenden Beispiel berechnen wir die partielle Ableitung der Euklidischen Norm im $\R^n$.

````{prf:example}
Wir betrachten die Abbildung
\begin{align*}
f :\R^n \ &\rightarrow \ \R_0^+\\
x \ &\mapsto \ \norm{x}{}_2 \ \coloneqq \ \sqrt{\sum_{i=1}^n x_i^2},
\end{align*}
welche die Euklidische Norm im $\R^n$ darstellt. 
Wir betrachten die *Niveaumengen* $N_f \subset \R^n$ von $f$ mit
\begin{align*}
N_f(c) \ \coloneqq \ \{x\in \R^n:f(x) = c\} \ = \ \{f^{-1}(c)\}.
\end{align*}

In diesem Fall sind die Niveaumengen $N_{f}(c)$ Sphären mit Radius $c\in \R^+_0$. 
Weiterhin sieht man leicht, dass die Funktion $f$ auf der Menge $\R^n \setminus \{0\}$ partiell differenzierbar 
ist, da wir für $x\neq 0$ mittels Kettenregel die folgende partielle Ableitung erhalten
\begin{align*}
\partial_i \norm{x}{}_2 \ &= \ \partial_i \left( (\sum_{i=1}^n x_i)^{\frac{1}{2}} \right) \ = \ \partial_i \left(x_i^2 + \sum_{j\neq i} x_j^2\right)^{1/2}\\
\ &= \ \frac{1}{2}\left(x_i^2+\sum_{j\neq i} x_j^2\right)^{-1/2}\cdot 2x_i \ = \ \frac{x_i}{\norm{x}{}_2}.
\end{align*}
````

Der Begriff der partiellen Differenzierbarkeit in Definition {prf:ref}`def:partielle_diffbarkeit` ist der schwächste Ableitungsbegriff für Funktionen in mehreren Veränderlichen.
Anders als im eindimensionalen Fall gilt beispielsweise nicht, dass aus der partiellen Differenzierbarkeit einer Funktion schon folgt, dass diese stetig ist.
Das soll uns das folgende Beispiel vor Augen führen.

````{prf:example}
Wir betrachten im Folgenden eine Funktion auf $\R^n$ mit $n\geq 2$ die zeigt, dass aus partieller Differenzierbarkeit keine Stetigkeit folgt. 
Dazu definieren wir
\begin{align*}
f(x) \ \coloneqq \
\begin{cases}
\ \frac{x_1 \cdot x_2 \cdot \ldots \cdot x_n}{\norm{x}{}_2^n}, \quad &\text{falls } x\neq 0,\\
\ 0, \quad &\text{falls } x=0.
\end{cases}
\end{align*}
Man sieht sofort, dass die Funktion $f$ auf $\R^n\setminus \{0\}$ stetig und auch partiell differenzierbar ist. 

Wir überprüfen nun die partielle Differenzierbarkeit im Punkt $x=0$.
Hierzu betrachten wir für $h\neq 0$
\begin{align*}
f(0+h\cdot e_i) \, - \, f(0) \ = \ \frac{0 \cdot \ldots \cdot 0\cdot h\cdot 0\cdot \ldots \cdot 0}{\norm{h\cdot e_i}{}_2^n} \, - \, 0 \ = \ 0  
\end{align*} 
und somit folgt direkt
\begin{align*}
\lim_{h\rightarrow 0} \frac{f(0+h\cdot e_i) - f(0)}{h} \ = \ 0
\end{align*}
für alle Richtungen $i\in\{1,\ldots,n\}$. 
Daher wissen wir also, dass die Funktion $f$ auch im Punkt $x=0$ partiell differenzierbar ist. 

Tatsächlich ist die Funktion aber nicht stetig in der Null.
Dafür betrachten wir eine Folge $(a_k)_{k\in \N}\subset\R^n\setminus \{0\}$, die diagonal in den Nullpunkt hineinläuft, d.h., konkret betrachten wir
\begin{equation*}
a_k \ \coloneqq \ (\frac1k,\ldots,\frac1k)^T, \quad k\in\N.
\end{equation*}
Für jedes Folgeglied $a_k, k\in\N$, der Folge gilt dann $\norm{a_k}{}_2 = \frac{\sqrt{n}}{k}$ und somit ist der Funktionswert von $f$ für diese Folgeglieder gegeben durch
\begin{align*}
f(a_k) \ = \ \frac{(1/k)^n}{(\sqrt{n}/k)^n} \ \equiv \ \left( \frac{1}{\sqrt{n}} \right)^n \ = \ n^{-\frac{n}{2}}, \quad k\in\N.
\end{align*}
Daraus folgt aber schon, dass 
\begin{align*}
\lim_{k\rightarrow\infty} f(a_k) \ \equiv \ n^{-\frac{n}{2}} \ \neq \ 0 \ = \ f(0) \ = \ f(\lim_{k\rightarrow\infty} a_k).
\end{align*}
Das bedeutet also, dass die Funktion $f$ nicht stetig im Punkt $x=0$ ist. 

Man bemerke, dass diese Konstruktion nur für höherdimensionale Räume $\R^n$ mit $n\geq 2$ möglich ist, da die analog  definierte Funktion im Eindimensionalen nicht differenzierbar ist.
````
