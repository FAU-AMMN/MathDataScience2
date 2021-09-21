# Integration rationaler Funktionen

Im Gegensatz zur Differentiation gibt es keine Aussage darüber, dass das Integral einer elementaren Funktion wieder eine elementare Funktion ergibt. Insbesondere gibt es keinen allgemein gültigen Algorithmus zur Bestimmung des Integrals, was die analytische Integration sehr schwierig macht. Im Spezialfall von rationalen Funktionen, die als Quotient zweier Polynome dargestellt werden können, kann man eine solche Rechenvorschrift erarbeiten.

## Polynomfunktionen

Bevor wir uns mit der Integration rationaler Funktionen beschäftigen können, wollen wir im Folgenden die wichtigsten Begriffe und Erkenntnisse zu Polynomen wiederholen.
Wir beginnen mit der Definition von Polynomfunktionen.

````{prf:definition} Polynomfunktion
Für den Körper $\K=\R$ oder $\K=\C$ nennen wir jede Funktion $p\colon\K\to\K$ der Form

```{math}
:label: def:poly
  p(x) \ = \ \sum_{k=0}^n a_k x^k \ = \ a_0 + a_1x + a_2x^2 + \ldots + a_nx^n \quad\text{mit}\quad a_k\in\K
```

_reelle_ oder _komplexe Polynomfunktion_ oder (ungenauerweise) häufig auch kurz _Polynom_.

Wir nennen den Koeffizienten $a_n \in \K$ mit dem höchsten Index den _Leitkoeffizienten_ des Polynoms.
Wenn der Leitkoeffizient ungleich Null ist, d.h., $a_n\neq 0$, dann sagen wir, dass $p$ ein Polynom vom _Grad_ $\deg(p) = n$ ist.
Ist der Leitkoeffizient gleich Eins, d.h, $a_n = 1$, so nennen wir das Polynom $p$ _normiert_.

Der _Ring der Polynome_ $p$ mit Koeffizienten aus dem Körper $\K$ wird häufig mit $\K[x]$ bezeichnet.
````

````{prf:remark}
:label: rem:polynome

Für Polynomfunktionen können wir folgende Beobachtungen festhalten:

$i)$ Da die Monome der Form $1, x, x^2, \ldots$ eine Basis des Polynomrings $\K[x]$ (betrachtet als Vektorraum) bilden, sind Koeffizienten $a_k \in \K$ in {eq}`def:poly` für jedes Polynom $p\in\K[x]$ eindeutig bestimmt.

$ii)$ Allgemein soll gelten, dass die Summe zweier Polynome höchstens den maximalen Grad der beiden einzelnen Polynome hat, d.h., für zwei Polynome $f,g \in \K[x]$ gilt:
\begin{equation*}
  \deg(f+g) \ \leq \ \max(\deg(f), \deg(g)).
\end{equation*}
Der Grad von $(f+g) \in \K[x]$ kann sich jedoch verringern, z.B., wenn für die Polynome $\deg(f) = \deg(g) = n$  gilt und die jeweils höchsten Koeffizienten $a_n, b_n \in \K$ sich durch $a_n = - b_n$ aufheben.

Für die Multiplikation zweier Polynome stellen wir fest, dass sich der Grad des resultierenden Polynoms als Summe der Grade der einzelnen Polynome ergibt, d.h.,
```{math}
:label: eq:polynom_grad_multi
  \deg{fg} \ = \ \deg(f) + \deg(f)\,,
```

$iii)$ Das konstante Polynom 
\begin{equation*}
\pmb{0} \colon \K\to\K
\end{equation*} 
mit $\pmb{0}(x) = 0$ für alle $x\in\K$ heißt _Nullpolynom_ und hat per Definition den Grad 
\begin{equation*}
\deg(\pmb{0}) \, \coloneqq \, -\infty.
\end{equation*}
Die Festlegung des Grades des Nullpolynoms erscheint willkürlich, kann aber durch die Rechenregeln für den Grad von Polynomen in {eq}`eq:polynom_grad_multi` gerechtfertigt werden, wenn man für beliebiges $k\in\N$ annimmt, dass $k+(-\infty) = -\infty$ gilt.
````

Lassen wir als Argumente in {eq}`def:poly` beliebige komplexe Zahlen zu, dann lässt sich ein reelles Polynom als komplexes Polynom auffassen mit der Einbettung $\R[x]\subset\C[x]$.
Wir erinnern daran, dass reelle Polynome vom Grad $\deg(p) > 0$ keine Nullstellen besitzen müssen, im Gegensatz zu komplexen Polynomen.
Der _Fundamentalsatzes der Algebra_ Theorem 1.3.9 {cite:p}`fischer` hat zur Folge, dass ein Polynom $p\in\C[x]$ vom Grad $\deg(p) = n$ sich in ein Produkt von Linearfaktoren, d.h., in Polynome von Grad Eins, zerlegen lässt, d.h.,

```{math}
:label: eq:linearfaktorzerlegung

 p(x) \ = \ \prod\limits_{i=1}^n(x-x_i).
```

Die Nullstellen $x_i \in \C$ in der Linearfaktorzerlegung {eq}`eq:linearfaktorzerlegung` müssen nicht zwingend paarweise verschieden sein.
Tritt ein Linearfaktor $k$-mal auf so spricht man von einer $k$-fachen Nullstelle.

