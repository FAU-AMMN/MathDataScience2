# Kompaktheit

Ein zentraler Begriff in der mathematischen Topologie ist Kompaktheit einer Menge, die für viele Existenzaussagen essentiell ist. 
Aus \cite[Kapitel 5.1]{burger_2020} kennen Sie bereits kompakte Mengen in metrischen Räumen, so dass die folgende Definition einer Wiederholung darstellt.
\begin{definition}[Kompaktheit]
    Eine Teilmenge $ M \subseteq X $ eines normierten Raumes $ X $ ist kompakt genau dann,
    wenn jede Folge $ (x_n)_{n\in\N} \subseteq M $ eine konvergente Teilfolge enthält,
    deren Grenzwert in $ M $ liegt.
\end{definition}

% vielleicht besser zu Teilfolgen?
In endlichen Dimensionen haben Sie bereits ein wichtiges Resultat für konvergente Teilfolgen kennengelernt. 
Der Satz von Bolzano-Weierstrass, dass abgeschlossene Kugeln in $ \mathbb{K}^n$ mit Körper $\K=\R$ oder $\K=\C$ kompakt sind.
\begin{thm}[Bolzano-Weierstrass]\label{satz:bolzano}
Sei $\K=\R$ oder $\K=\C$ ein Körper und $(x_k)_{k\in\N} \subset \K^n$ eine beschränkte Folge, d.h. es gibt eine Konstante $C \in \R^+$, so dass alle Folgenglieder $x_k, k\in\N,$ in der abgeschlossenen Kugel $B_C(0) \subset \K^n$ liegen, d.h.
\begin{equation*}
\Vert x_k \, \Vert \, \leq \, C.
\end{equation*}
Dann existiert eine konvergente Teilfolge $(x_{k_j})_{j\in\N}$ mit dem Grenzwert $\overline{x} \in X$ und es gilt $\Vert \overline{x} \Vert \leq C$. 
\end{thm}
\begin{proof}
Siehe \cite[Satz 4.19]{burger_2020}
\end{proof}

\begin{comment}
Wir können folgende Beobachtungen zum Satz von Bolzano-Weierstrass \ref{satz:bolzano} festhalten.
\begin{enumerate}
    \item In endlich-dimensionalen Vektorräumen $X$ lässt sich eine noch stärkere Aussage beweisen, die sich auf den Satz von Heine-Borel \cite[Satz 5.18]{burger_2020} zurückführen lässt.
    Anstatt nur einer hinreichenden Bedingung, kann man aussagen, dass eine Teilmenge $M \subset X$ genau dann kompakt ist, wenn Sie beschränkt and abgeschlossen ist.
    \item Der Satz gilt nicht mehr, wenn der betrachtete normierte Raum unendlich-dimensional ist, beispielsweise in Funktionen- bzw. Folgenräumen wie $C([a,b]; \R) $ oder 
\begin{equation*}
\ell^2(\R) \ = \ \{ (x_n)_{n\in\N} : x_n \in \R, \; \sum_{n=1}^\infty |x_n|^2 < \infty \}.
\end{equation*}
Betrachten wir beispielsweise die Folge $(x_n)_{n\in\N} \subset \ell^2(R)$ der unendlich-dimensionalen Einheitsvektoren $e_n \in \ell^2(\R)$ mit 
\begin{equation*}
x_n\ = \ e_n \ \coloneqq \ (0, \ldots, 0, 1, 0, \ldots), \quad n \in \N,
\end{equation*}
d.h., das Folgenglied $x_n$ besitzt eine Eins an der $n$-ten Stelle und sonst nur Nullen.
\end{enumerate}
Es wird klar, dass jedes Folgenglied auf der Einheitskugel des Vektorraums $\ell^2(\R)$ liegt, da offensichtlich gilt $||x_n|| = 1$ für alle $n \in \N$.
Das heißt, dass die Folge $(x_n)_{n\in\N}$ beschränkt ist und in der abgeschlossenen Einheitskugel liegt.
Dennoch besitzt die Folge keine konvergente Teilfolge, da 
\begin{equation*}
||x_m - x_n|| \ = \ ||e_m - e_n|| \ = \ \sqrt{2}, \quad \text{ für alle } m,n \in \N, m \neq n,
\end{equation*}
d.h., der Abstand eines beliebigen Folgeglieds zu allen anderen Folgegliedern ist konstant $\sqrt{2}$.
Somit kann keine konvergente Teilfolge von $(x_n)_{n\in\N}$ existieren und damit ist die Einheitskugel in $\ell^2(\R)$ nicht kompakt.
\end{comment}

