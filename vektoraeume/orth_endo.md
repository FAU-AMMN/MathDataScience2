# Orthogonale und unitäre Endomorphismen

Mit Hilfe des in den vorangegangenen Kapiteln eingeführten Skalarprodukts ist es uns möglich eine besondere Gruppe von Endomorphismen zu untersuchen - die orthogonalen und unitären Endomorphismen.
Wir werden hierbei sehen, dass diese Abbildungen schöne mathematische Eigenschaften haben und insbesondere Längen- und Winkel-erhaltend sind.
Daher sind sie besonders geeignet bei der Lösung von linearen Gleichungssystemen und Eigenwertproblemen.

Orthogonale bzw. unitäre Endomorphismen lassen sich durch ihr Verhalten bezüglich des Standardskalarprodukts charakterisieren, worauf die folgende Definition basiert.
\begin{definition}[Orthogonale und unitäre Endomorphismen]\label{def:orthogonale_endomorphismen}
Sei $V$ ein Euklidischer bzw. unitärer Vektorraum und $F \colon V \rightarrow V$ ein Endomorphismus von $V$.
Dann heißt $F$ \emph{orthogonal} bzw. \emph{unitär}, wenn
\begin{equation*}
\langle F(v), F(w)\rangle \ = \ \langle v, w\rangle\qquad\text{für alle }v,w\in V\,.
\end{equation*}
\end{definition}

Wir können nur mit Hilfe von Definition \ref{def:orthogonale_endomorphismen} bereits viele interessante Eigenschaften für orthogonale bzw. unitäre Endomorphismen ableiten, wie der folgende Satz zeigt.
\begin{satz}\label{satz:orthogonale_endomorphismen}
Sei $V$ ein Euklidischer bzw. unitärer Vektorraum und $F \colon V \rightarrow V$ ein orthogonaler bzw. unitärer Endomorphismus von $V$.
Seien außerdem $v,w \in V$ beliebige Vektoren.
Dann besitzt $F$ folgende Eigenschaften:
\begin{enumerate}[i)]
\item $\Vert F(v)\Vert \ = \ \Vert v\Vert$,
\item $\measuredangle (F(v), F(w) ) \ = \ \measuredangle (v,w)$,
\item $v\perp w \ \Leftrightarrow \ F(v) \perp F(w)$,
\item $F$ ist Isomorphismus und $F^{-1}$ ist auch orthogonal bzw. unitär,
\item Für alle Eigenwerte $\lambda\in\K$ von $F$ gilt $\vert\lambda\vert=1.$
\end{enumerate}
\end{satz}
\begin{proof}
Wir beweisen die verschiedenen Eigenschaften des Endomorphismus $F$ durch Ausnutzen der Definition von orthogonalen bzw. unitären Endomorphismen.
\begin{enumerate}[i)]
\item Sei $v \in V$, dann gilt
\begin{equation*}
|| F(v) || \ = \ \sqrt{ \langle F(v), F(v) \rangle } \ = \ \sqrt{  \langle v, v \rangle } \ = \ ||v||.
\end{equation*}
\item Seien $v,w \in V$, dann können wir unter Ausnutzung von i) zeigen, dass gilt:
\begin{equation*}
\measuredangle (F(v), F(w) )  \ = \ \arccos \frac{\langle F(v), F(w) \rangle }{||F(v)|| \cdot ||F(w)||} \ = \ \arccos \frac{\langle v, w \rangle }{||v|| \cdot ||w||} \ = \ \measuredangle (v, w ).
\end{equation*}
\item Seien $v,w \in V$ mit $v \perp w$, dann ist die Aussage natürlich ein Spezialfall von ii).
Wir können aber auch direkt nachrechnen, dass gilt:
\begin{equation*}
\langle F(v), F(w) \rangle \ = \ \langle v, w \rangle \ = \ 0.
\end{equation*}
\item Wir müssen für die Aussage zeigen, dass $F \colon V \rightarrow V$ injektiv ist und der Kern von $F$ nur die Null enthält, denn dann gilt nach dem Dimensionssatz \cite[Satz 2.2.4]{fischer} schon, dass $\Bild(F) = V$ gelten muss und es sich somit um einen Isomorphismus handelt.
Sei also $v \in \Kern(F)$, dann gilt schon:
\begin{equation*}
\langle v, v \rangle \ = \ \langle F(v), F(v) \rangle \ = \ \langle 0, 0 \rangle \ = \ 0.
\end{equation*}
Wegen der positiven Definitheit des Skalarprodukt muss $v = 0$ gelten und damit haben wir gezeigt, dass $F$ injektiv und somit ein Isomorphismus ist.

Um zu zeigen, dass auch $F^{-1}$ orthogonal bzw. unitär ist betrachten wir für beliebiges $v \in V$ mit $F^{-1}(v) \eqqcolon w$ folgende Gleichung:
\begin{equation*}
\langle F^{-1}(v), F^{-1}(v) \rangle \ = \ \langle w, w \rangle \ = \ \langle F(w), F(w) \rangle \ = \ \langle F \circ F^{-1}(v), F \circ F^{-1}(v) \rangle \ = \ \langle v, v \rangle.
\end{equation*}
Daher ist $F^{-1}$ also auch orthogonal bzw. unitär.
\item Sei $\lambda \in \mathbb{K}$ ein Eigenwert von $F$ mit zugehörigem Eigenvektor $v \in V$, so gilt wegen i):
\begin{equation*}
||v|| \ = \ ||F(v)|| \ = \ ||\lambda v|| \ = \ |\lambda| \cdot ||v||.
\end{equation*}
Diese Gleichung kann nur gelten, wenn $|\lambda| = 1$ ist.
\end{enumerate}
\end{proof}