````{prf:example}
Ein Beispiel für die Bedeutung der Einbettung zur Interpretation von Nullstellen ist das Polynom
\begin{equation*}
p(x) \ = \ x^2 + 1.
\end{equation*}
Wird das Polynom $p$ über den reellen Zahlen aufgefasst, also $p \in \R[x]$, so besitzt $p$ keine Nullstellen.
Interpretieren wir $p \in \C[x]$ jedoch als Polynom über den komplexen Zahlen so hat es die Nullstellen $x_1 = -i$ und $x_2 = +i$ und es gilt
\begin{equation*}
p(x) \ = \ x^2 + 1 \ = \ (x + i)\cdot (x-i).
\end{equation*}
````

Das folgende Lemma charakterisiert die Nullstellen eines reellen Polynoms noch genauer und besagt, dass die komplexe Konjugation einer Nullstelle selbst eine Nullstelle sein muss.
Dies deckt sich mit der Aussage aus Satz {prf:ref}`satz:eigenwert_komplex_konjugiert`, der besagt, dass zu jedem Eigenwert einer reellwertigen Matrix auch dessen komplexe Konjugation ein Eigenwert der Matrix sein muss

````{prf:lemma}
:label: lem:nullstelle_komplex_kojugiert

Sei $p \in \R[x]$ ein reelles Polynom und sei $k \in \N$ mit $k \leq \deg(p)$.
Ist $x_1\in\C$ eine Nullstelle von $p$, dann ist auch $\overline x_1\in \C$ eine Nullstelle von $p$.
`````

````{prf:proof}
Sei das Polynom $p\in\R[x] \subset C[x]$ aufgefasst über den komplexen Zahlen von der Form
\begin{equation*}
p(x) \ = \ \sum_{k=0}^n a_kx^k.
\end{equation*}
Sei $x_1\in\C$ nun eine Nullstelle von $p$, dann gilt 
\begin{equation*}
  p(x_1) \ = \ \sum_{k=0}^n a_kx_1^k \ = \ 0.
\end{equation*}
Da die komplexe Konjugation verträglich mit der Addition und Multiplikation in $\C$ ist, können wir daraus folgern
\begin{equation*}
\bar{0} \ = \ \overline{p(x_1)} \ = \ \overline{\sum_{k=0}^n a_kx_1^k} \ = \ \sum_{k=0}^n \overline{a_kx_1^k} \ = \ \sum_{k=0}^n \bar{a}_k\bar{x}_1^k
\end{equation*}
Da wir aber $p\in\R[x]$ als reelles Polynom angenommen haben gilt $\bar{a}_k = a_k$ für alle Koeffizienten.
Damit folgt schon, dass
\begin{equation*}
0 \ = \  \bar{0} \ = \ \overline{p(x_1)} \ = \ \sum_{k=0}^n \bar{a}_k\bar{x}_1^k \ = \ \sum_{k=0}^n a_k\bar{x}_1^k \ = \ p(\bar{x}_1).
\end{equation*}
Also haben wir gezeigt, dass $\bar{x}_1 \in \C$ auch eine Nullstelle von $p$ ist.
````

Eine Zerlegung in Linearfaktoren wie in {eq}`eq:linearfaktorzerlegung` können wir für reelle Polynome im Allgemeinen nicht erwarten.
Dennoch lässt sich der folgende Satz für die Zerlegung reeller Polynom in eindeutige reelle Linearfaktoren und quadratische Polynome formulieren.

````{prf:theorem} Faktorisierungssatz für reelle Polynome
:label: satz:polynom_faktorisierung

Sei $p \in \R[x]$ ein reelles, normiertes Polynom mit Grad $\deg(p) = n$.
Dann existieren Koeffizienten $a_1, \ldots, a_l, b_1, \ldots, b_l, c_1, \ldots, c_m\in\R$ mit 
\begin{equation*}   
2l+m \, = \, n, \qquad a_i^2-b_i \, < \, 0,
\end{equation*}
so dass sich das Polynom $p$ faktorisieren lässt in die folgende Form
\begin{equation}\label{eq:polynom_faktorisierung}
  p(x) \ = \ \prod\limits_{i=1}^l(x^2 - 2a_ix+b_i) \: \cdot \: \prod\limits_{j=1}^m(x-c_j)\,.
\end{equation}
````

````{prf:proof}
Nach dem Fundamentalsatz der Algebra können wir $p$ in Linearfaktoren zerlegen mit
\begin{equation*}
  p(x) \ = \ \prod\limits_{i=1}^n(x-x_i) \ = \ \prod\limits_{i=1}^m(x-x_i) \, \cdot \, \prod\limits_{i=m+1}^n(x-x_i),
\end{equation*}
wobei $x_1, \ldots, x_m\in\R$ die reellen Nullstellen und $x_{m+1}, \ldots, x_n\in\C\setminus\R$ die echt komplexen Nullstellen von $p$ sind.
Wir setzen einen neuen Index 
\begin{equation*}
l \,\coloneqq \, \frac{n-m}2\in\N_0
\end{equation*}
und wissen nach Lemma \ref{lem:nullstelle_komplex_kojugiert}, dass für jede komplexe Nullstelle $x_i\in\C, i=m+1,\ldots, n$, von $p$ eine komplex-konjugierte Nullstelle $\bar{x_i}\in\C$ von $p$ existiert.
Durch eine geeignete Umnummerierung der Indizes können wir also schreiben:
\begin{equation*}
  \prod\limits_{i=m+1}^n(x-x_i) \ = \ \prod\limits_{i=m+1}^{m+l}(x-x_i)\cdot(x-\bar{x}_i)\,.
\end{equation*}
Um die Form in {eq}`eq:polynom_faktorisierung` zu erhalten setzen wir für die Linearfaktoren 
\begin{equation*}
c_i \, \coloneqq \, x_i, \qquad i=1, \ldots, m.
\end{equation*}
Für die quadratischen Polynome setzen wir schließlich
\begin{equation*} 
a_i \coloneqq \operatorname{Re}(x_{i+m}) \quad \text{ und } \quad b_i \, \coloneqq \, x_{i+m}\cdot\bar{x}_{i+m} \, = \, |x_{i+m}|^2, \qquad i=1\ldots, l.
\end{equation*}
Es ist klar, dass $a_i^2 - b_i < 0$ für die quadratischen Polynome mit komplexen Nullstellen gelten muss, da dieser Term gerade den Radikand in der Formel zur Berechnung von Nullstellen $x_{1/2} \in \C$ normierter, quadratischer Polynome der Form $q(x) = x^2 - 2ax + b$ darstellt mit
\begin{equation*}
x_{1/2} \ = \ a \pm \sqrt{a^2 - b}.
\end{equation*}
Falls $a_i^2 -b_i \geq 0$ wäre, so ließe sich das Polynom $q$ in zwei Linearfaktoren mit reellen Nullen faktorisieren.
````

Wir wollen die Aussage aus Satz \ref{satz:polynom_faktorisierung} im folgenden Beispiel mit konkreten Faktorisierungen reeller Polynome illustrieren.

````{prf:example}
Wir interessieren uns für eine Faktorisierung verschiedener reeller Polynome $p \in \R[x]$ in lineare und quadratische Polynome.

* Sei $p(x) = x^4 - 1$. Wir bezeichnen mit 
\begin{equation*}
\zeta_k \, \coloneqq \, \exp\left(\frac{2\pi i k}{4}\right), \quad k=0,\ldots,3
\end{equation*}
die 4. Einheitswurzeln. Dann lässt sich das Polynom $p$ wie folgt faktorisieren:
\begin{equation*}
p(x) \ = \ x^4 - 1 \ = \ \prod_{k=0}^4 (x - \zeta_k) \ = \ (x - 1) \cdot (x + 1) \cdot (x - i) \cdot (x + i) \ = \ (x - 1) \cdot (x + 1) \cdot (x^2 + 1)
\end{equation*}

* Sei $p(x) = x^5 - 1$. Wir bezeichnen mit 
\begin{equation*}
\zeta_k \, \coloneqq \, \exp\left(\frac{2\pi i k}{5}\right), \quad k=0,\ldots,4
\end{equation*}
die 5. Einheitswurzeln. Dann lässt sich das Polynom $p$ wie folgt faktorisieren:
\begin{equation*}
p(x) \ = \ x^5 - 1 \ = \ \prod_{k=1}^4 (x - \zeta_k) \ = \ (x - 1) \cdot (x^2 - 2\operatorname{Re}(\zeta_1) + 1) \cdot (x^2 - 2\operatorname{Re}(\zeta_2) + 1)
\end{equation*}
\item Sei $p(x) = x^4 - 6x^2 + 7x - 6$ und sei $c = \sqrt{-\frac{3}{4}} \in \C$.
Dann lässt sich das Polynom $p$ wie folgt faktorisieren:
\begin{equation*}
\begin{split}
p(x) \ &= \ x^4 - 6x^2 + 7x - 6 \ = \  (x - 2) \cdot (x + 3) \cdot (x +\frac{1}{2} + c)  \cdot (x + \frac{1}{2} - c) \\
 &= \ (x - 2) \cdot (x + 3) \cdot (x^2 - x + 1).
\end{split}
\end{equation*}
````

## Rationale Funktionen

Nachdem wir die wichtigsten Erkenntnisse und Begriffe für Polynomfunktionen wiederholt haben können wir uns im Folgenden mit den rationalen Funktionen beschäftigen, die als Quotient von Polynomen definiert sind.

````{prf:definition} Rationale Funktion
Seien $p,q \in \K[x]$ zwei Polynome mit $\deg(p) = n$ und $\deg(q) = m$ für $n,m \in \N$.
Dann bezeichnen wir den Quotienten der beiden Polynome
\begin{equation*}
r(x) \ \coloneqq \ \frac{p(x)}{q(x)} \ = \ \frac{\sum_{k=0}^n a_kx^k}{\sum_{k=0}^m b_kx^k}
\end{equation*}
als _rationale Funktion_.
Hierbei ist es wichtig, dass wir den Definitionsbereich von $r \in \K[x]$ einschränken auf die $x \in \K$ für die $q(x) \neq 0$.

Enthält der Zähler von $r$ ein Polynom, dass einen echt kleineren Grad als der Nenner besitzt, d.h., $n < m$, so sprechen wir von einer _echt gebrochenrationalen_ Funktion.
Ist das Gegenteil der Fall, d.h., $n \geq m$, so sprechen wir von einer _unecht gebrochenrationalen_ Funktion.
Ist $r$ ein Polynom, d.h. es gilt $m = 0$, so sprechen wir von einer _ganzrationalen_ Funktion.
````

````{prf:remark}
Wir wollen folgende Bemerkungen zu rationalen Funktionen festhalten.

* Rationale Funktionen können als Elemente eines Funktionskörpers $\K(x)$ aufgefasst werden, der über einem Körper $\K$ definiert ist, da jedes Element $r = \frac{p}{q}$ nun auch ein multipli\-kativ-inverses Element $r^{-1} = \frac{q}{p}$ besitzt im Gegensatz zu Elementen des Polynomrings $\K[x]$.
Dafür muss jedoch der Definitionsbereich in $D \subset \K$ so eingeschränkt werden, dass $q(x) \neq 0$ für alle $x \in D$.
Insbesondere gilt $\K[x] \subset \K(x)$.

* Rationale Funktionen sind nicht eindeutig, da sowohl Zähler als auch Nenner mit einem beliebigen Polynom $s \in \K[x], s \neq \pmb{0}$, erweitert werden können.
Jedoch lässt sich jede rationale Funktion $r \in \K(x)$ mittels _Polynomdivision_ {cite:p}`burger_2020` Kapitel 1.4 in eine eindeutige Summe aus einer ganzrationalen Funktion $g \in \K[x]$ (also einem Polynom) und einer echt gebrochenrationalen Funktion $\tilde{r}$ schreiben, d.h.
\begin{equation*}
r \ = \ \frac{p}{q} \ = \ g + \frac{\tilde{p}}{q} \ = \ g + \tilde{r} \qquad \text{ mit } \qquad \deg(\tilde{p}) \, < \, \deg(q).
\end{equation*}
````

Wir wollen die letzte Bemerkung zusätzlich an Hand eines Beispiels mittels Polynomdivision nachvollziehen.

````{prf:example} Polynomdivision
Sei $r\in \K(x)$ eine rationale Funktion mit
\begin{equation*}
r(x) \ = \ \frac{p(x)}{q(x)} \ = \ \frac{x^4}{x^3+2x^2-1}.
\end{equation*}  
Dann können wir $r$ schreiben als eine Summe eines Polynoms und einer echt gebrochenrationalen Funktion und es gilt:
  \begin{equation*}
    \frac{x^4}{x^3+2x^2-1} = x-2 + \frac{4x^2 + x-2}{x^3+2x^2-1}\,,
  \end{equation*}
Hierzu führen wir eine Polynomdivision mit dem Euklidischen Algorithmus durch:
```{warning}
Berechnung fehlt
```
````

## Partialbruchzerlegung rationaler Funktionen

Wir wissen also nun, dass wir jede rationale Funktion $r\in \K(x)$ darstellen können als
\begin{equation*}
r \ = \ g + \frac{\tilde{p}}{q} \qquad \text{ mit } \qquad \deg(\tilde{p}) \, < \, \deg(q).
\end{equation*}
Die Polynome $g\in\R[x]$ können wir offensichtlich sehr einfach integrieren jedoch müssen wir uns noch um die Bestimmung des unbestimmten Integrals für echt gebrochenrationale Funktionen $\frac{\tilde{p}}{q} \in \K(x)$ kümmern.
Ein sehr hilfreiches Werkzeug hierbei stellt die sogenannte _Partialbruchzerlegung_ dar, die es ermöglicht rationale Funktionen in eine Summe rationaler Funktionen von einfacher Gestalt zu zerlegen.
Wird die Ausgangsfunktion als komplexe rationale Funktion aus $\C(x)$ betrachtet, so besteht die Zerlegung sogar aus Summanden deren Nennerpolynom maximal eine Nullstelle besitzt.

Wir wollen zunächst den folgenden Satz für die Partialbruchzerlegung für den allgemeinen Fall $\K=\R$ oder $\K=\C$ formulieren.
In dieser Formulierung sagt der Satz aus, dass wir Nullstellen des Nennerpolynoms von echt gebrochenrationalen Funktionen aus dem Bruch herausziehen können, um somit den Grad des Nennerpolynoms zu verringern und dadurch einfachere Terme zu generieren.

````{prf:theorem} Partialbruchzerlegung
:label: satz:partialbruchzerlegung

Seien $p,q\in\K[x]$ beliebige Polynome mit $q \neq \pmb{0}$.  
Sei außerdem $x_1\in\K$ eine $k$-fache Nullstelle von $q$ mit $k\in\N$.
Falls die rationale Funktion $r\in \K(x)$ mit
\begin{equation*}
  r(x) \ \coloneqq \ \frac{p(x)}{q(x)} \ = \ \frac{p(x)}{\tilde{q}(x)\cdot(x-x_1)^k}
\end{equation*}
echt gebrochenrational ist, d.h., $\deg(p) < \deg(q)$, dann existiert ein eindeutig bestimmtes Polynom $\tilde{p} \in\K[x]$ und Skalare $A_1,\ldots, A_k\in\K$, so dass die folgende Partialbruchzerlegung gilt
\begin{equation*}
  r(x) \ = \ \frac{p(x)}{\tilde{q}(x)(x-x_1)^k} \ = \ \frac{\tilde p(x)}{\tilde{q}(x)} \, + \, \sum\limits_{j=1}^k \frac{A_j}{(x-x_1)^j} \qquad \text{ mit } \qquad \deg(\tilde p) < \deg(\tilde{q}).
\end{equation*}
````

````{prf:proof}
Da $x_1 \in \K$ eine $k$-fache Nullstelle des Nennerpolynoms ist, kann man rekursiv die Vielfachheit dieser Nullstelle reduzieren, was wir im Folgenden für den ersten Schritt zeigen werden.
Dazu müssen wir zeigen, dass    

```{math}
:label: eq:partialbruchzerlegung

