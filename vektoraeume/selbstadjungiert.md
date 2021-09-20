# Selbstadjungierte Endomorphismen

Dieser Abschnitt widmet sich hauptsächlich den Eigenschaften und der Herleitung einer Normalform von symmetrischen bzw. hermetischen Matrizen.
Wir werden insbesondere zeigen, dass diese Matrizen immer diagonalisierbar sind, was sie besonders attraktiv für numerische Verfahren macht.
Da diese Familie von Matrizen auch in der Theorie sehr häufig auftaucht haben sie zahlreiche Anwendungen in Geometrie, Analysis und in der Physik.

Wir beginnen mit der Definition von adjungierten und selbstadjungierten Endomorphismen, die eine zentrale Rolle in diesem Abschnitt spielen werden.
\begin{definition}[(Selbst-)Adjungierter Endomorphismus]\label{def:adjungierte}
Wir nennen eine Abbildung $F^* \colon V \to V$ den \emph{adjungierten Endomorphismus} von $F$, falls die folgende Beziehung bezüglich des Standardskalarprodukts gilt:
\begin{equation}\label{eq:endoAdj}
\langle F(v), w\rangle \ = \ \langle v, F^* (w)\rangle\qquad\text{ für alle } v,w\in V.
\end{equation}
 Ein Endomorphismus $F$ eines Euklidischen bzw. unitären Vektorraums $V$ heißt \emph{selbstadjungiert}, wenn $F=F^*$, d.h.
  \begin{equation*}
    \langle F(v), w\rangle \ = \ \langle v, F(w)\rangle \qquad\text{ für alle } v,w\in V.
      \end{equation*}
\end{definition}

Für orthogonale bzw. unitäre Matrizen haben wir bereits in Kapitel \ref{s:unitäre_endomorphismen} gesehen, dass $A^* = A^{-1}$ gilt.
Diese Beobachtung überträgt sich mit folgendem Lemma auch auf adjungierte Endomorphismen.
\begin{lemma}
  Ist $F$ orthogonal bzw. unitär, so gilt $F^* = F^{-1}$.
  \begin{proof}
    Seien $u,v\in V$ mit $w=F(u)$, also $u=F^{-1}(w)$, so folgt 
    \begin{equation*}
      \langle F(v), w\rangle \ = \ \langle F(v), F(u)\rangle \ = \ \langle v, u\rangle \ = \ \langle v, F^{-1}(w)\rangle\,.
    \end{equation*}
  \end{proof}
\end{lemma}

Folgender Satz garantiert uns die Existenz eines adjungierten Endomorphismus und stellt eine Beziehung zur Adjungierten der darstellenden Matrix her.
\begin{satz}\label{satz:adjEndo_existenz}
  Sei $V$ ein endlich-dimensionaler Euklidischer bzw. unitärer $\K$-Vektorraum und $F\colon V\to V$ ein Endomorphismus.
  Dann existiert genau ein adjungierter Endomorphismus $F^*$ von $F$.
  Ist $B$ eine Orthonormalbasis von $V$ und $A:=M_{B}(F)$ die darstellende Matrix von $F$ bezüglich $B$, so gilt 
  \begin{equation*}
  M_{B}(F^*) \ = \ A^*.
  \end{equation*}  
  \begin{proof}
    Da $B$ orthonormal ist, gilt für $v=\Phi_{B}(x)$ und $w=\Phi_{B}(y)$ mit $x,y\in\K^n$,  so dass 
    \begin{equation*}
    \langle v, w\rangle \ = \ x^T E_n \bar{y} \ = \ x^T\bar{y}.
    \end{equation*}
    Die Bedingung \eqref{eq:endoAdj} bedeutet also
    \begin{equation*}
   \langle F(v), w \rangle \ = \ (Ax)^T\bar{y} \ = \ x^TA^T\bar{y} \ \overset{!}{=} \ x^T \bar{C}\bar{y} \ = \ \langle v, F^*(w) \rangle \qquad\text{ für alle } x,y\in\K^n\,.
  \end{equation*}
  Daraus folgt nun, dass $A^T = \bar{C}$ gelten muss.
  Also ist $F^*$ durch die darstellende Matrix $C \coloneqq \bar{A}^T$ eindeutig definiert.
