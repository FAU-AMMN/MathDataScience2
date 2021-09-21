# Normale Endomorphismen

Zum Schluss betrachten wir noch eine weitere besondere Gruppe von Abbildungen.
Die sogenannten \emph{normalen Endomorphismen} zeichnen sich insbesondere dadurch aus, dass sie mit Ihrem adjungierten Endomorphismus kommutieren.
Hierzu betrachten wir die folgende Definition.

````{prf:definition} Normaler Endomorphismus
:label: def:endomorphismus_normal

Ist $V$ ein Euklidischer oder unitärer Vektorraum, so heißt ein Endomorphismus $F$ von $V$ \emph{normal}, wenn er mit seiner Adjungierten kommutiert, d.h.,
\begin{equation*}
F\circ F^* = F^* \circ F.
\end{equation*}
Ist $A=\operatorname{M}_{B}(F)$ eine darstellende Matrix von $F$ bezüglich einer Orthonormalbasis $B$ von $V$, so bedeutet das
\begin{equation*}
A\cdot A^* \ = \ A^* \cdot A.
\end{equation*}
````

````{prf:example}
Wir wollen im folgenden hinreichende Bedingungen für Normalität eines Endomorphismus angeben.

$i)$ Jeder unitäre Endomorphismus $F$ ist normal, da wegen $F^* = F^{-1}$ gilt
\begin{equation*}
F \circ F^* \ = \ F \circ F^{-1} \ = \ \operatorname{Id}_V \ = \ F^{-1} \circ F \ = \ F^* \circ F.
\end{equation*}

$ii)$ Jeder selbstadjungierte Endomorphismus $F$ ist normal, da wegen $F^* = F$ gilt
\begin{equation*}
F \circ F^* \ = \ F \circ F \ = \ F^2 \ = \ F \circ F \ = \ F^* \circ F.
\end{equation*}
````

Für normale Endomorphismen stellt sich heraus, dass sowohl ihr Kern (sowie ihr Bild) mit denen der adjungierten Abbildung übereinstimmen, wie folgender Satz aussagt.

````{prf:theorem}
:label: satz:kern_normal

Sei $V$ ein unitärer Vektorraum und $F \colon V \rightarrow V$ ein normaler Endomorphismus von $V$.
Dann gilt
\begin{equation*}
\Kern F^* \ = \ \Kern F \quad \text{ und } \quad \Bild F^* \ = \ \Bild F..
\end{equation*}
````

````{prf:proof}
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
````

Um die Normalform von normalen Endomorphismen zu untersuchen, beweisen wir zunächst das folgende Lemma.
````{prf:lemma}
:label: lem:normal_eigenschaften

Sei $V$ ein Euklidischer bzw. unitärer Vektorraum und $F\colon V\to V$ ein Endomorphismus.
Dann gelten die folgenden Aussagen:

$i)$ $F$ ist genau dann normal, wenn
\begin{equation*}
\langle F^*(v), F^*(w)\rangle \ = \ \langle F(v), F(w)\rangle\quad\text{für alle}~v,w\in V.
\end{equation*}

$ii)$ Ist $F$ normal, so folgt für alle $v\in V$
\begin{equation*}
    \Vert F^*(v)\Vert \ = \ \Vert F(v)\Vert.
\end{equation*}

$iii)$ Ist $F$ normal, so ist $G:=F-\lambda\operatorname{Id}_V$ für alle $\lambda\in\K$ normal.

$iv)$ Ist $F$ normal, so gilt für alle $v\in V$ und $\lambda\in\K$
\begin{equation*}
    F(v) = \lambda v\quad\Leftrightarrow\quad F^*(v) = \bar\lambda v.
\end{equation*}
````

````{prf:proof}
Die einzelnen Aussagen folgen direkt aus der Definition {prf:ref}`def:endomorphismus_normal` von normalen Endomorphismen.

**Ad $i)$** 

Ist $F$ normal, so können wir wegen $(F^*)^* = F$ und der Definition {prf:ref}`def:adjungierte` der Adjungierten folgern, dass gilt
\begin{equation*}
\langle F(v), F(w)\rangle  \ = \ \langle v, (F^*\circ F)(w)\rangle \ = \ \langle v, (F\circ F^*)(w)\rangle \ = \ \langle F^*(v), F^*(w)\rangle.
\end{equation*}

**Ad $ii)$** 

 sofort aus $i)$, da $||v|| = \sqrt{\langle v, v \rangle}$ für alle $v\in V$ gilt.

**Ad $iii)$** 

Wir leiten uns zunächst den adjungierten Endomorphismus $G^*$ von $G$ her.
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

**Ad $iv)$** 

Da $G = F - \lambda \operatorname{Id}_V$ nach iii) normal ist, können wir Satz {prf:ref}`satz:kern_normal` anwenden und erhalten damit:
\begin{equation*}
\Eig(F; \lambda) \ = \ \Kern G \ = \ \Kern G^* \ = \ \Eig(F^*; \bar\lambda).
\end{equation*}
Dies zeigt insbesondere, dass $F$ und $F^*$ die gleichen Eigenvektoren besitzen.
````

Schließlich stellen wir mit dem folgenden Satz fest, dass die Normalform von normale Endomorphismen Diagonalgestalt besitzt.

````{prf:theorem} Diagonalisierungssatz
Für einen Endomorphismus $F$ eines unitären Vektorraums $V$ sind die folgenden Eigenschaften äquivalent:

$i)$ $F$ ist normal.

$ii)$ Es gibt eine Orthonormalbasis $B$ von $V$ bestehend aus Eigenvektoren von $F$.
````

````{prf:proof}

**$i)\Rightarrow ii)$:**

Wir führen den Beweis mittels vollständiger Induktion über $n=\dim V$.

**Induktionsanfang: $n=1$**

Sei $\lambda_1 \in \mathbb{K}$ der Eigenwert von $F$ und $v_1 \in V$ der zugehörige Eigenvektor mit $||v_1|| = 1$ (durch Normalisierung).
Dann bildet $B = (v_1)$ eine Orthonormalbasis von $V$.

**Induktionsschritt: $n-1 \rightarrow n$**

Die Induktionsannahme ist, dass die Aussage bereits für den Fall $n-1$ gezeigt wurde.        
Sei $\lambda_1\in\C$ eine Nullstelle des charakteristischen Polynoms von $F$ und $v_1\in V$ ein zugehöriger Eigenvektor mit $\Vert v_1\Vert = 1$ (durch Normalisierung).
Wir definieren das orthogonale Komplement $W:=\lin(\lbrace v_1 \rbrace)^\perp\subset V$ von $v_1$.
Für jedes $w\in W$ gilt dann nach Lemma {prf:ref}`lem:normal_eigenschaften`
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

**$ii)\Rightarrow i)$:** 

Die Matrix $D:=\operatorname{M}_{B}(F)$ ist diagonal und es gilt
\begin{equation*}
\operatorname{M}_{\mathcal{B}}(F^*) \ = \ D^* \ = \ \bar D.
\end{equation*}
Da die folgende Gleichung gilt 
\begin{equation*}
D\cdot D^* \ = \ D\cdot \bar D \ = \ \bar D\cdot D \ = \ D^* \cdot D
\end{equation*}
ist $F$ normal.
````
