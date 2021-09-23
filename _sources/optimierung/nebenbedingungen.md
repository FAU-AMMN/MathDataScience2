# Optimierung unter Nebenbedingungen

Bisher haben wir uns nur mit unrestringierten Optimierungsproblemen beschäftigt und für diese Optimalitätsbedingungen hergeleitet.
Viele reale Aufgabenstellungen erfordern jedoch die Optimierung einer Zielfunktion unter Nebenbedingungen.
Daher wollen wir uns im Folgenden mit solchen Problemen beschäftigen und eine Möglichkeit aufzeigen stationäre Punkte unter Nebenbedingungen zu identifizieren.

Wir beschränken uns hierbei auf Optimierungsprobleme, bei denen die Nebenbedingung eine Gleichheit erfüllen müssen, lassen jedoch keine Ungleichungen zu, d.h., für die Indexmenge $\mathcal{I}$ der Ungleichungen im allgemeinen Optimierungsproblem {eq}`eq:optimierungsproblem_allgemein` gilt $\mathcal{I} = \emptyset$.
Der Grund für diese Einschränkung ist, dass die zugehörige Theorie der sogenannten _Karush-Kuhn-Tucker (KKT)_ Bedingungen für Optimierungsprobleme mit Ungleichungsnebenbedingungen den Rahmen dieser Vorlesung sprengen würde.
Interessierte Leser*innen seien auf Kapitel 12.3 {cite:p}`nocedal_2006` verwiesen.

Wir beginnen direkt mit der wichtigen geometrischen Beobachtung, dass die Gradienten einer Zielfunktion und der zugehörigen Nebenbedingung in einem Minimierer parallel ausgerichtet sein müssen.

````{prf:theorem} Lagrange-Multiplikatoren
:label: satz:lagrange_multiplikator
Seien $F,c \colon \Omega \rightarrow \R$ zwei stetig partiell differenzierbare Funktionen und sei
\begin{equation*}
M \, \coloneqq \, \lbrace x \in \Omega\colon c(x) = 0 \rbrace \subset \Omega
\end{equation*}
eine Untermannigfaltigkeit (z.B. eine Kurve in $\Omega$), die alle Nullstellen von $c$ enthält.

Zu jeder Lösung $x^*\in M$ des Minimierungsproblems
\begin{equation*}
\min_{x\in \Omega} \, F(x) \qquad \text{ mit } \qquad c(x) \ = \ 0
\end{equation*}
und $\nabla c(x^*) \neq 0$ existiert ein _Lagrange-Multiplikator_ $\lambda^* \in \R$, so dass
\begin{equation*}
\nabla F (x^*) + \lambda^* \nabla c(x^*) \ = \ 0.
\end{equation*}
Das heißt die beiden Gradienten $\nabla F$ und $\nabla c$ sind parallel in $x^* \in \Omega$.
````

````{prf:proof}
Sei $x^* \in M$ eine Lösung des Minimierungsproblems mit Nebenbedingung.
Wir sehen zunächst ein, dass der Gradient $\nabla c(x^*)$ senkrecht zu allen Tangentialvektoren der Untermannigfaltigkeit $M$ steht, da sich $c$ entlang aller Tangentialrichtungen von $M$ nicht ändert.
Wir schreiben nun den Gradienten der Zielfunktion $\nabla F$ mittels orthogonaler Projektion (vgl. Kapitel {prf:ref}`s:orthonormalisierung`) als eindeutige Summe zweier Vektoren $v_\perp \in \R^n$ und $v_\parallel \in \R^n$, die jeweils orthogonal und parallel zu $\nabla c$ sind mit
\begin{equation*}
\nabla F(x^*) \ = \ v_\perp + v_\parallel.
\end{equation*}

