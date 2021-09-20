# Taylor-Formel

Wie wir schon anhand der Definition des Fehlerfunktionals bei der totalen Differenzierbarkeit gesehen haben, liefert das Differential einer Funktion $f$ an einem Punkt $x$ eine affin-lineare Approximation der Funktion an dieser Stelle. Mithilfe der Taylor-Formel wollen wir nun eine bessere Annäherung an die Funktion erhalten, in dem wir höhere Ableitungen hinzunehmen.
Diese Formel ist ein sehr nützliches Werkzeug bei der Approximation von Funktionen durch einfachere Polynome und erfährt beispielsweise in der Physik oder in der Numerik regelmäßig Anwendung. Dadurch können beispielsweise nichtlineare Funktionen in einer lokalen Umgebung linear angenähert werden, was viele Berechnungen und Abschätzungen vereinfacht.

## Satz von Rolle

Bevor wir die Taylor-Formel für Funktionen in einer Veränderlichen betrachten, benötigen wir das folgende Hilfslemma.

````{prf:lemma} Satz von Rolle
:label: satz:rolle

Sei $[a,b] \subset \R$ ein Intervall mit $a < b$ und sei $f \colon [a,b] \rightarrow \R$ eine stetige Funktion, die auf dem offenen Intervall $(a,b)$ differenzierbar ist.
Es sei außerdem $f(a) = f(b)$.

Dann existiert eine Punkt $x_0 \in (a,b)$, so dass $f'(x_0) = 0$.
````

````{prf:proof}
Falls $f$ eine konstante Funktion ist mit $f(x) \equiv f(a) = f(b)$ für alle $x \in [a,b]$, so ist die Aussage des Lemmas trivialerweise erfüllt, da für konstante Funktionen $f'(x_0) = 0$ für alle $x_0 \in (a,b)$ gilt.

Sei also $f$ nicht konstant. Da $f$ auf dem kompakten Intervall $[a,b] \subset \R$ stetig ist nach Voraussetzung, nimmt die Funktion auf dem Intervall nach Satz dem Satz von Weierstraß \cite[Satz 5.19]{burger_2020} an einer Stelle $m \in [a,b]$ ein Minimum und an einer Stelle $M \in [a,b]$ ein Maximum an. 
Da $f$ nicht konstant ist muss wegen $f(a) = f(b)$ mindestens $m \in (a,b)$ oder $M \in (a,b)$ gelten.
Wir bezeichnen diese Extremstelle als den Punkt $x_0 \in (a,b)$.

Falls es sich bei $x_0$ um ein Maximum handelt, so folgt aus der Differenzierbarkeit von $f$ in $(a,b)$, dass
\begin{equation*}
f'(x_0) \ = \ \lim_{h\searrow 0} \frac{f(x_0 + h) - f(x_0)}{h} \ \leq \ 0 \quad \text{ und } \quad f'(x_0) \ = \ \lim_{h \nearrow 0} \frac{f(x_0 + h) - f(x_0)}{h} \ \geq \ 0.
\end{equation*}
Damit folgt schon, dass $f'(x_0) = 0$ sein muss.

Falls $f$ in $x_0$ ein Minimum annimmt, so kann man analog argumentieren und erhält auch in diesem Fall $f'(x_0) = 0$.
````

## Eindimensionale Taylor-Formel

Mit Hilfe des obigen Lemmas können wir nun einen der wichtigsten Sätze zur Approximation von beliebigen Funktionen formulieren.
Die Taylor-Formel erlaubt die Annäherung einer Funktion durch ein Polynom und erlaubt es den Fehler bei dieser Approximation abzuschätzen.

````{prf:theorem} Eindimensionale Taylor-Formel
:label: satz:taylor_eindimensional