Wir können über den Begriff der Kompaktheit sogar erkennen, ob ein Vektorraum endlich erzeugt ist. 
Als Vorbereitung dieser Beobachtung benötigen wir jedoch zuerst das folgende Hilfslemma.
Die Motivation für dieses Lemma ist, dass wir den Begriff eines senkrechten Vektors auf einen Unterraum aus Kapitel \ref{s:orthonormalisierung} nicht in beliebigen normierten Vektorräumen anwenden können (da ggfs. kein Skalarprodukt existiert).
Dennoch können wir nach dem folgenden Lemma Einheitsvektoren finden, die außerhalb dieses Unterraums liegen und einen positiven Abstand zu diesem besitzen.
\begin{lemma}[Lemma von Riesz]
    \label{lem:lemma von Riesz}
    Es sei $X$ ein normierter Vektorraum und $ U \subsetneq X $ ein abgeschlossener, echter Unterraum von $X$. 
    Sei außerdem ein $\delta \in \R$ mit $0 < \delta < 1$ gegeben.
    Dann existiert ein Element $y \in X$ der Einheitskugel mit $ \norm[X]{y} = 1 $, so dass 
    \begin{equation*}
    d(y, U) \ \coloneqq \ \inf_{u\in U}\norm[X]{y-u} \ \geq \ \delta.
    \end{equation*}
\end{lemma}
\begin{proof}
    Es sei $ \delta \in (0,1)$ beliebig vorgegeben.
    Wir wählen ein beliebiges Element $z \in X \setminus U$ aus dem Komplement von $U$ und erkennen, dass der Abstand $d(z,U)$ von $z$ zu $U$ positiv ist.
    Da wir den Unterraum $U \subsetneq X$ als abgeschlossen angenommen haben, existiert ein Element $u_0 \in U $ für das gilt
    \begin{equation*}
    d(z,U) \ \coloneqq \ \inf_{u\in U}\norm[X]{z-u} \ \leq \ \norm[X]{z-u_0} \ \leq \  \frac{d(z,U)}{\delta}.
    \end{equation*}
    Und damit können wir folgern, dass
    \begin{equation}\label{eq:riesz_lemma}
    \frac{\delta}{d(z,U)} \ \leq \ \frac{1}{\norm[X]{z-u_0}}.
    \end{equation}
    Wählen wir nun den Einheitsvektor 
    \begin{equation*}
    y \ \coloneqq \ \frac{z-u_0\phantom{X}}{\norm[X]{z-u_0}},
    \end{equation*}
    so ist offensichtlich $||y||_X = 1$.
    
    Für ein beliebiges Element $v \in U $ können wir nun nachrechnen, dass gilt
    \begin{equation*}
    	\norm[X]{y - v} \ = \ \left\Vert
          	\frac{z-u_0}{\norm[X]{z-u_0}}
            -
            v \cdot \frac{\norm[X]{z-u_0}}{\norm[X]{z-u_0}}
        \right\Vert_X
        \ = \ 
        \frac{1}{\norm[X]{z-u_0}}
        \left\Vert
            z
            -u_0
            -v \cdot \norm[X]{z-u_0}
        \right\Vert_X.
    \end{equation*}
    Da der Vektor $(u_0 - v\cdot \norm[X]{z-u_0}) \in U $ ist, können wir folgende Abschätzung treffen
    \begin{equation*}
    \begin{split}
        \frac{1}{\norm[X]{z-u_0}}
        \left\Vert
            z
            -u_0
            -v \cdot \norm[X]{z-u_0}
        \right\Vert_X
    	&\ \geq \
        \frac{1}{\norm[X]{z-u_0}}
        \ \inf_{u\in U}\norm[X]{z-u}\\
        \ &\overset{\eqref{eq:riesz_lemma}}{\geq} \
        \frac{\delta}{d(z,U)}d(z,U)
        \ = \ \delta.
        \end{split}
    \end{equation*}