Wir führen nun den Beweis über einen Widerspruch.
Nehmen wir an, dass $\nabla F$ und $\nabla c$ nicht parallel sind, dann folgt, dass $v_\perp \neq 0$ ist.
Betrachten wir nun die Richtungsableitung von $F(x^*)$ in Richtung des Vektors $-v_\perp \in \R^n$, dann gilt
\begin{equation*}
\begin{split}
D_{-v_\perp} F(x^*) \ &= \ \langle \nabla F(x^*), -v_\perp \rangle \ = \ -\langle v_\perp + v_\parallel, v_\perp \rangle \\
&= \ -\langle v_\perp,  v_\perp \rangle - \underbrace{\langle v_\parallel, v_\perp \rangle}_{=0} \ = \ -\langle v_\perp,  v_\perp \rangle \ < \ 0.
\end{split}
\end{equation*}
Das bedeutet, dass wir den Funktionswert der Zielfunktion $F$ noch weiter verkleinern können, indem wir entlang der Untermannigfaltigkeit $M$ in Richtung $-v_\perp \in \R^n$ gehen.
Dies ist jedoch ein Widerspruch zur Optimalität des Punkts $x^* \in M$.
Also müssen $\nabla F$ und $\nabla c$ parallel sein und es gilt:
\begin{equation*}
\nabla F(x^*) \ = \ -\lambda \cdot \nabla c(x^*).
\end{equation*}
Der Lagrange-Multiplikator $\lambda \in \R$ taucht in der Formel auf, da die Gradienten parallel aber nicht gleich lang sein müssen.
````

Die folgenden Bemerkungen erklären wie aus Satz {prf:ref}`satz:lagrange_multiplikator` das sogenannte _Verfahren der Lagrange-Multiplikatoren_ gewonnen werden kann, welches beispielsweise in der Physik bei Anwendungen der klassischen Mechanik eine Schlüsselrolle spielt.

````{prf:remark}
Wir wollen folgende Beobachtungen festhalten.
\begin{enumerate}
\item Die notwendige Bedingung, dass die Gradienten der Zielfunktion $F$ und der Nebenbedingung $c$ in einem Minimierer $x^* \in M$ parallel ausgerichtet sein müssen, d.h.,
\begin{equation*}
\nabla F (x^*) + \lambda^* \nabla c(x^*) \ = \ 0
\end{equation*}
lässt sich für das Verfahren der Lagrange-Multiplikatoren ausnutzen.
Hierzu definieren wir zunächst eine neue Funktion $\Lambda \colon \Omega \times \R \rightarrow \R$, genannt _Lagrange-Funktion_, die eine zusätzliche Variable $\lambda \in \R$ für die Nebenbedingung besitzt, als
\begin{equation*}
\Lambda(x, \lambda) \ \coloneqq \ F(x) + \lambda \cdot c(x).
\end{equation*}
Betrachtet man nämlich nun stationäre Punkte $(x^*, \lambda^*) \in \Omega \times \R$ von $\Lambda$, d.h.,
\begin{equation*}
\nabla_x \Lambda(x^*, \lambda^*) \, = \, \nabla F (x^*) + \lambda^* \nabla c(x^*) \, \overset{!}{=} \, 0, \qquad \nabla_\lambda \Lambda(x^*, \lambda*) \, = \, c(x^*) \, \overset{!}{=} \, 0,
\end{equation*}
so erfüllen diese Punkte automatisch die notwendigen Kriterien für einen Minimierer des ursprünglichen Optimierungsproblems unter Nebenbedingungen.
\item Das oben beschriebene Verfahren der Lagrange-Multiplikatoren lässt sich auch auf Optimierungsprobleme mit mehreren Nebenbedingungen $c_i \colon \Omega \rightarrow \R$ für $1 \leq i \leq m$ verallgemeinern.
Hierzu wird die Lagrange-Funktion als eine Linearkombination der Zielfunktion und den $m\in\N$ Nebenbedingungen geschrieben als
\begin{equation*}
\Lambda(x, \lambda) \ = \ F(x) + \sum_{i=1}^m \lambda_i c_i(x).
\end{equation*}
Zur Bestimmung stationärer Punkte geht man nun analog zum Fall mit nur einer Nebenbedingung vor.
\end{enumerate}
````