Es sei $I\subset\R$ ein offenes Intervall und es sei $f:I\rightarrow\R$ eine $(k+1)$-mal stetig differenzierbare Funktion für $k \in \N$. 
Dann existiert für ein beliebiges kompaktes Intervall $[t_0,t_1]\subset I$ ein $\theta\in[t_0,t_1]$, so dass die folgende \emph{Taylor-Formel} gilt
\begin{align*}
f(t_1) \ = \ \sum_{i=0}^k \frac{d^i}{dt^i} f (t_0)\cdot \frac{(t_1-t_0)^i}{i!}
+ \frac{d^{k+1}}{dt^{k+1}} f(\theta) \cdot \frac{(t_1-t_0)^{k+1}}{(k+1)!}
\end{align*}
Hierbei folgen wir der Konvention, dass $0! \coloneqq 1$ ist.
````

````{prf:proof}
Für ein beliebiges $a\in\R$ betrachten wir die Hilfsfunktion
\begin{align*}
g(t) \ \coloneqq \ f(t_1) - f(t) - \sum_{i=1}^k \frac{d^i}{dt^i} f(t)\cdot\frac{(t_1-t)^i}{i!} - a\cdot\frac{(t_1-t)^{k+1}}{(k+1)!}.
\end{align*}
Offensichtlich ist $t_1 \in I$ eine Nullstelle von $g$ mit $g(t_1) = 0$.
Wenn wir nun $a \in R$ wählen als
\begin{align}\label{eq:taylor_1d_a}
a \ \coloneqq \ \frac{(k+1)!}{(t_1-t_0)^{k+1}} \left(f(t_1) - f(t_0) -  \sum_{i=1}^k \frac{d^i}{dt^i} f(t_0)\cdot \frac{(t_1-t_0)^i}{i!} \right)
\end{align}
so erhalten wir auch $g(t_0)=0$. 

Nach Voraussetzung ist $g$ stetig differenzierbar und somit insbesondere stetig.
Damit folgt nach dem Satz {prf:ref}`satz:rolle` von Rolle, dass ein $\theta\in[t_0,t_1]$ existiert, so dass $g^\prime(\theta)=0$ gilt. 
Diese Stelle $\theta$ können wir nutzen um den Term $a$ noch näher zu charakterisieren. 
Wir erhalten mit der Produktregel der Differentialrechnung, dass
\begin{align*}
g^{\prime}(\theta) \ &= \ -f^{\prime}(\theta) - \sum_{i=1}^k \frac{d^{i+1}}{dt^{i+1}} f(\theta)\cdot \frac{(t_1-\theta)^i}{i!} + \sum_{i=1}^k \frac{d^{i}}{dt^{i}} f(\theta)\cdot\frac{(t_1-\theta)^{i-1}}{(i-1)!} + a\cdot\frac{(t_1-\theta)^{k}}{k!}\\
\ &= \ - \frac{d^{k+1}}{dt^{k+1}} f(\theta)\cdot\frac{(t_1-\theta)^k}{k!}  + a\cdot\frac{(t_1-\theta)^{k}}{k!} \ = \ \frac{(t_1-\theta)^{k}}{k!} \cdot \left( a - \frac{d^{k+1}}{dt^{k+1}}f(\theta) \right) \ = \ 0.
\end{align*}
Wir sehen also, dass der Term $a$ in \eqref{eq:taylor_1d_a} gleichzeitig folgende Identität erfüllt:
\begin{align*}
a \ = \ \frac{d^{k+1}}{dt^{k+1}} f(\theta).
\end{align*}
Setzen wir diese Darstellung in die Hilfsfunktion $g$ ein und werten diese in $t_0 \in I$ aus, so erhalten wir schließlich:
\begin{equation*}
g(t_0) \ = \ f(t_1) - f(t_0) - \sum_{i=1}^k \frac{d^i}{dt^i} f(t)\cdot\frac{(t_1-t_0)^i}{i!} - \frac{d^{k+1}}{dt^{k+1}} f(\theta)\cdot\frac{(t_1-t_0)^{k+1}}{(k+1)!} \ = \ 0.
\end{equation*}
Durch Umstellen folgt nun direkt die Taylor-Formel.
````