r(x) \ = \ \frac{p(x)}{q(x)} \ = \ \frac{p(x)}{\tilde{q}(x)(x-x_1)^k} \ \overset{!}{=} \ \frac{p_k(x)}{\tilde{q}(x)(x-x_1)^{k-1}} + \frac{A_k}{(x-x_1)^k},
```

wobei $p_k\in\K[x]$ ein eindeutig bestimmtes Polynom vom Grad $\deg(p_k) < \deg(\tilde{q}) + k -1$ ist und $A_k\in\K$ ein eindeutig bestimmtes Skalar.

Durch Multiplikation beider Seiten der Gleichung {eq}`eq:partialbruchzerlegung` mit $(x-x_1)^k$ erhalten wir

```{math}
:label: eq:partialbruchzerlegung_mult

\frac{p(x)}{\tilde{q}(x)} \ \overset{!}{=} \ \frac{p_k(x) (x-x_1)}{\tilde{q}(x)} + A_k.
```

Setzen wir nun $x=x_1$ in diese Gleichung ein, so ergibt sich für das unbekannte Skalar
\begin{equation*}
A_k \ = \ \frac{p(x_1)}{\tilde{q}(x_1)}\in\K.
\end{equation*}
Stellen wir jedoch {eq}`eq:partialbruchzerlegung_mult` nach der unbekannten Funktion $p_k\in \K(x)$ um, so erhalten wir
\begin{equation*}
p_k(x) \ = \ \frac{p(x)-A_k\tilde{q}(x)}{x-x_1} \ = \ \frac{p(x) \, - \, \frac{p(x_1)}{\tilde{q}(x_1)} \cdot \tilde{q}(x)}{x-x_1}.
\end{equation*}
Es wird klar, dass $p_k \in \K[x]$ ein Polynom ist, da das Zählerpolynom $(p(x) - A_k \tilde{q}(x)) \in \K[x]$ offensichtlich eine Nullstelle in $x = x_1$ besitzt und sich somit ein Linearfaktor $(x-x_1)$ abspalten lässt.

Abschließend lässt sich noch Folgendes feststellen.
Da nach Voraussetzung 
\begin{equation*}
\deg(p) \: < \: \deg(q) \: = \: \deg(\tilde{q}) + k
\end{equation*}
galt, ist wegen Bemerkung \ref{rem:polynome} auch 
\begin{equation*}
\deg(p-A_k\tilde{q}) \: < \: \deg(\tilde{q})+k.
\end{equation*}
Aus der Gestalt des Polynoms $p_k$ wissen wir daher, dass 
\begin{equation*}
\deg(p_k)< \deg(q)+k-1
\end{equation*}
gilt.
Wir haben also ein eindeutiges Skalar $A_k \in \K$ und ein eindeutiges Polynom $p_k \in \K[x]$ gefunden, so dass die Zerlegung in {eq}`eq:partialbruchzerlegung` gilt.
Auf die übrigbleibende echt gebrochenrationale Funktion  können wir also rekursiv den obigen Ansatz anwenden.
````

Wenn der zu Grunde liegende Körper $\K$ explizit gewählt wird, so lässt sich die Aussage aus Satz {prf:ref}`satz:partialbruchzerlegung` noch weiter präzisieren, wie folgende Bemerkung festhält.

````{prf:remark}
Im Folgenden wollen wir für die spezielle Wahl des Körpers $\K$ erklären, wie sich eine echt gebrochenrationale Funktion in möglichst einfache Summanden durch mehr

* Lässt sich das Nennerpolynom $q$ der echt gebrochenrationalen Funktion $r\in\K(x)$ in Satz \ref{satz:partialbruchzerlegung} in Linearfaktoren zerlegen (was für alle Polynome $q \in \C[x]$ der Fall ist nach dem Fundamentalsatz der Algebra), d.h., es besitzt die Form
\begin{equation*}
  q(x) \ = \ \prod\limits_{i=1}^m(x-x_i)^{d_i},
\end{equation*}
und sind die Nullstellen $x_i \in \K, i=1,\ldots,m$ der Vielfachheit $k_i\in\N$ paarweise verschieden, dann führt mehrfache Anwendung der Partialbruchzerlegung in Satz \ref{satz:partialbruchzerlegung} zu folgender Formel:

```{math}
:label: eq:partialbruchzerlegung_vollständig
  \frac{p(x)}{q(x)} \ = \ \sum_{i=1}^{m} \sum_{j=1}^{k_i}\frac{A_j^{(i)}}{(x-x_i)^j}\,.
