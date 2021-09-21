# Substitutionsregel

Aus der Kettenregel in Satz \ref{satz:produktregel} können wir ein wichtiges Werkzeug für die Integralrechnung ableiten, die sogenannte \emph{Substitutionsregel}.
Die Idee ist es eine neue Integrationsvariable so geschickt einzuführen, dass ein Teil des Integranden ersetzt wird um das Integral zu vereinfachen oder auf eine bekannte Form zurückzuführen.
\begin{satz}[Substitutionsregel]\label{satz:substitutionsregel}
  Sei $I \subset \R$ eine Teilmenge und $[a,b] \subset \R$ ein Intervall.
  Sei außerdem $f\colon I\to \R$ eine integrierbare Funktion und $g\colon [a,b] \to I$ eine stetig differenzierbare Funktion.
  Dann gilt die folgende Substitutionsregel für die Integralrechnung:
  \begin{equation}\label{eq:substitutionsregel}
    \int_a^b f(g(x))\cdot g'(x)\,\mathrm{d}x \ = \ \int_{g(a)}^{g(b)} f(y)\, \mathrm{d}y.
  \end{equation}
  \begin{proof}
   Sei $F$ eine Stammfunktion von $f$.
    Durch die Kettenregel für Differentiation in Satz \ref{satz:produktregel} wissen wir, dass 
    \begin{equation*}
    (F\circ g)^\prime(x) \ = \ F'(g(x)) \cdot g'(x) \ = \ f(g(x))\cdot g'(x).
    \end{equation*}
    Damit können wir schreiben
    \begin{equation*}
      \int_a^b f(g(x)) \cdot g'(x)\,\mathrm{d}x \ = \ \int_a^b (F\circ g)'(x)\, \mathrm{d}x \ = \ (F\circ g)\,\Big\vert_a^b \ = \ F \, \Big\vert_{g(a)}^{g(b)} \ = \ \int_{g(a)}^{g(b)} f(y)\, \mathrm{d}y.
    \end{equation*}
  \end{proof}
\end{satz}

\begin{remark}\label{bem:substitution_einfach}
Die Substitutionsregel für die Integralrechnung in Satz \ref{satz:substitutionsregel} ist besonders dann einfach, wenn die Ableitung der inneren Funktion $g(x)$ eine Konstante ist, d.h., $g'(x) \equiv c \neq 0$.
Wegen der Linearität des Integrals kann man diese dann Konstante herausziehen und vor die rechte Seite von \eqref{eq:substitutionsregel} schreiben und es ergibt sich damit folgender Zusammenhang:
\begin{equation*}
  \int_a^b f(g(x)) \,\mathrm{d}x \ = \ \frac{1}{c} \int_{g(a)}^{g(b)} f(y)\, \mathrm{d}y.
\end{equation*}
\end{remark}