Im Folgenden wollen wir einige Beobachtungen zur Taylor-Formel festhalten.

````{prf:remark}
Die zusätzlichen Bemerkungen helfen dabei die Taylor-Formel in Satz {prf:ref}`satz:taylor_eindimensional` vernünftig zu interpretieren.

* Wir nennen 
\begin{equation*}
f(t_1) \ = \ \underbrace{\sum_{i=0}^k \frac{d^i}{dt^i} f (t_0)\cdot \frac{(t_1-t_0)^i}{i!}}_{\eqqcolon T_k f(t_1; t_0)}
+ \underbrace{\frac{d^{k+1}}{dt^{k+1}} f(\theta) \cdot \frac{(t_1-t_0)^{k+1}}{(k+1)!}}_{\eqqcolon R_k f(t_1; t_0)}
\end{equation*}
die _Taylor-Entwicklung_ $k$-ter Ordnung von $f(t_1)$ im Punkt $t_0\in I$.
Sie gliedert sich in eine Approximation der ursprünglichen Funktion $f$ im Punkt $t_1 \in I$ durch ein (Taylor-)Polynom $T_k f(t_1; t_0)$ vom Grad $k$ ausgewertet in $t_1$ und einen Fehlerterm $R_k f(t_1; t_0)$.

* Der Term $R_k f(t_1; t_0)$ wird _Lagrangesches Restglied_ der Taylor-Entwicklung $k$-ter Ordnung genannt. 
Er beschreibt den Fehler, den man macht, wenn man den Funktionswert $f(t_1)$ durch eine Auswertung des Taylorpolynoms von Grad $k$ im Punkt $t_0 \in I$ approximiert.

Es wird klar, dass dieser Fehler maßgeblich durch den Abstand der beiden Punkte $t_0, t_1 \in I$ zueinander bestimmt wird.
Je näher der Entwicklungspunkt $t_0$ an der untersuchten Stelle $t_1$ liegt, desto besser ist die Approximation.
````

Das folgende Beispiel soll uns helfen zu verstehen, wie die Taylor-Entwicklung zur Approximation einer Funktion konkret eingesetzt werden kann.

````{prf:example}
Wir betrachten eine Funktion $f \colon \R \rightarrow \R$ mit $f(x) \coloneqq e^x$.
Wir möchten den Funktionswert von $f$ in $t_1 = 1$ approximieren durch eine Taylor-Entwicklung im Punkt $t_0 = 0$.

Hierzu formulieren wir zunächst die Taylor-Entwicklung **erster Ordnung**:
\begin{equation*}
\begin{split}
f(1) \ = \ T_1f(1; 0) + R_1 f(1; 0) \ &= \ f(0)\cdot 1 + f'(0) \cdot \frac{(1-0)^1}{1!} + R_1 f(1; 0) \\
& \approx \ f(0) + f'(0) \ = \ e^0 + e^0 \ = \ 2.
\end{split}
\end{equation*}
Durch den Wegfall des Restglieds $R_1 f(1;0)$ wird der Funktionswert nur linear approximiert.
Vergleichen wir diese Approximation mit dem echten Funktionswert, so erhalten wir
\begin{equation*}
| f(1) - T_1f(1;0)| \ = \ | e^1 - 2| \ \approx \ 0.72.
\end{equation*}

Betrachten wir nun die Taylor-Entwicklung **zweiter Ordnung**:
\begin{equation*}
\begin{split}
f(1) \ = \ T_2f(1; 0) + R_2 f(1; 0) \ &= \ f(0)\cdot 1 + f'(0) \cdot \frac{(1-0)^1}{1!} + f''(0) \cdot \frac{(1-0)^2}{2!} + R_2 f(1; 0) \\
& \approx \ f(0) + f'(0) + \frac{1}{2}f''(0) \ = \ e^0 + e^0 + \frac{1}{2}e^0 \ = \ 2.5 .
\end{split}
\end{equation*}
Durch den Wegfall des Restglieds $R_2 f(1;0)$ wird der Funktionswert nun quadratisch approximiert.
Vergleichen wir diese Approximation mit dem echten Funktionswert, so erhalten wir
\begin{equation*}
| f(1) - T_2f(1;0)| \ = \ | e^1 - 2.5| \ \approx \ 0.22.
\end{equation*}
Wir erkennen also, dass die Approximation durch Erhöhung der Ordnung der Taylorentwicklung genauer wird.
````

