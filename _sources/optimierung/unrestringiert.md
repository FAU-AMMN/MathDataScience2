# Unrestringierte Optimierung

Im Folgenden wollen wir uns auf eine bestimmte Klasse von allgemeinen Optimierungsproblemen konzentrieren, den \textit{unbeschränkten} oder \textit{unrestringierten} Optimierungsproblemen.
\begin{definition}[Unrestringierte Optimierung]
Liegt ein allgemeines Optimierungsproblem der Form \eqref{eq:optimierungsproblem_allgemein} ohne Nebenbedingungen vor, d.h., für die Indexmengen gilt $\mathcal{E} = \mathcal{I} = \emptyset$, so sprechen wir von einem \emph{unbeschränkten} oder \emph{unrestringierten Optimierungsproblem}.
\end{definition}
\begin{remark}
Häufig lassen sich restringierte Optimierungsprobleme in unrestringierte Optimierungsprobleme überführen, indem man zusätzliche Strafterme zur Zielfunktion hinzufügt, die eine Verletzung der ursprünglichen Nebenbedingungen zwar mit Kosten belegt, diese jedoch grundsätzlich erlaubt. Hierbei spricht man auch von \emph{relaxierten Optimierungsproblemen}.

Möchte man eine Zielfunktion $F \colon \Omega \rightarrow \R$ unter der Nebenbedingung $c(x) = 0$ für $x\in \Omega$ minimieren, so lässt sich beispielsweise folgendes relaxierte Optimierungsproblem gewinnen
\begin{equation*}
\min_{x\in\Omega} G_\lambda(x) \ \coloneqq \ \min_{x\in\Omega} F(x) + \lambda\cdot ||c(x)||^2.
\end{equation*}
Hierbei ist $\lambda > 0$ ein fest gewählter Parameter, der es erlaubt den Einfluss der Nebenbedingung auf die Minimerung der Zielfunktion zu steuern.
\end{remark}

Zur Bestimmung von Optima müssen wir zunächst den Begriff eines stationären Punkts einer zu optimierenden Zielfunktion einführen.
\begin{definition}[Stationärer Punkt]
Sei $\Omega \subset \mathbb{R}^n$ eine offene, zusammenhängende Teilmenge und sei $F \colon \Omega \rightarrow \mathbb{R}$ eine reellwertige Zielfunktion. 
Wir nennen einen Punkt $x^* \in \Omega$ \emph{stationären Punkt} von $F$, falls er die Bedingung 
\begin{equation*}
\nabla F(x^*) \, = \, 0
\end{equation*}
erfüllt.
\end{definition}

Stationäre Punkte sind in der Optimierung interessante Kandidaten für Extremstellen.
Für eine genaue Charakterisierung führen wir zunächst den Begriff eines lokalen bzw. globalen Minimums ein.
\begin{definition}[Lokales und globales Minimum]
Sei $\Omega \subset \mathbb{R}^n$ eine offene, zusammenhängende Teilmenge und sei $F \colon \Omega \rightarrow \mathbb{R}$ eine reellwertige Zielfunktion. 
Wir nennen einen Punkt $x^* \in \Omega$ ein \emph{lokales Minimum} der Funktion $F$, falls es eine lokale Umgebung $U \subset \Omega$ von $x^* \in U$ gibt, so dass für alle $x \in U$ gilt:
\begin{equation}
\label{eq:lokales_minimum}
F(x^*) \, \leq \, F(x), \quad \text{ für alle } x \in U.
\end{equation}
Wir nennen $x^* \in \Omega$ ein \emph{globales Minimum} von $F$, falls die Ungleichung \eqref{eq:lokales_minimum} für jede beliebige Umgebung $U \subset \Omega$ gilt und somit insbesondere für $U = \Omega$. 
\end{definition}
\begin{remark}

In obiger Definition sprechen wir nur von Minima, jedoch ist klar, dass sich jedes Maximierungsproblem durch einen Vorzeichenwechsel leicht in ein Minimierungsproblem umschreiben lässt, d.h.,
\begin{equation*}
\max_{x\in\Omega} F(x) \ \Leftrightarrow \ \min_{x\in\Omega} -F(x) \ \eqqcolon \ \min_{x_\in\Omega} G(x).
\end{equation*}
\end{remark}

