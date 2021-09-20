# Trigonalisierbarkeit

Aus Kapitel \ref{s:diagonalisierbarkeit} wissen wir nun, dass ein Endomorphismus genau dann diagonalisierbar ist, wenn das zugehörige charakteristische Polynom in Linearfaktoren über $\mathbb{K}$ zerfällt und die algebraischen und geometrischen Vielfachheiten der Eigenwerte übereinstimmen.
Das Beispiel \ref{bsp:diagonalisierung_gegenbeispiele} hat uns jedoch gezeigt, dass es sehr wohl Matrizen gibt deren charakteristisches Polynom zerfällt, jedoch nicht diagonalisierbar sind, da die Vielfachheiten der Eigenwerte nicht übereinstimmen.
Glücklicherweise werden wir im Folgenden jedoch feststellen, dass Endomorphismen, deren charakteristisches Polynom in Linearfaktoren zerfällt, zumindest ähnlich zu einer oberen, rechten Dreiecksmatrix sind.

\begin{definition}[Trigonalisierbarkeit]
Wir definieren den Begriff der \emph{Trigonalisierbarkeit} im Folgenden sowohl für Endomorphismen als auch für Matrizen.
\begin{enumerate}
\item Ein Endomorphismus $F$ von $V$ heißt \emph{trigonalisierbar}, wenn es eine Basis $B$ von $V$ gibt, so dass die darstellende Matrix $M_B(F)$ von $F$ bezüglich $B$ eine obere, rechte Dreiecksmatrix ist.
\item Eine Matrix $A \in \mathbb{K}^{n\times n}$ heißt \emph{trigonalisierbar}, wenn sie ähnlich zu einer oberen, rechten Dreiecksmatrix ist.
\end{enumerate}
\end{definition}


Es ist klar, dass wenn eine Matrix $A$ trigonalisierbar ist, so stehen auf der oberen, rechten Dreiecksmatrix. zu der $A$ ähnlich ist, die Eigenwerte von $A$.
Der folgende Satz gibt uns ein Kriterium mit dessen Hilfe wir direkt entscheiden können, ob ein Endomorphismus trigonalisierbar ist oder nicht.
\begin{satz}[Trigonalisierungssatz]\label{satz:trigonalisierbarkeit}
Für einen Endormorphismus $F$ eines $n$-dimensionalen $\mathbb{K}$-Vektorraums $V$ sind folgende Bedingungen äquivalent:
\begin{enumerate}[i)]
\item F ist trigonalisierbar
\item Das charakteristische Polynom $P_F$ zerfällt in Linearfaktoren über $\mathbb{K}$, d.h.,
\begin{equation*}
P_F(t) \ = \ \pm (t - \lambda_1) \cdot \ldots \cdot (t - \lambda_n).
\end{equation*}
\end{enumerate}
\end{satz}
\begin{proof}
Siehe \cite[Satz 4.4.3]{fischer}
\end{proof}

\begin{cor}
Der Fundamentalsatz der Algebra \cite[Theorem 1.3.9]{fischer} besagt, dass jedes Polynom über $\mathbb{C}$ in Linearfaktoren zerfällt.
Hieraus folgt schon, dass jeder Endomorphismus von einem endlich-dimensionalen $\mathbb{C}$-Vektorraum trigonalisierbar ist.
\end{cor}