## Multiindizes

Die Taylor-Formel aus Satz {prf:ref}`satz:taylor_eindimensional` gilt auch für vektorwertige Funktionen in mehreren Veränderlichen.
Für diese Verallgemeinerung müssen wir jedoch zunächst die folgende Notation einführen.

````{prf:definition} Multiindex
Für ein $n$-Tupel $\alpha=(\alpha_1,\ldots,\alpha_n)\in\N^n$, genannt _Multiindex_, definieren wir die folgenden Operationen
\begin{align*}
\abs{\alpha} \ \coloneqq \ \sum_{i=1}^n \alpha_i \qquad \text{ und } \qquad \alpha! \ \coloneqq \ \prod_{i=1}^n (\alpha_i!).
\end{align*}
Für eine $\abs{\alpha}$-mal stetig partiell differenzierbare Funktion $f$ definieren wir weiterhin
\begin{align*}
\partial^\alpha f = \partial_1^{\alpha_1}\ldots\partial_n^{\alpha_n} f.
\end{align*}
Das heißt wir leiten die Funktion $f$ in jede Koordinatenrichtung $i \in \lbrace 1, \ldots n \rbrace$ genau $\alpha_i$-mal ab. 
Analog setzen wir
\begin{align*}
x^{\alpha} \ \coloneqq \ \prod_{i=1}^n x_i^{\alpha_i}.
\end{align*}
````

Ähnlich zu den Überlegung zum Mittelwertsatz betrachten wir nun zunächst eine Funktion $g(t):=f(x+t\xi)$, das heißt eine eindimensionale Funktion welche entlang einer Richtung $\xi\in \R^n$ vom Punkt $x$ aus betrachtet wird. Das  Konzept entlang von eindimensionalen Strahlen zu operieren ist elementar für die Taylor-Formel, weshalb wir zunächst folgendes Hilfsresultat zeigen.

````{prf:lemma}
:label: lem:Taylor

Sei $U\subset\R^n$ eine offene Teilmenge und sei $f:U\rightarrow\R^m$ eine $k$-mal stetig partiell differenzierbare Abbildung.
Für einen beliebigen Punkt $x\in U$ und einen Richtungsvektor$\xi\in\R^n$ mit $x+t\xi\in U$ für alle 
$t\in[0,1]$, gilt für die $k$-te Ableitung der Funktion $g(t):=f(x+t\xi)$
\begin{align*}
\frac{d^k}{dt^k} g(t) \ = \ \sum_{\abs{\alpha}=k} \partial^\alpha f(x+t\xi) \cdot \frac{k!}{\alpha!} \cdot \xi^\alpha.
\end{align*}
````