Da wir nun eine Bedingung für das Vorliegen eines lokalen Minimums haben, können wir mit folgenden Satz die notwendigen Bedingungen für solch ein lokales Minimum angeben.
\begin{thm}[Notwendige Optimalitätsbedingungen erster Ordnung]\label{satz:minimum_notwendig_ersteOrdnung}
Sei $\Omega \subset \mathbb{R}^n$ eine offene, zusammenhängende Teilmenge und sei $F \colon \Omega \rightarrow \mathbb{R}$ eine reellwertige Zielfunktion. 
Sei $x^*\in \Omega$ ein lokales Minimum von $F$ in $\Omega$ und die Funktion $F$ sei stetig partiell differenzierbar in einer lokalen, offenen Umgebung $U \subset \Omega$ von $x^*$. 
Dann gilt 
\begin{equation*}
\nabla F(x^*) \: = \: 0.
\end{equation*}
\end{thm}
\begin{proof}[Beweis:]
Wir führen einen Beweis durch Widerspruch. 
Nehmen wir also an, dass $x^* \in \mathbb{R}$ ein lokales Minimum von $F$ sei, jedoch aber $\nabla F(x^*) \neq 0$ gelte.
Wir wählen den Richtungsvektor $\vec{p} \coloneqq -\nabla F(x^*) \neq 0$. 
Es ist somit klar, dass 
\begin{equation*}
\langle \vec{p}, \nabla F(x^*) \rangle \ = \ - \langle \nabla F(x^*), \nabla F(x^*) \rangle \ = \ - ||\nabla F(x^*)||^2 \ < \ 0.
\end{equation*}
Da $\nabla F$ nach Voraussetzung stetig in einer lokalen Umgebung $U \subset \Omega$ von $x^*$ ist existiert ein $T > 0$, so dass auch gilt:
\begin{equation*}
\langle \vec{p}, \nabla F(x^* + t\vec{p}) \rangle < 0, \quad \text{ für alle } t\in [0,T].
\end{equation*}
Nach dem Satz \ref{satz:taylorformel_mehrdimensional} von Taylor gilt aber auch für jedes $t \in [0,T]$:
\begin{equation*}
F(x^* + t\vec{p}) \ = \ F(x^*) +~\underbrace{t\langle \vec{p}, \nabla F(x^* + \tilde{t}\vec{p}) \rangle}_{<~0}, \quad \text{ für ein } \tilde{t} \in (0,t).
\end{equation*}
Somit gilt also $F(x^* + t\vec{p}) < F(x^*)$ und wir haben offenbar eine Richtung $\vec{p} \in \mathbb{R}^n \setminus \lbrace 0\rbrace$ gefunden in der die Funktionswerte von $F$ abnehmen. 
Also ist $x^* \in \Omega$ kein lokales Minimum von $F$. 
Das ist aber ein Widerspruch zur Annahme und somit ist die Behauptung bewiesen.
\end{proof}

Die Aussage des Satzes \ref{satz:minimum_notwendig_ersteOrdnung} lässt sich wie folgt zusammenfassen.
\begin{cor}
Jedes lokale Minimum $x^* \in \Omega$ einer Zielfunktion $F \colon \Omega \rightarrow \mathbb{R}$ ist ein stationärer Punkt.
\end{cor}

Die Umkehrung der Aussage in Satz \ref{satz:minimum_notwendig_ersteOrdnung} gilt im Allgemeinen nicht, wie uns das folgende Beispiel zeigt.
\begin{bsp}
Wir betrachten die Funktion
\begin{equation*}
F(x) \, \coloneqq \, -x^3.
\end{equation*}
Diese besitzt einen stationären Punkt in $x^* = 0$, d.h., es gilt $\nabla F(0) = 0$. 
Dennoch handelt es sich hierbei nicht um ein lokales Optimum, sondern lediglich um einen \emph{Sattelpunkt}.
\end{bsp}

Bei der Suche nach lokalen Minima einer Zielfunktion $F$ lässt sich ein weiteres Kriterium anwenden, welches die zweite Ableitung der Funktion verwendet.
\begin{thm}[Notwendige Optimalitätsbedingungen zweiter Ordnung]
Sei $\Omega \subset \mathbb{R}^n$ ein offenes, zusammenhängendes Gebiet und sei $F \colon \Omega \rightarrow \mathbb{R}$ eine reellwertige Zielfunktion. 
Sei $x^*\in \Omega$ ein lokales Minimum von $F$ in $\Omega$ und die Hessematrix $H_F$ von $F$ sei stetig in einer offenen Umgebung $U \subset \Omega$ von $x^*$, d.h., die Funktion $F$ ist zweimal stetig partiell differenzierbar auf der Teilmenge $U$.
Dann gilt $\nabla F(x^*) = 0$ und $H_F(x^*)$ ist positiv semidefinit, d.h., es gilt 
\begin{equation*}
\langle \vec{p}, H_F(x^*) \vec{p} \rangle \ \geq \ 0 \quad \text{ für alle } \ \vec{p} \in \mathbb{R}^n.
\end{equation*}
\end{thm}
\begin{proof}[Beweis:]
Der erste Teil der Behauptung folgt bereits aus Satz \ref{satz:minimum_notwendig_ersteOrdnung}, so dass wir uns nur auf den Beweis für die zweite Behauptung konzentrieren müssen.

