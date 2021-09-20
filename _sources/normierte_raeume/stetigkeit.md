# Stetigkeit

Aus \cite[Kapitel 5]{burger_2020} sind Sie bereits mit den verschiedenen Stetigkeitsbegriffen auf metrischen Räumen vertraut.
Im Fall von normierten Vektorräumen lassen sich diese Konzepte durch Verwendung der Norm für den Abstandsbegriff analog definieren.
\begin{definition}[Stetigkeit]
Wir wollen im Folgenden die wichtigsten Definitionen für Stetigkeit wiederholen.
Hierbei betrachten wir eine Funktion $ f\colon X \rightarrow Y $ zwischen zwei normierten Vektorräumen $(X, ||\cdot||_X)$ und $(Y, ||\cdot||_Y)$.
\begin{enumerate}
\item Die Funktion $f$  ist genau dann \emph{stetig} in einem Punkt $x_0 \in X$, wenn es für alle $ \varepsilon > 0 $ ein $ \delta > 0 $ gibt, so dass  für alle Punkte $x \in X$ mit
\begin{equation*}
||x - x_0||_X \: < \: \delta
\end{equation*}
für den Abstand der Funktionswerte gilt
\begin{equation*}
||f(x) - f(x_0)||_Y \: < \: \epsilon.
\end{equation*}
\item Die Funktion $f$ ist genau dann \emph{gleichmäßig stetig}, wenn es für alle $\varepsilon > 0$ ein 
$ \delta > 0 $ so gibt, dass für alle Punkte $x, y \in X$ mit
\begin{equation*}
\norm[X]{x-y} \: < \: \delta
\end{equation*}
für den Abstand der Funktionswerte gilt
\begin{equation*}
\norm[Y]{f(x)-f(y)} \: < \: \varepsilon.
\end{equation*}
\item Die Funktion $f$ ist genau dann \emph{Hölder-stetig} mit Exponent $ 0 < \alpha \leq 1 $, wenn 
für alle $ x, y \in X $ gilt:
\begin{equation*}
\norm[Y]{f(x) - f(y)} \: \leq \: L \cdot \norm[X]{x-y}^\alpha
\end{equation*}
für eine nicht-negative Konstante $L \in \R^+_0$.

Im Spezialfall $\alpha = 1$ nennen wir $f$ auch \emph{Lipschitz-stetig}.
Gilt sogar $0 \leq L < 1$, so nennen wir die Funktion $f$ eine Kontraktion.
\end{enumerate}
\end{definition}

Natürlich sind diese Stetigkeitsbegriffe unterschiedlich stark, wie folgende Bemerkung feststellt.
\begin{comment}
Für eine Funktion $f \colon X \rightarrow Y$ zwischen normierten Vektorräumen $X$ und $Y$ gelten folgende Implikationen:
\begin{equation*}
f \text{ ist Hölder-stetig } \ \Rightarrow \ f \text{ ist gleichmäßig stetig } \ \Rightarrow \ f \text{ ist stetig }.
\end{equation*}
\end{comment}

Folgende Beispiele zeigen den Unterschied zwischen den Stetigkeitsbegriffen.
\begin{bsp}
Die Wurzel-Funktion 
\begin{equation*}
\sqrt{\cdot} \: \colon \R_0^+ \ \rightarrow \ \R_0^+
\end{equation*}
ist stetig.
Sie ist jedoch nicht Lipschitz-stetig in $x=0$. 
\end{bsp}
\begin{proof}
In der Hausaufgabe zu zeigen.
\end{proof}

\begin{bsp}
Die Betragsfunktion
\begin{equation*}
|\cdot| \: \colon \R \ \rightarrow \ \R_0^+
\end{equation*}
Lipschitz-stetig mit Lipschitz Konstante $L = 1$.
\end{bsp}

Eine besonders interessante Klasse von stetigen Funktionen sind sogenannte \emph{Homöomorphismen}.
Diese Funktionen erlauben es zu untersuchen wann Teilmengen (topologischer) Vektorräume ineinander überführt werden können, z.B. durch Dehnen, Stauchen, Drehen oder Verzerren der Mengen.
Die folgende Definition charakterisiert Homöomorphismen genauer
\begin{definition}[Homöomorphismus]
Seien $X$ und $Y$ zwei normierte Vektorräume.
Wir nennen eine Funktion $f \colon X \rightarrow Y$ einen \emph{Homöomorphismus}, falls folgende Bedingungen erfüllt sind:
\begin{itemize}
\item $f$ ist stetig,
\item $f$ ist bijektiv,
\item die Umkehrfunktion $f^{-1}$ ist ebenfalls stetig.
\end{itemize}
\end{definition}

