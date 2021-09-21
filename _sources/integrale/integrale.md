Integralrechnung
============================

Im letzten Semester haben Sie bereits die wichtige Klasse der Riemann-integrierbaren Funktionen Kapitel 7.1 {cite:p}`burger_2020` kennengelernt.
Wir wollen damit beginnen die wichtigsten Konzepte und Beobachtungen nochmal kurz zu wiederholen und dann nützliche Formeln für die Integralrechnung für Riemann-integrierbare Funktionen in einer Variablen herleiten.
Insbesondere werden wir die Substitutionsregel und die Partialbruchzerlegung für die Integration rationaler Funktionen einführen.
Die Berechnung von Integralen für Funktionen in mehreren Variablen werden später im Studium behandelt und in diesem Zuge wird das Riemann-Integral durch einen allgemeineren Integralbegriff (dem Lebesgue-Integral) ersetzt.

Zunächst wollen wir wiederholen, was wir unter einem unbestimmten Integral und einer Stammfunktion verstehen.

````{prf:definition} Unbestimmtes Integral und Stammfunktion
Sei $[a,b] \subset \R$ ein Intervall und $f:[a,b] \rightarrow \R$ eine integrierbare Funktion, d.h., eine Funktion die auf jedem Teilintervall $I \subset [a,b]$ integrierbar ist.
Wir nennen eine Funktion $F:[a,b] \rightarrow \R$ \emph{unbestimmtes Integral} von $f$, wenn für alle $y,z \in [a,b]$ gilt
\begin{equation*}
F\Big\vert_y^z \ \coloneqq \ F(z) - F(y) \ = \ \int_y^z f(x) \, \mathrm{d}x.
\end{equation*}
Weiterhin nennen wir $F:[a,b] \rightarrow \R$ eine \emph{Stammfunktion} von $f$, wenn $F'(x)=f(x)$ für alle $x \in [a,b]$ gilt.
````

````{prf:remark}
Wir beachten, dass wir aus Konsistenzgründen ein Integral mit vertauschten Integralgrenzen mit negativem Vorzeichen definieren, d.h.
\begin{equation*}
\int_z^y f(x)~dx \ = \ - \int_y^z f(x) \, \mathrm{d}x.
\end{equation*}
````

Wegen seiner großen Bedeutung in der Analysis wiederholen wir im Folgenden den Hauptsatz der Differential- und Integralrechnung (auch Fundamentalsatz der Analysis genannt), der im Grunde aussagt, dass Integration und Differentiation die jeweilige Umkehrung voneinander sind.
Außerdem erklärt er, dass die Begriffe Stammfunktion und unbestimmtes Integral übereinstimmen.

````{prf:theorem} Fundamentalsatz der Analysis
Sei $f \colon [a,b] \rightarrow \R$ eine stetige Funktion. Dann ist 
\begin{equation*}
\begin{split}
F_a \colon [a,b] \ &\rightarrow \ \R\\
x \ & \mapsto \ F_a(x) \ \coloneqq \ \int_a^x f(y) \, \mathrm{d}y
\end{split}
\end{equation*}
eine Stammfunktion von $f$.
Eine Funktion $F \colon [a,b] \rightarrow \R$ ist genau dann Stammfunktion von $f$, wenn $F$ ein unbestimmtes Integral ist.
````

````{prf:proof}
Siehe Satz 7.10 {cite:p}`burger_2020`.
````

````{prf:remark}
Da unbestimmte Integrale und Stammfunktionen übereinstimmen schreibt man häufig etwas unpräzise für eine Stammfunktion $F(x)$ eines Integranden $f(x)$ folgenden Zusammenhang
\begin{equation*}
\int f(x)\, \mathrm{d}x \ = \ F(x) + C,
\end{equation*}
wobei $C$ eine beliebige Integrationskonstante ist.
````

Interpretieren wir die Integration als die Umkehrung der Differentiation, dann müssen wir die uns bekannten Ableitungsregeln noch einmal betrachten, da diese mit der Integration harmonieren sollen.
Die wohl wichtigsten Regeln der Differentiation einer Funktion in einer Variablen, sind im Folgenden zusammengefasst.

````{prf:theorem} Differentiationsregeln
:label: satz:produktregel
Sei $[a,b] \subset \R$ ein Intervall und $f,g \colon [a,b] \rightarrow \R$ differenzierbare Funktionen und $c \in \R$ ein Skalar.
Dann gelten die folgenden Regeln der Differentiationsrechnung für alle $x \in [a,b]$:
\begin{align*}
  (c \cdot f)'(x) \ &= \ c\cdot f'(x), \tag{Faktorregel}\\
  (f + g)'(x) \ &= \ f(x) + g(x), \tag{Summenregel}\\
  (f\cdot g)'(x) \ &= \ f'(x)\cdot g(x) + f(x)\cdot g'(x), \tag{Produktregel}\\
   \left(\frac{f}{g}\right)'(x) \ &= \ \frac{f'(x)\cdot g(x) - f(x)\cdot g'(x)}{(g(x))^2}, \tag{Quotientenregel}\\
     (f\circ g)'(x) \ &= \ (f' \circ g)(x)\cdot g'(x). \tag{Kettenregel}
\end{align*}
````

````{prf:proof}
Siehe Satz 6.5 {cite:p}`burger_2020`.
````

Im folgenden Beispiel werden die Rechenregeln der Differentiation aus Satz \ref{satz:produktregel} angewendet.

````{prf:example}
Es seien $f,g \colon \R^+ \rightarrow \R$ stetig differenzierbare Funktionen mit
\begin{equation*}
f(x) \, \coloneqq \, \ln(x), \quad g(x) \, \coloneqq \, x^2, \quad \text{ für alle } x > 0.
\end{equation*}
Wir wollen nun die Ableitung der folgenden Kombinationen von Funktionen mit den Regeln der Differentiation berechnen.

$i)$ Wir wenden zuerst die _Produktregel_ für die Differentiation an:
\begin{equation*}
\begin{split}
(f \cdot g)'(x) \ &= \ (\ln(x) \cdot x^2)' \ = \ \ln'(x) \cdot x^2 + \ln(x) \cdot (x^2)' \ = \ \frac{1}{x} \cdot x^2 + \ln(x) \cdot 2x \\
\ &= \ x + 2x \cdot \ln(x) \ = \ x \cdot (1 + 2 \ln(x)).
\end{split}
\end{equation*}

$ii)$ Es folgt die _Quotientenregel_ für die Differentiation:
\begin{equation*}
\begin{split}
\left(\frac{f}{g}\right)'(x) \: &= \: \left( \frac{\ln}{x^2} \right)'(x) \: = \: \frac{\ln'(x)\cdot x^2 - \ln(x) (x^2)'}{(x^2)^2} \: = \: \frac{ \frac{x^2}{x} - \ln(x) \cdot 2x}{x^4} \: = \: \frac{1 - 2\ln(x)}{x^3}.
\end{split}
\end{equation*}
\item Zuletzt wenden wir die _Kettenregel_ für die Differentiation an:
\begin{equation*}
\begin{split}
(f \circ g)'(x) \ &= \ (\ln \circ~x^2)'(x) \ = \ \ln'(x^2) \cdot (x^2)' \ = \ \frac{1}{x^2} \cdot 2x \ = \ \frac{2}{x} \ = \ (2 \ln(x))'.
\end{split}
\end{equation*}
````
