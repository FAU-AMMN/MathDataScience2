# Die Jordansche Normalform

An einer Triagonalmatrix können wir bereits Rang und Eigenwerte ablesen, jedoch keine weiteren charakteristischen Eigenschaften des zu Grunde liegenden Endomorphismus, wie z.B. die Dimension der Eigenräume.
Außerdem kann die obere, rechte Dreiecksmatrix voll besetzt in der oberen Hälfte sein, so dass sie für numerische Verfahren eher ungünstig ist.
Das wirkt sich vor allem bei der Potenzierung von Endomorphismen in iterativen Verfahren aus, bei der diese Mehrfachanwendung zu unerwünschten Rechenoperationen führt.
Ein weiteres Problem ist, das allgemeine Triagonalmatrizen ungeeignet sind um explizite Lösungen von Systemen linearer Differentialgleichungen anzugeben, da die Gleichungen nicht hinreichend entkoppeln in dieser Darstellung.

Es ist also ganz natürlich sich die Frage zu stellen, ob für eine gegebene trigonalisierbare Matrix $A$ eine kanonische Wahl einer oberen, rechten Dreiecksmatrix existiert, die einfach und interpretierbar aufgebaut ist und nur wenige Wahlmöglichkeiten bei der Bestimmung zulässt.
Die Frage, wie durch geschickte Wahl einer Basis $B$ von des endlich-dimensionalen Vektorraums $V$ die darstellende Matrix $M_B(F)$ des Endomorphismus $F$ auf eine möglichst einfache und eindeutige Gestalt gebracht werden kann, ist allerdings deutlich schwieriger als die bereits bekannte Triagonalisierung einer Matrix.
Diese Frage wird zentral in der Normalformentheorie von Endomorphismen behandelt.
Wie wir im Folgenden sehen werden existiert glücklicherweise eine kanonische Darstellung einer trigonalisierbaren Matrix, welche \emph{Jordansche Normalform} genannt wird, und die die gewünschten Eigenschaften hat.

Bevor wir uns jedoch mit dem Studium dieser Normalform beschäftigen führen die Definition eines nilpotenten Endomorphismus ein.
\begin{definition}[Nilpotenz]
Wir definieren den Begriff der \emph{Nilpotenz} im folgenden sowohl für Endomorphismen als auch für Matrizen.
\begin{enumerate}
\item Ein Endormorphismus $F \colon V \rightarrow V$ eines $\mathbb{K}$-Vektorraums $V$ heißt \emph{nilpotent}, falls es einen Index $k\in \mathbb{N}$ gibt, so dass $F^k =\!\!\!\!\!\!\underbrace{F \circ \ldots \circ F}_{k\text{-fache Anwendung}} \!\!\!\!\!\!= 0$ ist.\\
Der kleinste solche Index $k$ heißt dann \emph{Nilpotenzindex}.

\item  Eine Matrix $A \in \mathbb{K}^{n \times n}$ heißt \emph{nilpotent}, falls es einen Index $k\in \mathbb{N}$ gibt, so dass $A^k =\!\!\!\!\!\!\underbrace{A \cdot \ldots \cdot A}_{k\text{-fache Anwendung}} \!\!\!\!\!\!= 0$ ist.\\
Der kleinste solche Index $k$ heißt dann \emph{Nilpotenzindex}.
\end{enumerate}
\end{definition}

\begin{bsp}\label{bsp:nilpotenz}
Wir wollen im Folgenden den Nilpotenzindex zweier Matrizen durch ihre Potenzierung bestimmen.
\begin{enumerate}
\item Wir betrachten die Matrix $A \in \mathbb{R}^{3 \times 3}$  mit
\begin{equation*}
A \ \coloneqq \ 
\begin{pmatrix}
5 & -3 & 2\\
15 & -9 & 6\\
10 & -6 & 4
\end{pmatrix}.
\end{equation*}
Wir betrachten Potenzen von $A$ und erhalten:
\begin{equation*}
A^2 \ = \ 
\begin{pmatrix}
0 & 0 & 0\\
0 & 0 & 0\\
0 & 0 & 0
\end{pmatrix}.
\end{equation*}
Erstaunlicherweise ist der Nilpotenzindex der Matrix $A$ schon $k = 2$.
\item Wir betrachten die Matrix $A \in \mathbb{R}^{4 \times 4}$  mit
\begin{equation*}
A \ = \ 
\begin{pmatrix}
0 & 1 & 0 & 0\\
0 & 0 & 1 & 0\\
0 & 0 & 0 & 1\\
0 & 0 & 0 & 0
\end{pmatrix}.
\end{equation*}
Wir betrachten Potenzen von $A$ und erhalten:
\begin{equation*}
A^2 \ = \ 
\begin{pmatrix}
0 & 0 & 1 & 0\\
0 & 0 & 0 & 1\\
0 & 0 & 0 & 0\\
0 & 0 & 0 & 0
\end{pmatrix},  \quad
A^3 \ = \ 
\begin{pmatrix}
0 & 0 & 0 & 1\\
0 & 0 & 0 & 0\\
0 & 0 & 0 & 0\\
0 & 0 & 0 & 0
\end{pmatrix}, \quad
 A^4 \ = \ 
\begin{pmatrix}
0 & 0 & 0 & 0\\
0 & 0 & 0 & 0\\
0 & 0 & 0 & 0\\
0 & 0 & 0 & 0
\end{pmatrix}.
\end{equation*}
Der Nilpotenzindex der Matrix $A$ ist also $k = 4$.
\end{enumerate}
\end{bsp}

Die Matrix $A$ aus dem zweiten Beispiel \ref{bsp:nilpotenz} ist in einer besonderen Form, welche wir näher betrachten werden.
\begin{definition}[Normalform für nilpotente Matrizen]\label{def:normalform_nilpotent}
Sei $k \in \mathbb{N}, k \geq 1$, dann definieren wir eine \emph{nilpotente Matrix in Normalform} $N_k \in \mathbb{K}^{k\times k}$ durch:
\begin{equation*}
(N_k)_{i,j} \ \coloneqq \ \delta_{i,j-1} \ = \ \begin{cases}1, \quad \text{ falls } i=j-1,\\ 0, \quad \text{ sonst }.  \end{cases}
\end{equation*}
Hierbei bezeichnet $\delta_{i,j}$ das Kronecker-Delta.
Das heißt $N_k$ ist eine Matrix, die nur auf der oberen, ersten Nebendiagonale Einsen besitzt und deren sonstige Einträge alle Null sind.
Diese Normalform von nilpotenten Matrizen wird auch \emph{Jordanmatrix} genannt.
\end{definition}