```

Die Anzahl der zu bestimmenden Koeffizienten $A_j^{(i)}$ ist in diesem Fall $\sum\limits_{i=1}^{m}k_i = \deg(q)$.

* Betrachtet man lediglich reelle Polynome $p,q\in\R[x]$, so wissen wir aus dem Faktorisierungssatz \ref{satz:polynom_faktorisierung} für reelle Polynome, dass sich das Nennerpolynom in ein Produkt aus $\hat{k}\in\N$ Linearfaktoren und $\hat{l}\in\N$ quadratischen Polynomen mit je zwei echt komplexen Nullstellen faktorisieren lässt, d.h.,
\begin{equation*}
q(x) \ = \ \prod\limits_{i=1}^{\hat{l}}(x^2 - 2a_ix+b_i) \: \cdot \: \prod\limits_{j=1}^{\hat{k}}(x-c_j).
\end{equation*}

* Das bedeutet, dass $q \in \R[x]$ insgesamt $m = \hat{k} + 2\hat{l}$ Nullstellen besitzt.
Wir nehmen an, dass $k\in\N, k \leq \hat{k}$ reelle Nullstellen paarweise verschieden sind und außerdem noch $l\in\N, l \leq \hat{l}$ Paare von paarweise verschiedenen, echt komplexen Nullstellen von $q$ existieren.
Seien nun $s_1, \ldots, s_k \in \N$ die Vielfachheiten der reellen Nullstellen und $t_1,\ldots, t_l \in \N$ die Vielfachheiten der komplexen Nullstellen.
Dann können wir das Polynom $q\in\R[x]$ schreiben als die folgende Faktorisierung
\begin{equation*}
q(x) \ = \ \prod\limits_{i=1}^{l}(x^2 - 2a_ix+b_i)^{t_i} \: \cdot \: \prod\limits_{j=1}^k(x-c_j)^{s_j}.
\end{equation*}

Die mehrfache Anwendung der Partialbruchzerlegung in Satz {prf:ref}`satz:partialbruchzerlegung` führt dann für reelle echt gebrochenrationale Funktionen zu folgender Formel:

```{math}
:label: eq:partialbruchzerlegung_vollständig_reell
  \frac{p(x)}{q(x)} \ = \ \sum_{i=1}^{k} \sum_{j=1}^{s_i}\frac{A_j^{(i)}}{(x-x_i)^j} \: + \: \sum_{i=1}^{l} \sum_{j=1}^{t_i} \frac{B_j^{(i)}x+C^{(i)}_j}{(x^2 - 2ax + b)^j}.