\end{proof}
\end{satz}

Aus dem obigen Satz lässt sich folgende interessante Beziehung zwischen selbstadjungierten Endomorphismen und symmetrischen bzw. hermiteschen Matrizen direkt ableiten.
\begin{cor}\label{cor:selbstadjungiert_hermitesch}
  Ist $F \colon V \to V$ ein Endomorphismus und $B$ eine Orthonormalbasis von $V$, so gilt
  \begin{equation*}
    F \text{ selbstadjungiert } \ \Leftrightarrow \ A \coloneqq M_B(F) \text{ ist symmetrisch bzw. hermetisch, d.h. } A=A^*.
  \end{equation*}
\end{cor}
\begin{proof}
Mit den gleichen Argumenten wie im Beweis von Satz \ref{satz:adjEndo_existenz} können wir feststellen, dass $F$ selbstadjungiert ist genau dann wenn gilt:
\begin{equation*}
\langle F(v), w \rangle \ = \ (Ax)^T\bar{y} \ = \ x^TA^T\bar{y} \ \overset{!}{=} \ x^T \bar{A}\bar{y} \ = \ \langle v, F(w) \rangle \qquad\text{ für alle } x,y\in\K^n\,.
\end{equation*}
Das ist offensichtlich genau dann der Fall, wenn $A^T = \bar{A}$ gilt oder äquivalent, wenn gilt $A = \bar{A}^T = A^*$.
\end{proof}

Selbstadjungierte Endomorphismen haben die schöne Eigenschaft, dass sie nur reelle Eigenwerte besitzen, wie uns folgendes Lemma zeigt.
\begin{lemma}\label{lem:selbstadjungiert_ew}
  Sei $V$ ein Euklidischer bzw. unitärer $\K$-Vektorraum und $F\colon V\to V$ selbstadjungiert.
  Dann hat das charakteristische Polynom $P_F$ auch für $\K=\C$ nur reelle Nullstellen und zerfällt in Linearfaktoren über $\mathbb{R}$.
  Insbesondere sind alle Eigenwerte von $F$ reell.
  \begin{proof}
  Sei $\lambda \in \K$ ein Eigenwert von $F$ mit zugehörigem Eigenvektor $v \in V$, dann gilt $F(v) = \lambda v$.
  Wegen der Selbstadjungiertheit von $F$ können wir dann folgern:
  \begin{equation*}
    \lambda\langle v,v\rangle \ = \ \langle\lambda v,v\rangle \ = \ \langle F(v), v\rangle \ = \ \langle v, F(v)\rangle \ = \ \langle v, \lambda v\rangle \ = \ \bar\lambda \langle v,v\rangle.
  \end{equation*}
  Da $v \neq 0$ ist als Eigenvektor folgt also schon, dass $\bar\lambda = \lambda$ gilt und somit sind alle Eigenwerte von $F$ reell.
  
  Da das charakteristische Polynom $P_F$ von $F$ nach dem Fundamentalsatz der Algebra in Linearfaktoren über $\C$ zerfällt und die Nullstellen die Eigenwerte von $F$ darstellen, folgt die Aussage.
\end{proof}
\end{lemma}

Wenn wir die Aussagen aus Korollar \ref{cor:selbstadjungiert_hermitesch} und Lemma \ref{lem:selbstadjungiert_ew} zusammen nehmen, können wir folgern, dass alle symmetrischen und hermiteschen Matrizen nur reelle Eigenwerte besitzen.
Wir wollen diese Eigenschaft in folgendem Beispiel illustrieren.
\begin{example}
Wir untersuchen die Eigenwerte zweier hermitescher Matrizen $A \in \mathbb{K}^{2 \times 2}$ im Folgenden.
\begin{enumerate}
\item  Sei $A \in \mathbb{C}^{2 \times 2}$ mit  
  \begin{equation*}
    A \ \coloneqq \ \begin{pmatrix} 1&i\\-i&2\end{pmatrix}.
  \end{equation*}
  Dann ist das charakteristische Polynom gegeben durch $P_A(t) = t^2-3t +1$ dessen Nullstellen gegeben sind durch:
  \begin{equation*}
  \lambda_{1/2} \ = \ \frac12 (3\pm\sqrt{5})\in\R.
  \end{equation*}
  \item Sei $A \in \mathbb{R}^{2 \times 2}$ mit  
  \begin{equation*}
    A \ \coloneqq \ \begin{pmatrix} a&b\\b&c\end{pmatrix}.
  \end{equation*}
  Dann ist das charakteristische Polynom gegeben durch 
  \begin{equation*}
  P_A(t) \ = \ t^2-(a+c)t+(ac-b^2).
  \end{equation*}
  Die Diskriminante von $P_A$ ist in diesem Fall $(a-c)^2+4b^2\geq 0$, also sind die Eigenwerte reell.
  \end{enumerate}