Wir wollen im Folgenden einige nützliche Eigenschaften von nilpotenten Matrizen angeben.
\begin{lemma}\label{lem:dreieck_nilpotent}
Sei $A \in \mathbb{K}^{n \times n}$ eine strikte obere, rechte Dreiecksmatrix, d.h., für die Diagonalelemente gilt $a_{ii} = 0, 1 \leq i \leq n$. Dann ist $A$ nilpotent ist und besitzt einen Nilpotenzindex von $k\leq n$.
\end{lemma}
\begin{proof}
Wir beweisen die Behauptung per vollständige Induktion über die Dimension $ n $ von $ A $: \\[0.2cm]
    \textbf{Induktionsanfang $ n = 1 $:}\\[0.1cm]
    Falls $ n= 1 $, so $ A = (0) $ und $ A $ ist offensichtlich nilpotent mit Index $ 1 \leq n $.\\[0.3cm]
    \textbf{Induktionsschritt $ n-1 \rightarrow n $, $ n > 1  $:}\\[0.1cm]
    Wenn $ A \in \mathbb{K}^{n\times n } $ eine strikte obere Dreiecksmatrix ist, dann
    gibt es eine strikte obere Dreiecksmatrix $ A' \in \mathbb{K}^{(n-1)\times(n-1)} $, so dass
    \begin{equation*}
    	A = \begin{pmatrix}
             & \star \\
             A' & \vdots \\
             & \star \\
             0_{n-1} & 0
        \end{pmatrix}.
   \end{equation*}
    Hierbei kennzeichnet $ \star $ einen Eintrag, welcher nicht notwendigerweise Null ist.
    Wir sehen, dass
    \begin{equation*}
    	A^2 =
        \begin{pmatrix}
             (A')^2 & A'(\star,\dots,\star)^T \\
             0_{n-1} & 0
        \end{pmatrix}.
    \end{equation*}
    Per Induktionsvoraussetzung ist $ A' $ nilpotent mit Nilpotenzindex $ \ell \leq n-1 $.
    Wir rechnen nun
     \begin{equation*}
    	A^\ell =
        \begin{pmatrix}
             (A')^\ell & (A')^{\ell-1}(\star,\dots,\star)^T \\
             0_{n-1} & 0
        \end{pmatrix}
        =
        \begin{pmatrix}
             \mathbf{0}_{(n-1)\times(n-1)} & (A')^{\ell-1}(\star,\dots,\star)^T \\
             0_{n-1} & 0
        \end{pmatrix}.
    \end{equation*}
    Eine weitere Multiplikation mit $ A $ von links zeigt
    \begin{equation*}
    	A
        \begin{pmatrix}
             \mathbf{0}_{(n-1)\times(n-1)} & (A')^{\ell-1}(\star,\dots,\star)^T \\
             0_{n-1} & 0
        \end{pmatrix}
        =
        \begin{pmatrix}
             \mathbf{0}_{(n-1)\times(n-1)} & (A')^{\ell}(\star,\dots,\star)^T \\
             0_{n-1} & 0
        \end{pmatrix}
        =
        \mathbf{0}_{n\times n}
    \end{equation*}
    und der Nilpotenzindex von $ A $ ist höchstens $ \ell+1 \leq n $.
\end{proof}

Wir wollen im folgenden Satz Kriterien herleiten, die aussagen wann eine obere, rechte Dreiecksmatrix nilpotent ist.
\begin{satz}\label{satz:nilpotent_eigenschaften}
Sei $A \in \mathbb{K}^{n\times n}$ eine obere, rechte Dreiecksmatrix. Dann gelten die folgenden Aussagen:
\begin{enumerate}[i)]
\item $A$ ist genau dann nilpotent, wenn alle Diagonalelemente $a_{ii}, 1\leq i\leq n$, gleich $0$ sind.
\item $A$ ist genau dann nilpotent und diagonalisierbar, wenn $A$ die Nullmatrix $\mymathbb{0} \in \mathbb{K}^{n \times n}$ ist.
\item Ist $A$ nilpotent, so hat $A$ nur den Eigenwert $0$.
\end{enumerate}
\end{satz}
\begin{proof}
~\\[-0.5cm]
\begin{enumerate}[i)]
\item Man kann leicht zeigen, dass für eine obere, rechte Dreiecksmatrix $A$ stets gilt:
\begin{equation*}
A^j \ = \
\begin{pmatrix}
a_{11}^j &  & *\\
 & \ddots & \\
 0 & & a_{nn}^j
\end{pmatrix}.
\end{equation*}
Damit $A$ nilpotent ist, muss also für alle Diagonalelemente $a_{ii} = 0, 1 \leq i \leq n$, gelten.

Sei umgekehrt $A$ eine obere, rechte Dreiecksmatrix deren Diagonalelemente $a_{ii} = 0$ sind für $1 \leq i \leq n$. Dann folgt die Behauptung direkt mit Lemma \ref{lem:dreieck_nilpotent}.
\item Falls $A = 0$ die Nullmatrix ist, so ist $A$ nilpotent vom Index $1$ und trivialerweise diagonalisierbar.

Sei umgekehrt $A$ nilpotent und diagonalisierbar, dann existiert eine reguläre Matrix $S \in \GL(n; \mathbb{K})$, so dass
\begin{equation*}
S \cdot A \cdot S^{-1} \ = \
\begin{pmatrix}
\lambda_1 & & \\
& \ddots & \\
& & \lambda_n
\end{pmatrix} \ \eqqcolon \ D,
\end{equation*}
wobei $\lambda_i, 1 \leq i \leq n$, die Eigenwerte von $A$ sind.
Sei $k$ der Nilpotenzindex von $A$.
Wie man leicht einsieht gilt
\begin{equation*}
D^k \ = \ (S \cdot A \cdot S^{-1})^k \ = \ S \cdot A^k \cdot S^{-1} \ = \
\begin{pmatrix}
\lambda_1^k & & \\
& \ddots & \\
& & \lambda_n^k
\end{pmatrix}.
\end{equation*}
Da $A^k = 0$ die Nullmatrix ist, folgt schon, dass $\lambda_i = 0, 1 \leq i \leq n$, gelten muss.
Darum ist auch
\begin{equation*}
A \ = \ S^{-1} \cdot D \cdot S \ = \ 0.
\end{equation*}
\item Wir führen einen Beweis über Widerspruch. Nehmen wir an, dass die Behauptung nicht gelte, dann existiert ein Eigenwert $\lambda \neq 0$ und ein zugehörigen Eigenvektor $v \neq \vec{0}$, so dass $Av = \lambda v$.

Da $A$ nilpotent ist, existiert ein Index $k \in \mathbb{N}$, so dass $A^{k-1} \neq 0$, jedoch $A^k = 0$ gilt.
Aus der Eigenwertgleichung können wir folgern, dass
\begin{equation*}
0 \ = \ A^kv \ = \ A^{k-1} \lambda v \ = \ \lambda^k v.
\end{equation*}
Daraus folgt aber, dass $\lambda = 0$ oder $v = 0$ gilt, was zum Widerspruch führt.
\end{enumerate}
\end{proof}

Der folgende Satz sagt uns, dass wir für jeden nilpotenten Endomorphismus eine darstellende Matrix finden können, die eine strikte obere, rechte Dreiecksgestalt besitzt.
\begin{satz}\label{satz:nilpotenz}
Sei $V$ ein endlich-dimensionaler $\mathbb{K}$-Vektorraum und $F \colon V \rightarrow V$ ein nilpotenter Endomorphismus von $V$.
Dann existiert eine Basis $B$ von $V$, so dass die darstellende Matrix $M_B(F)$ von $F$ bezüglich $B$ eine obere, rechte Dreiecksmatrix mit Nullen auf der Hauptdiagonale ist, d.h.
\begin{equation*}
M_B(F) \ = \
\begin{pmatrix}
0 & & * \\
   & \ddots & \\
0 & & 0
\end{pmatrix}
\end{equation*}
und es gilt $P_F(t) = (-1)^n t^n$.
\end{satz}
\begin{proof}
Wir führen den Beweis durch Induktion über $n = \dim V$.

\textbf{Induktionsanfang: $n=1$}\\
Die Aussage ist trivialerweise erfüllt, da für einen nilpotenten Endomorphismus $F$ eines eindimensionalen Vektorraums $V$ gelten muss $F \equiv 0$.
Dadurch ist die darstellende Matrix für eine beliebige Basis $B$ von $V$ gegeben durch $M_B(F) = 0$ und das charakteristische Polynom ist dementsprechend $P_F(t) = 0-t = (-1)^1 \cdot t^1$.

\textbf{Induktionsschritt: $n-1 \rightarrow n$}\\
Die Induktionsannahme ist, dass die Aussage bereits für den Fall $n-1$ gezeigt wurde.
Sei $F$ nun ein nilpotenter Endomorphismus von $V$ mit $F \not \equiv 0$ (da ansonsten die Situation vom Induktionsanfang vorliegt).
Da nach Satz \ref{satz:nilpotent_eigenschaften} Null der einzige Eigenwert von $F$ ist wissen wir, dass $\dim \Bild(F(V)) < \dim V$ gilt und somit muss schon gelten, dass der Kern von $F$ nicht-trivial ist, d.h., $\Kern F \neq \vec{0}$.

Sei nun $v_1 \in \Kern(F), v \neq \vec{0}$. Wir ergänzen $v_1$ zu einer Basis $B' = (v_1, w_2, \ldots, w_n)$ von $V$.
Mit Hilfe des Algorithmus \ref{alg:trigonalisierung} zur Trigonalisierung einer Matrix erhalten wir also:
\begin{equation*}
M_{B'}(F) \ = \
\begin{pmatrix}
0 & a_{12} & \dots & a_{1n} \\
\vdots & & \\
\vdots & & B & \\
0 & & &
\end{pmatrix}
\end{equation*}
Da $W \coloneqq \lin(\lbrace w_2, \ldots, w_n \rbrace)$ im Allgemeinen nicht $F$-invariant ist, definieren wir die linearen Abbildungen
\begin{equation*}
H(w_j) \ = \ a_{1j} v_1 \quad \text{ und } \quad G(w_j) \ = \ a_{2j}w_2 + \ldots + a_{nj}w_n.
\end{equation*}
Dann können wir den Endomorphismus $F$ schreiben als: $F(w) = H(w) + G(w)$ für alle $w \in W$.
Bezüglich der Basis $\tilde{B}' = (w_2, \ldots, w_n)$ gilt dann $B = M_{\tilde{B}'}(G)$.
Außerdem gilt, dass $\operatorname{Bild}(H) \subset \Kern(F)$ und $G$ ist nilpotent, da auf Grund der Nilpotenz von $F$ für alle $w \in W$ gilt:
\begin{equation*}
\begin{split}
0 \ = \ F^k(w) \ &= \ F^{k-1}(F(w)) \\
&= \ F^{k-1}(H(w) + G(w)) \ = \ F^{k-1}(\lambda v_1 + G(w)) \\
&= \ F^{k-1}(G(w)) \ = \ \dots \ = \ F^{k-2}(G^2(w)) \ = \ \ldots \ = \ G^k(w).
\end{split}
\end{equation*}
Da $\dim W = \dim V - 1$ gilt, können wir auf $G$ die Induktionsvoraussetzung anwenden, d.h., es gibt eine Basis $\tilde{B} = (v_2, \ldots, v_n)$ von $W$, so dass
\begin{equation*}
M_{\tilde{B}}(G) \ = \
\begin{pmatrix}
0 & & * \\
   & \ddots & \\
0 & & 0
\end{pmatrix}
\end{equation*}
Damit folgt schon für die Basis $B = (v_1, \ldots, v_n)$ von $V$, dass
\begin{equation*}
M_B(F) \ = \
\begin{pmatrix}
0 & & * \\
   & \ddots & \\
0 & & 0
\end{pmatrix}
\end{equation*}
und das charakteristische Polynom ist dementsprechend $P_F(t) \ = \ (-1)^nt^n$.
\end{proof}

Man kann sogar noch mehr zeigen als die Aussage der vorangegangenen Sätze und Lemmata, nämlich eine vollständige Charakterisierung von nilpotenten Endomorphismen, wie der folgende Satz zeigt.
\begin{satz}\label{satz:nilpotent_charakterisierung}
Sei $F \colon V \rightarrow V$ ein Endomorphismus von $V$. Dann sind folgende Aussagen äquivalent:
\begin{enumerate}[i)]
\item $F$ ist nilpotent.
\item $F^k = 0$ für ein $k \in \mathbb{N}$.
\item Das charakterstische Polynom $P_F$ von $F$ hat die Form $P_F(t) = (-1)^n t^n$.
\item Es gibt eine Basis $B$ von $V$, so dass die darstellende Matrix $M_B(F)$ von $F$ die folgende Gestalt hat:
\begin{equation*}
M_B(F) \ = \
\begin{pmatrix}
0 & & * \\
   & \ddots & \\
0 & & 0
\end{pmatrix}
\end{equation*}
\end{enumerate}
\end{satz}
\begin{proof}
Siehe \cite[Satz 4.5.7]{fischer}
\end{proof}

\begin{remark}
Nilpotente Endomorphismen bzw. Matrizen besitzen nur den Eigenwert $\lambda = 0$, daher haben ihre darstellenden Matrizen keinen vollen Rang. Andersherum gibt es jedoch quadratische Matrizen, die nicht vollen Rang haben, jedoch nicht nilpotent sind, z.B. die Matrix
\begin{equation*}
A \ \coloneqq \
\begin{pmatrix}
1 & 1\\
0 & 0
\end{pmatrix}
\end{equation*}
mit $A^k = A$ für alle $k \in \mathbb{K}$ und den Eigenwerten $\lambda_1 = 0$ und $\lambda_2 = 1$ von $A$.
\end{remark}

Eine wichtige Erkenntnis zur Konstruktion der Jordanschen Normalform ist, dass der Kern des Endomorphismus $G \coloneqq (F - \lambda \operatorname{Id}_V)$ mit jeder Potenz von $G$ größer werden kann, wie folgendes Lemma zeigt.
\begin{lemma}\label{lem:einbettung_kern}
Sei $F \colon V \rightarrow V$ ein Endomorphismus des endlich-dimensionalen $\mathbb{K}$-Vektorraums $V$ mit Eigenwert $\lambda \in \mathbb{K}$. Dann gilt für alle $k \in \mathbb{N}$:
\begin{equation*}
\Kern(F - \lambda \operatorname{Id}_V) \ \subset \ \Kern([F - \lambda \operatorname{Id}_V]^k).
\end{equation*}
\end{lemma}
\begin{proof}
Sei $G \coloneqq (F - \lambda \operatorname{Id}_V)$. Wir müssen zeigen, dass für beliebiges $k \in \mathbb{N}$ gilt:
\begin{equation*}
v \in \Kern(G) \ \Rightarrow \ v \in \Kern(G^k), \quad \text{ für alle } v\in V.
\end{equation*}
Sei also $v \in \Kern(G)$, dann gilt offensichtlich $G v = 0$. Sei nun $k \in \mathbb{N}$ eine beliebige Potenz, dann betrachten wir
\begin{equation*}
G^k v \ = \ G^{k-1} \underbrace{G v}_{= 0} \ = \ 0.
\end{equation*}
Daraus folgt also schon, dass $v \in \Kern(G^k)$ gilt.
\end{proof}

Nach Satz \ref{satz:diagonalisierbarkeit} wissen wir, dass sich der Vektorraum $V$ genau dann in eine direkte Summe von $F$-invarianten Eigenräumen $\Eig(F; \lambda_i), i=1,\ldots,k,$ zerlegen lässt, wenn die Dimension jedes Eigenraums der algebraischen Vielfachheit $r_i \in \mathbb{N}$ der Nullstellen des charakteristischen Polynoms entspricht, d.h., 
\begin{equation*}
\dim \Eig(F; \lambda_i) \ = \ r_i, ¸\quad \text{ für } i=1,\ldots,k.
\end{equation*}
Falls die Dimension eines Eigenraums $\Eig(F; \lambda_i)$ jedoch zu klein ist, so lässt sie sich durch Potenzieren mit $r_i$ passend vergrößern, denn nach Lemma \ref{lem:einbettung_kern} gilt:
\begin{equation}\label{eq:eigenraum_potenz} 
\Eig(F; \lambda_i) \ = \ \Kern(F - \lambda_i \operatorname{Id}_V) \ \subset \ \Kern([F - \lambda_i \operatorname{Id}_V]^{r_i}).
\end{equation}

Die Einbettung in \eqref{eq:eigenraum_potenz} motiviert folgende Definition des Hauptraums.
\begin{definition}[Hauptraum und Hauptvektoren]
Sei $F \colon V \rightarrow V$ ein Endomorphismus des $\mathbb{K}$-Vektorraums $V$. 
Sei außerdem $\lambda \in \mathbb{K}$ ein Eigenwert von $F$ der algebraischen Vielfachheit $r \geq 1$.
Dann definieren wir den \emph{Hauptraum} oder \emph{verallgemeinerten Eigenraum} $\Hau(F; \lambda)$ von $F$ zum Eigenwert $\lambda$ als Kern der $r$-fachen Anwendung von $(F - \lambda \operatorname{Id}_V)$, d.h.
\begin{equation*}
\Hau(F; \lambda) \ \coloneqq \ \Kern([F - \lambda \operatorname{Id}_V]^r).
\end{equation*}

Die Vektoren $v \in \Hau(F; \lambda)$ werden \emph{Hauptvektoren} der Stufe $d \geq 1$ genannt, wenn gilt
\begin{equation*}
[F - \lambda \operatorname{Id}_V]^d (v) \ = \ 0, \quad [F - \lambda \operatorname{Id}_V]^{d-1} (v) \ \neq \ 0.
\end{equation*}
Damit ergibt sich, dass alle Eigenvektoren Hauptvektoren der Stufe $d=1$ sind.
\end{definition}

Um zu verstehen, wie sich die Potenzierung der Endomorphismen auswirkt betrachten wir einen Eigenwert $\lambda \in \mathbb{K}$ des Endomorphismus $F \colon V \rightarrow V$ und Potenzen des Endomorphimus $G \coloneqq F - \lambda \operatorname{Id}_V$.
Wir stellen fest, dass wir folgende Inklusionsketten erhalten:
\begin{align*}
\lbrace{\vec{0}\rbrace} &\subset \Kern G \subset \Kern G^2 \subset \ldots \subset \Kern G^l ,\\
V &\supset \Bild G \supset \Bild G^2 \supset \ldots \supset \Bild G^l.
\end{align*}
Außerdem gilt nach dem Dimensionssatz \cite[Satz 2.2.4]{fischer}, dass $\dim \Kern G^l + \dim \Bild G^l = \dim V$ ist.
Jedoch sind die Mengen im Allgemeinen nicht disjunkt wie bei einer direkten Summe, d.h., wir haben nicht
\begin{equation*}
\Kern G^l \cap \Bild G^l \ \neq \ \lbrace{\vec{0}\rbrace}.
\end{equation*}
Da $V$ jedoch endlich-dimensional ist, können die beiden obigen Inklusionsketten nicht beliebig auf- bzw. absteigen.

Das folgende nützliche Lemma charakterisiert die Eigenschaften dieser Inklusionsketten noch genauer.
\begin{lemma}[Lemma von Fitting]\label{lem:fitting}
Sei $G \colon V \rightarrow V$ ein Endomorphismus des $\mathbb{K}$-Vektorraums $V$.
Sei außerdem $\lambda = 0$ ein Eigenwert von $G$ mit algebraischer Vielfachheit $r \in \mathbb{N}, r \geq 1$.
Wir betrachten die kleinste Potenz $d \in \mathbb{N}$ für die der Kern von $G$ sich nicht mehr ändert, d.h.,
\begin{equation}\label{eq:fitting_index}
d \ \coloneqq \ \min\lbrace{l \in \mathbb{N} \: | \: \Kern(G^l) \, = \, \Kern(G^{l+1}) \rbrace},
\end{equation}
wobei $G^0 \coloneqq \operatorname{Id}_V$ gilt.
Dann gelten die folgenden Aussagen:
\begin{enumerate}
\item $d \, = \, \min \lbrace{l \in \mathbb{N} \: | \: \Bild(G^l) \, = \, \Bild(G^{l+1}) \rbrace}$,
\item $\Kern(G^{d+i}) = \Kern(G^{d}), \quad \Bild(G^{d+i}) = \Bild(G^{d})$ \quad für alle $i \in \mathbb{N}$,
\item Die Räume $U \coloneqq \Kern(G^d)$ und $W \coloneqq \Bild(G^d)$ sind $G$-invariant,
\item $(G|_{U})^d \ = \ 0$ \ und \ $G|_{W} \colon W \rightarrow W$ ist ein Isomorphismus,
\item $V \ = \ U \oplus W$.
\end{enumerate}
\end{lemma}
\begin{proof}
Wir nehmen an $d \in \mathbb{N}$ sei der kleinste Index mit der Eigenschaft aus \eqref{eq:fitting_index}.
Dann können wir mit der Dimensionsformel \cite[Satz 2.2.4]{fischer} folgern, dass gilt
\begin{equation*}
\begin{split}
\Kern(G^{d+1}) \, = \, \Kern(G^{d}) \ &\Leftrightarrow \ \dim(\Kern(G^{d+1})) \, = \, \dim(\Kern(G^{d})) \\
&\Leftrightarrow \ \dim(\Bild(G^{d+1})) \, = \, \dim(\Bild(G^{d})) \\
&\Leftrightarrow \ \Bild(G^{d+1}) \, = \, \Bild(G^{d}).
\end{split}
\end{equation*}
Das bedeutet schon, dass die Abbildung $G|_W$ für $W \coloneqq \Bild(G^d)$ mit
\begin{equation*}
G|_W \colon W \rightarrow \Bild(G^{d+1}) = W
\end{equation*}
ein Isomorphismus ist.
Aus dieser Beobachtung folgen schon die ersten drei Aussagen, sowie der zweite Teil der vierten Aussage.
Die Nilpotenz der Abbildung $G|_U$ mit Nilpotenzindex $d$ ist auch klar, da für alle $v \in U = \Kern(G^k)$ gilt, dass $G^d (v) = 0$  ist.

Sei nun $v \in U \cap W$, dann ist $G^d(v) = 0$ und es muss ein $w \in V$ geben, so dass $G^d(w) = v$ ist.
Setzen wir die erste Beobachtung in die zweite Beobachtung ein erhalten wir, dass auch $G^{2d}(w) = 0$ sein muss und somit gilt nach der zweiten Aussage des Lemmas, dass
\begin{equation*}
w \in \Kern(G^{2d}) = \Kern(G^{d}).
\end{equation*}
Damit folgt aber schon, dass
\begin{equation*}
0 \ = \ G^d(w) \ = \ v,
\end{equation*}
und somit gilt $V = U \oplus W$.
\end{proof}

Durch die Betrachtung von Haupträumen anstatt Eigenräumen lässt sich eine mögliche Differenz zwischen algebraischen und geometrischen Vielfachheiten der Eigenwerte eines Endomorphismus ausgleichen.
Wie wir im folgenden Satz sehen werden lässt sich der Vektorraum $V$ nun in eine innere direkte Summe der Haupträume zerlegen.
Dies war bisher nur für diagonalisierbare Endomorphismen mit Hilfe der Eigenräume in Satz \ref{satz:diagonalisierbarkeit} möglich und bringt uns einen großen Schritt in Richtung der Jordanschen Normalform voran.
\begin{satz}[Hauptraumzerlegung]\label{satz:hauptraumzerlegung}
Sei $F \colon V \rightarrow V$ ein Endomorphismus des $\mathbb{K}$-Vektorraums $V$ und sei
\begin{equation*}
P_F(t) \ = \ \pm (t - \lambda_1)^{r_1} \cdot \ldots \cdot (t  - \lambda_k)^{r_k}
\end{equation*}
das charakteristische Polynom von $F$ mit paarweisen verschiedenen $\lambda_1, \ldots, \lambda_k \in \mathbb{K}$, die die Eigenwerte von $F$ darstellen und deren algebraischen Vielfachheiten $r_i \in \mathbb{N}, r_i \geq 1$ sind.
Es sei außerdem $V_i \coloneqq \Hau(F; \lambda_i) \subset V$ für jedes $\lambda_i$ der entsprechende Hauptraum.
Dann gelten die folgenden Aussagen:
\begin{enumerate}
\item $V \ = \ V_1 \, \oplus \ldots \oplus \, V_k$
\item $F(V_i) \subset V_i$ und $\dim V_i = r_i$ für $i = 1,\ldots,k$
\item $F$ hat eine Zerlegung $F = F_D + F_N$ mit:
\begin{enumerate}[a)]
\item $F_D$ ist diagonalisierbar
\item $F_N$ ist nilpotent
\item $F_N$ und $F_D$ kommutieren, d.h., $F_D \circ F_N = F_N \circ F_D$
\end{enumerate}
\end{enumerate}
\end{satz}
\begin{proof}
Wir führen den Beweis mittels vollständiger Induktion über die Zahl $k \geq 1$ der paarweise verschiedenen Eigenwerte von $F$.
~\\[0.3cm]
\textbf{Induktionsanfang: $k=1$}\\
Für $k=1$ existiert nur ein Eigenwert $\lambda \in \mathbb{K}$ von $F$.
Das bedeutet, dass das charakteristische Polynom $P_F$ von der Form ist
\begin{equation*}
P_F(t) \ = \ \pm (t - \lambda)^n
\end{equation*}
und somit hat $\lambda$ die algebraische Vielfachheit $n = \dim(V)$.
Damit gilt für $V_1 = \Hau(F; \lambda)$ schon
\begin{equation*}
V_1 \ = \ \Kern([F - \lambda \operatorname{Id}_V]^n) \ = \ V,
\end{equation*}
da $F - \lambda \operatorname{Id}_V$ nilpotent ist mit Nilpotenzindex $k \leq n$ und wir erhalten damit die triviale Zerlegung aus der ersten Behauptung.