Wir führen wieder einen Beweis durch Widerspruch. 
Sei $x^* \in \Omega$ nach Voraussetzung ein lokaler Minimierer von $F$, das heißt nach Satz \ref{satz:minimum_notwendig_ersteOrdnung} gilt $\nabla F(x^*) = 0$. 
Wir nehmen an, dass $H_F F(x^*)$ nicht positiv semidefinit ist. 
Dann können wir einen Vektor $\vec{p} \in \mathbb{R}^n / \lbrace 0\rbrace$ finden, so dass
\begin{equation*}
\langle \vec{p}, H_F (x^*)\vec{p} \rangle \ < \ 0
\end{equation*}
gilt. 
Da $H_F$ nach Voraussetzung stetig ist in einer lokalen Umgebung $U \subset \Omega$ von $x^*$ existiert ein $T > 0$, so dass
\begin{equation*}
\langle \vec{p}, H_F(x^* + t\vec{p})\vec{p} \rangle \ < \ 0, \quad \text{ für alle } t\in[0,T]. 
\end{equation*}
Nach dem Satz \ref{satz:taylorformel_mehrdimensional} von Taylor gilt jedoch für alle $t \in (0,T)$ die folgende Identität
\begin{equation*}
F(x^* + t\vec{p}) \ = \ F(x^*) + \underbrace{t\langle \vec{p}, \nabla F(x^*) \rangle}_{=~0} \, + \, \frac{1}{2}\underbrace{t^2\langle \vec{p}, H_F(x^* + \tilde{t}\vec{p})\vec{p}\rangle}_{<~0}, \quad \text{ für ein } \tilde{t} \in (0,t).
\end{equation*}
Durch Weglassen des Terms auf der rechten Seite der Gleichung folgt also, dass $F(x^* + \hat{t}\vec{p}) < F(x^*)$ gilt.
Wir haben also eine Richtung $\vec{p} \in \mathbb{R}^n/\lbrace 0 \rbrace$ gefunden entlang der die Funktionswerte von $F$ abnehmen. 
Damit folgt, dass $x^*$ kein lokales Minimum von $F$ ist, was aber im Widerspruch zur Annahme steht. 
Das beweist die Aussage des Satzes.
\end{proof}

Schlussendlich wollen wir auch eine hinreichende Bedingung für das Vorliegen eines lokalen Minimums angeben.
\begin{thm}[Hinreichende Optimalitätsbedingungen zweiter Ordnung]
\label{thm:minimum_hinreichend}
Sei $\Omega \subset \mathbb{R}^n$ eine offene, zusammenhängende Teilmenge und sei $F \colon \Omega \rightarrow \mathbb{R}$ eine reellwertige Zielfunktion. 
Sei $x^*\in \Omega$ ein Punkt für den gelte
\begin{enumerate}[(i)]
\item $\nabla F(x^*) \ = \ 0$,
\item $H_F(x^*)$ ist positiv definit.
\end{enumerate}
Außerdem sei die Hesse-Matrix $H_F$ von $F$ stetig in einer offenen Umgebung $U \subset \Omega$ von $x^* \in U$. 
Dann ist $x^* \in \Omega$ ein striktes lokales Minimum von $F$.
\end{thm}
\begin{proof}
Da die Hesse-Matrix $H_F$ von $F$ stetig und positiv definit in $x^* \in \Omega$ ist nach Voraussetzung können wir einen Radius $r > 0$ finden, so dass $H_F(x)$ positiv definit ist für alle $x \in B_r(x^*)$. 
Für jeden Vektor $\vec{p} \in \mathbb{R}^n / \lbrace 0\rbrace$ mit $||\vec{p}|| < r$ gilt dann nach dem Satz \ref{satz:taylorformel_mehrdimensional} von Taylor:
\begin{equation*}
F(x^* + \vec{p}) \ = \ F(x^*) +~\underbrace{\langle \vec{p}, \nabla F(x^*) \rangle}_{=~0} \: + \: \frac{1}{2} \langle \vec{p}, H_F(x^* + t\vec{p})\vec{p} \rangle, \quad \text{ für ein } t\in (0,1).
\end{equation*}
Da $||t\vec{p}|| < r$ ist nach Konstruktion wissen wir, dass
\begin{equation*}
\langle \vec{p}, H_F(x^* + t\vec{p})\vec{p} \rangle \ > \ 0
\end{equation*}
gilt und somit schon $F(x^* + \vec{p}) > F(x^*)$ gelten muss. 
Da $\vec{p} \in \mathbb{R}^n / \lbrace 0 \rbrace$ mit $||\vec{p}|| < r$ beliebig gewählt war handelt es sich bei $x^* \in \Omega$ um ein striktes lokales Minimum der Funktion $F$.
\end{proof}