\begin{algorithm}[Trigonalisierung einer Matrix]\label{alg:trigonalisierung}
Sei $A \in \mathbb{K}^{n \times n}$ eine Matrix deren charakteristisches Polynom in Linearfaktoren zerfällt, d.h.,
\begin{equation*}
P_A(t) \ = \ (t - \lambda_1)\cdot \ldots \cdot (t - \lambda_n),
\end{equation*}
wobei die Eigenwerte $\lambda_1, \ldots, \lambda_n \in \mathbb{K}$ von $A$ nicht paarweise verschieden sein müssen.
Wir versuchen nun eine Matrix $S \in \GL(n; \mathbb{K})$ zu bestimmen, so dass
\begin{equation*}
D \ = \ S A S^{-1},
\end{equation*}
wobei $D \in \mathbb{K}^{n \times n}$ eine obere, rechte Dreiecksmatrix ist.
Für diese Trigonalisierung gehen wir folgt vor:\\[0.5cm]
\newpage
\noindent\textbf{1. Schritt:}\\[0.3cm]
Wir betrachten zunächst den Vektorraum $W_1 \coloneqq \mathbb{K}^n$ mit der kanonischen Einheitsbasis $B_1$ und den Endomorphismus $A_1 \coloneqq A$.
Zunächst berechnen wir den zugehörigen Eigenvektor $v_1 \in \mathbb{K}^n$ zum Eigenvektor $\lambda_1$ von $A$.
Nach dem Basisaustauschlemma \cite[Lemma 1.5.4]{fischer} können wir ein Element der kanonischen Einheitsbasis durch $v_1$ austauschen, so dass wir immer noch eine Basis erhalten.
Das heißt, wir bestimmen einen Index $1 \leq j_1 \leq n$, so dass
\begin{equation*}
B_2 \ \coloneqq \ (v_1, e_1, \ldots, \widehat{e_{j_1}}, \ldots, e_n)
\end{equation*}
wieder eine Basis von $\mathbb{K}^n$ ist.
Hierbei bedeutet die Notation $\widehat{e_{j_1}}$, dass dieses Basiselement ausgetauscht wurde.