```

Die Anzahl der zu bestimmenden Koeffizienten $A_j^{(i)}$ für die Linearfaktoren ist in diesem Fall $\sum\limits_{i=1}^{k}s_i = \hat{k}$.
Die Anzahl der zu bestimmenden Koeffizienten $B_j^{(i)}$ und $C_j^{(i)}$  für die quadratischen Polynome ist in diesem Fall jeweils $\sum\limits_{i=1}^{l}t_i = \hat{l}$.
Insgesamt müssen also $\hat{k} + 2\hat{l} = m = \deg(q)$ unbekannte Koeffizienten bestimmt werden.

* Nach Multiplikation beider Seiten von {eq}`eq:partialbruchzerlegung_vollständig` und {eq}`eq:partialbruchzerlegung_vollständig_reell` mit dem Nennerpolynom $q$ lassen sich die unbekannten Koeffizienten durch Koeffizientenvergleich der Polynome auf beiden Seiten berechnen.
Dies lässt sich am einfachsten durch die Lösung eines linearen Gleichungssystems realisieren.
````

Basierend auf den Beobachtungen oben können wir nun informell einen Algorithmus für die Partialbruchzerlegung einer rationalen Funktion angeben.

````{prf:algorithm} Partialbruchzerlegung
:label: alg:partialbruchzerlegung

Sei zu Anfang eine rationale Funktion $r\in\K(x)$ gegeben mit
\begin{equation*}
r(x) \ \coloneqq \ \frac{p(x)}{q(x)}
\end{equation*}
mit zwei Polynomen $p,q \in \K[x]$.

**1. Schritt: Überführung von $r$ in eindeutige Darstellung**

Ist die rationale Funktion $r$ bereits echt gebrochenrational, d.h. $\deg(q) > \deg(p)$ so ist in diesem Schritt nichts zu tun.
Andernfalls führen wir eine Polynomdivision durch um $r$ in die eindeutige Darstellung
\begin{equation*}
r \ = \ g + \frac{\tilde{p}}{q}
\end{equation*}
zu überführen, wobei $g \in \K[x]$ ein Polynom ist und $\deg(q) > \deg(\tilde{p})$ gilt.

**2. Schritt: Bestimmung der Nullstellen des Nennerpolynoms**

Wir bestimmen nun die Nullstellen des Nennerpolynoms $q\in\K[x]$ analytisch, d.h., wir versuchen das Polynom in die in {eq}`eq:linearfaktorzerlegung` oder {eq}`eq:polynom_faktorisierung` beschriebene Form zu faktorisieren (in Abhängigkeit des Körpers $\K$).
Ist eine analytische Bestimmung der Nullstellen von $q$ nicht möglich, können numerische Methoden angewendet werden zur Approximation der Nullstellen.

**3. Schritt: Bestimmung der Partialbruchzerlegung**

Basierend auf den im 2. Schritt bestimmten Nullstellen von $q$ kann eine Partialbruchzerlegung der Form {eq}`eq:partialbruchzerlegung_vollständig` oder {eq}`eq:partialbruchzerlegung_vollständig_reell` durchgeführt werden (in Abhängigkeit des Körpers $\K$).

**4. Schritt: Aufstellung des linearen Gleichungssystems**

Durch Multiplikation beider Seiten von {eq}`eq:partialbruchzerlegung_vollständig` oder {eq}`eq:partialbruchzerlegung_vollständig_reell` mit dem Nennerpolynom $q\in\K[x]$ kann ein Koeffizientenvergleich durchgeführt werden, der zu einem linearen Gleichungssystem mit einer Koeffizientenmatrix vom Rang $\deg(q)$ führt.

**5. Schritt: Lösung des linearen Gleichungssystems**

Die Lösung des entstehenden linearen Gleichungssystems kann entweder algebraisch oder numerisch erfolgen (basierend auf der Gestalt und Größe der Koeffizientenmatrix) und liefert die eindeutig bestimmten Koeffizienten $A^{(i)}_j, B^{(i)}_j, C^{(i)}_j \in \K$ der Partialbruchzerlegung.

Damit haben wir die rationale Funktion $r\in\K(x)$ in eine Summe einfacherer Terme durch Partialbruchzerlegung überführt.
````

Wir wollen den Algorithmus {prf:ref}`alg:partialbruchzerlegung` für die Partialbruchzerlegung an einem konkreten Beispiel anwenden und somit besser verdeutlichen.

````{prf:example} Partialbruchzerlegung
Wir wollen eine Partialbruchzerlegung für die rationale Funktion $r\in\R(x)$ durchführen mit
\begin{equation*}
r(x) \ \coloneqq \ \frac{2x^3 + 4x}{x^4-2x^2+1}.
\end{equation*}
Hierzu wenden wir Algorithmus {prf:ref}`alg:partialbruchzerlegung` schrittweise an.

**1. Schritt: Überführung von $r$ in eindeutige Darstellung**

Wir bemerken, dass die rationale Funktion $r \in \R(x)$ bereits echt gebrochenrational ist und wir deshalb keine Polynomdivision durchführen müssen.

**2. Schritt: Bestimmung der Nullstellen des Nennerpolynoms**

Durch Ausprobieren stellen wir fest, dass das Nennerpolynom $q \in \R[x]$ Nullstellen in $x_1 = 1$ und $x_2 = -1$ besitzt.
Faktorisieren wir diese Nullstellen heraus erhalten wir den Ausdruck
\begin{equation*}
q(x) \ = \ x^4-2x^2+1 \ = \ (x-1)\cdot (x+1) \cdot (x^2 - 1).
\end{equation*}
Die Nullstellen des übrig gebliebenen quadratischen Polynoms bestimmen wir durch Ausklammern (oder mittels $p$-$q$-Formel) und erhalten die folgende Faktorisierung von $q$ in zwei Linearfaktoren der Vielfachheit zwei:
\begin{equation*}
q(x) \ = \ x^4-2x^2+1 \ = \ (x-1)\cdot (x+1) \cdot (x^2 - 1) \ = \ (x-1)^2\cdot (x+1)^2.
\end{equation*}

**3. Schritt: Bestimmung der Partialbruchzerlegung**

Da wir Glück haben und sich das Nennerpolynom in Linearfaktoren über $\R$ faktorisieren lässt wie in {eq}`eq:linearfaktorzerlegung`, können wir die allgemeine Darstellung der Partialbruchzerlegung in {eq}`eq:partialbruchzerlegung_vollständig` anwenden:
```{math}
:label: eq:partialbruchzerlegung_beispiel