Da $F$ Endomorphismus ist folgt trivialerweise, dass $F(V_1) \subset V_1 = V$ und $\dim(V_1) = \dim(V) = n$ gilt, was die zweite Behauptung zeigt.

Da das charakteristische Polynom $P_F$ von $F$ in Linearfaktoren zerfällt wissen wir mit Satz \ref{satz:trigonalisierbarkeit}, dass eine Basis $B$ von $V$ existiert, so dass die darstellende Matrix $M_B(F)$ eine obere, rechte Dreiecksgestalt hat.
Wir können die darstellende Matrix dann zerlegen in $M_B(F) = D + N$, wobei $D$ eine Diagonalmatrix der Form $D = \lambda E_n$ ist und $N$ eine strikte obere, rechte Dreiecksmatrix ist.
Mit Satz \ref{satz:nilpotent_charakterisierung} wissen wir, dass $N$ nilpotent sein muss.
Eine einfache Rechnung zeigt, dass $D$ und $N$ kommutieren mit
\begin{equation*}
D \cdot N \ = \ \lambda \cdot N \ = \ N \cdot D,
\end{equation*}
womit die dritte Behauptung gezeigt ist.
~\\[0.3cm]
\textbf{Induktionsschritt: $k-1 \rightarrow k$}\\
Die Induktionsannahme ist, dass die Aussage bereits für den Fall $k-1$ gezeigt wurde.
Wir definieren uns also für den Eigenwert $\lambda_1 \in \mathbb{K}$ von $F$ mit algebraischer Vielfachheit $r_1 \in \mathbb{N}, r_1 \geq 1$ die Abbildung $G \ \coloneqq \ F - \lambda_1 \operatorname{Id}_V$. Seien $A$ eine darstellende Matrix von $G$ und $B$ eine darstellende Matrix von $F$ bezüglich einer beliebigen gemeinsamen Basis. Dann gilt offensichtlich $A = B - \lambda_1 I_n$. Damit sehen wir nun ein, dass gilt
\begin{equation*}
\begin{split}
P_G(t-\lambda_1) \ &= \ P_A(t - \lambda_1) \ = \ \det(A - (t - \lambda_1)I_n) \ \\
&= \ \det(B - \lambda_1I_n - (t - \lambda_1)I_n) \ = \ \det(B - tI_n) \ = \ P_B(t) \ = \ P_F(t),
\end{split}
\end{equation*}
womit schon folgt, dass $0$ ein Eigenwert von $G$ mit algebraischer Vielfachheit $r_1$ ist, da
\begin{equation*}
P_F(\lambda_1) \ = \ P_G(\lambda_1 - \lambda_1) \ = \ P_G(0). 
\end{equation*}
Nach dem Lemma \ref{lem:fitting} von Fitting lässt sich $V$ als direkte Summe schreiben mit
\begin{equation*}
V \ = \ \operatorname{Haupt}(F; \lambda_1) \: \oplus \: \Bild(G^{r_1}).%\Bild( [F - \lambda_1 \operatorname{Id}_V]^{r_1} ).
\end{equation*}