\end{example}

Die schönen mathematischen Eigenschaften von selbstadjungierten Endomorphismen führen dazu, dass ihre Normalform einer Diagonalmatrix entspricht wie uns folgender Satz erklärt.
\begin{satz}[Diagonalisierungssatz]
  Ist $F$ ein selbstadjungierter Endomorphismus auf einem Euklidischen bzw. unitären Vektorraum $V$, so gibt es eine Orthonormalbasis von $V$, die aus Eigenvektoren zu reellen Eigenwerten von $F$ besteht.
  \begin{proof}
   Wir führen den Beweis mittels vollständiger Induktion über $n=\dim V$.\\[0.3cm]
\textbf{Induktionsanfang: $n=1$}\\  
Da $F$ selbstadjungiert ist, ist der einzige Eigenwert von $F$ reell.
Sei $\lambda_1 \in \mathbb{R}$ der Eigenwert von $F$ und $v_1 \in V$ der zugehörige Eigenvektor mit $||v_1|| = 1$ (durch Normalisierung).
Dann bildet $B = (v_1)$ eine Orthonormalbasis von $V$.
~\\[0.3cm]
\textbf{Induktionsschritt: $n-1 \rightarrow n$}\\
Die Induktionsannahme ist, dass die Aussage bereits für den Fall $n-1$ gezeigt wurde.
Nach Lemma \ref{lem:selbstadjungiert_ew} zerfällt das charakteristische Polynom $P_F$ von $F$ in Linearfaktoren über $\R$ mit:
    \begin{equation*}
      P_F = \pm (t-\lambda_1)\cdot\ldots\cdot(t-\lambda_n)\qquad\text{ mit }\qquad\lambda_1,\ldots,\lambda_n\in\R.
    \end{equation*}
    Wir wählen den Eigenwert $\lambda_1$ von $F$ und den zugehörigen Eigenvektor $v_1$ mit $\Vert v_1\Vert = 1$ (durch Normalisierung) und definieren das orthogonale Komplement zu $v$ als
    \begin{equation*}
      W \ \coloneqq \ \left\{w\in V~|~v_1 \perp w \right\}.
    \end{equation*}
    Wir erkennen wieder, dass $W$ invariant ist unter $F$, d.h. $F(W)\subset W$, da für $w\in W$ wegen  der Selbstadjungiertheit gilt:
    \begin{equation*}
      \langle v_1, F(w)\rangle \ = \ \langle F(v_1), w\rangle \ = \ \langle \lambda_1v_1, w\rangle \ = \ \lambda_1 \langle v_1, w\rangle \ = \ 0\,.
    \end{equation*}
    Außerdem ist $F\vert_W\colon W\to W$ als Einschränkung von $F$ wieder selbstadjungiert.
    Da 
    \begin{equation*}
    P_{F|_W} \ = \ \pm (t-\lambda_2)\cdot\ldots\cdots(t-\lambda_n)
    \end{equation*}
    gilt können wir die Induktionsvorraussetzung anwenden, so dass eine Orthonormalbasis $B'$ von $W$ existiert aus Eigenvektoren von $F|_W$.
    Diese können wir nun zu der gewünschten Orthonormalbasis $B = (v_1, \ldots, v_n)$ von $V$ aus Eigenvektoren von $F$ ergänzen.
  \end{proof}
