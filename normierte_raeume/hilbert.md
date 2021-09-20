# Hilberträume

Im Folgenden führen wir den Begriff eines Hilbertraums als Spezialfall eines Banachraums ein.
Hilberträume weisen besonders viel Struktur auf, da ihre Norm durch ein Skalarprodukt induziert wird.
Daher ist es nicht verwunderlich, dass sie in vielen Theorien der Physik eine wichtige Rolle spielen, wie zum Beispiel in der Quantenmechanik.
Auch im Bereich des maschinellen Lernens sind Hilberträume ein gängiges Werkzeug, wie zum Beispiel bei den sogenannten \emph{Kernel Methods} in der statistischen Lerntheorie.
\begin{definition}[Hilbertraum]
Wir nennen einen Banachraum $(X, ||\cdot||_X)$, dessen Norm durch ein Skalarprodukt induziert ist einen \emph{Hilbertraum}.
\end{definition}

Das folgende Beispiel diskutiert verschiedene Banachräume und erklärt ob es sich jeweils um einen Hilbertraum handelt oder nicht.
\begin{example}
Im Folgenden untersuchen wir Beispiele für endlich- und unendlich-dimensionale Banachräume, d.h., vollständige normierte Vektorräume, und entscheiden ob diese einen Hilbertraum darstellen.
\begin{enumerate}
\item Der Euklidische Vektorraum $\R^n$ mit $n\in\N$ ist ausgestattet mit der Euklidischen Norm
\begin{equation*}
||x||_2 \ \coloneqq \ \sqrt{\sum_{i=1}^n |x_i|^2} \ = \ \sqrt{\langle x, x \rangle}, \quad \text{ für alle } x \in \R^n
\end{equation*}
ein endlich-dimensionaler Hilbertraum.
\item Der Banachraum $(\R^n, ||\cdot||_\infty)$ ist kein Hilbertraum.
\item Der Matrizenraum $\K^{m \times n}$ der reellen oder komplexen Matrizen ausgestattet mit dem Frobenius-Skalarprodukt
\begin{equation*}
\langle A, B \rangle \ \coloneqq \ \sum_{i=1}^m\sum_{j=1}^n \bar{a}_{ij}b_{ij}, \quad \text{ für alle Matrizen } A,B \in \K^{m\times n}
\end{equation*}
ist ein endlich-dimensionaler Hilbertraum.
\item Der Banachraum $(\ell^2(\R), ||\cdot||_{\ell^2})$ der Folgen, deren Summe ihrer Quadrate endlich ist, zusammen mit der Norm
\begin{equation*}
||(x_n)_{n\in\N}||_{\ell^2} \ \coloneqq \ \sqrt{\sum_{n=1}^\infty |x_n|^2}
\end{equation*}
ist ein unendlich-dimensionaler Hilbertraum.
\item Der unendlich-dimensionale Banachraum $(\ell^1(\R), ||\cdot||_{\ell^1})$ der Folgen, deren Summe ihrer Beträge endlich ist, zusammen mit der Norm
\begin{equation*}
||(x_n)_{n\in\N}||_{\ell^1} \ \coloneqq \ \sum_{n=1}^\infty |x_n|
\end{equation*}
ist kein Hilbertraum.
\item Der Raum der skalarwertigen, quadrat-integrierbaren Funktionen $L^2$ auf einem Gebiet $\Omega \subset \R^n$ ausgestattet mit der Norm
\begin{equation*}
||f||_{L^2} \ \coloneqq \ \left(\int_\Omega |f(x)|^2 \, \mathrm{d}x\right)^{\frac{1}{2}} \ = \ \left(\int_\Omega \overline{f(x)} f(x) \, \mathrm{d}x\right)^{\frac{1}{2}} \ = \ \sqrt{\langle f, f \rangle_{L^2} }
\end{equation*}
ist ein unendlich-dimensionaler Hilbertraum.
\end{enumerate}
\end{example}