\end{proof}

Mit Hilfe des obigen Lemmas können wir den folgenden interessanten Kompaktheitssatz beweisen, der es uns erlaubt einen endlich-dimensionalen Vektorraum an der Kompaktheit seiner Einheitskugel zu erkennen.
\begin{thm}[Kompaktheitssatz von Riesz]\label{satz:kompaktheit_riesz}
    Ein normierter Vektorraum $X$ ist genau dann endlich-dimensional, wenn seine entsprechende Einheitskugel 
    \begin{equation*}
	B_1(0) \ \coloneqq \ \{ x \in X : ||x||_X \leq 1 \}    
    \end{equation*}
    kompakt ist.
\end{thm}
\begin{proof}
Wir zeigen die beiden Implikationen der Äquivalenzaussage im Folgenden getrennt voneinander.\\[0.3cm]
    \glqq$\Rightarrow$\grqq: Aus der Linearen Algebra wissen wir, dass es für jeden endlich-dimensionalen $ \mathbb{K}$-Vektorraum $X$ ein 
   Homöomorphismus $ \Phi \colon X \rightarrow \mathbb{K}^n$ existiert.
    Es sei nun $ (x_k)_{k\in\N} \subseteq B^X_1(0) $ eine Folge in der Einheitskugel von $X$, so dass
    \begin{equation*}
    (\Phi(x_k))_{k\in\N} \: \subseteq \: B_1^{\mathbb{K}^n}(0).
    \end{equation*}
    Da die Einheitskugel $B_1^{\mathbb{K}^n}(0)$ nach dem Satz \ref{satz:bolzano} von Bolzano-Weierstraß kompakt ist, existiert eine konvergente Teilfolge 
    \begin{equation*}
    (y_k)_{k\in\N} \: \subseteq \: (\Phi(x_k))_{k\in\N}.
    \end{equation*} 
    Weil $\Phi$ als Homöomorphismus insbesondere eine stetige Umkehrabbildung $\Phi^{-1}$ besitzt, ist dann aber  auch 
    \begin{equation*}
    (z_k)_{k\in\N} \ \coloneqq \ (\Phi^{-1}(y_k))_{k\in\N}
    \end{equation*}
    eine konvergente Teilfolge in $B^X_1(0)$.
    Da die Folge $(x_k)_{k\in\N}$ beliebig gewählt war, folgt die Kompaktheit der Einheitskugel $B_1^X(0) \subset X$.\\[0.3cm]
    \glqq$\Leftarrow$\grqq: Um die Rückrichtung der Aussage zu beweisen, führen wir einen Beweis über die Kontraposition.
    Es sei $X$ nicht endlich-dimensional, d.h, unendlich-dimensional.
    Dann existiert eine aufsteigende Folge von echten, abgeschlossenen Unterräumen $(U_k)_{k\in\N} \subsetneq X$ von $X$ mit
    \begin{equation*}
    	U_1 \subsetneq U_2 \subsetneq \ldots \subsetneq U_k \subsetneq \ldots \ , \quad \dim U_k < \dim U_{k+1} \text{ für } k\in\N.
    \end{equation*}
    Für ein beliebiges $ \delta \in (0,1) $ wählen wir mit dem Lemma~\ref{lem:lemma von Riesz} von Riesz einen Einheitsvektor $ y_k \in U_k$,  so dass 
    \begin{equation*} 
    \inf_{u\in U_{k-1}} \norm[X]{y-u} \ \geq \ \delta. 
    \end{equation*}
	Für beliebige Wahl des ersten Einheitsvektors $y_1 \in X$ mit $||y_1|| = 1$ haben wir damit ein Folge $(y_k)_{k\in\N}$ auf der Einheitskugel $B_1^X(0)$ konstruiert, welche beschränkt ist, jedoch keine Cauchy-Folge sein kann, da der Abstand zwischen den Folgegliedern immer mindestens $\delta$ beträgt.
	Daraus folgt, dass die Einheitskugel in einem unendlich-dimensionalen Vektorraum $X$ nicht kompakt sein kann.
