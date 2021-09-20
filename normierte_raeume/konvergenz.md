# Konvergenz von Folgen

Im Folgenden wollen wir uns noch einmal mit allgemeinen Konvergenzbegriffen in normierten Vektorräumen beschäftigen, welche sich direkt aus der Konvergenz in metrischen Räumen ableiten lassen indem man den in einer Metrik gemessenen Abstand durch die Norm der Differenz von Punkten ersetzt.
Konvergente Folgen und Cauchy-Folgen können also in normierten Räumen analog wie in metrischen Räumen definiert werden.
Sie zeichnen sich dadurch aus, dass der Abstand der Punkte gemessen in der Norm eine Nullfolge ist.
Anders ausgedrückt, nennen wir eine Folge konvergent, wenn alle Folgeglieder ab einem bestimmten Index in einer $\epsilon$-Umgebung um den Grenzwert liegen.
\begin{definition}[Konvergente Folgen und Cauchy-Folgen]
Sei $X$ ein normierter Raum und $(x_n)_{n\in\N}$ eine Folge in $X$. 
\begin{enumerate}
\item Die Folge $(x_n)_{n\in\N}$ heißt \emph{konvergent} mit Grenzwert $\overline{x} \in X$, falls folgende Bedingung erfüllt ist
\begin{equation*}
\forall \epsilon  > 0 \ \exists n_0 \in \N ~\forall n \geq n_0: ||x_n - \overline{x}|| < \epsilon.
\end{equation*}
\item Die Folge $(x_n)_{n\in\N}$ heißt \emph{Cauchy-Folge} mit Grenzwert $\overline{x} \in X$, falls folgende Bedingung erfüllt ist
\begin{equation*}
\forall \epsilon  >0 ~\exists n_0 \in \N ~\forall\, m,n \geq n_0: ||x_n - x_m|| < \epsilon.
\end{equation*}
\end{enumerate}
\end{definition}


Genau wie im Fall von metrischen Räumen können wir auch leicht folgendes Resultat beweisen: 
\begin{thm}
Jede konvergente Folge in einem normierten Vektorraum ist eine Cauchy-Folge. 
\end{thm}
\begin{proof}
\cite[Satz 2.30 \& Satz 4.11]{burger_2020}
\end{proof}


\begin{definition}[Vollständigkeit und Banachraum]\label{def:banachraum}
Ein normierter Vektorraum $X$ heißt \emph{vollständig}, wenn jede Cauchy-Folge in $X$ konvergiert.
Ein vollständiger, normierter Vektorraum $X$ wird \emph{Banachraum} genannt.
\end{definition} 

\begin{example}\label{bsp:vollständigkeit}
Wir untersuchen die folgenden Beispiele mit Blick auf Vollständigkeit.
\begin{enumerate}[i)]
\item Der normierte Vektorraum $(\mathbb{R}^n, ||\cdot||_2)$ mit der Euklidischen Norm ist vollständig wie bereits in \cite[Satz 4.13]{burger_2020} bewiesen wurde.
\item
    Die Menge $C(\Omega; \R^n)$ der stetigen Funktionen auf einer kompakten Menge $ \Omega \subset \R^n $
    mit Werten in $ \R^n $ zusammen mit der Supremumsnorm
    $$
		\norm[\infty]{f} \colonequals \sup_{x\in\Omega}\norm[2]{f(x)}
    $$
    ist ein Banachraum.
\item
    Die Menge der reellwertigen, stetigen Funktionen $C([a,b]; \mathbb{R})$ auf dem abgeschlossenen Intervall $[a,b] \subset \R$ 
    zusammen mit der $L^1$-Norm 
    \begin{equation*}
    ||f||_{L^1([a,b])} \ \coloneqq \ \int_a^b |f(x)|\,\mathrm{d}x
    \end{equation*}
    ist ebenfalls ein Banachraum.
\item Der Vektorraum $\Q$ mit der Betragsfunktion aufgefasst als Norm ist nicht vollständig und somit kein Banachraum.
    Hierzu betrachten wir eine rekursiv definierte Folge
