# Eigenwerte und Eigenvektoren

In diesem Abschnitt definieren wir den Begriff der Eigenwerte und Eigenvektoren für Endomorphismen $F$ und deren darstellende Matrizen $A \coloneqq M_B(F)$ bezüglich einer Basis $B$ von $V$.

\begin{definition}[Eigenwert, Eigenvektor und Spektrum]\label{def:eigenwert}
Sei $F \colon V \rightarrow V$ ein Endomorphismus von $V$.
Ein Skalar $\lambda \in K$ heißt \emph{Eigenwert} von $F$, wenn ein sogenannter \emph{Eigenvektor} $v \in V, v \neq 0$ existiert, so dass
\begin{equation}\label{eq:eigenwertgleichung}
F(v) \, v \ = \ \lambda \, v.
\end{equation}
Die Menge aller Eigenwerte des Endomorphismus $F$ nennt man das \emph{Spektrum} von $F$.
\end{definition}

Die in \eqref{eq:eigenwertgleichung} gegebene \emph{Eigenwertgleichung} lässt sich ebenso für darstellende Matrizen $A \in \mathbb{K}^{n\times n}$  schreiben.
In diesem Fall interessieren wir uns für Eigenwerte und Eigenvektoren, die folgende lineare Gleichung erfüllen
\begin{equation}\label{eq:eigenwertgleichung_matrix}
A \, v \ = \ \lambda \, v.
\end{equation}

\begin{definition}[Eigenraum]
Sei $V$ ein $\mathbb{K}$-Vektorraum und sei $F \colon V \rightarrow V$ ein Endomorphismus von $V$.
Dann definieren wir den Eigenraum $\Eig(F; \lambda)$ zum Eigenwert $\lambda \in \mathbb{K}$ von $F$ als lineare Hülle der Eigenvektoren zum Eigenwert $\lambda$, d.h.
\begin{equation*}
\Eig(F; \lambda) \ = \ \Kern(F - \lambda \operatorname{id}_V ) \ = \ \lbrace v \in V \: | \: F(v) = \lambda v, v \neq \vec{0} \rbrace \cup \lbrace{\vec{0}\rbrace} \subset V.
\end{equation*}
Analog können wir den Eigenraum $\Eig(A; \lambda)$ zum Eigenwert $\lambda \in \mathbb{K}$ einer quadratischen Matrix $A \in \mathbb{K}^{n \times n}$ definieren als
\begin{equation*}
\Eig(A; \lambda) \ = \ \Kern(A - \lambda I_n ) \ = \ \lbrace v \in V \: | \: Av = \lambda v, v \neq \vec{0} \rbrace \cup \lbrace{\vec{0}\rbrace} \subset V,
\end{equation*}
wobei $I_n \in \mathbb{K}^{n \times n}$ die Einheitsmatrix bezeichnet.
\end{definition}

Wir können einen Eigenwert mittels der Dimension seines zugehörigen Eigenraums noch näher charakterisieren.

\begin{definition}[Geometrische Vielfachheit]
Wir bezeichnen mit der \emph{geometrischen Vielfachheit} eines Eigenwerts $\lambda \in \mathbb{K}$ die Dimension des zugehörigen Eigenraums $\dim \Eig(F; \lambda)$ bzw.~$\dim \Eig(A; \lambda)$.
\end{definition}

\begin{remark}
Wir bemerken, dass der Eigenraum $\Eig(F; \lambda) \subset V$ zum Eigenwert $\lambda \in \mathbb{K}$ von $F$ ein $F$-invarianter Untervektorraum von $V$ ist, da ja wegen der Eigenwertgleichung \eqref{eq:eigenwertgleichung} gelten muss
\begin{equation*}
F(v) = \lambda v \in \Eig(F; \lambda), \quad \text{ für alle } v \in \Eig(F; \lambda).
\end{equation*}
Das bedeutet, dass wenn wir $F$ auf $\Eig(F; \lambda)$ einschränken, so ist $F|_{\Eig(F; \lambda)}$ ein Endormorphismus von $\Eig(F; \lambda)$ mit 
\begin{equation*}
F|_{\Eig(F; \lambda)} \colon \Eig(F; \lambda)  \rightarrow \Eig(F; \lambda).
\end{equation*}
\end{remark}