Für $v \in \Hau(F; \lambda_1)$ gilt, dass $[F - \lambda_1 \operatorname{Id}_V]^{r_1} (v) = 0$.
Außerdem sieht man durch die Kommutativität der Identität ein, dass 
\begin{equation}\label{eq:kommutativ_identität}
[F - \lambda_1 \operatorname{Id}_V] (F(v)) \ = \ (F^2 - \lambda_1 F)(v) \ = \ F \circ (F - \lambda_1 \operatorname{Id}_V)(v)
\end{equation}
und somit durch sukzessive Anwendung von \eqref{eq:kommutativ_identität} auch
\begin{equation*}
[F - \lambda_1 \operatorname{Id}_V]^{r_1}(F(v)) \ = \ F \circ \underbrace{[F - \lambda_1 \operatorname{Id}_V]^{r_1}(v)}_{=0} \ = \ 0.
\end{equation*}
Das zeigt, dass $F(v) \in \Hau(F; \lambda_1)$ für alle $v \in \Hau(F; \lambda_1)$, d.h, dass der Unterraum $\Hau(F; \lambda_1)$ $F$-invariant ist.

Für $v \in V$ gilt, dass $G^{r_1}(v) \eqqcolon w \in \Bild(G^{r_1})$ ist.
Außerdem sehen wir ein, dass mit $F = (G + \lambda_1 \operatorname{Id}_V)$ gilt:
\begin{equation*}
F(w) \ = \ (G + \lambda_1 \operatorname{Id}_V)(w) \ = \ G(w) + \lambda_1 w = \ G \circ G^{r_1}(v) + \lambda_1 w \ \in \Bild(G^{r_1}),
\end{equation*}
da $\Bild(G^{r_1+1}) \subset \Bild(G^{r_1})$ ist.
Das zeigt, dass $F(w) \in \Bild([F-\lambda_1 \operatorname{Id}_V]^{r_1})$ für alle $w \in \Bild([F-\lambda_1 \operatorname{Id}_V]^{r_1})$ ist, d.h., der Unterraum $\Bild([F-\lambda_1 \operatorname{Id}_V]^{r_1})$ ist auch $F$-invariant.

Betrachten wir die Einschränkung $F|_W$ von $F$ auf den Unterraum $W$ so stellen wir fest, dass das charakteristische Polynom $P_{F|_W}$ in Linearfaktoren zerfällt mit
\begin{equation*}
P_{F|_W}(t) \ = \ \pm (t - \lambda_2)^{r_2} \cdot \ldots \cdot (t - \lambda_k)^{r_k}.
\end{equation*}
Da wir nun einen Endomorphismus betrachten, der $k-1$ verschiedene Eigenwerte besitzt und dessen charakteristischen Polynom in Linearfaktoren zerfällt, können wir die Induktionsvoraussetzung anwenden.
Damit folgen direkt schon die ersten beiden Aussagen des Satzes.

Die Zerlegung aus der dritten Aussage des Satzes erhält man durch die folgenden darstellenden Matrizen in Blockdiagonalgestalt, die existieren, da der Endomorphismus $F$ trigonalisierbar ist nach Satz \ref{satz:trigonalisierbarkeit}:
\begin{equation*}
D \ \coloneqq \
\begin{pmatrix}
\lambda_1 E_{r_1} & & \\
& \ddots & \\
& & \lambda_k E_{r_k}
\end{pmatrix}, \quad
N \ \coloneqq \
\begin{pmatrix}
N_1 & & \\
& \ddots & \\
& & N_k
\end{pmatrix}.
\end{equation*}
Man kann durch Nachrechnen leicht zeigen, dass gilt:
\begin{equation*}
D \cdot N \ = \
\begin{pmatrix}
\lambda_1 N_1 & & \\
& \ddots & \\
& & \lambda_k N_k
\end{pmatrix}
\ = \ N \cdot D.
\end{equation*}
Da $N$ und $D$ die darstellenden Matrizen der Endomorphismen $F_D$ und $F_N$ sind, folgt die Kommutativität jener.
\end{proof}

Im Fall von Matrizen lässt sich die Aussage von Satz \ref{satz:hauptraumzerlegung} wie folgt formulieren. 
\begin{cor}
Sei $A \in \mathbb{K}^{n \times n}$ eine Matrix, für die das charakteristische Polynom $P_A$ in Linearfaktoren zerfällt, d.h.
\begin{equation*}
P_A(t) \ = \ \pm (t - \lambda_1)^{r_1} \cdot \ldots \cdot (t  - \lambda_k)^{r_k}.
\end{equation*}
Dann existiert eine invertierbare Matrix $S \in \GL(n; \mathbb{K})$, so dass
\begin{equation*}
SAS^{-1} \ = \
\tikz[baseline=(M.west)]{%
    \node[matrix of math nodes,matrix anchor=west,left delimiter=(,right delimiter=),ampersand replacement=\&,  minimum height=1.2cm] (M) {%
\lambda_1 I_{r_1} + N_1 \& \& 0\\
 \& \ddots \& \\
 0 \& \& \lambda_k I_{r_k} + N_k \\
  };
\node[draw,fit=(M-1-1), inner sep=-1pt, minimum height=1.6cm] {};
\node[draw,fit=(M-3-3),inner sep=-1pt, minimum height=1.6cm] {};
} \ =: \ \tilde{A}.
\end{equation*}
Jede Blockmatrix für $i=1,\ldots,k$ hat hierbei die Gestalt einer rechten oberen Dreiecksmatrix, d.h.,
\begin{equation*}
\lambda_i I_{r_i} + N_i \ = \ \begin{pmatrix} \lambda_i & & *\\ & \ddots & \\ 0 & & \lambda_i \end{pmatrix} \in \mathbb{K}^{r_i\times r_i}, \quad i=1,\ldots,k.
\end{equation*}
Insbesondere lässt sich die  Matrix $\tilde{A}$ zerlegen in $\tilde{A} = D + N$, wobei $D$ Diagonalmatrix und $N$ nilpotent ist.
Schließlich gilt außerdem, dass $D$ und $N$ kommutieren, d.h.
\begin{equation*}
D \cdot N \ = \ N \cdot D.
\end{equation*}
\end{cor}

\begin{remark}
Die in Satz \ref{satz:hauptraumzerlegung} beschriebene Zerlegung $F = F_D + F_N$ ist die einzige Zerlegung in einen diagonalisierbaren und einen nilpotenten Endomorphismus, die kommutieren.
\end{remark}


Die Hauptraumzerlegung liefert uns zwar eine Blockdiagonalmatrix, die der Gestalt einer vollbesetzten oberen, rechten Dreiecksmatrix vorzuziehen ist, jedoch geben wir uns noch nicht zufrieden mit diesem Resultat.
Bisher haben wir die nilpotenten Anteile des Endomorphismus als gegeben angesehen.
Es stellt sich jedoch heraus, dass es möglich ist diese durch geschickte Basiswahl in die Normalform einer Jordanmatrix in Definition \ref{def:normalform_nilpotent} zu überführen, wie der folgende Satz aussagt.
\begin{satz}[Normalisierung nilpotenter Endomorphismen]\label{satz:normalform_nilpotent}
Es sei $ G \in \End(V) $ nilpotent mit Nilpotenzindex $ d \in \mathbb{N} $ über einem $ \mathbb{K} $-Vektorraum $ V $.
Dann gilt
\begin{equation*}
    	\{0\}\subseteq
    	\Kern G \subseteq \Kern G^2
        \subseteq \dots \subseteq 
        \Kern G^d = V