\begin{remark}
An Hand der Definitheit der Hesse-Matrix können wir also in vielen Fällen die Art des stationären Punkts charakterisieren.
Es stellt sich heraus, dass folgende Beobachtungen gelten:
\begin{itemize}
    \item Ist die Hesse-Matrix \emph{positiv definit}, handelt es sich um ein \textbf{lokales Minimum}.
    \item Falls die Hesse-Matrix \emph{negativ definit} ist, so ist der stationäre Punkt ein \textbf{lokales Maximum}.
    \item Ist die Hesse-Matrix \emph{indefinit}, so handelt es sich um einen \textbf{Sattelpunkt}.
\end{itemize}
Sollte die Hesse-Matrix in einem stationären Punkt \emph{semidefinit} sein, so lässt sich keine eindeutige Aussage treffen.
\end{remark}

Im Folgenden wollen wir die  notwendigen und hinreichenden Optimalitätsbedingungen für verschiedene Zielfunktionen prüfen.
\begin{example}
Wir untersuchen zwei unterschiedliche Zielfunktionen auf mögliche Extremstellen.
\begin{enumerate}
\item
Zuerst diskutieren wir eine einfache eindimensionale Zielfunktion $F \colon \R \rightarrow \R$ mit
\begin{equation*}
F(x) = x^4.
\end{equation*}
Wir prüfen die notwendigen Optimalitätsbedingungen erster Ordnung aus Satz \ref{satz:minimum_notwendig_ersteOrdnung} und bemerken, dass der einzige stationäre Punkt von $F$ in $x^* = 0$ vorliegt, da
\begin{equation*}
F'(x) \ = \ 4x^3 \ = \ 0 \quad \Leftrightarrow \ x \ = \ 0. 
\end{equation*}
Da $F''(x) = 12x^2$ ist gilt im stationären Punkt $x^* = 0$ nur $F''(0) = 0$.
Daher können wir nicht die hinreichenden Optimalitätsbedingungen zweiter Ordnung aus Satz \ref{thm:minimum_hinreichend} anwenden, da die zweite Ableitung nicht positiv ist.
Dennoch erkennen wir, dass $F$ ein striktes lokales Minimum in $x=0$ besitzt mit $\nabla F(0) = 0$.
Dies zeigt uns, dass die in Satz \ref{thm:minimum_hinreichend} genannten Bedingungen nur hinreichend sind, jedoch nicht notwendig für das Vorliegen eines strikten lokalen Minimums.
\item 
Nun diskutieren wir eine zweidimensionale Zielfunktion $F \colon \R^2 \rightarrow \R$ mit
\begin{equation*}
F(x,y) \ = \ 6 x^2-2 x-4 x y+y^2+1
\end{equation*}
Zur Bestimmung von möglichen Extremstellen der Zielfunktion müssen wir zunächst den Gradienten berechnen.
Hierzu bestimmen wir die ersten partiellen Ableitungen von $F$ als
\begin{equation*}
\begin{split}
\partial_x F(x,y) \ &= \ 12x -2 -4y, \\
\partial_y F(x,y) \ &= \ -4x + 2y 
\end{split}
\end{equation*}
Zur Bestimmung eines stationären Punkts setzen wir
\begin{equation*}
\nabla F(x,y) \ = \ (\partial_x F(x,y), \partial_y F(x,y))^T \ = \ (12x -2 -4y, -4x + 2y)^T \ \overset{!}{=} \ (0,0)^T.
\end{equation*}
Um mögliche Kandidaten für ein lokales Extremum zu finden müssen wir also folgendes lineares Gleichungssystem lösen:
\begin{equation*}
Ax \ = \ 
\begin{pmatrix}
12 & -4 \\
-4 & 2\\
\end{pmatrix}
\begin{pmatrix}
x \\
y
\end{pmatrix}
\ = \
\begin{pmatrix}
2\\
0
\end{pmatrix}
\ = \ f.
\end{equation*}
Durch Lösen des linearen Gleichungssystems erhalten wir den einzigen stationären Punkt in
\begin{equation*}
x^* \ = \ (0.5, 1)^T.
\end{equation*}
Wir berechnen als Nächstes die Hesse-Matrix $H_F$ von $F$ mit den zweiten Ableitungen:
\begin{align*}
\partial^2_x F(x,y) \ &= \ \partial_x (12x -2 - 4y) \ = \ 12,\\
\partial_y \partial_x F(x,y) \ &= \ \partial_y (12x -2 - 4y) \ = \ -4,\\
\partial_x \partial_y F(x,y) \ &= \ \partial_x (-4x + 2y) \ = \ -4,\\
\partial^2_y F(x,y) \ &= \ \partial_y (-4x + 2y) \ = \ 2.
\end{align*}
Insgesamt ergibt sich also für die Hesse-Matrix im stationären Punkt $x^* \in \R^2$
\begin{equation*}
H_F(x^*) \ = \
\begin{pmatrix}
12 & -4 \\
-4 & 2
\end{pmatrix}.
\end{equation*}
Zur Bestimmung der Definitheit von $H_F$ stellen wir das charakteristische Polynom $P_{H_F}$ auf als
\begin{equation*}
P_{H_F}(t) \ = \ (12 - t)*(2-t) - 16 \ = \ t^2 - 14t + 8.
\end{equation*}
Wir bestimmen die Eigenwerte der Hesse-Matrix $H_F$ als Nullstellen des charakteristischen Polynoms $P_{H_F}$ mittels p-q-Formel und erhalten somit
\begin{equation*}
\begin{split}
\lambda_{1/2} \ &= \ -\frac{p}{2} \pm \sqrt{\frac{p^2}{4} - q} \ = \ \frac{14}{2} \pm \sqrt{\frac{196}{4} -8}\\
\ &= \  7 \pm \sqrt{41}
\end{split}
\end{equation*}
Da beide Eigenwerte $\lambda_{1/2} = 7 \pm \sqrt{41}$ von $H_F$ positiv sind, ist die Hesse-Matrix positiv definit.
Damit sind die hinreichenden Bedingungen aus Satz \ref{thm:minimum_hinreichend} für ein striktes lokales Minimum von $F$ im Punkt $x^* \ = \ (0.5, 1)$ erfüllt.
Da die Hesse-Matrix auf ganz $\R^2$ positiv definit ist, handelt es sich sogar um ein globales Minimum.
%\item 
%\begin{equation*}
%F(x,y) = y (x-2)^2 - y^2
%\end{equation*}
\end{enumerate}
\end{example}