````{prf:proof}
Im ersten Schritt zeigen wir zunächst die Identität
\begin{align*}
\frac{d^k}{dt^k} g(t) \ = \  \sum_{i_1=1}^n\ldots\sum_{i_k=1}^n \partial_{i_k}\ldots\partial_{i_1} f(x+t\xi)
\cdot\xi_{i_1}\cdot\ldots\cdot\xi_{i_k}
\end{align*}
mittels vollständiger Induktion über $k\in \N$.\\[0.3cm]
\textbf{Induktionsanfang $k=1$:}\\
In diesem Fall betrachten wir die Funktion $\phi(t):=x+t\xi$ und erhalten so die Verkettung $g=f\circ\phi$.
Somit können wir die Kettenregel aus Satz {prf:ref}`satz:kettenregel` benutzen und erhalten, dass 
\begin{align*}
\frac{d}{dt} g(t) \ = \ \nabla f(\phi(t)) \cdot D\phi(t) \ = \ \sum_{i=1}^n \partial_i f(x+t\xi)\cdot\xi_i.
\end{align*}
~\\[0.3cm]
\textbf{Induktionsschritt $(k-1)\to k$:}\\
Die Induktionsannahme ist, dass die Aussage bereits für $k-1$ gelte. 
Mit der gleichen Rechnung wie im Fall $k=1$ sehen wir dann,
\begin{align*}
\frac{d^k}{dt^k} g(t) \ &= \ \frac{d}{dt}\left(\frac{d^{k-1}}{dt^{k-1}}g\right)(t)\\%
&= \ \frac{d}{dt} \left( \sum_{i_1,\ldots,i_{k-1}=1}^n \partial_{i_{k-1}}\ldots\partial_{i_1}  f(x + t\xi) \cdot\xi_{i_1}\cdot \ldots \cdot \xi_{i_{k-1}} \right)\\
&=
\sum_{j=1}^n\partial_j
\left(
\sum_{i_1,\ldots,i_{k-1}=1}^n \partial_{i_{k-1}}\ldots\partial_{i_1}  f(x + t\xi) \cdot\xi_{i_1}\cdot\ldots\cdot\xi_{i_{k-1}}
\right)\cdot\xi_j.
\end{align*}

Um die eigentliche Behauptung zu zeigen müssen wir nun lediglich die Indizierung über das Tupel $(i_1,\ldots,i_k)$ in die Multiindex Schreibweise umrechnen. 
Das funktioniert folgendermaßen: 
Für ein Tupel $\iota = (i_1,\ldots,i_k)$ definieren wir den zugehörigen Multiindex $\alpha^\iota \in\N^n$ durch 
\begin{align*}
\alpha^\iota_i \ \coloneqq \ \sum_{j=0}^k \delta_{i_j, i},
\end{align*}
wobei
\begin{align*}
\delta_{i_j, i} \ = \ 
\begin{cases}
1&\text{falls } i_j = i\\
0&\text{sonst}.
\end{cases}
\end{align*}

Anschaulich gesprochen zählt der Eintrag $\alpha^\iota_i$ wie oft der Index $i$ im Tupel $\iota$ vorkommt.
Offensichtlich gilt für derartige Multiinidizes stets
\begin{align*}
\abs{\alpha^\iota} \, = \, k
\end{align*}
und insbesondere 
\begin{align*}
\partial_{i_{k}}\ldots\partial_{i_1} f(x + t\xi) \cdot\xi_{i_1}\cdot\ldots\cdot\xi_{i_{k}} \ = \ \partial^{\alpha^\iota}f(x + t\xi)\cdot \xi^{\alpha^\iota}.
\end{align*}
Der letzte Schritt um die Behauptung zu zeigen ist zu zählen wie viele Tupel $\iota = (i_1,\ldots,i_k)$ auf den gleichen 
Multiindex $\alpha^\iota$ führen durch obige Konstruktion. 
Aus der Kombinatorik wissen wir, dass es genau $\frac{k!}{\alpha!}$ verschiedene solcher Tupel gibt, was man folgendermaßen sieht: 
\begin{itemize}
\item Zunächst wollen wir $\alpha_1$-mal den Index $1$ auf $k$ Plätze verteilen, wofür es 
\begin{align*}
\begin{pmatrix} k\\ \alpha_1\end{pmatrix} \ = \ \frac{k!}{\alpha_1!\cdot(k-\alpha_1)!}
\end{align*}
verschiedene Möglichkeiten gibt.
\item Im zweiten Schritt verteilen wir $\alpha_2$-mal den Index $2$ auf 
die verbliebenen $k-\alpha_1$ Plätze wofür es dann
\begin{align*}
\begin{pmatrix} k -\alpha_1\\ \alpha_2\end{pmatrix} \ = \ \frac{(k - \alpha_2)!}{\alpha_1!\cdot(k-\alpha_1-\alpha_2)!}
\end{align*}
verschiedene Möglichkeiten gibt.
\item Führen wir diesen Prozess iterativ weiter und multiplizieren die jeweiligen Möglichkeiten auf, so erhalten wir insgesamt
\begin{align*}
\frac{k!\cdot (k-\alpha_1)\cdot\ldots (k-\alpha_1-\ldots-\alpha_n)}
{\alpha_1!\cdot(k-\alpha_1)\cdot\ldots\cdot
(k-\alpha_1-\ldots-\alpha_n)\cdot\alpha_n!\cdot 0!} \ = \
\frac{k!}{\alpha!}.
\end{align*}
Dies vervollständigt den Beweis weil wir nun die folgende Identität gezeigt haben
\end{itemize}
\begin{align*}
\frac{d^k}{dt^k} g(t) \ &= \ 
\sum_{i_1,\ldots, i_k=1}^n
\partial_{i_k}\ldots\partial_{i_1} f(x+t\xi)
\cdot\xi_{i_1}\cdot\ldots\cdot\xi_{i_k}\\ 
\ &= \
\sum_{\abs{\alpha}=k}
\partial^\alpha f(x+t\xi)\cdot \frac{k!}{\alpha!} \cdot \xi^\alpha.
\end{align*}
````