\end{equation*}
und es gibt Koeffizienten $ s_i \in \mathbb{N}, 1 \leq i \leq d $, so dass eine Zahlpartition existiert mit
\begin{equation*}
s_1\cdot 1 + s_2\cdot 2 \dots + s_d \cdot d = n \coloneqq \Dim V.
\end{equation*}
Die Koeffizienten der Zahlpartition sind für den Endomorphismus $G$ eindeutig festgelegt durch die folgende Differenz:
\begin{equation*}
s_i \ = \ \Delta_i - \Delta_{i+1}, \quad 1 \leq i \leq d,
\end{equation*}
wobei $\Delta_i \coloneqq \dim \Kern(G_i) - \dim \Kern(G_{i-1})$ gerade die Anzahl der Hauptvektoren der Stufe $i$ sind.
%Die endliche Folge $(s_1, \ldots, s_d) \in \mathbb{N}^d)$ ist monoton 

Außerdem gibt es eine Basis $ B $ von $ V $, so dass die darstellende Matrix von $G$ bezüglich $B$ eine Blockdiagonalmatrix mit folgender Gestalt ist
\begin{equation}\label{equ:BJMF} % Block - Jordanmatrix - Form
        M_B(G)=
    	\diag\left(
          	\underset{s_d-\mathrm{mal}}{\underbrace{J_d,\dots,J_d}},
            \underset{s_{d-1}-\mathrm{mal}}{\underbrace{J_{d-1},\dots,J_{d-1}}},
        \dots\underset{s_{1}-\mathrm{mal}}{\underbrace{J_{1},\dots,J_{1}}} \right)
\end{equation}
wobei, die Matrizen $J_k$, $1 \leq k \leq d$, $k$-dimensionale Jordanmatrizen aus Definition \ref{def:normalform_nilpotent} sind mit
\begin{equation*}
      J_k \ = \ \begin{pmatrix}
        	0 & 1 &   &   & & \\
              & 0 & 1 &   & \mathbf{0} & \\
              &   & 0 & 1 \\
              & \mathbf{0}  &   &  \ddots & \ddots 
    \end{pmatrix} \in \mathbb{K}^{k \times k}.
\end{equation*}
\end{satz}
\begin{proof}
Siehe \cite[Theorem 4.6.5]{fischer}.
\end{proof}
Wir verzichten an dieser Stelle bewusst auf einen konstruktiven Beweis dieses wichtigen Satzes, da wir für ein vollständiges Verständnis viel mehr Theorie benötigen, die jedoch nicht Bestandteil dieser Vorlesung sein kann.
Diese unbefriedigende Lücke in der Normalformentheorie werden wir stattdessen mit der Diskussion eines Algorithmus zur Überführung der nilpotenten Anteile des Endomorphismus in die Normalform aus Satz \ref{satz:normalform_nilpotent} füllen.

\begin{algorithm}[Normalisierung einer nilpotenten Matrix]\label{alg:normalform_nilpotent}
Sei $B$ eine kanonische Basis des $\mathbb{K}$-Vektorraums $V$ und $A \coloneqq M_B(G)$ darstellende Matrix eines nilpotenten Endomorphismus $G \colon V \rightarrow V$ mit Nilpotenzindex $d \in \mathbb{N}$.

Um eine Transformationsmatrix $S \in \GL(\mathbb{K}; n)$ zu erhalten, so dass gilt
\begin{equation*}
N \ = \ S A S^{-1},
\end{equation*}
wobei $N$ eine Jordanmatrix ist, müssen wir geschickt Basisvektoren aus den verschiedenen Kernen der Potenzen von $G$ wählen.

\paragraph{Vorbereitung}
\begin{enumerate}
	\item Berechne Potenzen von $A$ als $A^i$ für $1 \leq i \leq d$
    \item Bestimme Basen $K_i$ der jeweiligen Kerne $\Kern(A^i)$ für $1 \leq i \leq d$
    \item Berechne die Differenzen der aufeinanderfolgenden Kerndimensionen:\\ $ \Delta_1 = \Dim\Kern(A) - \Dim\Kern(E_n)$, 
    \dots, $ \Delta_d = \Dim\Kern(A^d)-\Dim\Kern(A^{d-1}) $
\end{enumerate}
\paragraph{0. Schritt: Hauptvektoren der Stufe $d$}
	\begin{enumerate}
        \item Wähle $ s_d \coloneqq \Delta_d - \Delta_{d+1} = \Delta_d$ Hauptvektoren $ v^{(d)}_1,\dots, v_{s_d}^{(d)} $ der Stufe $d$ aus $K_d$
         %aus $ K_d $, welche linear unabhängig zu Vektoren aus $ \Kern(A^{(d-1)}) $ sind.
        \item  Notiere das Schema für den Aufbau von Jordanketten wie folgt\\[.5cm]
        \begin{tabular}{c | c | c |}
            $ v^{(d)}_1 $ & $ \dots $& $  v_{s_d}^{(d)} $ \\
            \hline
        \end{tabular}.
    \end{enumerate}

\paragraph{1. Schritt: Hauptvektoren der Stufe $d-1$}
	\begin{enumerate}
        \item Multipliziere alle Vektoren des vorigen Schritts (die unterste Zeile im Schema) mit $A$ und trage die resultierenden Vektoren
         $ A v^{(d)}_1, \dots, A v_{s_d}^{(d)} $ in eine neue Zeile \textbf{unter} das Schema ein.
        \item Ergänze um $ s_{d-1} = \Delta_{d-1}-\Delta_{d}$ Hauptvektoren
        $ v^{(d-1)}_1,\dots, v_{s_{d-1}}^{(d-1)} $ der Stufe $d-1$ aus $K_{d-1}$ und trage sie \textbf{rechts} neben die unterste Zeile des Schemas ein.
        \item Das resultierende Schema für den Aufbau von Jordanketten sollte die folgende Gestalt haben:\\[.5cm]
        \begin{tabular}{c | c | c || c | c | c |}
            $ v^{(d)}_1 $ & $ \dots $ & $ v_{s_d}^{(d)} $ & & & \\
            \hline
            $ A v^{(d)}_1 $ & $ \dots $ & $ A v_{s_d}^{(d)} $ & 
            $ v^{(d-1)}_1 $ & $ \dots $ & $ v_{s_{d-1}}^{(d-1)} $\\
            \hline
        \end{tabular}.
    \end{enumerate}

\paragraph{$i$. Schritt: Hauptvektoren der Stufe $d-i$}
	\begin{enumerate}
        \item Multipliziere alle Vektoren des vorigen Schritts (die unterste Zeile im Schema) mit $A$ und trage die resultierenden Vektoren
        in eine neue Zeile \textbf{unter} das Schema ein.
        \item Ergänze um $ s_{d-i} = \Delta_{d-i} - \Delta_{d-i+1}$ Hauptvektoren
        $ v^{(d-i)}_1,\dots, v^{(d-i)}_{s_{d-i}} $ der Stufe $d-i$ aus $K_{d-i}$ und trage sie \textbf{rechts} neben die unterste Zeile des Schemas ein.
        \item Das resultierende Schema für den Aufbau von Jordanketten sollte die folgende Gestalt haben:\\[.5cm]
        \begin{tabular}{c | c | c || c || c | c | c |}
            \vdots & \vdots & \vdots & & & &  \\
            \hline
            $ A^{i-1}v^{(d)}_1 $ & $\dots $ & $ A^{i-1}v^{(d)}_{s_d}$ & 
            $ \dots $ & & & \\
            \hline
            $ A^{i}v^{(d)}_1 $ & $ \dots $ & $ A^{i}v^{(d)}_{s_d} $ & 
            $ \dots $ & 
            $ v^{(d-
            i)}_1 $ & $ \dots $ & $ v^{(d-i)}_{s_{d-i}} $\\
            %\hline
            %$ \uparrow $ & \dots & $ \uparrow $& & & & \\
            %Jordankette & & Jordankette & & & &
        \end{tabular}.
    \end{enumerate}
    
\paragraph{$d-1$. Schritt: Hauptvektoren der Stufe $1$}
	\begin{enumerate}
        \item Multipliziere alle Vektoren des vorigen Schritts (die unterste Zeile im Schema) mit $A$ und trage die resultierenden Vektoren
        in eine neue Zeile \textbf{unter} das Schema ein.
        \item Ergänze um $ s_{1} = \Delta_{1} - \Delta_{2}$ Hauptvektoren
        $ v^{(1)}_1,\dots, v^{(1)}_{s_{1}} $ der Stufe $1$ aus $K_1 = \Eig(G; \lambda)$, also \textbf{Eigenvektoren}, und trage sie \textbf{rechts} neben die unterste Zeile des Schemas ein.
        \item Das resultierende Schema für den Aufbau von Jordanketten sollte die folgende Gestalt haben:\\[.5cm]
        \begin{tabular}{c | c | c || c || c | c | c |}
            \vdots & \vdots & \vdots & & & &  \\
            \hline
            $ A^{d-2}v^{(d)}_1 $ & $\dots $ & $ A^{d-2}v^{(d)}_{s_d}$ & 
            $ \dots $ & & & \\
            \hline
            $ A^{d-1}v^{(d)}_1 $ & $ \dots $ & $ A^{d-1}v^{(d)}_{s_d} $ & 
            $ \dots $ & 
            $ v^{(1)}_1 $ & $ \dots $ & $ v^{(1)}_{s_1} $\\
            \hline
            \hline
            $ \uparrow $ &  & $ \uparrow $& & & & \\
            \text{ Jordankette } & & \text{ Jordankette } & & & &
        \end{tabular}.
    \end{enumerate}
~\\[0.3cm]
\paragraph{Spaltenweises Eintragen des Schemas in $S^{-1}$:}~\\[0.3cm]
	Lesen wir die schließlich das fertige Schema zuerst von \textbf{unten nach oben} und dann von \textbf{links nach rechts} (entlang der Jordanketten) zellenweise ab und notieren die so gefundenen Vektoren \textbf{spaltenweise} von links nach rechts in die Transformationsmatrix $S^{-1}$, so liegt $ N = S A S^{-1} $ in der Normalform nilpotenter Endomorphismen in Definition \ref{def:normalform_nilpotent} vor.
\end{algorithm}