Wir können einen Endomorphismus $F$ von $V$ schon als orthogonal bzw. unitär erkennen, sobald er Längen-erhaltend ist, wie folgendes Lemma zeigt.
Solche Abbildungen werden \emph{Isometrien} genannt.
Damit gilt auch die Umkehrung von Aussage $i)$ in Satz \ref{satz:orthogonale_endomorphismen}.
\begin{lemma}
Sei $F \colon V \rightarrow V$ ein Endomorphismus mit 
\begin{equation*}
\Vert F(v)\Vert \, = \, \Vert v\Vert \quad \text{ für alle } v\in V.
\end{equation*}
Dann ist $F$ orthogonal bzw. unitär.
\end{lemma}
\begin{proof}
Aus der Invarianz der Norm $||F(v)|| = ||v||$ eines Vektors $v \in V$ folgt auch schon die Invarianz der quadratischen Norm $||v||^2$ von $v$.
Dies ist jedoch gerade die quadratische Form des kanonischen Skalarprodukts in $V$.
Mit Hilfe der Polarisierungsformel in Satz \ref{satz:polarisierung} folgt aus der Invarianz der quadratischen Form schon die Invarianz des Skalarprodukts selbst.
Dies bedeutet nach Definition \ref{def:orthogonale_endomorphismen}, dass $F$ orthogonal bzw. unitär sein muss.
\end{proof}

Nutzt man in $\R^n$ und $\C^n$ mit dem kanonischen Skalarprodukt die darstellende Matrix $A$ eines orthogonalen bzw. unitären Endomorphismus $F$ von $V$, so lässt sich beobachten, dass für alle $x,y \in \mathbb{K}^n$ gilt:
\begin{equation}\label{eq:unitäre_matrix}
\langle x, y \rangle \ = \ \langle Ax, Ay \rangle \ = \ (Ax)^T\overline{Ay} \ = \ x^T(A^T\bar{A})\overline{y} \ = \ x^T(\bar{A}^T A)^T\overline{y}.
\end{equation}

Die Matrix $\bar{A}^T$ in Gleichung \eqref{eq:unitäre_matrix} hat eine besondere Bedeutung wie die folgende Definition zeigt.
\begin{definition}[Adjungierte Matrix]\label{def:adjungierte_matrix}
Sei $A \in \mathbb{C}^{m \times n}$ eine komplexe Matrix mit 
\begin{equation*}
A \ = \
\begin{pmatrix}
a_{11} & \cdots & a_{1n}\\
\vdots & & \vdots \\
a_{m1} & \cdots & a_{mn}
\end{pmatrix},
\end{equation*}
dann definieren wir die \emph{adjungierte Matrix} $A^* \in \mathbb{C}^{n \times m}$, auch \emph{Adjungierte} genannt, als die komplexe Konjugation der transponierten Matrix von $A$, d.h.,
\begin{equation*}
A^* \ \coloneqq \ \bar{A}^T \ = \ \overline{A^T} \ = \ 
\begin{pmatrix}
\bar{a}_{11} & \cdots & \bar{a}_{m1}\\
\vdots & & \vdots \\
\bar{a}_{1n} & \cdots & \bar{a}_{mn}
\end{pmatrix}.
\end{equation*}
Ist $A$ eine reelle Matrix, so ist die Adjungierte lediglich die transponierte Matrix von $A$, d.h., $A^* = A^T$.
\end{definition}

Für die darstellende Matrix eines unitären Endomorphismus muss also nach Gleichung \eqref{eq:unitäre_matrix} gelten, dass $A^* \cdot A = E_n$ gilt, was die folgende Definition motiviert.
\begin{definition}[Orthogonale und unitäre Matrix]
Eine Matrix $A\in\operatorname{GL}(n;\R)$ heißt \emph{orthogonal}, falls gilt
\begin{equation*}
A^{-1} \ = \ A^T.
\end{equation*}
Eine Matrix $A\in\operatorname{GL}(n;\C)$ heißt \emph{unitär}, falls gilt
\begin{equation*}
A^{-1} \ = \ A^*.
\end{equation*}
\end{definition}

Aus der Gleichung $A^* \cdot A = E_n$ können wir folgende interessante Beobachtungen zur Gestalt und Determinante einer unitären Matrix machen.
\begin{lemma}
Sei $A$ eine unitäre Matrix.
Dann bilden sowohl die Spalten als auch die Zeilen von $A$ eine Orthonormalbasis des $\mathbb{K}^n$.
\end{lemma}
\begin{proof}
Da $A$ unitär ist gilt per Definition, dass $A^{-1} = A^*$ gilt. Daraus folgt einerseits
\begin{equation*}
\delta_{i,j} \ = \ E_n \ = \ A\cdot A^{-1} \ = \ A\cdot A^*,
\end{equation*}
also müssen die Zeilen von $A$ eine Orthonormalbasis des $\mathbb{K}^n$ bilden.
Gleichzeitig gilt aber auch
\begin{equation*}
\delta_{i,j} \ = \ E_n \ = \ A^{-1}\cdot A \ = \ A^*\cdot A,
\end{equation*}
also müssen die Spalten von $A$ eine Orthonormalbasis des $\mathbb{K}^n$ bilden.
\end{proof}