````{prf:example}
Wir wollen im Folgenden eine Zielfunktion $F \colon \R^2 \rightarrow \R$ mit
\begin{equation*}
F(x,y) \ \coloneqq \ x + y
\end{equation*}
minimieren unter der Nebenbedingung, dass der Lösungsvektor $x^* = (x,y)^T \in \R^2$ normiert sein soll, d.h., $x^2 + y^2 = 1$.
Dies führt also zu einem Optimierungsproblem mit Nebenbedingung der folgenden Gestalt:
\begin{equation}
:label: eq:lagrange_bsp
\min_{(x,y)\in \R^2} \, F(x,y) \, = \,  x+y \qquad \text{ mit } \qquad c(x,y) \, = \, x^2+y^2 - 1 \, = \, 0.
\end{equation}
Wir identifizieren zunächst Punkte in denen der Gradient von $c(x,y)$ verschwindet, d.h.,
\begin{equation*}
\nabla c(x,y) \ = \ (2x,2y)^T \ \overset{!}{=} \ 0.
\end{equation*}
Dies kann nur im Ursprung $(0,0)^T$ passieren.
Da dieser Punkt nicht die Nebenbedingung erfüllt, müssen wir ihn also bei den folgenden Berechnungen nicht explizit beachten.

Um das Verfahren der Lagrange-Multiplikatoren anwenden zu können, stellen wir zunächst die Lagrange-Funktion auf:
\begin{equation*}
\Lambda(x,y,\lambda) \ \coloneqq \ F(x,y) + \lambda \cdot c(x,y) \ = \ x+y + \lambda \cdot (x^2+y^2 - 1).
\end{equation*}
Nach dem Satz {prf:ref}`satz:lagrange_multiplikator` müssen wir für potentielle Lösungen des Optimierungsproblems {eq}`eq:lagrange_bsp` nur Extremstellen der Lagrange-Funktion berechnen, d.h., wir betrachten stationäre Punkte von $\Lambda$ durch
\begin{equation*}
\nabla \Lambda(x,y,\lambda) \ = \ 
\begin{pmatrix}
\partial_x F(x,y) + \lambda \partial_x c(x,y)\\
\partial_y F(x,y) + \lambda \partial_y c(x,y)\\
c(x,y)
\end{pmatrix} 
\ = \
\begin{pmatrix}
1 + \lambda \cdot 2x\\
1 + \lambda \cdot 2y\\
x^2 + y^2 - 1
\end{pmatrix} 
\ \overset{!}{=} \ 
\begin{pmatrix}
0 \\
0 \\
0
\end{pmatrix}
\in \R^3.
\end{equation*}
Obwohl es sich nicht um lineares Gleichungssystem handelt können wir dennoch eine Lösung für die drei Gleichungen herleiten.
Wenn wir annehmen, dass $\lambda \neq 0$ gilt, so können wir die ersten beiden Gleichungen jeweils nach $x$ und $y$ umstellen und erhalten so, dass
\begin{equation*}
x \ = \ - \frac{1}{2\lambda} \ = \ y.
\end{equation*}
Setzen wir diese Identitäten in die dritte Gleichung können wir für den Lagrange-Multiplikator folgende Bedingung herleiten
\begin{equation*}
x^2 + y^2 - 1 \ = \ \frac{1}{4\lambda^2} + \frac{1}{4\lambda^2} - 1 \ = \ \frac{1}{2\lambda^2} - 1 \ = \ 0 \quad \Leftrightarrow \quad 2 \lambda^2 \ = \ 1.
\end{equation*}
Wir erhalten für $\lambda$ also die beiden möglichen Lösungen
\begin{equation*}
\lambda_1 \ = \ \frac{1}{\sqrt{2}}, \quad \lambda_2 \ = \ -\frac{1}{\sqrt{2}}.
\end{equation*}
Setzen wir diese beiden Lagrange-Multiplikatoren wieder in die beiden ersten Optimalitätsbedingungen ein erhalten wir als stationäre Punkte der Lagrange-Funktion:
\begin{equation*}
x^*_1 \ = \ (\frac{\sqrt{2}}{2}, \frac{\sqrt{2}}{2})^T, \quad x^*_2 \ = \ (-\frac{\sqrt{2}}{2}, -\frac{\sqrt{2}}{2})^T.
\end{equation*}
Durch Einsetzen der Punkte in die Zielfunktion $F$ sehen wir, dass es sich bei $x_1^*$ um ein Maximum des Optimierungsproblems handelt und bei $x_2^*$ um ein Minimum, da
\begin{equation*}
F(x_1^*) \ = \ \frac{\sqrt{2}}{2} + \frac{\sqrt{2}}{2} \ = \ \sqrt{2}, \qquad F(x_2^*) \ = \ -\frac{\sqrt{2}}{2} -\frac{\sqrt{2}}{2} \ = \ -\sqrt{2}.
\end{equation*}
````