Durch geschickte Kombination der Hauptraumzerlegung aus Satz \ref{satz:hauptraumzerlegung} und der Normalform niolpotenter Endormorphismen in Satz \ref{satz:normalform_nilpotent} lässt sich eine kanonische Normalform für Endomorphismen bestimmen, die schöne Eigenschaften hat.
Diese \emph{Jordansche Normalform} wird im folgenden Satz näher beschrieben.
\begin{satz}[Jordansche Normalform]\label{satz:normalform_jordan}
Sei $A \in \mathbb{K}^{n \times n}$ eine Matrix, für die das charakteristische Polynom $P_A$ in Linearfaktoren zerfällt, d.h.
\begin{equation*}
P_A(t) \ = \ \pm (t - \lambda_1)^{r_1} \cdot \ldots \cdot (t  - \lambda_k)^{r_k}.
\end{equation*}
Dann existiert eine invertierbare Matrix $S \in \GL(n; \mathbb{K})$, so dass
\begin{equation}\label{eq:jordannormalform}
SAS^{-1} \ = \
\tikz[baseline=(M.west)]{%
    \node[matrix of math nodes,matrix anchor=west,left delimiter=(,right delimiter=),ampersand replacement=\&,  minimum height=1.2cm] (M) {%
\lambda_1 I_{r_1} + N_1 \& \& 0\\
 \& \ddots \& \\
 0 \& \& \lambda_k I_{r_k} + N_k \\
  };
\node[draw,fit=(M-1-1), inner sep=-1pt, minimum height=1.6cm] {};
\node[draw,fit=(M-3-3),inner sep=-1pt, minimum height=1.6cm] {};
} \ =: \ J.
\end{equation}
Die nilpotenten Anteile $N_i$ für $i=1,\ldots,k$ liegen hierbei (blockweise) in der Normalform aus Definition \ref{def:normalform_nilpotent} vor.
Die Blockmatrizen $\lambda_i I_{r_i} + N_i \in \mathbb{K}^{r_i \times r_i}$ in $J$ werden \emph{Jordanblöcke} genannt und sind von der Gestalt
\setcounter{MaxMatrixCols}{12}
\begin{equation}\label{eq:jordanblock}
\lambda_i I_{r_i} + N_i \ = \ 
\begin{pmatrix}
 \lambda_i & 1 & & & & & & & & &\\
& \ddots & \ddots & & & & & & & &\\
& & \ddots & 1 & & & & & & &\\
& & & \lambda_i & 0 & & & & & &\\
& & & & \lambda_i & 1 & & & & &\\
& & & & & \ddots & \ddots & & & &\\
& & & & & & \ddots & 1 & & &\\
& & & & & & & \lambda_i & 0 & &\\
& & & & & & & & \ddots & \ddots &\\
& & & & & & & & & \ddots & 0 \\
& & & & & & & & &  & \lambda_i \\
\end{pmatrix}
\end{equation}
Die \textbf{Anzahl der Kästchen} in einem Jordanblock der Form \eqref{eq:jordanblock} ist gegeben durch die \textbf{geometrische Vielfachheit} \, $\dim \Eig(F - \lambda_i I_n)$ des Eigenwerts $\lambda_i \in \mathbb{K}$ von $F$.
Insbesondere lässt sich die Jordansche Normalform $J$ von $A$ zerlegen in $J= D + N$, wobei $D$ Diagonalmatrix und $N$ nilpotent ist.
Schließlich gilt außerdem, dass $D$ und $N$ kommutieren, d.h.
\begin{equation*}
D \cdot N \ = \ N \cdot D.
\end{equation*}
\end{satz}
\begin{proof}
Der Beweis der Jordanschen Normalform besteht im Prinzip nur aus Anwendung der Hauptraumzerlegung aus Satz \ref{satz:hauptraumzerlegung} und dem Satz \ref{satz:normalform_nilpotent} über die Normalform für nilpotente Endomorphismen.
Wir bezeichnen für $i = 1, \ldots, k$ die Haupträume von $F$ bezüglich der Eigenwerte $\lambda_i$ mit
\begin{equation*}
V_i \ \coloneqq \ \Hau(F; \lambda_i),
\end{equation*}
und wir betrachten die nilpotenten Endomorphismen
\begin{equation*}
G_i \ \coloneqq \ (F - \lambda_i \operatorname{Id}_V)|_{V_i}.
\end{equation*}
Durch Anwendung des Satzes \ref{satz:normalform_nilpotent} können wir Basen $B_i$ der Haupträume $V_i$ finden, so dass die darstellenden Matrizen $M_{B_i}(G_i)$ der nilpotenten Endomorphismen in Normalform vorliegen.
Diese Basen kann man dann wegen der Hauptraumzerlegung in Satz \ref{satz:hauptraumzerlegung} zu einer Basis $B$ von $V$ zusammenführen, so dass die darstellende Matrix $M_B(F)$ in Jordanscher Normalform vorliegt.
\end{proof}

\begin{algorithm}[Berechnung der Jordannormalform]\label{alg:normalform_jordan}
Sei $B$ eine kanonische Basis des $\mathbb{K}$-Vektorraums $V$ und $A \coloneqq M_B(F)$ darstellende Matrix eines Endomorphismus $F \colon V \rightarrow V$, dessen charakteristisches Polynom in Linearfaktoren zerfällt von der Gestalt ist
\begin{equation*}
P_F(t) \ = \ \pm (t- \lambda_1)^{r_1} \cdot \ldots \cdot (t-\lambda_k)^r_k
\end{equation*}
für $k \in \mathbb{N}$ paarweise verschiedene Eigenwerte von $F$.

Das Ziel ist es eine Transformationsmatrix $S \in \GL(\mathbb{K}; n)$ zu konstruieren, so dass gilt
\begin{equation*}
J \ = \ S A S^{-1},
\end{equation*}
wobei $J$ die Jordannormalform aus \eqref{eq:jordannormalform} ist.

Hierfür müssen wir nur die nilpotenten Einschränkungen von $F$ auf die Haupträume $V_i \coloneqq \Hau(F; \lambda_i)$ mit 
\begin{equation*}
G_i \ \coloneqq \ (F-\lambda_i I_{r_i})|_{V_i}, \quad 1\leq i\leq k
\end{equation*}
betrachten und die nötigen Basen $B_i$ von $\Hau(F; \lambda_i)$ mit dem Algorithmus \ref{alg:normalform_nilpotent} zur Normalisierung von nilpotenten Endomorphismen berechnen.
Die Konkatenation der Basen $B_i, 1 \leq i \leq k$ ergibt wegen dem Satz zur Hauptraumzerlegung \ref{satz:hauptraumzerlegung} eine Basis des Vektorraums $V$.
Werden die Basisvektoren spaltenweise in die Transformationsmatrix $S^{-1}$ eingetragen, so erhält man unter dieser Ähnlichkeitstransformation die gewünschte Jordansche Normalform $J$ von $A$.

Diese Jordansche Normalform $J$ ist eindeutig bis auf Permutation der Jordanblöcke.
\end{algorithm}

Wir wollen ein abschließendes Beispiel zur Jordanschen Normalform für eine $(5 \times 5)$-Matrix durchrechnen.
\begin{bsp}[Berechnung der Jordanschen Normalform mit Transformationsmatrix]
Wir betrachten die Matrix
\begin{equation*}
	A\ \coloneqq \ \begin{pmatrix}
        5 & 0 & 1 & 0 & 0 \\
        0 & \frac{1}{2} & 0 & -\frac{1}{2} & 0 \\
        -1 & 0 & 3 & 0 & 0 \\
        0 & \frac{1}{2} & 0 & \frac{3}{2} & 0 \\
        0 & 0 & 0 & 0 & 4
    \end{pmatrix}
\end{equation*}
Um die Matrix $A$ in eine Jordansche Normalform zu überführen verwenden wir Algorithmus \ref{alg:normalform_nilpotent} und \ref{alg:normalform_jordan}.

Wir berechnen zuerst alle Eigenwerte von $A$ mit Hilfe des charakteristischen Polynoms:
\begin{equation*}
\begin{split}
	P_A(\lambda) \ &= \
	\det\begin{pmatrix}
        5-\lambda & 0 & 1 & 0 & 0 \\
        0 & \frac{1}{2}-\lambda & 0 & -\frac{1}{2} & 0 \\
        -1 & 0 & 3-\lambda & 0 & 0 \\
        0 & \frac{1}{2} & 0 & \frac{3}{2}-\lambda & 0 \\
        0 & 0 & 0 & 0 & 4-\lambda
    \end{pmatrix}        
    \\
    \ &= \ (-1)^{5+5}(4-\lambda)
      	\det\begin{pmatrix}
        5-\lambda & 0 & 1 & 0 \\
        0 & \frac{1}{2}-\lambda & 0 & -\frac{1}{2} \\
        -1 & 0 & 3-\lambda & 0  \\
        0 & \frac{1}{2} & 0 & \frac{3}{2}-\lambda \\
        \end{pmatrix}
    \\
    \ &= \
    (4-\lambda)\left[
      	(-1)^{4+2}\frac{1}{2}\det\begin{pmatrix}
            5-\lambda & 1 & 0 \\
            0 & 0 & -\frac{1}{2}\\
            -1 & 3-\lambda & 0
        \end{pmatrix} \right.
       \\
        &\qquad \qquad \left. + \ (-1)^{4+4}(\frac{3}{2}-\lambda)
        \det
        \begin{pmatrix}
            5-\lambda & 0 & 1 \\
            0 & \frac{1}{2}-\lambda & 0 \\
            -1 & 0 & 3-\lambda
        \end{pmatrix} \right]
     \\
    &=
    (4-\lambda) \left[
    	\frac{1}{2}(-1)^{2+3}(-\frac{1}{2})\det
        \begin{pmatrix}
            5-\lambda & 1 \\
            -1 & 3-\lambda
        \end{pmatrix} \right.
        \\
        & \qquad \qquad \left. +
        (\frac{3}{2}-\lambda)(-1)^{2+2}(\frac{1}{2}-\lambda)
        \det
        \begin{pmatrix}
            5-\lambda & 1 \\
            -1 & 3-\lambda
        \end{pmatrix}
    \right]
    \\
    &=
(4-\lambda) \left[
    	\frac{1}{4}\Bigl((5-\lambda)(3-\lambda)+1\Bigr)
        +
        (\frac{3}{2}-\lambda)(\frac{1}{2}-\lambda)\Bigl((5-\lambda)(3-\lambda)+1\Bigr)
    \right]
    \\
    &=
    (4-\lambda)\Bigl((5-\lambda)(3-\lambda)+1\Bigr)
    \left(\frac{1}{4}+(\frac{3}{2}-\lambda)(\frac{1}{2}-\lambda)\right)
    \\
    &=
    (4-\lambda)(16-8\lambda+\lambda^2)(1-2\lambda+\lambda^2)
    \\
    &=
    (4-\lambda)^3(1-\lambda)^2.
\end{split}
\end{equation*}
Es liegen somit die Eigenwerte $ \lambda_1 = 1 $ und $ \lambda_2 = 4 $ von $A$ mit den jeweiligen algebraischen Vielfachheiten $ r_1 = 2 $ und $ r_2 = 3 $ vor.

Für den \textbf{ersten Jordanblock} zum Eigenwert $\lambda_1 = 1$ von $A$ betrachten wir zunächst den Endomorphismus
\begin{equation*}
	G_1 \ \colonequals \
    A - 1 \cdot I_5
    \ = \
    \begin{pmatrix}
        4 & 0 & 1 & 0 & 0 \\
        0 & -\frac{1}{2} & 0 & -\frac{1}{2} & 0 \\
        -1 & 0 & 2  & 0 & 0 \\
        0 & \frac{1}{2} & 0 & \frac{1}{2} & 0 \\
        0 & 0 & 0 & 0 & 3
    \end{pmatrix}