\end{satz}

Wegen der Diagonalisierbarkeit eines selbstadjungierten Endomorphismus lassen sich direkt zwei Beobachtungen ableiten.
\begin{cor}
  Ist $A\in \K^{n\times n}$ eine symmetrische bzw. hermitesche Matrix, so gibt es eine orthogonale bzw. unitäre Matrix $S \in U(n)$, so dass
  \begin{equation*}
   S \cdot A \cdot S^* \ = \ \begin{pmatrix} \lambda_1&&0\\&\ddots&\\0&&\lambda_n\end{pmatrix} \qquad \text{ mit }\quad\lambda_1, \ldots, \lambda_n\in\R.
  \end{equation*}
  \begin{proof}
    Als Spalten von $S^* = S^{-1}$ verwendet man eine orthonormale Basis des $\C^n$, die aus Eigenvektoren von $A$ besteht.
  \end{proof}
\end{cor}

Außerdem lässt sich aus dem Satz \ref{satz:hauptraumzerlegung} über die Hauptraumzerlegung folgende Zerlegung in orthogonale $F$-invariante Unterräume folgern.
\begin{cor}
  Sind $\lambda_1, \ldots, \lambda_k \in \R$ die paarweise verschiedenen Eigenwerte eines selbstadjungierten oder unitären Endomorphismus $F$ von $V$, so ist
  \begin{equation*}
    V \ = \ \Eig (F;\lambda_1) \, \obot \, \cdots \, \obot \, \Eig(F;\lambda_k),
  \end{equation*}
  wobei $\obot$ die orthogonale Summe bezeichnet.
\end{cor}

%Um nun in der Praxis eine Orthonormalbasis aus Eigenvektoren zu berechnen kann man wie folgt vorgehen:
%\begin{enumerate}
%  \item Man bestimme die Linearfaktorzerlegung des charakteristischen Polynoms
%    \begin{equation*}
%      P_F = \pm (t-\lambda_1)^{r_1} \cdot\ldots\cdot (t-\lambda_k)^{r_k}\,,
%    \end{equation*}
%    wobei $\lambda_1,\ldots,\lambda_k$ paarweise verschieden.
%  \item Für jeden Eigenwert $\lambda$ der Vielfachheit $r$ bestimmt man nun eine Basis von $\Eig(F;\lambda)$ durch Lösen eines linearen Gleichungssystems.
%  \item Orthonomalisiere die im vorherigen Punkt erhaltene Basis, und zwar unabhängig voneinander in den verschiedenen Eigenräumen.
%  \item Die $k$ Basen der Eigenräume bilden zusammen die gesuchte Basis aus Eigenvektoren von $V$.
%\end{enumerate}
%
%\begin{bsp}
%  Sei 
%  \begin{equation*}
%    A:=\frac1{15}\left(\begin{array}{rrr}10&5&10\\5&-14&2\\10&2&-11\end{array}\right)\in\operatorname{M}(3\times 3;\R)\,.
%  \end{equation*}
%  Wie man leicht nachrechnet, bilden die Spaltenvektoren eine Orthonormalbasis von $\R^3$, und es ist $\det A=1$.
%  Also ist $A\in\operatorname{SO}(3)$.
%  Als charakteristisches Polynom erhält man
%  \begin{equation*}
%    P_A = -t^3-t^2+t+1 = -(t-1)(t+1)^2\,.
%  \end{equation*}
%  Zur Bestimmung von $\Eig(A;1)$ hat man das homogene lineare Gleichungssystem mit der Koeffizientenmatrix
%  \begin{equation*}
%    \frac1{15}\left(\begin{array}{rrr}-5&5&10\\5&-29&2\\10&2&-26\end{array}\right)
%  \end{equation*}
%  zu lösen.
%  Man findet $\Eig(A;1) = \lin( \lbrace(5,1,2)^T \rbrace )$.
%  
%  $\Eig(A;-1)$ ist Lösungsraum des homogenen linearen Gleichungssystems mit der Koeffizientenmatrix
%  \begin{equation*}
%    \frac1{15}\left(\begin{array}{rrr}25&5&10\\5&1&2\\10&2&4\end{array}\right)\,,
%  \end{equation*}
%  und man erhält $\Eig A;-1) = \Eig(A;1)^\perp$.
%  Etwa $(0,-2,1)^T$ und $(1,-1,-2)^T$ bilden eine orthogonale Basis von $\Eig(A;-1)$.
%  Also ist 
%  \begin{equation*}
%    \mathcal B := \left(\frac1{\sqrt{30}}(5,1,2)^T,\frac1{\sqrt{5}}(0,-2,1)^T,\frac1{\sqrt{6}}(1,-1,-2)^T\right)
%  \end{equation*}
%  eine Orthonormalbasis des $\R^3$, bestehend aus Eigenvektoren von $A$.
%  Setzen wir
%  \begin{equation*}
%    S^* \ \coloneqq \ \left(\begin{array}{rrr}\frac5{\sqrt{30}}&0&\frac1{\sqrt6}\\
%        \frac1{\sqrt{30}}&-\frac2{\sqrt5}&-\frac1{\sqrt6}\\
%    \frac2{\sqrt{30}}&\frac1{\sqrt5}&-\frac2{\sqrt6}\end{array}\right)
%  \end{equation*}
%  so folgt
%  \begin{equation*}
%   S A S^* \ = \ \left(\begin{array}{rrr}1&0&0\\0&-1&0\\0&0&-1\end{array}\right) \ \eqqcolon \ D.
%  \end{equation*}
%\end{bsp}