Das folgende Beispiel soll die Anwendung der Substitutionsregel für verschiedene Funktion mit unterschiedlichen Formen des Integrals illustrieren.
\begin{bsp}
Wir untersuchen drei Beispiele zur Anwendung der Substitutionsregel für die Integralrechnung mit aufsteigendem Schwierigkeitsgrad.
  \begin{enumerate}[i)]
  \item 
  Sei $c\in\R, c\neq 0$, ein Skalierungsfaktor und $d\in\R$ eine Translationskonstante.
  Sei außerdem $f$ eine beliebige integrierbare Funktion auf dem Intervall $[ca+d, cb+d] \subset \R$.
  Wir wollen das folgende Integral vereinfachen:
  \begin{equation*}
   \int_a^b f(cx+d)\,\mathrm{d}x.
  \end{equation*}
  Hierzu können wir eine einfache Substitution vornehmen:
  \begin{equation*}
  	y \ \coloneqq \ g(x) \ = \ cx + d \qquad \Rightarrow \qquad  g'(x) \ \equiv \ c.
  \end{equation*}
  Wir erkennen, dass die einfache Situation aus Bemerkung \ref{bem:substitution_einfach} vorliegt, bei der die innere Ableitung eine Konstante ergibt.
  
  Für die Substitution des Differentials $\mathrm{d}x$ berechnen wir:
  \begin{equation*}
  		c \, = \, g'(x) \, = \, \frac{\mathrm{d}g}{\mathrm{d}x} \, = \, \frac{\mathrm{d}y}{\mathrm{d}x} \qquad \Rightarrow \qquad \d x \, = \, \frac{1}{g'(x)}\,\d y \, = \, \frac{1}{c}\,\d y.
  \end{equation*}
  Damit ergibt sich für das Integral einer Funktion unter einer linearen Transformation die folgende Rechenvorschrift:
  \begin{equation*}
    \int_a^b f(cx+d)\,\mathrm{d}x \ = \ \int_a^b f(g(x))\,\mathrm{d}x \ = \ \int_{g(a)}^{g(b)}f(y)\frac{1}{c}\,\d y \ =  \ \frac{1}{c} \int_{ca+d}^{cb+d}f(y)\, \d y.
  \end{equation*}
  \item Wir nutzen die Substitutionsregel für die Berechnung des Integrals
  \begin{equation*}
  \int_0^2 \cos(x^2 + 1)\cdot x\, \d x.
  \end{equation*}
  Wir setzen $f(x) \coloneqq \cos(x)$ und entscheiden uns für die folgende Substitution:
  \begin{equation*}
  	y \ \coloneqq \ g(x) \ = \ x^2 + 1 \qquad \Rightarrow \qquad  g'(x) \ = \ 2x.
  \end{equation*}
  Die innere Ableitung $g'(x) = 2x$ ist leider keine Konstante, daher können wir sie nicht aus dem Integral herausziehen.
  Dennoch haben wir Glück, dass ein Vielfaches der Ableitung im Integranden vorkommt, nämlich der Faktor $x$, und somit können wir die Substitutionsregel für die Integralrechnung aus Satz \ref{satz:substitutionsregel} anwenden.
  
  Für die Substitution des Differentials $\mathrm{d}x$ berechnen wir:
  \begin{equation*}
  		2x \, = \, g'(x) \, = \, \frac{\mathrm{d}g}{\mathrm{d}x} \, = \, \frac{\mathrm{d}y}{\mathrm{d}x} \qquad \Rightarrow \qquad x\,\d x \, = \, \frac{1}{2}\,\d y.
  \end{equation*}
    Damit ergibt sich für das Integral die folgende Rechenvorschrift:
  \begin{equation*}
  \begin{split}
    \int_0^2 \cos(x^2 + 1)\cdot x\, \d x \ &= \ \int_0^2 f(g(x))\cdot x\, \d x \ = \ \int_{g(0)}^{g(2)} f(y) \cdot \frac{1}{2}\,\d y \ = \ \frac{1}{2} \int_1^5 \cos(y)\, \d y \\
     &= \ \frac{1}{2} \sin(y)\Big\vert_1^5 \ = \ \frac{1}{2} (\sin(5) - \sin(1)) \ \approx \ -0.900.
    \end{split}
  \end{equation*}
  \item 
  Zuletzt wollen wir das verbliebene Integral aus Beispiel \ref{bsp:partielle_integration} mit Hilfe der Substitutionsregel berechnen.
  Wir hatten hierzu bereits hergeleitet, dass gilt
  \begin{equation*}
  \int_0^y\arcsin(x)\,\d x \ = \ y \cdot \arcsin(y) - \int_0^y \frac{x}{\sqrt{1-x^2}}\, \d x.
  \end{equation*}
  Wir setzen $f(x) \coloneqq \frac{1}{\sqrt{1 - x}}$ und entscheiden uns für die folgende Substitution:
  \begin{equation*}
  	z \ \coloneqq \ g(x) \ = \ x^2 \qquad \Rightarrow \qquad  g'(x) \ = \ 2x.
  \end{equation*}
   Die innere Ableitung $g'(x) = 2x$ ist leider keine Konstante, daher können wir sie nicht aus dem Integral herausziehen.
  Dennoch haben wir Glück, dass ein Vielfaches der Ableitung im Integranden vorkommt, nämlich der Faktor $x$, und somit können wir die Substitutionsregel für die Integralrechnung aus Satz \ref{satz:substitutionsregel} anwenden.
  
  Für die Substitution des Differentials $\mathrm{d}x$ berechnen wir:
  \begin{equation*}
  		2x \, = \, g'(x) \, = \, \frac{\mathrm{d}g}{\mathrm{d}x} \, = \, \frac{\mathrm{d}z}{\mathrm{d}x} \qquad \Rightarrow \qquad x\,\d x \, = \, \frac{1}{2}\,\d z.
  \end{equation*}
  Damit ergibt sich für das verbliebene Integral die folgende Rechenvorschrift:
  \begin{equation*}
  \begin{split}
    \int_0^y \frac{x}{\sqrt{1-x^2}}\, \d x \ &= \ \int_0^y f(g(x)) \cdot x\,\d x \ = \ \int_{g(0)}^{g(y)} f(z) \cdot \frac{1}{2}\, \d z \ = \ \frac{1}{2} \int_{0}^{y^2} \frac{1}{\sqrt{1-z}}\, \d z \\
    \ &= \ \frac{1}{2} \cdot (-2\sqrt{1 - z} )\Big\vert^{y^2}_0 \ = \ -(\sqrt{1 - y^2} - \sqrt{1 - 0}) \ = \ 1 - \sqrt{1 - y^2}. 
    \end{split}
  \end{equation*}
  Insgesamt erhalten wir also für das Integral der Arkussinus Funktion in Beispiel \ref{bsp:partielle_integration}:
  \begin{equation*}
  \int_0^y\arcsin(x)\,\d x \ = \ y \cdot \arcsin(y) - 1 + \sqrt{1 - y^2}.
  \end{equation*}
  \end{enumerate}
\end{bsp}