\end{equation*}
und wenden Algorithmus~\ref{alg:normalform_nilpotent} zur Bestimmung einer Normalform an.\\[0.5cm]
\textbf{Vorbereitung}
~\\[0.3cm]
Wir bestimmen eine Basis $K_1$ des Eigenraums $ \Kern(G_1) $ mittels Gaußschen Eliminiationsverfahren:
\begin{align*}
    &\begin{pmatrix}
        4 & 0 & 1 & 0 & 0 \\
        0 & -\frac{1}{2} & 0 & -\frac{1}{2} & 0 \\
        -1 & 0 & 2  & 0 & 0 \\
        0 & \frac{1}{2} & 0 & \frac{1}{2} & 0 \\
        0 & 0 & 0 & 0 & 3
    \end{pmatrix}
    \overset{I + 4 \cdot III}{\mapsto}
    \begin{pmatrix}
        0 & 0 & 9 & 0 & 0 \\
        0 & -\frac{1}{2} & 0 & -\frac{1}{2} & 0 \\
        -1 & 0 & 2  & 0 & 0 \\
        0 & \frac{1}{2} & 0 & \frac{1}{2} & 0 \\
        0 & 0 & 0 & 0 & 3
    \end{pmatrix}
    \overset{I\leftrightarrow III}{\mapsto}\\
    &\begin{pmatrix}
        -1 & 0 & 2  & 0 & 0 \\
        0 & -\frac{1}{2} & 0 & -\frac{1}{2} & 0 \\
        0 & 0 & 9 & 0 & 0 \\
        0 & \frac{1}{2} & 0 & \frac{1}{2} & 0 \\
        0 & 0 & 0 & 0 & 3
    \end{pmatrix}
    \overset{IV + II}{\mapsto}
    \begin{pmatrix}
        -1 & 0 & 2  & 0 & 0 \\
        0 & -\frac{1}{2} & 0 & -\frac{1}{2} & 0 \\
        0 & 0 & 9 & 0 & 0 \\
        0 & 0 & 0 & 0 & 0 \\
        0 & 0 & 0 & 0 & 3
    \end{pmatrix}    \overset{IV\leftrightarrow V}{\mapsto}\\
    &\begin{pmatrix}
        -1 & 0 & 2  & 0 & 0 \\
        0 & -\frac{1}{2} & 0 & -\frac{1}{2} & 0 \\
        0 & 0 & 9 & 0 & 0 \\
        0 & 0 & 0 & 0 & 3\\
        0 & 0 & 0 & 0 & 0 \\
    \end{pmatrix}.
\end{align*}
Wir erhalten also als mögliche Basis
\begin{equation*}
	K_1 \ \coloneqq \ \left\{
      \begin{pmatrix}
          0 \\ 1 \\ 0 \\ -1 \\ 0
      \end{pmatrix}
    \right\}.
\end{equation*}
Da $\dim K_1 = \dim \Eig(A; 1) = 1$ gilt, wissen wir nach Satz \ref{satz:normalform_jordan}, dass es nur ein Jordankästchen innerhalb des Jordanblocks zum Eigenwert $\lambda_1 = 1$ von $A$ geben kann.
Die Größe dieses Jordankästchens entspricht in diesem Fall der algebraischen Vielfachheit $r_1 = 2$ von $\lambda_1$.

Wir bestimmen nun eine Basis $K_2$ des Eigenraums $ \Kern(G_1^2) $ mittels Gaußschen Eliminationsverfahren mit
\begin{equation*}
	G_1^2
    \ = \
    \begin{pmatrix}
        15 & 0 & 6 & 0 & 0 \\
        0 & 0 & 0& 0 & 0 \\
        -6 & 0 & 3 & 0 & 0 \\
        0 & 0 & 0 & 0 & 0 \\
        0 & 0 & 0 & 0 & 9
    \end{pmatrix}
\end{equation*}
und erhalten somit
\begin{align*}
    &\begin{pmatrix}
        15 & 0 & 6 & 0 & 0 \\
        0 & 0 & 0& 0 & 0 \\
        -6 & 0 & 3 & 0 & 0 \\
        0 & 0 & 0 & 0 & 0 \\
        0 & 0 & 0 & 0 & 9
    \end{pmatrix}
    \overset{II\leftrightarrow V \& II \leftrightarrow III}{\mapsto}
    \begin{pmatrix}
        15 & 0 & 6 & 0 & 0 \\
        -6 & 0 & 3 & 0 & 0 \\
        0 & 0 & 0 & 0 & 9\\
        0 & 0 & 0 & 0 & 0 \\
        0 & 0 & 0& 0 & 0 \\
    \end{pmatrix}
    \overset{2 \cdot I \& 5 \cdot II}{\mapsto}
    \\
    &\begin{pmatrix}
        30 & 0 & 12 & 0 & 0 \\
        0 & 0 & 0& 0 & 0 \\
        -30 & 0 & 15 & 0 & 0 \\
        0 & 0 & 0 & 0 & 0 \\
        0 & 0 & 0 & 0 & 9
    \end{pmatrix}
    \overset{II+I}{\mapsto}
    \begin{pmatrix}
        30 & 0 & 12 & 0 & 0 \\
        0 & 0 & 0& 0 & 0 \\
        0 & 0 & 27 & 0 & 0 \\
        0 & 0 & 0 & 0 & 0 \\
        0 & 0 & 0 & 0 & 9
    \end{pmatrix}.
\end{align*}
Wir erhalten somit als mögliche Basis von $\Kern(G_1^2)$
\begin{equation*}
	K_2 
    \ \coloneqq \ \left\{
      \begin{pmatrix}
          0 \\ 1\\ 0 \\ -1 \\ 0
      \end{pmatrix},
      \begin{pmatrix}
          0 \\ -1\\ 0 \\ -1 \\ 0
      \end{pmatrix}
    \right\}.
\end{equation*}
Wir haben den Nilpotenzindex von $d = 2$ von $G_1|_{\Hau(A; \lambda_1)}$ erreicht.
Das bedeutet, dass der Kern von $G_1$ sich nicht mehr ändert für jede weitere Potenz von $G_1$, da gilt
\begin{equation*}
2 \ = \ \dim \Kern(G_1^2) \ = \ \dim \Hau(A; 1) \ = \ r_1.
\end{equation*}
Entsprechend brauchen wir keine weiteren Potenzen von $ G_1 $ mehr zu betrachten.

Wir berechnen abschließend zur Vorbereitung
\begin{equation*}
\Delta_2 \, \coloneqq \, \dim K_2 - \dim K_1 \, = \, 2 - 1 \, = \, 1, \quad \Delta_1 \, \coloneqq \, \dim K_1 \, = \, 1.
\end{equation*}
~\\[0.3cm]
\paragraph{1. Schritt: Hauptvektoren der Stufe $2$}~\\[0.3cm]
Wir wählen aus dem Kern $ K_2 $ einen ($\Delta_2 = 1 $) Hauptvektor der Stufe $2$, d.h., einen Vektor der linear unabhängig zu Vektoren aus $ K_1 $ ist, also beispielsweise $  (0,-1,0,-1,0)^T $.
Wir notieren diesen Vektor in ein Schema wie folgt:\\[.5cm]
\begin{tabular}{c |}
$\begin{pmatrix}0\\-1\\0\\-1\\0\end{pmatrix}$
\\
\hline
\end{tabular}
~\\[0.3cm]
\paragraph{2. Schritt: Hauptvektoren der Stufe $1$}~\\[0.3cm]
Wir berechnen zunächst $ G_1 \cdot (0,-1,0,-1,0)^T = (0,1,0,-1,0)^T$ und tragen diesen Vektor in einer neuen Zeile unten in das Schema ein.
Wir berechnen
\begin{equation*}
s_1 \, = \, \Delta_1 - \Delta_2 \, = \, 1 - 1 \, = \, 0,
\end{equation*} 
also brauchen wir keine weiteren Vektoren hinzufügen.
Dies ist konsistent zu der Beobachtung, dass das Schema bereits $r_1 = 2$ Vektoren enthält.

Das finale Schema für den \textbf{ersten Jordanblock} sieht entsprechend so aus:\\[.5cm]
\begin{tabular}{c |}
$\begin{pmatrix}0\\-1\\0\\-1\\0\end{pmatrix}$
\\
\hline
$
\begin{pmatrix}
	0\\1\\0\\-1\\0
\end{pmatrix}
$\\
\hline
\end{tabular}
~\\[0.3cm]
Die Basis $ B_1 $ für den Hauptraum $\Hau(A; 1)$ von $A$ zum Eigenwert $\lambda_1 = 1$ ergibt sich entsprechend durch Ablesen des Schemas \emph{\glqq von unten nach oben, von links nach rechts\grqq}:
\begin{equation*}
	B_1 \ \coloneqq \ \begin{pmatrix}
        	0 & 0  \\ 1 & -1  \\ 0 & 0  \\ -1 & -1 \\ 0 & 0
        \end{pmatrix}
\end{equation*}

Für den \textbf{zweiten Jordanblock} zum Eigenwert $\lambda_1 = 4$ von $A$ betrachten wir zunächst den Endomorphismus
\begin{equation*}
	G_2 \ \colonequals \ A - 4\cdot I_5 \ = \
    \begin{pmatrix}
        1 & 0 & 1 & 0 & 0 \\
        0 & -\frac{7}{2}& 0 & -\frac{1}{2} & 0 \\
        -1 & 0 & -1 & 0 & 0 \\
        0 & \frac{1}{2} & 0 & -\frac{5}{2} & 0 \\
        0 & 0 & 0 & 0 & 0 
    \end{pmatrix}
\end{equation*}
und wenden Algorithmus~\ref{alg:normalform_nilpotent} zur Bestimmung einer Normalform an.\\[0.5cm]
\textbf{Vorbereitung}
~\\[0.3cm]
Wir bestimmen eine Basis $K_1$ des Eigenraums $ \Kern(G_2) $ mittels Gaußschen Eliminiationsverfahren:
\begin{align*}
    &\begin{pmatrix}
        1 & 0 & 1 & 0 & 0 \\
        0 & -\frac{7}{2} & 0 & -\frac{1}{2} & 0 \\
        -1 & 0 & -1 & 0 & 0 \\
        0 & \frac{1}{2} & 0 &-\frac{5}{2} & 0 \\
        0 & 0 & 0 & 0 & 0 
    \end{pmatrix}
    \overset{III+I}{\mapsto}
    \begin{pmatrix}
        1 & 0 & 1 & 0 & 0 \\
        0 & -\frac{7}{2} & 0 & -\frac{1}{2} & 0 \\
        0 & 0 & 0 & 0 & 0 \\
        0 & \frac{1}{2} & 0 & -\frac{5}{2} & 0 \\
        0 & 0 & 0 & 0 & 0 
    \end{pmatrix}
    \overset{III\leftrightarrow IV}\mapsto
    \\
    &\begin{pmatrix}
        1 & 0 & 1 & 0 & 0 \\
        0 &  -\frac{7}{2} & 0 & -\frac{1}{2} & 0 \\
        0 & \frac{1}{2} & 0 & -\frac{5}{2} & 0 \\
        0 & 0 & 0 & 0 & 0 \\
        0 & 0 & 0 & 0 & 0 
    \end{pmatrix}
    \overset{II\leftrightarrow III}{\mapsto}
    \begin{pmatrix}
        1 & 0 & 1 & 0 & 0 \\
        0 & \frac{1}{2} & 0 & -\frac{5}{2} & 0 \\
        0 & -\frac{7}{2} & 0 & -\frac{1}{2} & 0 \\
        0 & 0 & 0 & 0 & 0 \\
        0 & 0 & 0 & 0 & 0 
    \end{pmatrix}
    \overset{III + 7\cdot II}{\mapsto}
    \\
    &\begin{pmatrix}
        1 & 0 & 1 & 0 & 0 \\
        0 & \frac{1}{2} & 0 &-\frac{5}{2} & 0 \\
        0 & 0 & 0 & -18 & 0 \\
        0 & 0 & 0 & 0 & 0 \\
        0 & 0 & 0 & 0 & 0 
    \end{pmatrix}