Für symmetrische bzw. hermitesche Matrizen können wir die positive Definitheit mittels des folgenden Satzes am Vorzeichen der Eigenwerte ablesen.
\begin{satz}\label{satz:hermitesch_positivdefinit}
  Für eine symmetrische bzw. hermitesche Matrix $A\in \K^{n \times n}$ sind die folgenden Bedingungen äquivalent:
  \begin{enumerate}[i)]
    \item $A$ ist positiv definit.
    \item Alle Eigenwerte $\lambda_1, \ldots, \lambda_n\in\R$ von $A$ sind positiv.
  \end{enumerate}

  \begin{proof}
    Für führen den Beweis für den allgemeineren Fall von unitären Vektorräumen, da er den Euklidischen Fall mit abdeckt.\\[0.2cm]
    \underline{$i)\Rightarrow ii)$:} Sei $\lambda \in \R$ ein beliebiger Eigenwert von $A$ und $v\in\C^n$ der zugehörige Eigenvektor, so ist wegen der Eigenwertgleichung
    \begin{equation*}
      Av \ = \ \lambda v \quad \Rightarrow \quad \bar{A}\bar{v} \ = \ \lambda\bar{v}\,.
    \end{equation*}
    Somit ist $\bar{v} \in \C^n$ offensichtlich ein Eigenvektor von $\bar{A}$ zum Eigenwert $\lambda$.
    Mit $w:=\bar{v}\neq0$ folgt wegen der Hermizität von $A$
    \begin{equation*}
      0 \ < \ w^TA\bar{w} \ = \ (A^Tw)^T \bar{w} \ = \ (\bar{A} w)^T\bar{w} \ = \ (\lambda w)^T\bar{w} \ = \ \lambda \cdot w^T\bar{w}\,.
    \end{equation*}
    und aus der positiven Definitheit des Skalarprodukts, d.h., $w^T\bar{w} > 0$, folgt $\lambda>0$.

    \underline{$ii)\Rightarrow i)$}: Wir wählen eine Orthonormalbasis $(w_1, \ldots, w_n)$ bestehend aus Eigenvektoren von $\bar A$, so dass $\bar Aw_i = \lambda_iw_i$ für alle $1 \leq i \leq n$.
    Ähnlich wie im Beweis der ersten Folgerung erhält man
    \begin{equation*}
     w_i^TA\bar w_j \ = \ \lambda_i\cdot w_i^T\bar w_j \ = \ \begin{cases}\lambda_i, &\text{für}~i=j\,,\\0, &\text{für}~i\neq j\,.\end{cases}
    \end{equation*}
    Jeder beliebige Vektor $v\in\C^n$ hat nun eine Darstellung aus Eigenvektoren mit $v=\sum\limits_{i=1}^n\mu_iw_i$, also ist
    \begin{equation*}
     v^TAv \ = \ \sum\limits_{i=1}^n\lambda_i\mu_i\bar\mu_i \ > \ 0\quad\text{für}~v\neq0\,.
    \end{equation*}
  \end{proof}