\frac{2x^3 + 4x}{(x+1)^2(x-1)^2} \ = \ \sum_{i=1}^{2} \sum_{j=1}^{2}\frac{A_j^{(i)}}{(x-x_i)^j} \ = \ \frac{A_1^{(1)}}{x+1} \, + \, \frac{A_2^{(1)}}{(x+1)^2} \, + \, \frac{A_1^{(2)}}{x-1} \, + \, \frac{A_2^{(2)}}{(x-1)^2}.
```

**4. Schritt: Aufstellung des linearen Gleichungssystems**

Durch Multiplikation beider Seiten der Partialbruchzerlegung in {eq}`eq:partialbruchzerlegung_beispiel` mit dem Nennerpolynom $q(x) = (x-1)^2(x+1)^2$ ergibt dann:
\begin{align*}
2x^3 + 4x \ &= \ A_1^{(1)} (x+1)(x-1)^2 + A_2^{(1)} (x-1)^2 + A_1^{(2)} (x+1)^2(x-1) + A_2^{(2)}(x+1)^2\\
          \ &= \ \left(A_1^{(1)} + A_1^{(2)}\right) x^3 + \left(-A_1^{(1)}+A_2^{(1)}+A_1^{(2)}+A_2^{(2)}\right)x^2\\
          & \quad + \left(-A_1^{(1)}-2A_2^{(1)}-A_1^{(2)}+2A_2^{(2)}\right)x + A_1^{(1)} + A_2^{(1)} + A_1^{(2)} + A_2^{(2)}\,.
\end{align*}
Durch Koeffizientenvergleich erhalten wir das folgende lineare Gleichungssystem
\begin{equation*}
\left(\begin{array}{rrrr}%
    1&0&1&0\\
    -1&1&1&1\\
    -1&-2&-1&2\\
    1&1&-1&1
    \end{array}\right)\left(\begin{array}{r}%
  A_1^{(1)}\\
  A_2^{(1)}\\
  A_1^{(2)}\\
  A_2^{(2)}
    \end{array}\right) = \left(\begin{array}{r}%
    2\\0\\4\\0
\end{array}\right).
\end{equation*}

**5. Schritt: Lösung des linearen Gleichungssystems**

Mittels Gauß'schem Eliminationsverfahren können wir die eindeutige Lösung für die Koeffizienten bestimmen als
\begin{equation*}
A_1^{(1)}=1, \quad A_2^{(1)}=-\frac32, \quad A_1^{(2)}=1, \quad A_2^{(2)}=\frac32.
\end{equation*}
~\\[0.3cm]
Insgesamt erhalten wir also die folgende Partialbruchzerlegung
\begin{equation*}
\frac{2x^3 + 4x}{(x+1)^2(x-1)^2} \ = \ \frac{1}{x+1} \, + \, \frac{-\frac32}{(x+1)^2} \, + \, \frac{1}{x-1} \, + \, \frac{\frac32}{(x-1)^2}.
\end{equation*}
````

## Stammfunktionen rationaler Funktionen

Mit Hilfe des Algorithmus {prf:ref}`alg:partialbruchzerlegung` für die Partialbruchzerlegung können wir also beliebige rationale Funktionen in eine Summe aus wesentlich einfacheren Termen zerlegen.
Nun müssen wir nur noch festhalten, wie die Stammfunktionen dieser einfachen Summanden aussehen, damit wir rationale Funktionen integrieren können.
Hierzu hält die folgende Bemerkung die relevanten Ergebnisse fest.

````{prf:remark}
:label: bem:stammfunktion

Wir erwarten als Resultat der Partialbruchzerlegung im Allgemeinen zwei verschiedene Arten von Summanden.
Für diese zwei Arten werden wir im Folgenden Stammfunktionen angeben, so dass sich die Stammfunktion von beliebigen rationalen Funktionen bestimmen lässt.
Auf eine explizite Herleitung der Stammfunktionen wird verzichtet, da sich die Resultate durch die Rechenregeln der Differentiation direkt verifizieren lassen.

* Die erste Art von Summanden der Partialbruchzerlegung ist von der Gestalt
\begin{equation*}
s(x) \ = \ \frac{A}{(x-a)^j}, \quad j\in\N, A\in\K
\end{equation*}
und entsteht durch das Ausklammern von Linearfaktoren aus dem Nennerpolynom $q \in \K[x]$ für eine Nullstelle $a \in \K$.
Da das Skalar $A\in\K$ nicht von der Variable $x$ abhängt, lässt es sich linear aus dem Integral herausziehen und somit können wir die Stammfunktion direkt angeben als
  \begin{equation*}
    \int s(x) \, \mathrm{d}x \ = \ A\int\frac1{(x-a)^j}\, \mathrm{d}x  \ = \ \begin{cases}\ A \cdot \ln\vert x-a\vert \quad &\text{für}\ j=1\,,\\ \ \frac{-A}{(j-1)(x-a)^{j-1}}\quad &\text{für}\ j>1\,.\end{cases}
  \end{equation*}

* Die zweite Art von Summanden der Partialbruchzerlegung ist von der Gestalt
\begin{equation*}
s(x) \ = \  \frac{Bx+C}{(x^2 - 2ax + b)^j}, \quad j\in\N, \ A,B\in\K
\end{equation*}
und entsteht im Fall von reellen rationalen Funktionen durch das Ausklammern von quadratischen Polynomen aus dem Nennerpolynom $q \in \R[x]$, die je ein Paar von echt komplexe Nullstellen besitzen (da in diesem Fall $a^2<b$ gilt).
Um eine Stammfunktion für $s\in\R(x)$ zu bestimmen formen wir die Funktion zuerst geeignet um, so dass wir im Zähler ein Vielfaches des linearen Terms $(x-a)$ erhalten:
```{math}
:label: eq:stammfunktion_umformung
\frac{Bx+C}{(x^2 - 2ax + b)^j} \ = \ \frac{B\cdot(x-a)}{(x^2 - 2ax + b)^j} + \frac{C + B\cdot a}{(x^2 - 2ax + b)^j}, \quad j\in\N, \ B, C\in\K
```

Für den linken Summanden in {eq}`eq:stammfunktion_umformung` können wir folgende Stammfunktion angeben:
\begin{equation*}
   B \int \frac{x-a}{(x^2-2ax+b)^j} \, \mathrm{d}x \ = \ \begin{cases}\ \frac B 2\ln(x^2 -2ax + b)\,,\quad &\text{für}\ j=1\\
      \ -\frac{B}{2(j-1)(x^2-2ax+b)^{j-1}}\,,\quad &\text{für} \ j>1\,.\end{cases}
\end{equation*}
Für den rechten Summanden in {eq}`eq:stammfunktion_umformung` können wir folgende Stammfunktion rekursiv angeben: 
\begin{equation*}
\begin{split}
    I_j \ &\coloneqq \ \underbrace{(C+B\cdot a)}_{\eqqcolon D} \int \frac1{(x^2-2ax+b)^j} \, \mathrm{d}x \\
    &= \ \begin{cases} \ \frac{D}{\sqrt{b-a^2}} \cdot \arctan\left(\frac{x-a}{\sqrt{b-a^2}}\right)\,,& \quad \text{für} \ j=1,\\
    \ D\cdot \left(\frac{x-a}{2(b-a^2)(j-1)(x^2-2ax + b)^{j-1}} + \frac{2j-3}{2(b-a^2)(j-1)} I_{j-1}\right)\,,& \quad \text{für} \ j>1.\end{cases}
 \end{split}
  \end{equation*}
````

Glücklicherweise sind moderne Computerprogramme in der Lage die oben beschriebenen Stammfunktionen analytisch zu bestimmen.
Abschließend wollen wir im folgenden Beispiel die Stammfunktion einer einfachen rationalen Funktion mit Hilfe der Aussagen aus Bemerkung {prf:ref}`bem:stammfunktion` ausrechnen.

````{prf:example} Integration einer rationalen Funktion
Sei $s\in\R(x)$ eine rationale Funktion, deren Nennerpolynom quadratisch ist mit
\begin{equation*}
s(x) \ \coloneqq \ \frac{x+2}{x^2-4x+7}.
\end{equation*}
Zur Bestimmung einer Stammfunktion von $s$ sehen wir ein, dass die Koeffizienten $a=2$ und $b=7$ im Nennerpolynom sind. 
Außerdem ist $B=1, C=2$ und $j=1$.
Mit diesen Informationen formen wir den Zähler wie in {eq}`eq:stammfunktion_umformung` um und erhalten als Stammfunktion
\begin{align*}
\int\frac{x+2}{x^2-4x+7}\, \mathrm{d}x \ &= \ \int\frac{x-2}{x^2-4x+7}\, \mathrm{d}x \, + \, 4\int \frac1{x^2-4x+7}\, \mathrm{d}x\\
                            &= \frac12\ln(x^2-4x+7) \, + \, \frac4{\sqrt3}\arctan\left(\frac{x-2}{\sqrt3}\right)\,.
\end{align*}
````