\begin{lemma}
Sei $A$ eine unitäre Matrix.
Dann gilt entweder $\det A = 1$ oder $\det A = -1$.
\end{lemma}
\begin{proof}
Für eine komplexe Zahl $z \in \mathbb{C}$ mit $z \coloneqq a + ib$ und $a,b \in \mathbb{R}$ gilt offensichtlich:
\begin{equation*}
z \cdot \bar{z} \ = \ (a + ib) \cdot (a - ib) \ = \ a^2 - aib + aib - i^2 b^2 \ = \ a^2 + b^2 \ = \ |z|^2.
\end{equation*}
Daher können wir für die Determinante von $A$ folgern, dass gilt:
\begin{equation*}
| \det A |^2 \ = \ \det A\cdot\overline{\det A} \ = \ \det A\cdot \det A^*\ = \ \det(A\cdot A^*) \ = \ \det(E_n) \ = \ 1.
\end{equation*}
Damit wissen wir, dass für unitäre Matrizen gilt $\det A = \pm1.$
\end{proof}

Das Vorzeichen der Determinante hat eine wichtige geometrische Bedeutung, denn falls $\det A=+1$ gilt, bleiben Orientierungen unter der Wirkung von $A$ erhalten.
Solch orthogonale Matrizen nennt man daher auch \emph{eigentlich orthogonal} und sie bilden eine abgeschlossene Gruppe, wie folgende Bemerkung feststellt.
\begin{remark}
Die Mengen
\begin{align}
\operatorname{O}(n) \ &:= \ \left\lbrace A\in\operatorname{GL}(n;\R) ~\vert~ A^{-1} = A^T\right\rbrace,\tag{orthogonale Gruppe}\\
\operatorname{SO}(n)\ &:= \ \left\lbrace A\in\operatorname{O}(n) ~\vert~ \det A=1\right\rbrace,\tag{spezielle orthogonale Gruppe}\\
\operatorname{U}(n) \ &:= \ \left\lbrace A\in\operatorname{GL}(n;\C) ~\vert~ A^{-1} = \bar{A}^T\right\rbrace,\tag{unitäre Gruppe}\\
\operatorname{SU}(n) \ &:= \ \left\lbrace A\in\operatorname{U}(n) ~\vert~ \det A=1\right\rbrace,\tag{spezielle unitäre Gruppe}
\end{align}
der \emph{orthogonalen}, \emph{speziellen orthogonalen}, \emph{unitären} und \emph{speziellen unitären} Matrizen sind Untergruppen von $\operatorname{GL}(n;\R)$ bzw. $\operatorname{GL}(n;\C)$.
\end{remark}

Wir diskutieren im Folgenden zwei Beispiele von orthogonalen bzw. unitären Matrizen.
\begin{example}
Sei $A \in \mathbb{K}^{3\times3}$, dann betrachten wir zwei einfache Beispiele.
\begin{enumerate}
\item Die Einheitsmatrix $A = E_3 \in \mathbb{R}^{3\times 3}$ mit
\begin{equation*}
A \ \coloneqq \ 
\begin{pmatrix}
1 & 0 & 0 \\
0 & 1 & 0\\
0 & 0 & 1
\end{pmatrix}
\end{equation*}
ist eine orthogonale Matrix, da offensichtlich gilt $A^T = A = A^{-1}$.
Es gilt sogar $A \in \operatorname{SO}(3)$, da $\det A = +1$ ist.
\item Die Matrix $A \in \mathbb{C}^{3\times 3}$ mit 
\begin{equation*}
A \ \coloneqq \
\begin{pmatrix}
1 & 0 & 0 \\
0 & 0 & -i\\
0 & i & 0
\end{pmatrix}
\end{equation*}
ist eine unitäre Matrix, denn offensichtlich gilt $A^* = A^{-1}$ mit
\begin{equation*}
A \cdot A^* \ = \ 
\begin{pmatrix}
1 & 0 & 0 \\
0 & 0 & -i\\
0 & i & 0
\end{pmatrix}
\cdot 
\begin{pmatrix}
1 & 0 & 0 \\
0 & 0 & \bar{i}\\
0 & -\bar{i} & 0
\end{pmatrix}
 \ = \ 
\begin{pmatrix}
1 & 0 & 0 \\
0 & 0 & -i\\
0 & i & 0
\end{pmatrix}
\cdot 
\begin{pmatrix}
1 & 0 & 0 \\
0 & 0 & -i\\
0 & i & 0
\end{pmatrix}
\ = \ 
\begin{pmatrix}
1 & 0 & 0 \\
0 & 1 & 0\\
0 & 0 & 1
\end{pmatrix}.
\end{equation*}
Es gilt sogar $A \in \operatorname{SU}(3)$, da $\det A = +1$ ist.
\end{enumerate}
\end{example}