Eine äußerst wertvolle Eigenschaft bei der Optimierung ist die Konvexität einer Zielfunktion, da jedes lokale Optimum einer konvexen Funktion bereits ein globales Optimum ist.
\begin{definition}[Konvexität]
Sei $\Omega \subset \mathbb{R}^n$ eine offene, zusammenhängende Teilmenge und sei $F \colon \Omega \rightarrow \mathbb{R}$ eine reellwertige Zielfunktion. 
Wir nennen $F$ \emph{konvex} wenn für beliebige Vektoren $x,y \in \Omega$ die folgende Ungleichung für alle $0 \leq \alpha \leq 1$ gilt:
\begin{equation}\label{eq:konvex}
F(\alpha x + (1-\alpha)y) \ \leq \ \alpha F(x) + (1-\alpha)F(y).
\end{equation}
Wir nennen die Funktion $F$ \emph{strikt konvex}, falls \eqref{eq:konvex} eine echte Ungleichung ist.

Anschaulich bedeutet Konvexität einer Funktion $F$, dass jede Verbindungsgerade zwischen zwei Punkten $x,y \in \Omega$ oberhalb des Graphen der Funktion $F$ durch die Punkte $x$ und $y$ verläuft.
\end{definition}

Folgende Bemerkung stellt die Bedeutung von Konvexität für die Optimierung fest.
\begin{remark}
Sei $\Omega \subset \R^n$ eine offene, zusammenhängende Teilmenge und $F \colon \Omega \rightarrow \R$ eine Zielfunktion.
Man kann zeigen, dass die Hesse-Matrix $H_F(x)$ genau dann positiv definit ist für alle $x\in \Omega$, wenn $F$ eine strikt konvexe Funktion ist.

Dies hat zur Konsequenz, dass wenn man einen stationären Punkt $x^* \in \Omega$ findet mit $\nabla F(x^*) = 0$, so ist dieser Punkt das eindeutige, globale Minimum der Zielfunktion.
\end{remark}