\end{satz}

Abschließend wollen wir die Behauptung aus Satz \ref{satz:hermitesch_positivdefinit} an einem konkreten Beispiel nachvollziehen.
\begin{bsp}
  Für $a,b\in\R$ und die hermetische Matrix
  \begin{equation*}
    A = \left(\begin{array}{rr}a&\i\\-\i&b\end{array}\right)\in\C^{2 \times 2}
  \end{equation*}
  ist
  \begin{equation*}
    P_A(t) \ = \ t^2 - (a+b)t + (ab-1)\,.
  \end{equation*}
  Also ist $A$ genau dann positiv definit, wenn $a+b>0$ und $ab>1$ ist.
  In diesem Fall kann man die Eigenwerte einfach ausrechnen:
  \begin{equation*}
    \lambda_{1,2} \ = \ \frac12 \left( a+b\pm\sqrt{(a-b)^2+4}\right)\,.
  \end{equation*}
  Sie sind beide positiv, wenn $a+b>0$ und $ab>1$ ist, wie man leicht nachprüfen kann.
\end{bsp}

\section{Normale Endomorphismen}
Zum Schluss betrachten wir noch eine weitere besondere Gruppe von Abbildungen.
Die sogenannten \emph{normalen Endomorphismen} zeichnen sich insbesondere dadurch aus, dass sie mit Ihrem adjungierten Endomorphismus kommutieren.
Hierzu betrachten wir die folgende Definition.
\begin{definition}[Normaler Endomorphismus]\label{def:endomorphismus_normal}
  Ist $V$ ein Euklidischer oder unitärer Vektorraum, so heißt ein Endomorphismus $F$ von $V$ \emph{normal}, wenn er mit seiner Adjungierten kommutiert, d.h.,
  \begin{equation*}
    F\circ F^* = F^* \circ F.
  \end{equation*}
  Ist $A=\operatorname{M}_{B}(F)$ eine darstellende Matrix von $F$ bezüglich einer Orthonormalbasis $B$ von $V$, so bedeutet das
  \begin{equation*}
    A\cdot A^* \ = \ A^* \cdot A.
  \end{equation*}
\end{definition}

\begin{example}
Wir wollen im folgenden hinreichende Bedingungen für Normalität eines Endomorphismus angeben.
\begin{enumerate}[i)]
\item Jeder unitäre Endomorphismus $F$ ist normal, da wegen $F^* = F^{-1}$ gilt
\begin{equation*}
F \circ F^* \ = \ F \circ F^{-1} \ = \ \operatorname{Id}_V \ = \ F^{-1} \circ F \ = \ F^* \circ F.
\end{equation*}
\item Jeder selbstadjungierte Endomorphismus $F$ ist normal, da wegen $F^* = F$ gilt
\begin{equation*}
F \circ F^* \ = \ F \circ F \ = \ F^2 \ = \ F \circ F \ = \ F^* \circ F.
\end{equation*}
\end{enumerate}
\end{example}

Für normale Endomorphismen stellt sich heraus, dass sowohl ihr Kern (sowie ihr Bild) mit denen der adjungierten Abbildung übereinstimmen, wie folgender Satz aussagt.
\begin{satz}\label{satz:kern_normal}
Sei $V$ ein unitärer Vektorraum und $F \colon V \rightarrow V$ ein normaler Endomorphismus von $V$.
Dann gilt
\begin{equation*}
\Kern F^* \ = \ \Kern F \quad \text{ und } \quad \Bild F^* \ = \ \Bild F..
\end{equation*}
\end{satz}
\begin{proof}
Sei $v \in \Kern F$, so können wir wegen der Normalität von $F$ folgern
\begin{equation*}
\begin{split}
0 \ = \ \langle F(v), F(v) \rangle \ &= \ \langle v, F^* \circ F(v) \rangle \\
\ &= \ \langle v, F \circ F^*(v) \rangle \ = \ \overline{\langle F \circ F^*(v), v  \rangle} \ = \ \overline{\langle F^*(v), F^*(v) \rangle}.
\end{split}
\end{equation*}
Da das komplexe Skalarprodukt positiv definit ist muss also schon gelten, dass $F^*(v) = 0$ gilt und somit $v \in \Kern F^*$ ist.
Damit haben wir gezeigt, dass $\Kern F^* = \Kern F$ gilt.
Wegen der Dimensionsformel von Bild und Kern \cite[Satz 2.2.4]{fischer} folgt dann auch schon direkt, dass $\Bild F^* = \Bild F$ ist.
\end{proof}