Der folgende Satz stellt eine direkte Beziehung zwischen orthogonalen bzw. unitären Endomorphismen und den Eigenschaften ihrer darstellenden Matrizen bezüglich bestimmter Basen fest.
\begin{satz}\label{satz:orthogonale_matrizen}
Sei $V$ ein Euklidischer bzw. unitärer Vektorraum mit einer Orthonormalbasis $B$ und $F$ ein Endomorphismus von $V$. Dann gilt: 
\begin{equation*}
F \text{ ist orthogonal (bzw. unitär)} \ \Leftrightarrow \ M_B(F) \text{ ist orthogonal (bzw. unitär)}\,.
\end{equation*}
\end{satz}
\begin{proof}
Wir zeigen die Aussage für den allgemeineren Fall eines unitären Vektorraums.
Sei $A:= M_B(F)\in \mathbb{K}^{n\times n}$ die darstellende Matrix von $F$ bezüglich der Orthonormalbasis $B$ und für $v,w\in V$ seien $x, y \in \mathbb{K}^n$ die zugehörigen Koordinaten, d.h.
  \begin{equation*}
  v \ = \ \Phi_B(x), \quad w \ = \ \Phi_B(y).
  \end{equation*}
  Da $B$ eine Orthonormalbasis ist gilt offensichtlich
\begin{equation*}
\langle v, w \rangle \ = \ \langle \Phi_B(x), \Phi_B(y) \rangle \ = \ \langle x, y \rangle.
  \end{equation*}
 Der Endomorphismus $F$ ist also genau dann unitär, falls gilt
 \begin{equation*}
 \langle F(v), F(w) \rangle \ = \ \langle Ax, Ay \rangle \ = \ x^TA^T\bar{A}\bar{y} \ = \ x^T \bar{y} \ = \ \langle x, y \rangle \ = \ \langle v, w \rangle.
 \end{equation*}
 Also genau dann wenn $A^T \cdot \bar{A} = I_n$ gilt, was der Fall ist, wenn $A$ unitär ist.
\end{proof}

Wir wollen im folgenden untersuchen wie die Normalform eines orthogonalen bzw. unitären Endomorphismus aussieht.
Hierbei werden wir die mathematischen Werkzeuge aus der Eigenwerttheorie in Kapitel \ref{ch:eigenwerttheorie} einsetzen können.
Hierzu beginnen wir mit der (mathematisch schöneren) \textbf{Normalform von unitären Endomorphismen}, die im folgenden Satz beschrieben ist.
\begin{satz}[Diagonalisierungssatz]\label{satz:endomorphismen_diagonalisierung}
  Jeder unitäre Endomorphismus $F$ eines unitären Vektorraums $V$ besitzt eine Orthonormalbasis aus Eigenvektoren von $F$.
  Insbesondere ist er diagonalisierbar.
\end{satz}
\begin{proof}
  Wir führen den Beweis mittels vollständiger Induktion über $n=\dim V$.\\[0.3cm]
\textbf{Induktionsanfang: $n=1$}\\  
 Da $F$ unitär ist muss gelten 
 \begin{equation*}
 \langle F(v), F(w) \rangle = \langle v, w \rangle, \quad \text{ für alle } v,w \in V.
 \end{equation*}
 Im eindimensionalen Fall, kann dies nur gelten, falls $F(v) = v$ oder $F(v) = -v$ für alle $v \in V$ gilt.
 Dies erfüllt aber schon die Eigenwertgleichung für den Eigenwert $\lambda_1 = 1$ oder $\lambda_1 = -1$.
 Für beide Fälle ist $v_1 = 1$ der zugehörige Eigenvektor und es ist klar, dass $v_1$ eine Orthonormalbasis von $V$ bildet.
 Damit ist $F$ nach Definition \ref{def:diagonalisierbarkeit} diagonalisierbar.
~\\[0.3cm]
\textbf{Induktionsschritt: $n-1 \rightarrow n$}\\
Die Induktionsannahme ist, dass die Aussage bereits für den Fall $n-1$ gezeigt wurde.
Wir betrachten für $n \geq 1$ das charakteristische Polynom $P_F$ von $F$, welches nach dem Fundamentalssatz der Algebra in Linearfaktoren über dem Körper $\mathbb{C}$ zerfällt in
  \begin{equation*}
    P_F(t) \ = \ \pm (t-\lambda_1) \cdot \ldots \cdot
    (t-\lambda_n)\qquad\text{mit}\quad\lambda_1,\ldots,\lambda_n\in\C.
  \end{equation*}
  Zum Eigenwert $\lambda_1 \in \mathbb{C}$ von $F$ wählen wir einen zugehörigen Eigenvektor $v_1$ mit $\Vert v_1\Vert = 1$.
  Wir betrachten das orthogonale Komplement zum Unterraum $\lin(\lbrace v_1 \rbrace)$, d.h.
  \begin{equation*}
    W:=\left\{w\in V \, | \,  v_1 \perp w \right\}\,.
  \end{equation*}
  Wir müssen nun $F(W) = W$ zeigen, d.h., dass $W$ ein $F$-invarianter Unterraum ist.
  Da $F$ nach Satz \ref{satz:orthogonale_endomorphismen} ein Isomorphismus ist, genügt es $F(W)\subset W$ zu beweisen.
  Für alle $w \in W$ folgt aus der Gleichung
  \begin{equation*}
    \lambda_1\langle v_1, F(w)\rangle \ = \ \langle \lambda_1v_1, F(w)\rangle
    \ = \ \langle F(v_1), F(w)\rangle \ = \ \langle v_1, w\rangle \ = \ 0\,,
  \end{equation*}
  dass $\langle F(w), v_1\rangle = 0$, da $\vert \lambda_1\vert = 1$ und damit insbesondere $\lambda_1\neq0$ gilt.
  Das zeigt jedoch schon, dass $F(W) \subset W$ gilt.
  
  Nun betrachten wir den Endomorphismus $G:=F|_W$ von $W$.
  Als Einschränkung von $F$ ist $G$ weiterhin unitär und wegen $\dim W = n-1$ können wir auf $G$ die Induktionsannahme anwenden.
  Danach gibt es eine Orthonormalbasis $(v_2, \ldots, v_n)$ von $W$ bestehend aus Eigenvektoren von $G$ und somit auch von $F$.
  Die um den Eigenvektor $v_1 \in V$ ergänzte Basis $(v_1, v_2, \ldots, v_n)$ ist orthonormal und besteht aus Eigenvektoren von $F$.