\end{proof}

Der Kompaktheitssatz \ref{satz:kompaktheit_riesz} von Riesz besagt zwar, dass Kugeln in unendlich-dimensio\-nalen Banachräumen nicht kompakt sind. 
Dennoch heißt das nicht, dass es in unendlich-dimensio\-nalen Banachräumen keine kompakten Teilmengen gibt.
Um dies zu verdeutlichen beschäftigen uns abschließend mit einem fundamentalen Satz, der Aussagen über die Kompaktheit bestimmter Teilmengen des Funktionenraumes $(C([a,b],\R^n), \norm[\infty]{\cdot})$ der stetigen Funktionen auf einem Intervall $[a,b] \subset \R$ zusammen mit der Supremumsnorm erlaubt.
Dies ist nur ein Spezialfall des Satzes von Arzelà-Ascoli, der in der allgemeinen Formulierung abstraktere Räume untersucht.
\begin{thm}[Arzelà-Ascoli]
	Sei $[a,b] \subset \R$ ein Intervall und es sei $(f_n)_{n\in\N} $ eine Folge von Funktionen aus $ C([a,b], \R) $, welche punktweise beschränkt und gleichgradig stetig ist, d.\,h.
    \begin{enumerate}[(i)]
        \item \label{it:arzela:pktw beschr}
        $ \forall x \in [a,b]\: \exists K \in \R^+ \colon \sup_{n\in\N} |f_n(x)| \leq K$,
        \item \label{it:arzela:glgr stet}
        $ \forall \varepsilon > 0\, \exists \delta > 0\, \forall n \in \N \
        \forall x, y \in [a,b] \colon (|x-y| < \delta \Rightarrow |f_n(x)-f_n(y)| < \varepsilon) $.
    \end{enumerate}
    Dann besitzt die Folge $(f_n)_{n\in\N}$ eine gleichmäßig konvergente Teilfolge.