Um die Normalform von normalen Endomorphismen zu untersuchen, beweisen wir zunächst das folgende Lemma.
\begin{lemma}\label{lem:normal_eigenschaften}
  Sei $V$ ein Euklidischer bzw. unitärer Vektorraum und $F\colon V\to V$ ein Endomorphismus.
  Dann gelten die folgenden Aussagen:
  \begin{enumerate}[i)]
    \item $F$ ist genau dann normal, wenn
      \begin{equation}
        \langle F^*(v), F^*(w)\rangle \ = \ \langle F(v), F(w)\rangle\quad\text{für alle}~v,w\in V.
      \end{equation}
  \item Ist $F$ normal, so folgt für alle $v\in V$
    \begin{equation*}
      \Vert F^*(v)\Vert \ = \ \Vert F(v)\Vert.
    \end{equation*}
  \item Ist $F$ normal, so ist $G:=F-\lambda\operatorname{Id}_V$ für alle $\lambda\in\K$ normal.
  \item Ist $F$ normal, so gilt für alle $v\in V$ und $\lambda\in\K$
    \begin{equation*}
      F(v) = \lambda v\quad\Leftrightarrow\quad F^*(v) = \bar\lambda v.
    \end{equation*}
\end{enumerate}
\begin{proof}
Die einzelnen Aussagen folgen direkt aus der Definition \ref{def:endomorphismus_normal} von normalen Endomorphismen.
  \begin{enumerate}[i)]
    \item Ist $F$ normal, so können wir wegen $(F^*)^* = F$ und der Definition \ref{def:adjungierte} der Adjungierten folgern, dass gilt
      \begin{equation*}
       \langle F(v), F(w)\rangle  \ = \ \langle v, (F^*\circ F)(w)\rangle \ = \ \langle v, (F\circ F^*)(w)\rangle \ = \ \langle F^*(v), F^*(w)\rangle.
      \end{equation*}
    \item Folgt sofort aus i), da $||v|| = \sqrt{\langle v, v \rangle}$ für alle $v\in V$ gilt.
    \item Wir leiten uns zunächst den adjungierten Endomorphismus $G^*$ von $G$ her.
    Seien $v,w \in V$ und $G \coloneqq F - \lambda \operatorname{Id}_V$, dann gilt:
    \begin{equation*}
    \begin{split}
    \langle G(v), w \rangle \ &= \ \langle (F(v) - \lambda \operatorname{Id}_V) (v), w \rangle \ = \ \langle F(v), w \rangle - \lambda \langle \operatorname{Id}_V (v), w \rangle \\
    \ &= \ \langle v, F^*(w) \rangle - \lambda \langle v, \operatorname{Id}_V(w) \rangle \ = \ \langle v, (F^*(w) -\bar\lambda \operatorname{Id}_V) (w) \rangle \ = \ \langle v, G^*(w) \rangle.
    \end{split}
    \end{equation*}
    Es gilt also
    \begin{equation*}
    G^* \ = \ F^* - \bar\lambda\operatorname{Id}_V.
    \end{equation*}
      Durch Einsetzen erhalten wir die Normalität von $G$ durch
      \begin{equation*}
      \begin{split}
        G\circ G^* \ &= \ F\circ F^* - \lambda F^* - \bar\lambda F + \lambda\bar\lambda \\
        \ &= \ F^*\circ F - \bar\lambda F - \lambda F^* + \lambda\bar\lambda \ = \ G^*\circ G.
        \end{split}
      \end{equation*}
    \item Da $G = F - \lambda \operatorname{Id}_V$ nach iii) normal ist, können wir Satz \ref{satz:kern_normal} anwenden und erhalten damit:
    \begin{equation*}
    \Eig(F; \lambda) \ = \ \Kern G \ = \ \Kern G^* \ = \ \Eig(F^*; \bar\lambda).
    \end{equation*}
    Dies zeigt insbesondere, dass $F$ und $F^*$ die gleichen Eigenvektoren besitzen.
  \end{enumerate}
