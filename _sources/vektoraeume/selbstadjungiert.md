# Selbstadjungierte Endomorphismen

Dieser Abschnitt widmet sich hauptsächlich den Eigenschaften und der Herleitung einer Normalform von symmetrischen bzw. hermetischen Matrizen.
Wir werden insbesondere zeigen, dass diese Matrizen immer diagonalisierbar sind, was sie besonders attraktiv für numerische Verfahren macht.
Da diese Familie von Matrizen auch in der Theorie sehr häufig auftaucht haben sie zahlreiche Anwendungen in Geometrie, Analysis und in der Physik.

Wir beginnen mit der Definition von adjungierten und selbstadjungierten Endomorphismen, die eine zentrale Rolle in diesem Abschnitt spielen werden.

````{prf:definition} (Selbst-)Adjungierter Endomorphismus
:label: def:adjungierte

Wir nennen eine Abbildung $F^* \colon V \to V$ den \emph{adjungierten Endomorphismus} von $F$, falls die folgende Beziehung bezüglich des Standardskalarprodukts gilt:
\begin{equation}:label: eq:endoAdj}
\langle F(v), w\rangle \ = \ \langle v, F^* (w)\rangle\qquad\text{ für alle } v,w\in V.
\end{equation}

 Ein Endomorphismus $F$ eines Euklidischen bzw. unitären Vektorraums $V$ heißt \emph{selbstadjungiert}, wenn $F=F^*$, d.h.
\begin{equation*}
  \langle F(v), w\rangle \ = \ \langle v, F(w)\rangle \qquad\text{ für alle } v,w\in V.
\end{equation*}
````

Für orthogonale bzw. unitäre Matrizen haben wir bereits in Kapitel {ref}`s:unitäre_endomorphismen` gesehen, dass $A^* = A^{-1}$ gilt.
Diese Beobachtung überträgt sich mit folgendem Lemma auch auf adjungierte Endomorphismen.

````{prf:lemma}
  Ist $F$ orthogonal bzw. unitär, so gilt $F^* = F^{-1}$.
````

````{prf:proof}
Seien $u,v\in V$ mit $w=F(u)$, also $u=F^{-1}(w)$, so folgt 
\begin{equation*}
  \langle F(v), w\rangle \ = \ \langle F(v), F(u)\rangle \ = \ \langle v, u\rangle \ = \ \langle v, F^{-1}(w)\rangle\,.
\end{equation*}
````

Folgender Satz garantiert uns die Existenz eines adjungierten Endomorphismus und stellt eine Beziehung zur Adjungierten der darstellenden Matrix her.

````{prf:theorem}
:label: satz:adjEndo_existenz

Sei $V$ ein endlich-dimensionaler Euklidischer bzw. unitärer $\K$-Vektorraum und $F\colon V\to V$ ein Endomorphismus.
Dann existiert genau ein adjungierter Endomorphismus $F^*$ von $F$.
Ist $B$ eine Orthonormalbasis von $V$ und $A:=M_{B}(F)$ die darstellende Matrix von $F$ bezüglich $B$, so gilt 
\begin{equation*}
M_{B}(F^*) \ = \ A^*.
\end{equation*}  
````

````{prf:proof}
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
````

Aus dem obigen Satz lässt sich folgende interessante Beziehung zwischen selbstadjungierten Endomorphismen und symmetrischen bzw. hermiteschen Matrizen direkt ableiten.

````{prf:corollary}
:label: cor:selbstadjungiert_hermitesch

Ist $F \colon V \to V$ ein Endomorphismus und $B$ eine Orthonormalbasis von $V$, so gilt
\begin{equation*}
  F \text{ selbstadjungiert } \ \Leftrightarrow \ A \coloneqq M_B(F) \text{ ist symmetrisch bzw. hermetisch, d.h. } A=A^*.
\end{equation*}
````

````{prf:proof}
Mit den gleichen Argumenten wie im Beweis von Satz {prf:ref}`satz:adjEndo_existenz` können wir feststellen, dass $F$ selbstadjungiert ist genau dann wenn gilt:
\begin{equation*}
\langle F(v), w \rangle \ = \ (Ax)^T\bar{y} \ = \ x^TA^T\bar{y} \ \overset{!}{=} \ x^T \bar{A}\bar{y} \ = \ \langle v, F(w) \rangle \qquad\text{ für alle } x,y\in\K^n\,.
\end{equation*}
Das ist offensichtlich genau dann der Fall, wenn $A^T = \bar{A}$ gilt oder äquivalent, wenn gilt $A = \bar{A}^T = A^*$.
````