## Mehrdimensionale Taylor-Formel

Diese Hilfsaussage erlaubt es uns nun den eigentlichen Hauptsatz dieses Abschnitts zu zeigen, die mehrdimensionale Taylor-Formel.

````{prf:theorem} Mehrdimensionale Taylor-Formel
:label: satz:taylorformel_mehrdimensional

Sei $U\subset\R^n$ eine offene Teilmenge und $f:U\rightarrow\R^m$ eine $(k+1)$-mal stetig partiell differenzierbare Abbildung. 
Für einen beliebigen Punkt $x\in U$ und einen Richtungsvektor $\xi\in\R^n$ mit $x+t\xi\in U$ für alle $t\in[0,1]$, existiert ein $\theta\in[0,1]$, so dass
\begin{align*}
f(x+\xi) \ = \ 
\sum_{\abs{\alpha}\leq k} \partial^\alpha f(x)\cdot\frac{1}{\alpha!} \cdot \xi^\alpha + 
\sum_{\abs{\alpha}=k+1} \partial^\alpha f(x+\theta\xi) \cdot \frac{1}{\alpha!} \cdot \xi^\alpha.
\end{align*}
\end{satz}
\begin{proof}
Wir betrachten erneut die eindimensionale Funktion
\begin{align*}
g(t) \ \coloneqq \ f(x+t\xi)
\end{align*}
und da $g$ somit eine $(k+1)$-mal differenzierbare Funktion ist können wir die eindimensionale Taylor-Formel aus Satz \ref{satz:taylor_eindimensional} anwenden und erhalten somit ein $\theta\in[0,1]$, so dass
\begin{align*}
g(1) \ = \ \sum_{i=0}^k \frac{d^i}{dt^i} g(0) \cdot\frac{1}{i!} + \frac{d^{k+1}}{dt^{k+1}} g(\theta) \cdot \frac{1}{(k+1)!}.
\end{align*}
In dieser Form können wir nun Lemma {prf:ref}`lem:Taylor` auf jede der Ableitungen $\frac{d^i}{dt^i} g$ anwenden, was die Aussage beweist.
````

Die folgende Bemerkung hält einige Beobachtungen zur Taylor-Formel fest.

````{prf:remark}
Wir bemerken zur mehrdimensionalen Taylor-Formel in Satz {prf:ref}`satz:taylorformel_mehrdimensional` die folgenden Aussagen.