\end{align*}
Wir erhalten also als mögliche Basis
\begin{equation*}
	K_1 \ \coloneqq \ \left\{
      \begin{pmatrix}
          1 \\ 0 \\ -1 \\ 0 \\ 0
      \end{pmatrix},
      \begin{pmatrix}
          0 \\ 0 \\ 0 \\ 0 \\ 1
      \end{pmatrix}
   \right\}.
\end{equation*}
Da $\dim K_1 = \dim \Eig(A; 4) = 2$ gilt, wissen wir nach Satz \ref{satz:normalform_jordan}, dass es zwei Jordankästchen innerhalb des Jordanblocks zum Eigenwert $\lambda_2 = 4$ von $A$ gibt.
Die Summe der Größen dieser Jordankästchen entspricht in diesem Fall der algebraischen Vielfachheit $r_2 = 3$ von $\lambda_2$.

Wir bestimmen nun eine Basis $K_2$ des Eigenraums $ \Kern(G_2^2) $ mittels Gaußschen Eliminiationsverfahren mit
\begin{equation*}
	G_2^2 \ = \
    \begin{pmatrix}
        0 & 0 & 0 & 0 & 0 \\
        0 & 12 & 0 & 3 & 0 \\
        0 & 0 & 0& 0 & 0 \\
        0 & -3 & 0 & 6 & 0 \\
        0 & 0 & 0 & 0 & 0
    \end{pmatrix}
\end{equation*}
und erhalten somit
\begin{equation*}
    \begin{pmatrix}
        0 & 0 & 0 & 0 & 0 \\
        0 & 12 & 0 & 3 & 0 \\
        0 & 0 & 0& 0 & 0 \\
        0 & -3 & 0 & 6 & 0 \\
        0 & 0 & 0 & 0 & 0
    \end{pmatrix}
    \overset{I\leftrightarrow IV}{\mapsto}
    \begin{pmatrix}
        0 & -3 & 0 & 6 & 0 \\
        0 & 12 & 0 & 3 & 0 \\
        0 & 0 & 0 & 0 & 0 \\
        0 & 0 & 0& 0 & 0 \\
        0 & 0 & 0 & 0 & 0
    \end{pmatrix}
    \overset{II + 4\cdot I}{\mapsto}
    \begin{pmatrix}
        0 & -3 & 0 & 6 & 0 \\
        0 & 0 & 0 & 27 & 0 \\
        0 & 0 & 0 & 0 & 0 \\
        0 & 0 & 0& 0 & 0 \\
        0 & 0 & 0 & 0 & 0
    \end{pmatrix}.
\end{equation*}
Wir erhalten somit als mögliche Basis von $\Kern(G_1^2)$
\begin{equation*}
	K_2 \ \coloneqq \ \left\{
      \begin{pmatrix}
          1 \\ 0 \\ 0 \\ 0 \\ 0
      \end{pmatrix},
      \begin{pmatrix}
          0 \\ 0 \\ 1 \\ 0 \\ 0
      \end{pmatrix},
      \begin{pmatrix}
          0 \\ 0 \\ 0 \\ 0 \\ 1
      \end{pmatrix}
    \right\}.
\end{equation*}
Wir haben den Nilpotenzindex von $d = 3$ von $G_2|_{\Hau(A; \lambda_2)}$ erreicht.
Das bedeutet, dass der Kern von $G_2$ sich nicht mehr ändert für jede weitere Potenz von $G_2$, da gilt
\begin{equation*}
3 \ = \ \dim \Kern(G_2^2) \ = \ \dim \Hau(A; 4) \ = \ r_2.
\end{equation*}
Entsprechend brauchen wir keine weiteren Potenzen von $ G_2 $ zu betrachten.

Wir berechnen abschließend zur Vorbereitung
\begin{equation*}
\Delta_2 \, \coloneqq \, \dim K_2 - \dim K_1 \, = \, 3 - 2 \, = \, 1, \quad \Delta_1 \, \coloneqq \, \dim K_1 \, = \, 2.
\end{equation*}
~\\[0.3cm]
\paragraph{1. Schritt: Hauptvektoren der Stufe $2$}~\\[0.3cm]
Wir wählen aus dem Kern $ K_2 $ einen ($\Delta_2 = 1 $) Hauptvektor der Stufe $2$, d.h., einen Vektor der linear unabhängig zu Vektoren aus $ K_1 $ ist, also beispielsweise $	( 1, 0 , 0 , 0 , 0)^T $.
Wir notieren diesen Vektor in ein Schema wie folgt:\\[.5cm]
\begin{tabular}{c |}
  $ \begin{pmatrix}
      1 \\ 0 \\ 0 \\ 0 \\ 0
  \end{pmatrix} $\\
  \hline
\end{tabular}
~\\[0.3cm]
\paragraph{2. Schritt: Hauptvektoren der Stufe $1$}~\\[0.3cm]
Wir berechnen zunächst $ G_2 \cdot ( 1, 0 , 0 , 0 , 0)^T  = (1,0,-1,0,0)^T $ und tragen diesen Vektor in einer neuen Zeile unten in das Schema ein.
Wir berechnen
\begin{equation*}
s_1 \, = \, \Delta_1 - \Delta_2 \, = \, 2 - 1 \, = \, 1.
\end{equation*} 
Dies bedeutet, dass wir noch einen weiteren Hauptvektor der Stufe $1$ aus $K_1$ zu unserem Schema hinzufügen müssen.
Hierzu wählen wir den Vektor $ (0,0,0,0,1)^T $.
Dies ist konsistent zu der Beobachtung, dass das Schema nun $r_2 = 3$ Vektoren enthält.

Das finale Schema für den \textbf{zweiten Jordanblock} sieht entsprechend so aus:\\[.5cm]
\begin{tabular}{c | c |}
  $ \begin{pmatrix}
      1 \\ 0 \\ 0 \\ 0 \\ 0
  \end{pmatrix} $ & \\
  \hline
  $ \begin{pmatrix} 1 \\ 0 \\ -1 \\ 0 \\ 0 \end{pmatrix} $ & 
  $\begin{pmatrix} 0 \\ 0 \\ 0 \\ 0 \\ 1 \end{pmatrix}$ \\
  \hline
\end{tabular}
~\\[0.3cm]

Die Basis $ B_2 $ für den Hauptraum $\Hau(A; 4)$ von $A$ zum Eigenwert $\lambda_2 = 4$ ergibt sich entsprechend durch Ablesen des Schemas \emph{\glqq von unten nach oben, von links nach rechts\grqq}:
\begin{equation*}
	B_2 \ \coloneqq \ 
    \begin{pmatrix}
        1 & 1 & 0 \\ 0 & 0 & 0 \\ -1 & 0 & 0 \\ 0 & 0 & 0 \\ 0 & 0 & 1
    \end{pmatrix}.
\end{equation*}

Wir fügen abschließend die beiden Basen $B_1$ und $B_2$ der zwei Haupträume zu einer Basis $B$ von $V$ zusammen und schreiben die Basisvektoren von $B$ als Spalten der Transformationsmatrix
\begin{equation*}
	S^{-1} \ \coloneqq \ 
    \begin{pmatrix}
        0 & 0 & 1 & 1 & 0 \\ 
        1 & -1 & 0 & 0 & 0 \\ 
        0 & 0 & -1 & 0 & 0 \\ 
        -1 & -1 & 0 & 0 & 0 \\ 
        0 & 0 & 0 & 0 & 1
    \end{pmatrix},
    \quad
    S \ \coloneqq \ 
    \begin{pmatrix}
        0 & \frac{1}{2} & 0 & -\frac{1}{2} & 0 \\ 
        0 & -\frac{1}{2} & 0 & -\frac{1}{2} & 0 \\ 
        0 & 0 & -1 & 0 & 0 \\ 
        1 & 0 & 1 & 0 & 0 \\ 
        0 & 0 & 0 & 0 & 1
    \end{pmatrix}.
\end{equation*}
Entsprechend erhalten wir
\begin{center}
\begin{tikzpicture}
    \matrix[matrix of math nodes,left delimiter=(,right delimiter=)] (JNF)
    {
        1 & 1 & 0 & 0 & 0 \\
        0 & 1 & 0 & 0 & 0 \\
        0 & 0 & 4 & 1 & 0 \\
        0 & 0 & 0 & 4 & 0 \\
        0 & 0 & 0 & 0 & 4 \\
    };
    \node[anchor=east,outer sep=.5cm] at (JNF.west) {$S\cdot A\cdot S^{-1}\ =\ $};
    \draw (JNF-1-1.north west) -- (JNF-1-2.north east) -- (JNF-2-2.south east) -- (JNF-2-1.south west)
    -- (JNF-1-1.north west);
    \draw (JNF-3-3.north west) -- (JNF-3-4.north east) -- (JNF-4-4.south east) -- (JNF-4-3.south west)
    -- (JNF-3-3.north west);
    \draw (JNF-5-5.north west) -- (JNF-5-5.north east) -- (JNF-5-5.south east) -- (JNF-5-5.south west)
    -- (JNF-5-5.north west);
\end{tikzpicture}
\end{center}

Wir können uns während der Bestimmung einer Jordanschen Normalform auch mittels der Jordanketten die passende Jordannormalform schon überlegen.
Zu $\Hau(A;1)$ gehört nur ein Jordankästchen der Dimension $ 2 \times 2 $ (eine Jordankette der Länge $2$). 
Zu $\Hau(A;4)$  gehört ein Jordankästchen der Dimension $ 2 \times 2 $ (eine Jordankette der Länge $2$) und eine Jordankästchen der Dimension $ 1 \times 1 $ (eine Jordankette der Länge $1$).
\end{bsp}
Glücklicherweise  existieren Algorithmen, die die obigen Berechnungen automatisiert in einem Computer durchführen und dabei mögliche Rechenfehler vermeiden und uns somit viel Zeit sparen.