Selbstadjungierte Endomorphismen haben die schöne Eigenschaft, dass sie nur reelle Eigenwerte besitzen, wie uns folgendes Lemma zeigt.

`````{prf:lemma}
:label: lem:selbstadjungiert_ew

Sei $V$ ein Euklidischer bzw. unitärer $\K$-Vektorraum und $F\colon V\to V$ selbstadjungiert.
Dann hat das charakteristische Polynom $P_F$ auch für $\K=\C$ nur reelle Nullstellen und zerfällt in Linearfaktoren über $\mathbb{R}$.
Insbesondere sind alle Eigenwerte von $F$ reell.
````

````{prf:proof}
Sei $\lambda \in \K$ ein Eigenwert von $F$ mit zugehörigem Eigenvektor $v \in V$, dann gilt $F(v) = \lambda v$.
Wegen der Selbstadjungiertheit von $F$ können wir dann folgern:
\begin{equation*}
  \lambda\langle v,v\rangle \ = \ \langle\lambda v,v\rangle \ = \ \langle F(v), v\rangle \ = \ \langle v, F(v)\rangle \ = \ \langle v, \lambda v\rangle \ = \ \bar\lambda \langle v,v\rangle.
\end{equation*}
Da $v \neq 0$ ist als Eigenvektor folgt also schon, dass $\bar\lambda = \lambda$ gilt und somit sind alle Eigenwerte von $F$ reell.

Da das charakteristische Polynom $P_F$ von $F$ nach dem Fundamentalsatz der Algebra in Linearfaktoren über $\C$ zerfällt und die Nullstellen die Eigenwerte von $F$ darstellen, folgt die Aussage.
````

Wenn wir die Aussagen aus Korollar {prf:ref}`cor:selbstadjungiert_hermitesch` und Lemma {prf:ref}`lem:selbstadjungiert_ew` zusammen nehmen, können wir folgern, dass alle symmetrischen und hermiteschen Matrizen nur reelle Eigenwerte besitzen.
Wir wollen diese Eigenschaft in folgendem Beispiel illustrieren.

````{prf:example}
Wir untersuchen die Eigenwerte zweier hermitescher Matrizen $A \in \mathbb{K}^{2 \times 2}$ im Folgenden.

* Sei $A \in \mathbb{C}^{2 \times 2}$ mit  
\begin{equation*}
  A \ \coloneqq \ \begin{pmatrix} 1&i\\-i&2\end{pmatrix}.
\end{equation*}
Dann ist das charakteristische Polynom gegeben durch $P_A(t) = t^2-3t +1$ dessen Nullstellen gegeben sind durch:
\begin{equation*}
\lambda_{1/2} \ = \ \frac12 (3\pm\sqrt{5})\in\R.
\end{equation*}

* Sei $A \in \mathbb{R}^{2 \times 2}$ mit  
\begin{equation*}
  A \ \coloneqq \ \begin{pmatrix} a&b\\b&c\end{pmatrix}.
\end{equation*}
Dann ist das charakteristische Polynom gegeben durch 
\begin{equation*}
P_A(t) \ = \ t^2-(a+c)t+(ac-b^2).
\end{equation*}
Die Diskriminante von $P_A$ ist in diesem Fall $(a-c)^2+4b^2\geq 0$, also sind die Eigenwerte reell.
\end{enumerate}
````

Die schönen mathematischen Eigenschaften von selbstadjungierten Endomorphismen führen dazu, dass ihre Normalform einer Diagonalmatrix entspricht wie uns folgender Satz erklärt.

````{prf:theorem} Diagonalisierungssatz
  Ist $F$ ein selbstadjungierter Endomorphismus auf einem Euklidischen bzw. unitären Vektorraum $V$, so gibt es eine Orthonormalbasis von $V$, die aus Eigenvektoren zu reellen Eigenwerten von $F$ besteht.
````

````{prf:proof}
Wir führen den Beweis mittels vollständiger Induktion über $n=\dim V$.

**Induktionsanfang: $n=1$**

Da $F$ selbstadjungiert ist, ist der einzige Eigenwert von $F$ reell.
Sei $\lambda_1 \in \mathbb{R}$ der Eigenwert von $F$ und $v_1 \in V$ der zugehörige Eigenvektor mit $||v_1|| = 1$ (durch Normalisierung).
Dann bildet $B = (v_1)$ eine Orthonormalbasis von $V$.

**Induktionsschritt: $n-1 \rightarrow n$**

Die Induktionsannahme ist, dass die Aussage bereits für den Fall $n-1$ gezeigt wurde.
Nach {prf:ref}`lem:selbstadjungiert_ew` zerfällt das charakteristische Polynom $P_F$ von $F$ in Linearfaktoren über $\R$ mit:
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
````

Wegen der Diagonalisierbarkeit eines selbstadjungierten Endomorphismus lassen sich direkt zwei Beobachtungen ableiten.

````{prf:corollary}
Ist $A\in \K^{n\times n}$ eine symmetrische bzw. hermitesche Matrix, so gibt es eine orthogonale bzw. unitäre Matrix $S \in U(n)$, so dass
\begin{equation*}
  S \cdot A \cdot S^* \ = \ \begin{pmatrix} \lambda_1&&0\\&\ddots&\\0&&\lambda_n\end{pmatrix} \qquad \text{ mit }\quad\lambda_1, \ldots, \lambda_n\in\R.
\end{equation*}
````

````{prf:proof}
Als Spalten von $S^* = S^{-1}$ verwendet man eine orthonormale Basis des $\C^n$, die aus Eigenvektoren von $A$ besteht.
````

Außerdem lässt sich aus dem Satz {prf:ref}`satz:hauptraumzerlegung` über die Hauptraumzerlegung folgende Zerlegung in orthogonale $F$-invariante Unterräume folgern.

````{prf:corollary}
Sind $\lambda_1, \ldots, \lambda_k \in \R$ die paarweise verschiedenen Eigenwerte eines selbstadjungierten oder unitären Endomorphismus $F$ von $V$, so ist
\begin{equation*}
  V \ = \ \Eig (F;\lambda_1) \, \obot \, \cdots \, \obot \, \Eig(F;\lambda_k),
\end{equation*}
wobei $\obot$ die orthogonale Summe bezeichnet.
````

Für symmetrische bzw. hermitesche Matrizen können wir die positive Definitheit mittels des folgenden Satzes am Vorzeichen der Eigenwerte ablesen.

````{prf:theorem}
:label: satz:hermitesch_positivdefinit

Für eine symmetrische bzw. hermitesche Matrix $A\in \K^{n \times n}$ sind die folgenden Bedingungen äquivalent:

$i) $A$ ist positiv definit.

$ii)$ Alle Eigenwerte $\lambda_1, \ldots, \lambda_n\in\R$ von $A$ sind positiv.
````

````{prf:proof}
Für führen den Beweis für den allgemeineren Fall von unitären Vektorräumen, da er den Euklidischen Fall mit abdeckt.

**$i)\Rightarrow ii)$:**

Sei $\lambda \in \R$ ein beliebiger Eigenwert von $A$ und $v\in\C^n$ der zugehörige Eigenvektor, so ist wegen der Eigenwertgleichung
\begin{equation*}
  Av \ = \ \lambda v \quad \Rightarrow \quad \bar{A}\bar{v} \ = \ \lambda\bar{v}\,.
\end{equation*}
Somit ist $\bar{v} \in \C^n$ offensichtlich ein Eigenvektor von $\bar{A}$ zum Eigenwert $\lambda$.
Mit $w:=\bar{v}\neq0$ folgt wegen der Hermizität von $A$
\begin{equation*}
  0 \ < \ w^TA\bar{w} \ = \ (A^Tw)^T \bar{w} \ = \ (\bar{A} w)^T\bar{w} \ = \ (\lambda w)^T\bar{w} \ = \ \lambda \cdot w^T\bar{w}\,.
\end{equation*}
und aus der positiven Definitheit des Skalarprodukts, d.h., $w^T\bar{w} > 0$, folgt $\lambda>0$.

**$ii)\Rightarrow i)$:** 

Wir wählen eine Orthonormalbasis $(w_1, \ldots, w_n)$ bestehend aus Eigenvektoren von $\bar A$, so dass $\bar Aw_i = \lambda_iw_i$ für alle $1 \leq i \leq n$.
Ähnlich wie im Beweis der ersten Folgerung erhält man
\begin{equation*}
  w_i^TA\bar w_j \ = \ \lambda_i\cdot w_i^T\bar w_j \ = \ \begin{cases}\lambda_i, &\text{für}~i=j\,,\\0, &\text{für}~i\neq j\,.\end{cases}
\end{equation*}
Jeder beliebige Vektor $v\in\C^n$ hat nun eine Darstellung aus Eigenvektoren mit $v=\sum\limits_{i=1}^n\mu_iw_i$, also ist
\begin{equation*}
  v^TAv \ = \ \sum\limits_{i=1}^n\lambda_i\mu_i\bar\mu_i \ > \ 0\quad\text{für}~v\neq0\,.
\end{equation*}
````

Abschließend wollen wir die Behauptung aus Satz {prf:ref}`satz:hermitesch_positivdefinit` an einem konkreten Beispiel nachvollziehen.

````{prf:example}
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
````