* Wir sehen ein, dass der Mittelwertsatz {prf:ref}`satz:mittelwertsatz_reellwertig` ein Spezialfall der Taylor-Formel für $k=0$ ist, da er aussagt, dass
\begin{equation*}
f(x + \xi) - f(x) \ = \ \langle \nabla f(x + \theta \xi), \xi \rangle \quad \text{ für ein } \quad \theta \in [0,1].
\end{equation*}
* Oftmals spricht man im Zusammenhang mit der Taylor-Form auch von den sogenannten _Taylorpolynomen_. 
In der typischen Schreibweise wird nun $x$ zur Variable, wir fixieren $a\in\R^n$ und nennen dann
\begin{align*}
T_k(x;a) \ \coloneqq \ \sum_{\abs{\alpha}\leq k} \partial^\alpha f (a)\cdot \frac{(x - a)^\alpha}{\alpha!}
\end{align*}
_Taylorpolynom_ der Ordnung $k$ an der Entwicklungsstelle $a$. 
Hierbei ist zu beachten, dass $T_k(\cdot;a)$ ein Polynom ist für jedes _fixierte_ $a\in\R^n$. 
Wir bemerken auch, dass in dieser Schreibweise $(x - a)$ nun die Rolle von $\xi$ in Satz {prf:ref}`satz:taylorformel_mehrdimensional` inne hat, während die Rolle von $x$ durch $a$ übernommen wurde.
````

Im obigen Satz haben wir vorausgesetzt, dass die Funktion $(k+1)$-mal stetig partiell differenzierbar ist.
Ist sie jedoch nur $k$-mal stetig partiell differenzierbar, so erhalten wir keinen expliziten Ausdruck für das Restglied, aber zumindest eine Fehlerabschätzung.

````{prf:corollary}
:label: cor:taylor_approximation

Sei $U\subset\R^n$ eine offene Teilmenge und sei $f:U\rightarrow\R$ eine $k$-mal stetig partiell differenzierbare Funktion. 
Dann gilt für jeden Punkt $x\in U$, dass die Funktion 
\begin{align*}
r(\xi) \ \coloneqq \ f(x+\xi) - \sum_{\abs{\alpha}\leq k} \partial^\alpha f(x)\cdot \frac{1}{\alpha!} \cdot \xi^\alpha
\end{align*}
folgende Grenzwert-Eigenschaft hat:
\begin{align*}
\lim_{\xi\rightarrow 0}\frac{\abs{r(\xi)}}{\norm{\xi}^k} \ = \ 0.
\end{align*}
````

````{prf:proof}
Wir wählen $\delta>0$, so dass $B_\delta(x)\subset U$.
Wir wissen nach der Taylor-Formel in Satz {prf:ref}`satz:taylorformel_mehrdimensional`, dass für $\xi\in B_\delta(x)$ ein $\theta\in[0,1]$ existiert, so dass
\begin{align*}
f(x+\xi) \ &= \ \sum_{\abs{\alpha}\leq k-1} \partial^\alpha f(x) \cdot  \frac{1}{\alpha!} \cdot\xi^\alpha + 
\sum_{\abs{\alpha}=k} \partial^\alpha f(x+\theta\xi)\cdot \frac{1}{\alpha!} \cdot \xi^\alpha\\
&= \ \sum_{\abs{\alpha}\leq k} \partial^\alpha f(x)\cdot \frac{1}{\alpha!} \cdot \xi^\alpha + 
\underbrace{
\sum_{\abs{\alpha}=k} \left( \partial^\alpha f(x+\theta\xi)-\partial^\alpha f(x)\right)
\cdot \frac{1}{\alpha!} \cdot \xi^\alpha}_{=r(\xi)}.
\end{align*}
Weiterhin sehen wir, dass 
\begin{align*}
\abs{\xi^\alpha} \ \leq \ \norm{\xi}^{\alpha_1}\cdot\ldots\cdot\norm{\xi}^{\alpha_n}
\ = \ \norm{\xi}^k.
\end{align*}
Somit erhalten wir also
\begin{align*}
\abs{r(\xi)}\ \leq \ \norm{\xi}^k \cdot  
\sum_{\abs{\alpha}=k} \abs{(\partial^\alpha f)(x+\theta\xi)-(\partial^\alpha f)(x)} \cdot \frac{1}{\alpha!}.
\end{align*}
Wegen der Stetigkeit aller partiellen Ableitungen folgt, dass für jedes 
$\varepsilon>0$ ein $\delta>0$ existiert, so dass 
\begin{align*}
\abs{(\partial^\alpha f)(x+\theta\xi)-(\partial^\alpha f)(x)} \ \leq \ \varepsilon
\end{align*} 
für alle $\xi\in B_\delta(x)$ und alle $\alpha$ mit $\abs{\alpha}\leq k$. 
Hierbei ist zu beachten, dass $\theta$ zwar jeweils von $\xi$ abhängt, aber da $\theta\in[0,1]$ gilt, wissen wir, dass 
\begin{align*}
\xi\in B_\delta(x) \ \Rightarrow  \ \theta\xi\in B_\delta(x).
\end{align*}

