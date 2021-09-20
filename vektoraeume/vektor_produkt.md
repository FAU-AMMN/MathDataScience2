# Das Vektorprodukt in $\mathbb{R}^3$

Im Folgenden beschäftigen wir uns mit einer ganz speziellen Abbildung in $\mathbb{R}^3$, die zum Einen aus Sicht der Geometrie sehr nützlich ist und zum Anderen in der Physik eine wichtige Rolle spielt.
Diese Abbildung wird Vektorprodukt genannt und taucht beispielsweise bei der Berechnung der Lorentzkraft im Elektromagnetismus auf oder wird für die Berechnung des Drehmoments in der klassischen Mechanik verwendet.

Das Vektorprodukt zweier Vektoren ist wie folgt definiert.
\begin{definition}[Vektorprodukt in $\mathbb{R}^3$]\label{def:vektorprodukt}
Seien $x,y \in \mathbb{R}^3$ zwei Vektoren mit $x=(x_1, x_2, x_3)^T$ und $y=(y_1, y_2, y_3)^T$. 
Dann wird das \emph{Vektorprodukt} von $x$ und $y$, auch häufig \emph{Kreuzprodukt} oder \emph{äußeres Produkt} genannt, als folgende Abbildung definiert
\begin{equation*}
\begin{split}
( \cdot \times \cdot) \colon \mathbb{R}^3 \times \mathbb{R}^3 \ &\rightarrow \ \mathbb{R}^3 \\
(x,y) \ &\mapsto \ x \times y \ \coloneqq \ \begin{pmatrix}x_2y_3 - x_3y_2\\ x_3y_1 - x_1y_3\\ x_1y_2 - x_2y_1 \end{pmatrix}.
\end{split}
\end{equation*}
\end{definition}

Wir wollen zuerst einige grundlegende Eigenschaften des Vektorprodukts in $\mathbb{R}^3$ festhalten.
\begin{lemma}[Eigenschaften des Vektorprodukts]\label{lem:vektorprodukt}
Seien $x, x', y, y' \in \mathbb{R}^3$ Vektoren und $\lambda \in \mathbb{R}$ ein Skalar.
Dann gelten folgende Eigenschaften für das Vektorprodukt:
\begin{enumerate}[i)]
\item Bilinearität:
\begin{equation*}
\begin{split}
(x + x') \times y \ &= \ x \times y + x' \times y, \quad  x \times (y + y') \ = \ x \times y + x \times y',\\
&\lambda x \times y \ = \  \lambda (x \times y) \ = \  (x \times \lambda y).
\end{split}
\end{equation*}
\item Antikommutativität:
\begin{equation*}
x \times y \ = \ - y \times x.
\end{equation*}
\item Alternierende Abbildung:
\begin{equation*}
x \times y \ = \ \vec{0} \quad \Leftrightarrow \quad x \text{ und } y \text{ sind linear abhängig}.
\end{equation*}
\end{enumerate}
\end{lemma}
\begin{proof}
Man kann die Eigenschaften des Vektorprodukts durch Anwendung der Definition direkt nachrechnen.
Daher verzichten wir an dieser Stelle auf einen Beweis.
Es sei jedoch angemerkt, dass man sowohl aus Eigenschaft $ii)$ als auch Eigenschaft $iii)$ des Vektorprodukts folgern kann, dass $x \times x = \vec{0}$ gilt.
\end{proof}

Es gibt außerdem einen engen Zusammenhang zwischen dem Vektorprodukt in $\mathbb{R}^3$ und dem kanonischen Skalarprodukt aus Kapitel \ref{s:skalarprodukt_r}, wie die folgenden Rechenregeln zeigen.
\begin{lemma}\label{lem:vektorprodukt_skalarprodukt}
Seien $x,y,z \in \mathbb{R}^3$ Vektoren, dann gelten die folgenden Rechenregeln für das Vektorprodukt in $\mathbb{R}^3$:
\begin{enumerate}[i)]
\item $\langle x \times y, z \rangle \ = \ \det
\begin{pmatrix}
x_1 & x_2 & x_3 \\
y_1 & y_2 & y_3 \\
z_1 & z_2 & z_3 
\end{pmatrix}$,
\item $\langle x \times y, x \rangle \ = \ \langle x \times y, y \rangle \ = \ 0$,
\item $||x \times y||^2 \ = \ ||x||^2\cdot ||y||^2 - \langle x, y \rangle^2$,
\item $||x \times y||^2\ = \ ||x||^2\cdot ||y||^2 \cdot (\sin \measuredangle (x,y))^2$.
\end{enumerate}
\end{lemma}
\begin{proof}
In der Hausaufgabe zu zeigen.