\end{proof}

Übertragen auf unitäre Matrizen liefert uns der Diagonalisierungssatz \ref{satz:endomorphismen_diagonalisierung} folgende Ähnlichkeitstransformation.
\begin{cor}\label{cor:unitäre_matrix_diag}
  Zu $A\in\operatorname{U}(n)$ gibt es ein $S\in\operatorname{U}(n)$ mit
  \begin{equation*}
   S \cdot A\cdot S^* \ = \ \left(\begin{array}{rrr}\lambda_1 &&0\\
    &\ddots&\\ 0&&\lambda_n\end{array}\right),
  \end{equation*}
  wobei $\lambda_i\in\C$ mit $\vert\lambda_i\vert = 1$ für $i=1,\ldots,n\,.$
  \begin{proof}
    Als Spalten von $S^* = S^{-1}$ verwendet man eine orthonormale Basis des $\C^n$, die aus Eigenvektoren von $A$ besteht.
  \end{proof}
\end{cor}

Im folgenden Beispiel wollen wir die Diagonalisierbarkeit einer unitären Matrix nach Korollar \ref{cor:unitäre_matrix_diag} prüfen.
\begin{bsp}\label{bsp:drehung_unitär}
  Die Matrix $A \in \mathbb{R}^{2\times 2}$ mit
  \begin{align*}
    A:=\left(\begin{array}{rr}0&-1\\1&0\end{array}\right)
  \end{align*}
  beschreibt eine Drehung um $90^\circ$ im $\R^2$ und ist offensichtlich orthogonal.
  Da das charakteristische Polynom von $A$ die Form $P_A(t) = t^2 + 1$ hat, sind die Eigenwerte $\lambda_1 = i$ und $\lambda_2 = -i$ nicht reell.
  Die zugehörigen Eigenvektoren in $\C^2$ sind:
  \begin{equation*}
    v_1 = \begin{pmatrix} i \\ 1 \end{pmatrix} \qquad v_2
  = \begin{pmatrix} -i\\ 1 \end{pmatrix} \qquad\text{mit}\quad \langle v_1, v_2 \rangle = v_1^T\bar{v_2} = 0 \ \text{ und } \ \Vert
v_i\Vert = \sqrt{2}.
\end{equation*}
  Durch Normalisierung der Eigenvektoren mit dem Faktor $\sqrt{2}$ erhalten wir
  \begin{equation*}
    S^* \, = \, S^{-1} \, \coloneqq \, \frac{1}{\sqrt{2}} \begin{pmatrix} i&-i\\1&1\end{pmatrix},\quad S \ \coloneqq \ \frac1{\sqrt{2}}\begin{pmatrix}-i&1\\i&1\end{pmatrix}
  \end{equation*}
  und wir erhalten damit
  \begin{equation*}
  SAS^* \ = \ \begin{pmatrix} i&0\\0&-i\end{pmatrix}.
  \end{equation*}
\end{bsp}

Um den komplizierteren Fall von \textbf{orthogonalen Endomorphismen} besser zu verstehen beginnen wir mit einer Falldiskussion für kleine Dimensionen $n = 1,2,3$ des Vektorraums $V$.
Sei also im Folgenden $F \colon V \rightarrow V$ ein orthogonaler Endomorphismus und $A \coloneqq M_B(F)$ die darstellende Matrix von $F$ bezüglich einer Basis $B$.
Aus Satz \ref{satz:orthogonale_matrizen} wissen wir, dass $A$ dann auch orthogonal ist und wir können unsere Diskussion auf diese Matrix beschränken.

Im \emph{eindimensionalen Fall} kann wegen $A^{-1} = A^T$ nur gelten $A = \pm 1$.

