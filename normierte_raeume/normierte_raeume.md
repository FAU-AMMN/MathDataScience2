Normierte Vektorräume
============================

Sie haben in Kapitel 4 & 5{cite:p}`burger_2020` bereits die fundamentalen Konzepte von Folgen, Stetigkeit und Kompaktheit in _metrischen Räumen_ kennengelernt. Wir werden diese grundlegenden Begriffe im Folgenden durch Verwendung der Norm aus Kapitel \ref{s:skalarprodukt_r} wiederholen, weiter präzisieren und durch neue Erkenntnisse erweitern.

Die zugrunde liegende Struktur für dieses Kapitel ist ein Vektorraum auf dem eine Norm definiert ist. 
\begin{definition}[Normierter Vektorraum]
Sei $X$ ein $\mathbb{K}$-Vektorraum und sei
\begin{equation*}
|| \cdot ||_X \colon V \ \rightarrow \ \R_0^+
\end{equation*}
eine Norm auf $X$.
Dann nennen wir das Paar $(X, || \cdot ||_X)$ einen \emph{normierten Vektorraum}.
Wenn der mathematische Kontext eindeutig ist schreiben wir häufig nur $||\cdot ||$ anstatt $|| \cdot ||_X$ und $X$ anstatt dem Paar $(X, ||\cdot||_X)$.
In diesen Fällen nehmen wir immer die kanonische Norm des Vektorraums an, z.B., die Euklidische Norm für den $\mathbb{R}^n$.
\end{definition}

Zwischen Metriken und Normen gibt es einen direkten Zusammenhang, den wir kurz wiederholen wollen.
\begin{remark}
Es ist klar, dass jeder normierte Vektorraum auch ein metrischer Raum ist, da jede Norm $||\cdot||_X$ eine Metrik $d$ auf $X$ induziert durch: 
\begin{equation*}
\begin{split}
d \colon X \times X \ &\rightarrow \ \R_0^+,\\
(x,y) \ &\mapsto \ d(x,y) \, \coloneqq \, \Vert x - y \Vert_X ,\qquad \forall x,y \in X. 
\end{split}
\end{equation*}
Metriken sind jedoch viel allgemeiner und nicht alle Metriken entstehen aus Normen. 
Beispielsweise ist die geodätische Distanz (der kürzeste Weg) auf der Erdoberfläche eine Metrik, die nicht durch eine Norm induziert wird.
\end{remark}


Sie haben bereits einige Normen in Ihrem Studium kennengelernt.
Die wichtigsten Beispiele sind im Folgenden nochmal zusammengefasst.
\begin{example}
Wir können die folgenden Vektorräume mit einer Norm ausstatten.
\begin{enumerate}
\item Das Paar $(\mathbb{R}^n, ||\cdot||_p)$ mit der $p$-Norm
\begin{equation*}
\Vert x \Vert_p \ \coloneqq \ \left( \sum_{i=1}^n |x_i|^p \right)^{1/p}
\end{equation*}
ist für $1 \leq p < \infty$ ein normierter Vektorraum.
Ein wichtiger Spezialfall für $p=2$ ist der Euklidische Vektorraum. 

\item Das Paar $(\mathbb{R}^n, ||\cdot||_\infty)$ mit der Maximumsnorm
\begin{equation*}
\Vert x \Vert_\infty \ \coloneqq \ \max_{i=1,\ldots,n} |x_i|
\end{equation*}
ist ein normierter Vektorraum.

\item Sei $\ell^\infty$ der Raum der beschränkten Folgen.
Für unendliche Folgen gilt dann beispielsweise $(x_n)_{n\in\N} \coloneqq n \not\in \ell^\infty$, jedoch $(x_n)_{n\in\N} \coloneqq 1 - \frac{1}{n} \in \ell^\infty$.

Das Paar $(\ell^\infty, ||\cdot||_\infty)$ mit der Supremumsnorm 
\begin{equation*}
\Vert x \Vert_\infty \ \coloneqq \ \sup_{i \in \N} |x_i|
\end{equation*}
ist ein normierter (unendlich-dimensionaler) Vektorraum. 
\end{enumerate} 
\end{example}

Jede Norm induziert eine Metrik, welche wiederum eine Topologie auf dem Vektorraum induziert.
Hierdurch definieren sich insbesondere die fundamentalen Begriffe von offenen und abgeschlossenen Mengen in normierten Vektorräumen, wie wir im Folgenden sehen werden.
\begin{definition}[Umgebung]
Sei $X$ ein normierter Raum und $\epsilon \in \R_+$ ein positives Skalar. 
Sei außerdem $x \in X$ ein beliebiger Punkt.
Dann heisst für
$$ U_\epsilon(x) \ \coloneqq \ \{ y \in X : ||x - y|| < \epsilon \} $$
die \emph{$\epsilon$-Umgebung} von $x$. 
\end{definition} 

\begin{definition}[Offene und abgeschlossene Mengen]
Sei $X$ ein normierter Raum.
Dann definieren wir folgende Begriffe für Teilmengen von $X$:
\begin{enumerate}
\item Eine Teilmenge $M \subset X$ heißt offen, wenn für alle Punkte $x \in M$ eine $\epsilon$-Umgebung $U_\epsilon(x) \subset M$ existiert. 
\item Eine Teilmenge $M \subset X$ heißt abgeschlossen, wenn $X \setminus M$ offen ist.
\end{enumerate}
\end{definition} 

\begin{example}
Wir betrachten folgende typische Beispiele für offene und abgeschlossene Mengen in $\mathbb{R}$.
\begin{enumerate}[i)]
\item Sei $X=\R$ und $a,b \in \R$ mit $a < b$.
Dann ist das Intervall $[a,b]$ abgeschlossen und das Intervall $(a,b)$ offen. 
Die Intervalle $[a,b)$ bzw. $(a,b]$ sind weder abgeschlossen noch offen. 
\item Die leere Menge $\emptyset$ sowie der gesamte normierte Raum $X$ sind die einzigen Mengen, die sowohl abgeschlossen als auch offen sind.
\item In allgemeinen normierten Vektorräumen $X$ können wir für einen positiven Radius $r > 0$ abgeschlossene Kugeln  $B^X_r$ um einen Punkt $x\in X$ betrachten mit
\begin{equation*}
B^X_r(x) \ \coloneqq \ \{y \in X : \norm[X]{x-y} \leq r \}
\end{equation*}
Wenn der mathematische Kontext eindeutig ist, schreiben wir häufig auch nur $B_r(x)$.
\end{enumerate}
\end{example} 