Abschließend wollen wir das Vektorprodukt für zwei Beispiele berechnen.
\begin{bsp}
Seien $x, y \in \mathbb{R}^3$ Vektoren für die wir im Folgenden das Kreuzprodukt berechnen wollen.
\begin{enumerate}
\item Seien die Vektoren $x$ und $y$ gegeben als
\begin{equation*}
x \ \coloneqq \ 
\begin{pmatrix}
1 \\ 2 \\ 1
\end{pmatrix},\qquad
y \ \coloneqq \ 
\begin{pmatrix}
-1 \\ 0 \\ 2
\end{pmatrix}.
\end{equation*}
Wir berechnen das Vektorprodukt $x \times y$ von $x$ und $y$ als
\begin{equation*}
x \times y \ = \ 
\begin{pmatrix}
x_2y_3 - x_3y_2\\
x_3y_1 - x_1y_3\\
x_1y_2 - x_2y_1
\end{pmatrix} 
\ = \ 
\begin{pmatrix}
2\cdot2 - 1\cdot 0\\
1\cdot (-1) - 1\cdot 2\\
1\cdot0 - 2\cdot (-1)
\end{pmatrix}
\ = \ 
\begin{pmatrix}
4\\
-3\\
2
\end{pmatrix}
\ \eqqcolon \ z.
\end{equation*}
Wir verifizieren, dass das Vektorprodukt $x \times y \eqqcolon z$ orthogonal zu $x$ und $y$ steht.
\begin{equation*}
\begin{split}
\langle x, z \rangle \ = \ (1, 2, 1) \cdot 
\begin{pmatrix}
4\\
-3\\
2
\end{pmatrix}
\ = \ 1\cdot 4 + 2\cdot(-3) + 1\cdot 2 \ = \ 4-6+2 \ = \ 0,\\
\langle y, z \rangle \ = \ (-1, 0, 2) \cdot 
\begin{pmatrix}
4\\
-3\\
2
\end{pmatrix}
\ = \ (-1)\cdot 4 + 0\cdot(-3) + 2\cdot 2 \ = \ -4 +0 +4 \ = \ 0.
\end{split}
\end{equation*}
\item Seien die Vektoren $x$ und $y$ gegeben als
\begin{equation*}
x \ \coloneqq \ 
\begin{pmatrix}
1 \\ 2 \\ 1
\end{pmatrix},\qquad
y \ \coloneqq \ 
\begin{pmatrix}
-2 \\ -4 \\ -2
\end{pmatrix}.
\end{equation*}
Wir berechnen das Vektorprodukt $x \times y$ von $x$ und $y$ als
\begin{equation*}
x \times y \ = \ 
\begin{pmatrix}
x_2y_3 - x_3y_2\\
x_3y_1 - x_1y_3\\
x_1y_2 - x_2y_1
\end{pmatrix} 
\ = \ 
\begin{pmatrix}
2\cdot(-2) - 1\cdot(-4)\\
1\cdot (-2) - 1\cdot(-2)\\
1\cdot(-4) - 2\cdot (-2)
\end{pmatrix}
\ = \ 
\begin{pmatrix}
0\\
0\\
0
\end{pmatrix}
\ \eqqcolon \ z.
\end{equation*}
Da die Vektoren $x$ und $y$ offensichtlich linear abhängig sind ist das Vektorprodukt $x \times y = \vec{0}$.
\end{enumerate}
\end{bsp}