Im \emph{zweidimensionalen Fall} erhalten wir im folgenden Lemma eine interessante geometrische Interpretation von orthogonalen Matrizen, die besagt, dass orthogonale $(2 \times 2)$-Matrizen spezielle geometrische Transformationen realisieren.
%entweder eine Drehung oder eine Spiegelung realisieren.
\begin{lemma}\label{lem:orthogonal_2d}
  Ist $A\in\operatorname{O}(2)$, so gibt es ein $\alpha\in\left[0, 2\pi\right[$, so dass
  \begin{align*}
    A = \begin{pmatrix} \cos\alpha&-\sin\alpha\\\sin\alpha&\cos\alpha\end{pmatrix}
      \quad\text{oder}\quad
      A = \begin{pmatrix}\cos\alpha&\sin\alpha\\\sin\alpha&-\cos\alpha\end{pmatrix}.
  \end{align*}
  %Im ersten Fall ist die Abbildung $A\in\operatorname{SO}(2)$ eine \emph{Drehung} mit $\det A = 1$.
  %Im zweiten Fall ist $\det A=-1$, die Abbildung ist eine \emph{Spiegelung} an einer Geraden.
    \end{lemma}
    \begin{proof}
    In der Hausaufgabe zu zeigen.
    \end{proof}
%  \Uebung{
%  \begin{proof}
%    Ist $A\in\operatorname{O}(2)$, so muss per Definition $ A^T\cdot A=E_2$ gelten.
%    Für eine allgemeine Matrix $A \in \mathbb{R}^{2 \times 2}$ mit 
%    \begin{align*}
%      A \ = \ \begin{pmatrix}a&b\\c&d\end{pmatrix},
%    \end{align*}
%    muss also gelten
%    \begin{enumerate}
%      \item $a^2+b^2 = 1\,,$
%      \item $c^2+d^2 = 1\,,$
%      \item $ac+bd=0\,.$
%    \end{enumerate}
%    Wegen 1. und 2. gibt es zwei Winkel $\alpha, \alpha^\prime\in[0, 2\pi[$, so dass
%    \begin{equation*}
%      a=\cos\alpha, \qquad b=\sin\alpha, \qquad c=\sin\alpha^\prime, \qquad
%      d=\cos\alpha^\prime\,.
%    \end{equation*}
%    Nach 3. ist $0=\cos\alpha\cdot\sin\alpha^\prime + \sin\alpha\cdot\cos\alpha^\prime = \sin(\alpha+\alpha^\prime)$.
%    Also ist $\alpha + \alpha^\prime$ entweder ein geradzahliges under ein ungeradzahliges Vielfaches von $\pi$.
%    Deshalb ist entweder
%    \begin{align*}
%      c&=\sin\alpha^\prime=-\sin\alpha\qquad\text{und}\qquad
%      d=\cos\alpha^\prime=\phantom{-}\cos\alpha\qquad\text{oder}\\
%      c&=\sin\alpha^\prime=\phantom{-}\sin\alpha\qquad\text{und}\qquad
%      d=\cos\alpha^\prime=-\cos\alpha\,.
%    \end{align*}
%  Diese beiden Fälle realisieren also gerade eine Drehung oder eine Spiegelung in $\mathbb{R}^2$.
%  \end{proof}
%  }

Im \emph{dreidimensionalen Fall} eines orthogonalen Endomorphismus $F\colon\R^3\to\R^3$ betrachten wir das charakteristische Polynom $P_F$.
Da $P_F$ den Grad $3$ besitzt, existiert nach dem Zwischenwertsatz der Analysis mindestens eine reelle Nullstelle von $P_F$.
Also hat $F$ mindestens einen Eigenwert $\lambda_1 \in \mathbb{R}$ und nach Satz \ref{satz:orthogonale_endomorphismen} wissen wir, dass $\lambda_1=\pm1$ gilt.
Sei $v_1\in\R^3$ der zugehörige Eigenvektor, für den wir $\Vert v_1\Vert = 1$ annehmen können (durch Normalisierung).
Dann können diesen Eigenvektor von $F$ nach Satz \ref{satz:orthonormalisierung}  zu einer Orthonormalbasis $B = (v_1,w_2,w_3)$ von $V$ ergänzen.

Wir bezeichnen mit $W\subset V = \R^3$ die von $w_2$ und $w_3$ aufgespannte zweidimensionale Ebene.
Da $v_1$ ein Eigenvektor von $F$ ist, gilt natürlich $F(v_1) \subset \lin(\left\lbrace v_1 \right\rbrace)$. 
Da außerdem $v_1 \perp W$ und $F$ nach Satz \ref{satz:orthogonale_endomorphismen} ein Isomorphismus ist muss gelten, dass $F(W)=W$ gilt.
Betrachten wir die darstellende Matrix $M_B(F)$ von $F$ bezüglich der Orthonormalbasis $B$ mit
\begin{equation*}
  M_{B}(F) \ = \ \left(
  \begin{array}{cc}
    \lambda_1 & \begin{array}{cc}0 & 0\end{array}\\
    \begin{array}{c}0\\0\end{array} & \begin{array}{|c|}\hline
  \\[-.8em]\hphantom{i}A^\prime\hphantom{i}\\[-.8em]\\\hline\end{array}
  \end{array}
\right)  \ \eqqcolon \ A,
\end{equation*}
so folgt aus Satz \ref{satz:orthogonale_matrizen}, dass $A^\prime \in\operatorname{O}(2)$ orthogonal ist.
Weiter gilt wegen der Determinantenregel für Blockmatrizen in Lemma \ref{lem:det_blockmatrix}, dass gilt $\det A = \lambda_1 \cdot \det A^\prime$.
Betrachten wir also die möglichen Fälle im Folgenden basierend auf unseren Erkenntnissen aus Lemma \ref{lem:orthogonal_2d}.

\begin{enumerate}
\item Sei $\det A = +1$. Ist $\lambda_1 = -1$, dann muss $\det A^\prime = -1$ sein.
Daher kann man $w_2$ und $w_3$ als Eigenvektoren zu den Eigenwerten $\lambda_2 = + 1$ und $\lambda_3 = -1$ wählen, also
\begin{equation*}
  A = \left(\begin{array}{rrr}-1 & 0 & 0\\ 0 & \phantom{-}1 & 0\\ 0 & 0 & -1\end{array}\right)\,.
\end{equation*}
Ist $\lambda_1 = +1$, dann muss auch $\det A^\prime = +1$ sein, also gibt es ein $\alpha \in \left[0, 2\pi\right[$, so dass
\begin{equation*}
  A = \left(\begin{array}{rrr}1 & 0 & 0\\ 0 & \cos\alpha & -\sin\alpha\\
  0 & \sin\alpha & \cos\alpha\end{array}\right)\,.
\end{equation*}

\item Ist $\det A = -1$, dann gibt es bei geeigneter Wahl von $w_2$ und $w_3$ die Möglichkeiten
\begin{equation*}
 A \ = \ \begin{pmatrix}1 & 0 & 0\\ 0 & 1 & 0\\
      0 & 0 & -1\end{pmatrix}\qquad\text{ und }\qquad
      A \ = \ \begin{pmatrix}-1 & 0 & 0\\ 0 &\cos\alpha & -\sin\alpha\\
      0 & \sin\alpha & \cos\alpha\end{pmatrix}.
\end{equation*}
\end{enumerate}

Wir nutzen unsere Erkenntnisse aus der gerade durchgeführten Diskussion für die Fälle $\dim V  \in \lbrace 1,2,3\rbrace$ um eine \emph{Normalform für unitäre und orthogonale Endomorphismen} im allgemeinen Fall anzugeben.


Im Gegensatz zu der gerade im komplexen Fall bewiesenen Diagonalisierbarkeit unitärer Endomorphismen gibt es im Reellen orthogonale Endomorphismen ohne Eigenwerte in $\mathbb{R}$.
Das einfachste Beispiel sind Drehungen in der Ebene $\R^2$ wie in Beispiel \ref{bsp:drehung_unitär} beschrieben. 

Bevor wir uns der Normalform von orthogonalen Endomorphismen widmen benötigen wir das folgende hilfreiche Lemma.
  \begin{lemma}\label{lem:orthogonal_2d_unterraum}
    Zu einem orthogonalen Endomorphismus $F \colon V \rightarrow V$ eines Euklidischen Vektorraums $V$ mit $\dim V \geq 1$ gibt es stets einen Untervektorraum $W \subset V$ mit
    \begin{equation*}
      F(W) \subset W\quad\text{und}\quad 1\leq\dim W\leq 2\,.
    \end{equation*}
  \end{lemma}
\begin{proof}
Sei $A \in \mathbb{R}^{n \times n}$ die darstellende Matrix des orthogonalen Endomorphismus $F$ auf $V$.
Wir führen den Beweis des Lemmas durch eine Symmetrisierung von $A$.
Sei hierfür die Symmetrisierung $A^s$ von $A$ definiert als
\begin{equation*}
A^s \ \coloneqq \ A + A^T \ = \ A + A^{-1}.
\end{equation*}
Offensichtlich ist $A^s$ symmetrisch, da für alle Indizes $1 \leq i,j \leq n$ gilt
\begin{equation*}
A^s_{i,j} \ = \ A_{i,j} + A^T_{i,j} \ = \ A_{i,j} + A_{j,i} \ = \ A^T_{j,i} + A_{j,i} \ = \ A^s_{j,i}.
\end{equation*}
Wie wir im nächsten Kapitel sehen werden, bedeutet dies, dass ein reeller Eigenwert $\lambda \in \mathbb{R}$ und ein zugehöriger reeller Eigenvektor $v$ von $A^s$, so dass die Eigenwertgleichung $A^sv=\lambda v$ erfüllt ist.

Dieser Eigenvektor erzeugt den $F$-invarianten Unterraum $W$ mit 
\begin{equation*}
  W:=\operatorname{span}(v, Av).
\end{equation*}
Die Invarianz von $W$ unter Anwendung von $A$ folgt aus den folgenden Argumenten.
Wenden wir $A$ auf $v$ an, so erhalten wir den Vektor $Av \in W$.
Außerdem gilt, dass $A \cdot Av = A^2v \in W$, da wir aus der Eigenwertgleichung sehen:
\begin{equation*}
Av+A^{-1}v \, = \,  A^sv \, = \, \lambda v \quad \Rightarrow \quad A^2v \, = \, -v+\lambda Av\ \in W.
\end{equation*}
\end{proof}

Wir zeigen nun, dass sich die Normalform eines orthogonalen Endomorphismus auf eine darstellende Matrix zurückführen lässt, die im Wesentlichen nur die Eigenwerte $\pm 1$ auf der Hauptdiagonalen und eben jene $(2 \times 2)$-Drehmatrizen besitzt.
\begin{satz}
  Ist $F$ ein orthogonaler Endomorphismus eines Euklidischen Vektorraums $V$, dann gibt es in $V$ eine Orthonormalbasis $B$ derart, dass die darstellende Matrix $M_B(F) \in \GL(n; \mathbb{R})$ folgende Gestalt einer \emph{Normalform} hat
  \begin{equation*}
    M_{B}(F) = \left(\begin{array}{rrrrrrrrr}
        +1&&&&&&&&\\
        &\ddots&&&&&&&\\
        &&+1&&&&0 &&\\
        &&&-1&&&&&\\
        &&&&\ddots&&&&\\
        &&&&&-1&&&\\
        &&0&&&&A_1&&\\
        &&&&&&&\ddots&\\
        &&&&&&&&A_k
      \end{array}\right)\,,
  \end{equation*}
  wobei für $j=1,\ldots,k$ folgende Drehmatrizen existieren:
  \begin{equation*}
    A_j = \begin{pmatrix} \cos    \alpha_j&-\sin\alpha_j\\\sin\alpha_j&\cos\alpha_j\end{pmatrix} \in \operatorname{SO}(2)\qquad\text{mit}\quad\alpha_j\in[0,2\pi[, \text{ jedoch } \alpha_j\not\in\{0,\pi\}\,.
  \end{equation*}
  $F$ ist also charakterisiert durch die Anzahl $r\in \mathbb{N}$ der Eigenwerte $+1$  die Anzahl $s\in \mathbb{N}$ der Eigenwerte  $-1$, sowie durch die Winkel $\alpha_1, \ldots,\alpha_k$, wobei gilt
  \begin{equation*}
  r+s+2k \ = \ \dim V.
  \end{equation*}
\end{satz}
\begin{proof}[Beweis]
 Sei $A$ eine darstellende Matrix von $F$. 
 Wir führen den Beweis durch vollständige Induktion über $n=\dim V$.\\[0.3cm]
\textbf{Induktionsanfang: $n=1$ und $n=2$}\\
Der Induktionsanfang folgt direkt aus der Beobachtung, dass $A = \pm 1$ für $n=1$ gilt und der Aussage von Lemma \ref{lem:orthogonal_2d} für $n=2$.
~\\[0.3cm]
\textbf{Induktionsschritt: $n-1 \rightarrow n$ für $n \geq 3$}\\
Die Induktionsannahme ist, dass die Aussage bereits für den Fall $n-1$ und $n-2$ gezeigt wurde.

Da $F$ orthogonal ist existiert nach Lemma \ref{lem:orthogonal_2d_unterraum} ein Untervektorraum $W\subset V$ mit 
\begin{align*}
  1 \, \leq \, \dim W \, \leq \, 2\qquad\text{ und }\quad F(W) \, \subset \,W.
\end{align*}
Aus Satz \ref{satz:orthogonale_endomorphismen} wissen wir, dass $F$ injektiv und somit gilt schon, dass $F(W) = W$ sein muss.
Außerdem existiert existiert ein Endomorphismus $F^{-1}$, der auch orthogonal ist und für den gilt $F^{-1}(W) = W$.
Daher können wir für die Vektoren $w\in W$ und $v\in W^\perp$ folgern, dass gilt
\begin{align*}
\langle F(v), w\rangle \ = \ \langle F^{-1} (F(v)), F^{-1} (w)\rangle \ = \ \langle v, F^{-1}(w)\rangle \ = \ 0.
\end{align*}
Daraus folgt schon, dass $F(W^\perp) \subset W^\perp$ gilt.
Da $F$ nach Satz \ref{satz:orthogonale_endomorphismen} insbesondere ein Isomorphismus ist, muss schon gelten, dass $F(W^\perp) = W^\perp$.
Damit haben wir $F$ zerlegt in zwei orthogonale Abbildungen
\begin{align*}
G \,:= \, F|_W\colon W\to W\qquad\text{ und }\quad H \, := \, F|_{W^\perp}\colon W^\perp\to W^\perp\,.
\end{align*}
Da $n-2 \leq \dim W^\perp < n$ ist können wir können wir auf $H$ die Induktionvorrausetzung anwenden und erhalten eine Basis $B^\prime$ von $W^\perp$ der gewünschten Art.

Für den orthogonalen Endomorphismus $G$ müssen wir abschließend noch zwei Fälle in Abhängigkeit von $\dim W \in \lbrace 1,2 \rbrace$ betrachten.
\begin{enumerate}
\item Ist $\dim W = 1$, so gibt es einen Eigenvektor $v\in W$ mit $\Vert v\Vert = 1$ zu einem Eigenwert $\pm1$.
Ergänzt man $B^\prime$ an passender Stelle durch $v$ zu $B$, so hat diese Basis von $V$ die gewünschten Eigenschaften.
\item Im Fall $\dim W = 2$ gibt es eine Orthonormalbasis $(v_1, v_2)$ von $W$, bezüglich der $G$ nach Lemma \ref{lem:orthogonal_2d} beschrieben wird durch eine Matrix der Form
\begin{align*}
  \left(\begin{array}{rr}\pm1&0\\0&\pm1\end{array}\right)\quad\text{oder}\quad\left(\begin{array}{rr}\cos\alpha_j&-\sin\alpha_j\\\sin\alpha_j&\cos\alpha_j\end{array}\right)\qquad\text{ mit }\quad\alpha_j\neq0, \alpha_j\neq\pi.
\end{align*}
Indem man $v_1$ und $v_2$ an den passenden Stellen in $B^\prime$ einfügt, erhält man wieder einen gewünschte Basis $B$ von $V$.
\end{enumerate}
Wie der Beweis zeigt lässt sich $V$ rekursiv in eine orthogonale direkte Summe von invarianten Unterräume der Dimension $1$ oder $2$ zerlegen.
\end{proof}