Der folgende berühmte Satz ist ein wichtiges Hilfsmittel zur Untersuchung von Fixpunktgleichungen, z.B. in der Numerik, und wird uns später bei der Behandlung von gewöhnlichen Differentialgleichungen noch hilfreich sein.
\begin{thm}[Fixpunktsatz von Banach]
Es sei $X$ ein Banachraum und $ F\colon X\rightarrow X $ eine Lipschitz-stetige Funktion mit Lipschitz-Konstante $ L < 1 $, d.h. es gilt
\begin{equation*}
  	 ||F(x) - F(y)|| \ \leq \ L \cdot ||x - y|| \quad \text{ für alle } x, y \in X.
\end{equation*}
Dann existiert ein genau ein Fixpunkt $\bar{x} \in X $, so dass 
\begin{equation*}
F(\bar{x}) \ = \ \bar{x}.
\end{equation*}
\end{thm}
\begin{proof}
Es sei $x_0 \in X$ beliebiger Startwert der Folge $(x_k)_{k\in\N}$, die durch wiederholte Anwendung der Funktion $F$ definiert ist, d.h,
\begin{equation*}
x_k \ \coloneqq \ F(x_{k-1}), \quad k \geq 1.
\end{equation*}
Wir werden im Folgenden zeigen, dass $(x_k)_{k\in\N}$ eine Cauchy-Folge in $X$ ist.
Da $F$ Lipschitz-stetig mit Lipschitz Konstante $L$ ist, gilt offensichtlich für alle $n\in \mathbb{N}$
\begin{equation*}
||x_{n+1} - x_n|| \ = \ ||F(x_n) - F(x_{n-1})|| \ \leq L \cdot || x_n - x_{n-1}||.
\end{equation*}
Damit folgt induktiv aber auch schon, dass
\begin{equation*}
||x_{n+1} - x_n|| \ \leq L^n \cdot || x_1 - x_0||.
\end{equation*}

Seien nun $n,m \in \mathbb{N}$ zwei beliebige Indizes mit $1 \leq n < m$, dann gilt wegen der Dreiecksungleichung der Norm und unter Ausnutzung der geometrischen Reihe:
\begin{equation*}
\begin{split}
||x_m - x_n|| \ &\leq \ \sum_{k=n+1}^m ||x_k - x_{k-1}|| \ \leq \ ||x_1 - x_0|| \cdot \sum_{k=n+1}^m L^{k-1} \\
\ &= \ ||x_1 - x_0|| \cdot L^n \sum_{k=0}^{m-n-1} L^{k} \ \leq \ ||x_1 - x_0|| \cdot L^n \sum_{k=0}^\infty L^{k} \ = \ ||x_1 - x_0|| \cdot \frac{L^n}{1 - L}.
\end{split} 
\end{equation*}
Da $L < 1$ nach Voraussetzung ist folgt, dass $L^n \rightarrow 0$ für $n \rightarrow \infty$ und somit gilt auch
\begin{equation*}
\lim_{n, m \rightarrow \infty} ||x_m - x_n|| \ = \ 0
\end{equation*}
und daraus folgt, dass $(x_k)_{k\in\N}$ eine Cauchy-Folge in $X$ ist.
Da $X$ vollständig ist, muss $(x_k)_{k\in\N}$ nach Definition \ref{def:banachraum} konvergieren gegen einen Grenzwert $\bar{x} \in X$.
Das heißt wir haben gezeigt, dass die Funktion einen Fixpunkt $\bar{x} = F(\bar{x})$ besitzt, da gilt
\begin{equation*}
\lim_{k \rightarrow \infty} F(x_k) \ = \ \lim_{k \rightarrow \infty} x_{k+1} \ = \ \bar{x}.
\end{equation*}

Sei $\hat{x} \in X$ nun ein weiterer Fixpunkt von $F$ mit $F(\hat{x}) = \hat{x}$, dann gilt
\begin{equation*}
||\bar{x} - \hat{x}|| \ = \ ||F(\bar{x}) - F(\hat{x})|| \ \leq \ L \cdot ||\bar{x} - \hat{x}||.
\end{equation*}
Da $L < 1$ ist kann diese Ungleichung nur gelten wenn $||\bar{x} - \hat{x}||  = 0$ ist.
Aus der positiven Definitheit der Norm folgt dann schon, dass $\bar{x} = \hat{x}$ sein muss, d.h., der Fixpunkt ist eindeutig.
\end{proof}

\begin{remark}
Der Banach'sche Fixpunktsatz kann noch allgemeiner für abgeschlossene Untermengen vollständiger metrischer Vektorräume formuliert werden, da man nur einen Abstandsbegriff (also eine Metrik) und die Existenz des Grenzwertes benötigt.
\end{remark}