\begin{equation*}
x_{n+1} \ \coloneqq \ \frac{1}{2} \left( x_n + \frac{2}{x_n} \right).
\end{equation*}
Man kann zeigen, dass die Folge $(x_n)_{n\in\N}$ eine Cauchy-Folge ist bei der alle Folgenglieder offensichtlich rational sind.
Anderseits konvergiert die Folge gegen den Grenzwert $\sqrt{2} \not\in \Q$ (siehe \cite[Satz 2.27]{burger_2020}) und ist somit nicht konvergent in $(\Q, |\cdot|)$.
\item Die Menge der reellwertigen, stetig-differenzierbaren Funktionen $C^1(I; \mathbb{R}) $ auf einem offenen Intervall
    $ I \subseteq \R $ bildet zusammen mit der Supremumsnorm $||\cdot||_\infty$ als auch mit der sogenannten \emph{Sobolev-Norm}
    \begin{equation*}
	||f||_{W^{1,\infty}(I)} \ \coloneqq \ \norm[\infty]{f} + \norm[\infty]{f'}
    \end{equation*} 
	 einen normierten Vektorraum.
    Allerdings ist $(C^1(I; \R), ||\cdot||_\infty)$ nicht vollständig, sondern nur $(C^1(I; \R), ||\cdot||_{W^{1,\infty}(I)})$.
    
    Intuitiv kann man sich klar machen, dass hier lediglich die Sobolev-Norm auch die Ableitung der Funktionen $u \in C^1(I; \R)$ berücksichtigt und damit für konvergente Folgen sicherstellt, dass auch die erste Ableitung gleichmäßig konvergiert. 
    Die Supremumsnorm hingegen \glqq beachtet\grqq\ diese gar nicht.
\end{enumerate}
\end{example}

Wir wollen im Folgenden auch den Begriff einer konvergenten Teilfolge nochmals für normierte Vektorräume definieren und charakterisieren.
\begin{definition}[Teilfolge]
Sei $(x_n)_{n\in\N}$ eine Folge in einem normierten Vektorraum $(X, ||\cdot||_X)$ und sei $K: \N \rightarrow \N$ eine streng monoton wachsende Abbildung, d.h. $K(i) > K(j)$ für $i > j$. 
Dann heißt $(x_{K(n)})_{n \in \N}$ Teilfolge von $(x_n)_{n\in\N}$.
Wir werden im Folgenden für Teilfolgen auch kurz $(x_{k_n})_{n \in \N}$ schreiben.
\end{definition} 

Um die Konvergenz von Teilfolgen festzustellen, führt man den Begriff eines Häufungs\-punktes einer Folge ein.
\begin{definition}[Häufungspunkt]
Sei $(X,||\cdot||_X)$ ein normierter Raum. 
Dann nennen wir einen Punkt $y \in X$ \emph{Häufungspunkt} der Folge $(x_n)_{n\in\N} \subset X$, wenn eine Teilfolge $(x_{n_k})_{k\in\N} \subset (x_n)_{n\in\N}$ existiert, die gegen $y$ konvergiert, d.h.
\begin{equation*}
\forall \epsilon  > 0 \ \exists n_0 \in \N ~\forall k \geq n_0: ||x_{n_k} - \overline{x}|| < \epsilon.
\end{equation*}
\end{definition}

Das folgende Beispiel veranschaulicht die Beziehung zwischen Häufungspunkten und konvergenten Teilfolgen.
\begin{example}
Die reelle Folge $(x_n)_{n\in\N} \subset \R$ mit
\begin{equation*}
x_n \ \coloneqq \ (-1)^n + \frac{1}{n+1}
\end{equation*}
besitzt zwei Häufungspunkte $\bar{x}_1 = +1$ und $\bar{x}_2 = -1$.
Das bedeutet, dass die Folge $(x_n)_{n\in\N}$ selbst nicht konvergent ist, jedoch zwei konvergente Teilfolgen besitzt, die sich gerade aus den geraden und ungeraden Folgegliedern bilden.
\end{example} 