\end{proof}
\end{lemma}

Schließlich stellen wir mit dem folgenden Satz fest, dass die Normalform von normale Endomorphismen Diagonalgestalt besitzt.
\begin{satz}[Diagonalisierungssatz]
  Für einen Endomorphismus $F$ eines unitären Vektorraums $V$ sind die folgenden Eigenschaften äquivalent:
  \begin{enumerate}[i)]
    \item $F$ ist normal.
    \item Es gibt eine Orthonormalbasis $B$ von $V$ bestehend aus Eigenvektoren von $F$.
  \end{enumerate}
  \begin{proof}\
    
    \underline{$i)\Rightarrow ii)$}: 
	   Wir führen den Beweis mittels vollständiger Induktion über $n=\dim V$.\\[0.3cm]
\textbf{Induktionsanfang: $n=1$}\\  
Sei $\lambda_1 \in \mathbb{K}$ der Eigenwert von $F$ und $v_1 \in V$ der zugehörige Eigenvektor mit $||v_1|| = 1$ (durch Normalisierung).
Dann bildet $B = (v_1)$ eine Orthonormalbasis von $V$.
~\\[0.3cm]
\textbf{Induktionsschritt: $n-1 \rightarrow n$}\\
Die Induktionsannahme ist, dass die Aussage bereits für den Fall $n-1$ gezeigt wurde.        
    Sei $\lambda_1\in\C$ eine Nullstelle des charakteristischen Polynoms von $F$ und $v_1\in V$ ein zugehöriger Eigenvektor mit $\Vert v_1\Vert = 1$ (durch Normalisierung).
   Wir definieren das orthogonale Komplement $W:=\lin(\lbrace v_1 \rbrace)^\perp\subset V$ von $v_1$.
    Für jedes $w\in W$ gilt dann nach Lemma \ref{lem:normal_eigenschaften}
    \begin{equation*}
      \langle F(w), v_1\rangle \ = \  \langle w, F^*(v_1)\rangle \ = \ \langle w, \bar\lambda_1v_1\rangle \ = \ \lambda_1\langle w, v_1\rangle \ = \ 0.
    \end{equation*}
    Daraus folgt $F(W)\subset W$.
    $F\vert_W\colon W\to W$ ist als Einschränkung von $F$ wieder normal und für die charakteristischen Polynome gilt
    \begin{equation*}
      P_F \ = \ (t-\lambda_1) \cdot P_{F\vert_{W}}.
    \end{equation*}
    Nach Induktionsvorraussetzung wissen wir also, dass es eine Orthonormalbasis $B' = (v_2, \ldots, v_n)$ von $W$ aus Eigenvektoren von $F|_W$ gibt.
    Diese ergänzen wir um den Eigenvektor $v_1$ von $F$ zu einer Orthonormalbasis $B = (v_1, \ldots, v_n)$ von $V$ aus Eigenvektoren von $F$.
    ~\\[0.3cm]
    \underline{$ii)\Rightarrow i)$}: Die Matrix $D:=\operatorname{M}_{B}(F)$ ist diagonal und es gilt
    \begin{equation*}
    \operatorname{M}_{\mathcal{B}}(F^*) \ = \ D^* \ = \ \bar D.
    \end{equation*}
    Da die folgende Gleichung gilt 
    \begin{equation*}
    D\cdot D^* \ = \ D\cdot \bar D \ = \ \bar D\cdot D \ = \ D^* \cdot D
    \end{equation*}
     ist $F$ normal.
  \end{proof}
\end{satz}