Wir schreiben nun die Basiselemente von $B_2$ als Spalten der Transformationsmatrix
\begin{equation*}
S_1^{-1} \ \coloneqq \ T_{B_1}^{B_2}.
\end{equation*}
Dann wird klar, dass wir die erste Spalte von $A_1$ in obere rechte Dreiecksform bringen können durch:
\begin{equation*}
A_2 \ \coloneqq \ S_1 \cdot A \cdot S_1^{-1} \ = \
\begin{pmatrix}
\lambda_1 & * & \dots & *\\
0 & & & \\
\vdots & & A_2' & \\
0 & & &
\end{pmatrix}.
\end{equation*}
~\\[0.1cm]
\textbf{2. Schritt:}\\[0.3cm]
Nun betrachten wir $W_2 \subset \mathbb{K}^n$ mit der Basis 
\begin{equation*}
B_2' \ \coloneqq \  (e_1, \ldots, \widehat{e_{j_1}}, \ldots, e_n)
\end{equation*}
und dem Endomorphismus $A_2' \colon W_2 \rightarrow W_2$.
Das charakteristische Polynom von $A_2'$ ist wegen der Determinantenregel für Blockmatrizen in Lemma \ref{lem:det_blockmatrix} gegeben durch
\begin{equation*}
P_{A_2'}(t) \ = \ (t - \lambda_2) \cdot \ldots \cdot (t - \lambda_n).
\end{equation*}
Wir berechnen zum Eigenwert $\lambda_2 \in \mathbb{K}$ wieder einen Eigenvektor $v_2 \in W_2$ und nutzen das Basisaustauschlemma, um einen Index $j_2 \neq j_1$ zu finden, für den
\begin{equation*}
B_3' \ \coloneqq \  (v_2, e_1, \ldots, \widehat{e_{j_1}}, \ldots, \widehat{e_{j_2}},  \ldots, e_n)
\end{equation*}
wieder eine Basis von $W_2$ ist.
Damit ist auch
\begin{equation*}
B_3 \ \coloneqq \  (v_1, v_2, e_1, \ldots, \widehat{e_{j_1}}, \ldots, \widehat{e_{j_2}},  \ldots, e_n)
\end{equation*}
eine Basis von $W_1 = \mathbb{K}^n$.
Schreiben wir wiederum die Basis $B_3$ als Spalten der Transformationsmatrix
\begin{equation*}
S_2^{-1} \coloneqq \ T_{B_1}^{B_3},
\end{equation*}
so erhalten wir
\begin{equation*}
A_3 \ \coloneqq \ S_2 \cdot A \cdot S_2^{-1} \ = \
\begin{pmatrix}
\lambda_1 & * & \dots & \dots & *\\
0 & \lambda_2 & * & \dots & * \\
\vdots & 0 & & & \\
\vdots & \vdots & & A_3' & \\
0 & 0 & & & 
\end{pmatrix}.
\end{equation*}
Bei der Berechnung der Matrix $S_2$ kann man ausnutzen, dass
\begin{equation*}
T_{B_1}^{B_3} \ = \ T_{B_1}^{B_2} \cdot T_{B_2}^{B_3}, \quad \text{ wobei } \ T_{B_2}^{B_3} \ \coloneqq \
\begin{pmatrix}
1 & 0 & \dots &0 \\
0 & & &\\
\vdots & & T_{B_2'}^{B_3'} &\\
0 & & & 
\end{pmatrix}
\end{equation*}
Spätestens nach $(n-1)$ Schritten erhält man eine obere, rechte Dreiecksmatrix, da $A_n'$ eine $(1 \times 1)$-Matrix ist.
Insgesamt erhalten wir also eine zu $A$ ähnliche obere, rechte Dreiecksmatrix $D$ durch
\begin{equation*}
D \ \coloneqq \ A_n \ = \ S_{n-1} \cdot A \cdot S_{n-1}^{-1}.
\end{equation*}
\end{algorithm}

Das folgende Beispiel zeigt, wie Algorithmus \ref{alg:trigonalisierung} angewendet werden kann, um eine Matrix, deren charakteristisches Polynom in Linearfaktoren zerfällt, zu trigonalisieren.
\begin{bsp}\label{bsp:trigonalisierung}
Sei $A \in \mathbb{R}^{3 \times 3}$ eine quadratische Matrix, die wir trigonalisieren wollen, mit
\begin{equation*}
A \ \coloneqq \
\begin{pmatrix}
3 & 4 & 3\\
-1 & 0 & -1\\
1 & 2 & 3
\end{pmatrix}.
\end{equation*}
Wir bestimmen zuerst das charakteristische Polynom $P_A$ von $A$ als
\begin{equation*}
P_A(t) \ = \ -(t-2)^3,
\end{equation*}
also ist $\lambda = 2$ der einzige Eigenwert von $A$ mit algebraischer Vielfachheit $3$.
Das charakteristische Polynom zerfällt offensichtlich in Linearfaktoren und nach Satz \ref{satz:trigonalisierbarkeit} wissen wir folglich, dass $A$ trigonalisierbar ist.

Wir betrachten den Eigenraum $\Eig(A; 2)$ von $A$ durch Bestimmung von $\Kern(A - 2\cdot I_3)$ als
\begin{equation*}
\Eig(A; 2) \ = \ \Kern(A - 2 \cdot I_3) \ = \ \Kern
\begin{pmatrix}
3 - 2 & 4 & 3\\
-1 & 0 - 2 & -1\\
1 & 2 & 3 - 2
\end{pmatrix}
\ = \ \Kern
\begin{pmatrix}
1 & 4 & 3\\
-1 & -2 & -1\\
1 & 2 & 1
\end{pmatrix}.
\end{equation*}
Wir sehen direkt, dass die letzten beiden Zeilen der Matrix $(A - 2 \cdot I_3)$ linear abhängig sind und sie daher den Rang $2$ hat.
Daraus folgt mit der Dimensionsformel von Bild und Kern \cite[Satz 2.2.4]{fischer}, dass der Kern von $A-2 \cdot I_3$ die Dimension $1$ besitzt und daher der Eigenwert $\lambda = 2$ die geometrische Vielfachheit $1$ hat.
Da geometrische und algebraische Vielfachheit des Eigenwerts nicht übereinstimmen wissen wir mit Satz \ref{satz:diagonalisierbarkeit}, dass die Matrix $A$ nicht diagonalisierbar ist.
Konkret können wir den Eigenvektor $v_1 \in \mathbb{R}^3$ zum Eigenwert $\lambda = 2$ angeben als
$v_1 = (1, -1, 1)^T$.

Wir wenden nun den Algorithmus \ref{alg:trigonalisierung} an, um die Matrix $A$ zu trigonalisieren.\\[0.5cm]
\textbf{1. Schritt:}\\[0.3cm]
Wir wählen den Index $j_1 = 1$, d.h., wir tauschen den Einheitsvektor $e_1$ durch $v_1$ aus und erhalten $B_2$ als neue Basis von $W_1 = \mathbb{R}^3$ mit
\begin{equation*}
B_2 \ \coloneqq \ (v_1, e_2, e_3).
\end{equation*}
Daraus ergibt sich für die Transformationmatritzen
\begin{equation*}
S_1^{-1} \ \coloneqq \ T_{B_1}^{B_2} \ = \ 
\begin{pmatrix}
1 & 0 & 0\\
-1 & 1 & 0\\
1 & 0 & 1
\end{pmatrix},
\qquad
S_1 \ = \ 
\begin{pmatrix}
1 & 0 & 0\\
1 & 1 & 0\\
-1 & 0 & 1
\end{pmatrix}.
\end{equation*}
Damit erhalten wir für
\begin{equation*}
A_2 \ \coloneqq S_1 \cdot A \cdot S_1^{-1} \ = \
\begin{pmatrix}
2 & 4 & 3\\
0 & 4 & 2\\
0 & -2 & 0
\end{pmatrix}.
\end{equation*}
\\[0.1cm]
\textbf{2. Schritt:}\\[0.3cm]
Wir betrachten den verbleibenden Block $A_2'$ von $A_2$, der noch nicht in oberer, rechter Dreiecksgestalt ist mit
\begin{equation*}
A_2' \ \coloneqq \ 
\begin{pmatrix}
4 & 2\\
-2 & 0
\end{pmatrix}.
\end{equation*}
Wir bestimmen den Eigenvektor $v_2' \in \mathbb{R}^2$ von $A_2'$ zum Eigenwert $\lambda_2 = 2$ als $v_2' = (1, -1)^T$.
Die Basis $B'_2$ ist gegeben durch $B'_2 = (e_1, e_2)$ und wir tauschen das erste Basiselement durch den Eigenvektor $v_2'$ aus, so dass wir eine neue Basis $B_3' = (v_2', e_2)$ erhalten.
Die entsprechende Transformationsmatrix ist dann gegeben durch
\begin{equation*}
T^{B_3'}_{B_2'} \ \coloneqq \
\begin{pmatrix}
1 & 0\\
-1 & 1
\end{pmatrix}.
\end{equation*}
Bezogen auf die Basen $B_2 = (v_1, e_2, e_3)$ von $W_1$ können wir das zweite Basiselement $e_2$ durch den um $0$ erweiterten Eigenvektor $v_2'$ ersetzen und erhalten $B_3$ als neue Basis mit
\begin{equation*}
B_3 \ \coloneqq \ (v_1, v_2, e_3),
\end{equation*}
wobei $v_2 \coloneqq (0, 1, -1)^T$ ist.
Wir betten $T^{B_3'}_{B_2'}$ als unteren, rechten Block in eine Transformationsmatrix von Basis $B_2$ zur neuen Basis $B_3$ ein und erhalten
\begin{equation*}
T^{B_3}_{B_2} \ \coloneqq \ 
\begin{pmatrix}
1 & 0 & 0\\
0 & 1 & 0\\
0 & -1 & 1
\end{pmatrix}.
\end{equation*}
Damit können wir nun die globale Transformationsmatrix $S_2^{-1}$ bestimmen durch
\begin{equation*}
S_2^{-1} \ = \ S_1^{-1} \cdot T^{B_3}_{B_2} \ = \
\begin{pmatrix}
1 & 0 & 0\\
-1 & 1 & 0\\
1 & -1 & 1
\end{pmatrix},
\qquad
S_2 \ = \ 
\begin{pmatrix}
1 & 0 & 0\\
1 & 1 & 0\\
0& 1 & 1
\end{pmatrix}.
\end{equation*}
Damit erhalten wir schlussendlich eine zu $A$ ähnliche Triagonalmatrix $D$ für
\begin{equation*}
A_3 \ \coloneqq S_2 \cdot A \cdot S_2^{-1} \ = \
\begin{pmatrix}
2 & 1 & 3\\
0 & 2 & 2\\
0 & 0 & 2
\end{pmatrix} \ = \ D.
\end{equation*}
\end{bsp}


Wie wir in Beispiel \ref{bsp:trigonalisierung} gesehen haben, können wir eine trigonalisierbare Matrix zwar in eine obere, rechte Dreiecksform überführen, jedoch gibt es viele Möglichkeiten dies zu tun, abhängig von der Wahl der auszutauschenden Basiselemente in Algorithmus \ref{alg:trigonalisierung}.
Da Mathematiker im Allgemeinen allergisch auf Wahlfreiheit reagieren, wollen wir uns im Folgenden mit der Bestimmung eines kanonischen Repräsentanten für eine ähnliche obere, rechte Dreiecksmatrix beschäftigen, die besonders schöne Eigenschaft hat.

\section{Die Jordansche Normalform}