Insgesamt haben wir damit
\begin{align*}
\lim_{\xi\rightarrow 0}\frac{\abs{r(\xi)}}{\norm{\xi}^k} 
\ = \ \lim_{\xi\rightarrow 0}
\sum_{\abs{\alpha}=k} \abs{\partial^\alpha f(x+\theta\xi)-\partial^\alpha f(x)} \cdot \frac{1}{\alpha!} \ = \ 0.
\end{align*}
````

````{prf:remark}
Im Sinne des Korollars {prf:ref}`cor:taylor_approximation` gilt für den Fehler des Taylorpolynoms an einer Stelle $x$, dass der Approximationsfehler
\begin{align*}
r(x) \ \coloneqq \ f(x) - T_k(x,a) 
\end{align*}
den Grenzwert
\begin{align*}
\lim_{x\rightarrow a}\frac{|r(x)|}{\norm{x-a}^k} \ = \ 0
\end{align*}
erfüllt.

Speziell für den Fall $k=1$ sehen wir, dass 
\begin{align*}
\sum_{\abs{\alpha}= 1}  
\partial^\alpha f(x)\cdot\frac{1}{\alpha!}\cdot\xi^\alpha \ = \ 
\sum_{i=1}^n \partial_i f(x) \cdot\xi_i \ = \
\langle \nabla f(x), \xi \rangle
\end{align*}
gilt.
Für den Fall $k=2$ erhalten wir
\begin{align*}
\sum_{\abs{\alpha}= 2}
\partial^\alpha f(x)\cdot\frac{1}{\alpha!} \cdot \xi^\alpha \ = \ 
\sum_{i,j=1}^n \partial_i \partial_j f(x)\cdot\frac{1}{2} \cdot \xi_i\cdot\xi_j \ = \
\frac{1}{2} \cdot \langle \xi, H_f(x)\xi \rangle,
\end{align*}
wobei $H_f(x)$ die Hesse-Matrix von $f$ an der Stelle $x$ bezeichnet. 
````

Da der Fall $k=2$ in obiger Bemerkung relevant für die grundlegenden Aussagen der Optimierung im nächsten Kapitel sind, fassen wir die obigen Überlegungen in einem Korollar zusammen.

````{prf:corollary}
Sei $U\subset\R^n$ eine offene Teilmenge und sei $f:U\rightarrow\R$ eine zweimal stetig partiell differenzierbare Funktion. Für jeden Punkt $x\in U$ existiert dann ein $\delta>0$ und eine Funktion $r \colon B_\delta(x)\rightarrow \R$, so dass
\begin{align*}
f(x+\xi) \ = \ f(x) + \langle \nabla f(x), \xi \rangle + \frac{1}{2}\langle H_f(x)\xi,\xi\rangle + r(\xi),
\end{align*}
für alle $\xi\in B_\delta(0)$ gilt.
Außerdem gilt
\begin{align*}
\lim_{\xi\rightarrow 0}\frac{\abs{r(\xi)}}{\norm{\xi}^2} \ = \ 0.
\end{align*}
````
