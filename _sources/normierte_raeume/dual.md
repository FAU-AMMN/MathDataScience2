# Dualräume

Zu einem normierten Vektorraum können wir seinen sogenannten topologischen Dualraum betrachten.
Dieser Dualraum erlaubt es beispielsweise in der Differentialgeometrie eine Integration auf einer Mannigfaltigkeit zu definieren oder aber Optimierungsprobleme in eine (manchmal angenehmere) äquivalente, duale Form zu überführen.
Wir definieren daher zunächst den Begriff des topologischen Dualraums im Folgenden.

````{prf:definition} Topologischer Dualraum und Funktional
Der _topologische Dualraum_ $X'$ zu einem normierten $\K$-Vektorraum $X$ ist definiert als die Menge aller stetigen, linearen Funktionen von $X$ in den Körper $\K$ der reellen oder komplexen Zahlen.
Oft spricht man nur von dem zugehörigen Dualraum, wenn der mathematische Kontext eindeutig ist.

Insbesondere wenn $X$ unendlich-dimensional ist, nennt man eine Funktion $F \in X'$
\begin{equation*}
F \colon X \rightarrow \K
\end{equation*} 
häufig ein _Funktional_.
````

Folgendes Beispiel erinnert an Funktionale, die Sie bereits kennengelernt haben.

````{prf:example}
Die Abbildung
\begin{equation*}
\begin{split}
F  \colon C([a,b]; \R) \ &\rightarrow \ \R,\\ 
f \ &\mapsto \ F(f) \ \coloneqq \ \int_a^b f(x) \, \mathrm{d}x
\end{split}
\end{equation*}
ist linear und stetig für Funktionen $f$, die auf einem Intervall $I \subset \R$ integrierbar sind, d.h., es handelt sich um ein Funktional $F \in C([a,b]; \R)'$.

Ein physikalisch motiviertes Beispiel für die Anwendung von Funktionalen wäre die Bewegung eines Massepunkt entlang einer Kurve $\varphi \colon [0,1] \rightarrow \R^3$ in einem Potentialfeld $V\colon \R^3 \rightarrow [0,\infty) $.
Hierbei berechnet man die verrichtete Arbeit durch das folgende Funktional
\begin{equation*}
F(V) \ \coloneqq \ \int_0^1 V(\varphi(s)) \, \mathrm{d}s.
\end{equation*}
````

````{prf:remark}
Folgende Anmerkungen zum Dualraum wollen wir festhalten.

* Neben dem topologischen Dualraum $X'$ existiert in der Literatur der _algebraische Dualraum_ $X^*$, aller linearen (aber nicht notwendigerweise stetigen) Funktionale von $X$ nach $\K$.
Für endlich-dimensionale Vektorräume $X$ stimmen der algebraische und topologische Dualraum überein, da in diesem Fall alle linearen Operatoren auf $X$ automatisch stetig sind.

* Da $X$ ein normierter Vektorraum ist, ist sein zugehöriger topologischer Dualraum $X'$ auch ein normierter Vektorraum ausgestattet mit der folgenden Operatornorm
\begin{equation*}
||F||_{X'} \ = \ \sup_{||x||_X \leq 1} |F(x)|.
\end{equation*}
Da die Funktionale $F\in X'$ per Definition in den vollständigen Körper $\K$ abbilden ist $X'$ selbst ein Banachraum, unabhängig davon ob $X$ ein Banachraum ist.

* Falls $X$ sogar ein Hilbertraum ist, so ist sein zugehöriger topologischer Dualraum $X'$ nach dem Darstellungssatz von Fréchet-Riesz \cite{} isometrisch isomorph zum Vektorraum $X$ selbst.
Das bedeutet, dass ein isometrischer Isomorphismus $\Phi$ existiert, der jedem Element $x \in X$ ein eindeutiges Funktional $F \in X'$ zuordnet mit
\begin{equation*}
\begin{split}
\Phi \colon X \ &\rightarrow \ X'\\
x \ &\mapsto \ \Phi(x) \ \coloneqq \ \langle x, \cdot \rangle_X \ \eqqcolon \ F(x).
\end{split}
\end{equation*}
````

Das folgende Beispiel illustriert noch einmal die Isomorphie eines Hilbertraums mit seinem Dualraum für den endlich-dimensionalen Fall.

````{prf:example}
Wir betrachten den Hilbertraum $(\R^n, ||\cdot||_2)$ und versuchen zu verstehen, wie sein zugehöriger Dualraum $X'$ aussieht.
Da alle Elemente $a \in X'$ mit $a \colon \R^n \rightarrow \R$ linear sein müssen,  wird klar, dass diese Abbildungen von der Form $\langle a, \cdot \rangle$ sein müssen mit:
\begin{equation*}
a(x) \ \coloneqq \ \langle a, x \rangle \ = \ (a_1,\ldots, a_n)^T \cdot (x_1, \ldots, x_n) \ = \ \sum_{i=1}^n a_i x_i, \quad \text{ für alle } x\in \R^n.
\end{equation*}
Offensichtlich realisieren diese linearen Abbildungen Skalarprodukte mit $n$-dimensionalen Vektoren, welche auch häufig _kovariante Vektoren_ oder _Kovektoren_ genannt werden.
Ein Isomorphismus zwischen $X$ und seinem Dualraum $X'$ lässt sich mittels darstellender Matrizen bezüglich der Standardbasen der beiden Räume bestimmen.
````