\end{thm}
\begin{proof}
  Der Beweis dieses Satzes beruht auf dem \emph{Cantorschen Diagonalverfahren}, das rekursiv Teilfolgen konstruiert die partiell konvergieren und dann anschließend aus all diesen Teilfolgen eine überall konvergente Teilfolge zu konstruieren. 
    Wir betrachten hierfür zunächst die abzählbar unendliche Teilmenge $\Q \cap [a,b]$ des Intervalls $[a,b]$ mit der Abzählung 
    \begin{equation*}
    \Phi \colon \Q\cap[a,b] \rightarrow \N. 
    \end{equation*}
    Für $ x \in \Q\cap [a,b]$ mit $ \Phi(x) = i $ schreiben wir $x_i$.
    Weil alle Folgeglieder $(f_n(x_1))_{n\in\N} $ beschränkt sind nach Voraussetzung, existiert eine konvergente Teilfolge $(f^1_n(x_1))_{n\in\N}$ von $(f_n(x_1))_{n\in\N}$ nach dem Satz \ref{satz:bolzano} von Bolzano-Weierstraß.
    Aus dieser konvergenten Teilfolge können wir wiederum eine Teilfolge $(f^2_n(x_2))_{n\in\N} $ mit der gleichen Argumentation bestimmen.
    Dies können wir sukzessive weiterführen für alle Punkte $(x_n)_{n\in\N} \subset [a,b]$.

    Wir definieren nun eine spezielle Funktionenfolge $(g_n)_{n\in\N} \subset (f_n)_{n\in\N}$ mit
    \begin{equation*}
    \begin{split}
    g_n \colon [a,b] &\rightarrow \R,\\
     x &\mapsto f^n_n(x)
     \end{split}
    \end{equation*}
    und beweisen, dass diese Folge gleichmäßig konvergiert in $C([a,b]; \R)$.
    Hiebei reicht es zu zeigen, dass $(g_n)_{n\in\N}$ eine Cauchy-Folge ist, da wir aus Beispiel \ref{bsp:vollständigkeit} wissen, dass $C([a,b]; \R)$ vollständig bezüglich der Supemumsnorm ist.
    
    Sei nun $ \epsilon > 0 $ beliebig gewählt. 
    Nach Voraussetzung existiert nun ein entsprechendes $ \delta > 0 $ so dass für alle $x, y \in [a,b]$ folgt, dass $|f_n(x) - f_n(y)| < \epsilon$ falls $|x - y| < \delta$ gilt.
    Wir partitionieren das Intervall $[a,b]$ in kleine Teilintervalle $I_j, j=1,\ldots,m$ mit $\operatorname{diam}(I_j) < \delta$, so dass
    \begin{equation*}
    [a,b] \ = \ \biguplus_{j=1}^m I_j.
    \end{equation*}
 Dann wählen wir Punkte aus jedem Teilintervall mit
 \begin{equation*}
 x_1 \in I_1\cap\Q, \quad x_2 \in I_2\cap\Q, \ \dots, \quad x_m \in I_m\cap\Q.
 \end{equation*}
    Für einen beliebigen Index $j \in \{1,\dots,m\} $ seien $ k(j) > \ell(j) $ so groß, dass die Teilfolge $ (f^\ell_n(x_j))_{n\in\N}$ punktweise konvergiert. 
    Als Teilfolge jener Folge konvergiert auch $ (f^k_n(x_i))_{n\in\N} $ gegen den gleichen Grenzwert.
    Wir finden daher $ \ell(j)$ so groß, dass 
    \begin{equation}
        \label{equ:arzela:erste abschaetzung}
        |g_k(x_i) - g_\ell(x_i)| \  = \ |f^k_k(x_i)-f^\ell_\ell(x_i)| \ < \ \frac{\varepsilon}{3}.
    \end{equation}
    Nehmen wir nun einen globalen Index über alle Teilintervalle mit $ \ell > \max\{\ell(1),\dots,\ell(m)\} $, so gilt die obige Abschätzung für alle $ x_i $, $ i \in \{1,\dots,m\} $.
    
    Es sei nun $x \in [a,b]$ ein beliebiger Punkt. 
    Dann existiert ein Index $j \in \{1,\dots,m\}$, so dass der Punkt $x$ im Teilintervall $I_j$ liegt.
    Für ein $k > \ell > \max\{\ell(1),\dots,\ell(m)\}$ gilt nun mit Abschätzung \eqref{equ:arzela:erste abschaetzung} und wegen der geradlinigen Stetigkeit der Folge:
    \begin{align*}
        |g_k(x) - g_\ell(x)|
        \ \leq \ |g_k(x) - g_k(x_j)| + |g_k(x_j) - g_\ell(x_j)| + |g_\ell(x_j) - g_\ell(x)|
        \ \leq \
        \varepsilon
    \end{align*}
    Da dies für beliebige Punkte $x \in [a,b]$ gilt ist $(g_k)_{k\in\N}$ eine Cauchy-Folge bezüglich der Supremumsnorm und konvergiert somit gleichmäßig in $C([a,b]; \R)$.
\end{proof}
