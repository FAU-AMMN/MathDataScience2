(s:diagonalisierbarkeit)=
# Diagonalisierbarkeit

Wichtige Eigenschaften eines Endomorphismus lassen sich bereits am Rang und am Spektrum einer darstellenden Matrix ablesen. 
Leider lassen sich diese Charakteristika im Allgemeinen (bis auf Spezialfälle) nicht direkt an den Einträgen der Matrix ablesen.
Die grundlegende Frage in diesem Abschnitt wird sein, wie wir durch eine geeignete Wahl von Basen eine besonders einfache Gestalt der darstellenden Matrix erreichen können, die die Eigenschaften des zu Grunde liegenden Endomorphismus erhält.

Aus dem Basiswechselsatz {prf:ref}`satz:basiswechselsatz` wissen wir, dass ein Basiswechsel für Abbildungsmatrizen einer Multiplikation mit zwei regulären Basiswechselmatrizen von links und rechts entspricht.
Die hierdurch beschriebene Relation der Abbildungsmatrizen motiviert die folgende Definition.

````{prf:definition} Äquivalenz und Ähnlichkeit von Matrizen
:label: def:matrix_aequiv_aehnlich

Wir definieren im folgenden zwei Begriffe, die eine spezielle Relation zweier Matrizen beschreibt.

* Zwei Matrizen $A, B \in \mathbb{K}^{n \times m}$ heißen _äquivalent_, wenn es Matrizen $S \in \GL(n; \mathbb{K})$ und $T \in \GL(m; \mathbb{K})$ gibt mit
\begin{equation}
B  \ = \ SAT^{-1}.
\end{equation}

* Zwei Matrizen $A, B \in \mathbb{K}^{n \times n}$ heißen _ähnlich_ oder _konjugiert_, wenn es eine Matrix $S \in \GL(n, \mathbb{K})$ gibt mit
```{math}
:label: eq:aehnlichkeit
B  \ = \ SAS^{-1}.
```

````

Man sieht sofort, dass ähnliche Matrizen ein Spezialfall von äquivalenten Matrizen sind für $m = n$ und $T^{-1} \coloneqq S^{-1}$.
Während man für äquivalente Matrizen zeigen kann, dass der Rang der Matrizen unter den in Definition {prf:ref}`def:matrix_aequiv_aehnlich` beschriebenen Transformationen erhalten bleibt, so gilt für ähnliche Matrizen sogar die noch stärkere Invarianz des Spektrums, wie das folgende Lemma zeigt.

````{prf:lemma}
:label: lem:aehnlich_polynom

Seien $A, B \in \mathbb{K}^{n\times n}$ zwei quadratische Matrizen. Falls $A$ und $B$ ähnlich zueinander sind, so haben sie das gleiche charakteristische Polynom.
````

````{prf:proof}
Seien $A,B \in \mathbb{K}^{n \times n}$ zwei ähnliche Matrizen, d.h., es existiert eine Matrix $S \in \GL(n; \mathbb{K})$, so dass $B = S A S^{-1}$. Ferner gilt wegen Linearität und der Kommutativität der Einheitsmatrix $I_n$ für jedes Skalar $t \in \mathbb{K}$
\begin{equation*}
S \cdot t \cdot I_n \cdot S^{-1} = t \cdot I_n.
\end{equation*}
Wir können also schreiben:
\begin{equation*}
B - t \cdot I_n \ = \ S A S^{-1} - t \cdot I_n \ = \ S A S^{-1} - S \cdot t \cdot I_n \cdot S^{-1} \ = \ S (A - t \cdot I_n) S^{-1}.
\end{equation*}
Wenden wir nun die Determinante an, so erhalten wir aus dem Produktsatz für Determinanten \cite{burger_2020}[Satz 3.40]
\begin{equation*}
\det(B - t \cdot I_n) \ = \ \det(S (A - t \cdot I_n) S^{-1}) \ = \ \det(S) \cdot \det(A - t \cdot I_n) \cdot \underbrace{\det(S^{-1})}_{= \det(S)^{-1}} \ = \ \det(A - t \cdot I_n).
\end{equation*}
Die Ausdrücke auf der linken und rechten Seite der obigen Gleichung sind gerade die Definitionen der charakteristischen Polynome von $A$ bzw. $B$, was die Aussage dieses Lemmas beweist.
````

Ein besonders interessanter Fall liegt vor, wenn eine Matrix $A \in \mathbb{K}^{n\times n}$ ähnlich zu einer Diagonalmatrix $D \in \mathbb{K}^{n\times n}$ ist.
Dies wird in der folgenden Definition weiter präzisiert.

````{prf:definition} Diagonalisierbarkeit
:label: def:diagonalisierbarkeit

Wir definieren den Begriff der _Diagonalisierbarkeit_ im folgenden sowohl für Endomorphismen als auch für Matrizen.

* Ein Endormorphismus $F \colon V \rightarrow V$ eines $\mathbb{K}$-Vektorraums $V$ heißt \emph{diagonalisierbar}, wenn $V$ eine Basis aus Eigenvektoren von $F$ besitzt.

* Eine Matrix $A \in \mathbb{K}^{n \times n}$ heißt \emph{diagonalisierbar}, wenn sie ähnlich zu einer Diagonalmatrix ist.
````

Auf Grund von Lemma {prf:ref}`lem:aehnlich_polynom` wird klar, dass eine diagonalisierbare Matrix $A$ ähnlich zu einer Diagonalmatrix $D$ sein muss, die die Eigenwerte von $A$ auf der Diagonalen enthält.
Im Folgenden wollen wir verstehen, wie wir entscheiden können, ob ein Endomorphismus $F$ bzw. eine darstellende Matrix von $F$ diagonalisierbar ist.

````{prf:theorem} Diagonalisierbarkeit
:label: satz:diagonalisierbarkeit

Sei $V$ ein endlichdimensionaler $\mathbb{K}$-Vektorraum und $F \colon V \rightarrow V$ ein Endomorphismus von $V$.
Dann sind die folgenden Bedingungen äquivalent:

i) $F$ ist diagonalisierbar

ii) Das charakteristische Polynom $P_F$ zerfällt in Linearfaktoren über $\mathbb{K}$ und die algebraische Vielfachheit ist gleich der geometrischen Vielfachheit für alle Eigenwerte $\lambda \in \mathbb{K}$ von $F$.

iii) Sind $\lambda_1, \ldots, \lambda_k \in \mathbb{K}$ die paarweise verschiedenen Eigenwerte von $F$, so lässt sich $V$ als direkte Summe der korrespondierenden Eigenräume schreiben, d.h.
\begin{equation*}
V \ = \ \Eig(F; \lambda_1) \oplus \ldots \oplus \Eig(F; \lambda_k).
\end{equation*} 
````

````{prf:proof}
Wir zeigen die Äquivalenz der drei Aussagen mittels eines Ringschlusses.

**i) $\rightarrow$ ii):**

Nehmen wir an, dass $F$ diagonalisierbar ist.
Dann ist jede darstellende Matrix von $F$ ähnlich zu einer Diagonalmatrix $D \in \mathbb{K}^{n \times n}$ auf deren Hauptdiagonalen die Eigenwerte $\lambda_1, \ldots, \lambda_k \in \mathbb{K}$ von $F$ mit algebraischen Vielfachheiten $r_1,\ldots, r_k \in \mathbb{N}$ stehen.
Das charakteristische Polynom $P_D$ von $D$ zerfällt offensichtlich in Linearfaktoren über $\mathbb{K}$ in der Form
\begin{equation*}
P_D(t) \ = \ (\lambda_1 - t)^{r_1} \cdot \ldots \cdot (\lambda_k - t)^{r_k}
\end{equation*}
und die Summe der algebraischen Vielfachheiten entspricht dem Grad des Polynoms, d.h., $\sum_{i=1}^k r_i = n$.
Aus Lemma {prf:ref}`lem:aehnlich_polynom` wissen wir aber schon, dass das charakteristische Polynom von $F$ und $D$ gleich sein müssen.


Da $F$ diagonalisierbar ist existiert eine Basis von $V$ aus Eigenvektoren von $F$.
Die Eigenvektoren dieser Basis können wir anhand ihrer zugehörigen Eigenwerte sortieren, so dass sich Basen der jeweiligen Eigenräume mit geometrischen Vielfachheiten $s_1, \ldots, s_k$  ergeben, d.h., wir betrachten die Eigenvektoren $v^i_1, \ldots, v^i_{s_i} \in V$ von $F$ zum Eigenwert $\lambda_i \in \mathbb{K}$  mit geometrischer Vielfachheit $s_i \in \mathbb{N}$ als Basis des Eigenraums $\Eig(F; \lambda_i)$ für $1\leq i \leq k$.
Daraus ergibt sich, dass $\sum_{i=1}^k s_i = n$ gelten muss, da wir von einer Basis von $V$ ausgegangen sind.
Gleichzeitig wissen wir aus dem Argument von oben, dass $\sum_{i=1}^k r_k = n$ gelten muss und nach Satz {prf:ref}`satz:vielfachheiten` die algebraischen Vielfachheiten größer oder gleich den geometrischen Vielfachheiten sind, d.h., es gilt $r_i \geq s_i$.
Diese drei Bedingungen können jedoch nur dann erfüllt werden, wenn schon gilt $r_i = s_i$.

**ii) $\rightarrow$ iii):**

Seien $\lambda_1, \ldots, \lambda_k \in \mathbb{K}$ die paarweise verschiedenen Eigenwerte von $F$, deren algebraische Vielfachheit gleich der geometrischen Vielfachheit ist, d.h., $r_i = s_i$ für $1 \leq i \leq k$.
Wir nehmen an, dass das charakteristische Polynom $P_F$ von $F$ in Linearfaktoren über $\mathbb{K}$ zerfällt und von der Form ist
\begin{equation*}
P_F(t) \ = \ (t - \lambda_1)^{r_1} \cdot \ldots \cdot (t - \lambda_k)^{r_s}.
\end{equation*}
Wir betrachten die lineare Hülle der Eigenräume $\Eig(F; \lambda_i), 1 \leq i \leq k$, von $F$ 
\begin{equation*}
W \ \coloneqq  \ \lin(\Eig(F; \lambda_1) \cup \ldots \cup \Eig(F; \lambda_k)) \subset V.
\end{equation*}
Da die geometrische Vielfachheit $s_i = r_i$ für $i=1,\ldots, k$ ist, wird $W$ durch $n$ Eigenvektoren aufgespannt.
Aus Satz {prf:ref}`satz:eigenvektoren_lu` wissen wir, dass Vektoren aus verschiedenen Eigenräumen paarweise linear unabhängig sind.
Damit folgt aber schon, dass $W$ eine direkte Summe der Eigenräume sein muss mit
\begin{equation*}
W \ = \ \Eig(F; \lambda_1) \oplus \ldots \oplus \Eig(F; \lambda_k) = V.
\end{equation*}

**iii) $\rightarrow$ i):**

Sei $B_i = (v_1^i, \ldots, v_{s_i}^i)$ eine Basis aus Eigenvektoren zum Eigenwert $\lambda_i \in \mathbb{K}$ vom Eigenraum $\Eig(F; \lambda_i)$ für $1 \leq i \leq k$.
Da die Eigenräume als direkte Summe den ganzen Vektorraum $V$ bilden, wissen wir, dass
\begin{equation*}
B \ \coloneqq \ (v_1^1, \ldots, v_{s_1}^1, \ldots, v_1^k, \ldots, v_{s_k}^k)
\end{equation*}
eine Basis von $V$ ist.
Da diese Basis aus Eigenvektoren von $F$ besteht ist $F$ schon diagonalisierbar per Definition.
````

````{prf:corollary}
:label: cor:eigenwerte_verschieden

Aus Satz {prf:ref}`satz:diagonalisierbarkeit` wird direkt klar, dass der Endomorphismus $F$ diagonalisierbar ist, wenn er $n \in \mathbb{N}$ paarweise verschiedene Eigenwerte besitzt. Dies ist eine hinreichende aber keineswegs notwendige Bedingung, wie etwa das Beispiel $F=\operatorname{Id}_V$ zeigt.
````

````{prf:example}
:label: bsp:diagonalisierung_gegenbeispiele
Im Folgenden wollen wir zwei Beispiele untersuchen in denen eine reellwerte Matrix $A \in \mathbb{R}^{3 \times 3}$ nicht diagonalisierbar ist und die Gründe hierfür genauer beleuchten.

* Sei die Matrix $A \in \mathbb{R}^{3 \times 3}$ gegeben durch:
\begin{equation*}
A \ = \
\begin{pmatrix}
1 & -\sqrt{3} & 0\\
\sqrt{3} & -1 & 0\\
0 & 0 & 1
\end{pmatrix}.
\end{equation*}
Wir bestimmen das charakteristische Polynom $P_A$ von $A$ mit der Produktregel für Determinanten von Blockmatrizen in Lemma {prf:ref}`lem:det_blockmatrix` als
\begin{equation*}
\begin{split}
P_A(t) \ &= \ \det(A - tI_3) \ = \
\begin{pmatrix}
1 -t & -\sqrt{3} & 0\\
\sqrt{3} & -1 - t & 0\\
0 & 0 & 1 - t
\end{pmatrix} \\
\ &= \ (1 - t) \bigl((1- t)(-1 -t) + \sqrt{3}\cdot\sqrt{3}\bigr)
\ = \ (1 - t) (t^2 - 1 + 3)\\
\ &= \ (1 - t) (t^2 + 2).
\end{split}
\end{equation*}
Da das quadratische Polynom $(t^2 + 2)$ keine Nullstellen in $\mathbb{R}$ besitzt, lässt sich das charakteristische Polynom $P_A$ nicht vollständig in Linearfaktoren über $\mathbb{R}$ zerlegen.
Daraus folgt mit Satz {prf:ref}`satz:diagonalisierbarkeit`, dass die Matrix $A$ nicht diagonalisierbar ist.

* Sei die Matrix $A \in \mathbb{R}^{3 \times 3}$ gegeben durch:
\begin{equation*}
A \ = \
\begin{pmatrix}
3 & 4 & -3\\
2 & 7 & -4\\
3 & 9 & -5
\end{pmatrix}.
\end{equation*}
Wir bestimmen das charakteristische Polynom $P_A$ von $A$ durch die Regel von Sarrus in Lemma {prf:ref}`lem:sarrus` oder Umformung mittels Gaußschen Eliminationsverfahren und erhalten:
\begin{equation*}
P_A(t) \ = \ \det(A - tI_3) \ = \ -(t -2)^2 \cdot (t - 1).
\end{equation*}
Das charakteristische Polynom zerfällt also in Linearfaktoren über $\mathbb{R}$ und wir können die beiden Eigenwerte $\lambda_1 = 2$ und $\lambda_2=1$ ablesen.
Hierbei bemerken wir, dass der Eigenwert $\lambda_1$ die algebraische Vielfachheit $2$ und der Eigenwert $\lambda_2$ die algebraische Vielfachheit $1$ besitzt.
Außerdem kann man die zugehörigen Eigenräume wie folgt bestimmen:
\begin{equation*}
\Eig(A; \lambda_1) \ = \ \left\{ \alpha\cdot\!\!\begin{pmatrix} 1 \\ 1 \\ 2 \end{pmatrix} \ | \ \alpha \in \mathbb{R} \right\},
\quad
\Eig(A; \lambda_2) \ = \ \left\{ \alpha\cdot\!\!\begin{pmatrix} 1 \\ 2 \\ 3 \end{pmatrix} \ | \ \alpha \in \mathbb{R} \right\}.
\end{equation*}
Wir sehen also, dass die geometrischen Vielfachheiten der Eigenwerte $\lambda_1, \lambda_2 \in \mathbb{R}$ jeweils 1 betragen und somit die algebraische Vielfachheit von $\lambda_1$ nicht mit der geometrischen Vielfachheit übereinstimmt.
Daraus folgt mit Satz {prf:ref}`satz:diagonalisierbarkeit`, dass die Matrix $A$ nicht diagonalisierbar ist.
````

Das folgende Beispiel untersucht wann eine allgemeine  $(2 \times 2)$-Matrix $A \in \mathbb{R}^{2 \times 2}$ nicht diagonalisierbar ist.
\begin{example}
Sei $A \in \mathbb{R}^{2 \times 2}$ eine quadratische Matrix mit
\begin{equation*}
A \ \coloneqq \
\begin{pmatrix}
a & b\\
c & d
\end{pmatrix}
\end{equation*}
für $a,b,c,d \in \mathbb{R}$.
Um zu untersuchen wann $A$ nicht diagonalisierbar ist, betrachten wir das charakteristische Polynom $P_A$ von $A$ mit
\begin{equation*}
\begin{split}
P_A(t) \ &= \ \det(A - t I_2) \ = \ \det
\begin{pmatrix}
a-t & b\\
c & d-t
\end{pmatrix}
\ = \ (a-t)(d-t) - bc \\
&= \ t^2 - (a+d)t + (ad - bc).
\end{split}
\end{equation*}
Um die Nullstellen des charakteristischen Polynoms zu bestimmen verwenden wir in diesem einfachen Fall die $p$-$q$-Formel mit $p \coloneqq -(a+d)$ und $q \coloneqq (ad - bc)$, so dass für die Eigenwerte von $A$ gilt
\begin{equation*}
\lambda_{1/2} \ = \ - \frac{p}{2} \pm \sqrt{\frac{p^2}{4} - q} \ = \ \frac{(a+d)}{2} \pm \sqrt{\frac{(a+d)^2}{4} - (ad - bc)}.
\end{equation*}
Wir bemerken zuerst, dass der Radikand $R$ unter der Wurzel von der folgenden Form ist
\begin{equation*}
R \ = \ \frac{(a+d)^2}{4} - (ad - bc) \ = \ \frac{\tr(A)^2}{4} - \det(A).
\end{equation*}
Nun macht es Sinn eine Fallunterscheidung nach dem Vorzeichen von $R$ zu machen.

1. Falls $R > 0$ gilt, so existieren zwei Lösungen der quadratischen Gleichung und somit zwei verschiedene Eigenwerte $\lambda_1 \neq \lambda_2$ von $A$.
Nach Korollar {prf:ref}`cor:eigenwerte_verschieden` wissen wir, dass $A$ dann schon diagonalisierbar ist.
2. Falls $R < 0$ gilt, so liegt die Wurzel nicht mehr im Körper $\mathbb{R}$ und somit gibt es keine reellen Eigenwerte von $A$.
Für diesen Fall ist $A$ nicht diagonalisierbar.
3. Der spannende Fall tritt ein für $R = 0$.
Hier besitzt die Matrix $A$ nur einen Eigenwert $\lambda \ = \ \frac{(a+d)}{2}$ mit algebraischer Vielfachheit $2$.
Nach Satz {prf:ref}`satz:diagonalisierbarkeit` ist $A$ genau dann diagonalisierbar, wenn die geometrische Vielfachheit des zugehörigen Eigenraums $\Eig(A; \lambda)$ auch $2$ beträgt.
Wir betrachten also den Eigenraum zum Eigenwert $\lambda$ im Folgenden.
\begin{equation*}
\Eig(A; \lambda) \ = \ \Kern(A - \lambda I_2)  \ = \ \Kern(A - \frac{(a+d)}{2} I_2) \ = \ \Kern
\begin{pmatrix}
\frac{(a-d)}{2} & b\\
c & \frac{(d-a)}{2}
\end{pmatrix}.
\end{equation*}
Wir versuchen also folgendes lineares Gleichungssystem für einen unbekannten Vektor $x = (x_1, x_2)^T \in \mathbb{R}^2$ zu lösen:
\begin{equation*}
\begin{pmatrix}
\frac{(a-d)}{2} & b\\
c & \frac{(d-a)}{2}
\end{pmatrix}
\begin{pmatrix}
x_1\\
x_2
\end{pmatrix} \ = \
\begin{pmatrix}
0 \\
0
\end{pmatrix}.
\end{equation*}
Mittels Gaußschen-Eliminationsverfahren bringen wir die Matrix in eine obere, rechte Dreiecksgestalt und erhalten so:
\begin{equation*}
\begin{pmatrix}
c\frac{(a-d)}{2} & bc\\
0 & \frac{-(a-d)^2}{4} - bc
\end{pmatrix}
\begin{pmatrix}
x_1\\
x_2
\end{pmatrix} \ = \
\begin{pmatrix}
0 \\
0
\end{pmatrix}.
\end{equation*}
Wir erkennen, dass der Eintrag unten, rechts in der Matrix von folgender Gestalt ist:
\begin{equation*}
\begin{split}
\frac{-(a-d)^2}{4} - bc \ &= \ \frac{-a^2 + 2ad - d^2}{4} - bc \ = \ \frac{-a^2 - 2ad - d^2}{4} + (ad - bc) \\
&= \  \frac{-(a+d)^2}{4} + (ad - bc) \ = \ -\frac{\tr(A)^2}{4} + \det(A) \ = \ -R \ = \ 0.
\end{split}
\end{equation*}
Das bedeutet, dass wir zur Bestimmung des Kern Lösungen des folgenden Gleichungssystems bestimmen müssen.

```{math}
:label: eq:bsp_nicht_diagonalisierbar
\begin{pmatrix}
c\frac{(a-d)}{2} & bc\\
0 & 0
\end{pmatrix} 
\begin{pmatrix}
x_1\\
x_2
\end{pmatrix} \ = \ 
\begin{pmatrix}
0 \\
0
\end{pmatrix}.
```

Auch hier gibt es zwei Möglichkeiten.
Falls die Matrix $A$ bereits in Diagonalgestalt ist, so steht ihr Eigenwert $\lambda$ auf der Hauptdiagonalen und es gilt $a = d = \lambda$ und $b = c = 0$.
Wie man leicht einsieht ist die Matrix in {eq}`eq:bsp_nicht_diagonalisierbar` dann die Nullmatrix und jeder Vektor $x \in \mathbb{R}^2$ löst das lineare Gleichungssystem.
Also ist der Kern bereits der gesamte Vektorraum $V = \mathbb{R}^2$ und die geometrische Vielfachheit des Eigenwerts $\lambda$ ist in der Tat $2$.
Damit ist die Matrix trivialerweise diagonalisierbar.

In allen anderen Fällen können wir den Eigenraum explizit angeben als
\begin{equation*}
\Eig(A; \lambda) \ = \ \lin( \lbrace{ \begin{pmatrix} bc \\ -c \frac{(a-d)}{2} \end{pmatrix} \rbrace} ).
\end{equation*}
Der Eigenraum $\Eig(A; \lambda)$ hat also die Dimension $1$ und somit stimmen geometrische Vielfachheit und algebraische Vielfachheit nicht überein.
Nach Satz {prf:ref}`satz:diagonalisierbarkeit` ist die Matrix $A$ also nicht diagonalisierbar.

Um ein konkretes Beispiel für den dritten Fall der Fallunterscheidung oben anzugeben, müssen wir eine Matrix $A \in \mathbb{R}^{2 \times 2}$ konstruieren, so dass $R = 0$ ist, bzw., so dass gilt $\tr(A)^2 = 4 \det(A)$.
Hierzu betrachten wir die folgende Matrix
\begin{equation*}
A \ \coloneqq \
\begin{pmatrix}
3 & -1\\
1 & 1
\end{pmatrix}.
\end{equation*}
Wir sehen sofort ein, dass gilt
\begin{equation*}
\tr(A)^2 \ = \ (3 + 1)^2 \ = \ 16 \ = \ 4 \cdot (3\cdot1 - (-1)\cdot 1) \ = \ 4 \det(A).
\end{equation*}
Mit unseren allgemeinen Vorüberlegungen oben, können wir den Eigenwert $\lambda$ von $A$ angeben als
\begin{equation*}
\lambda \ = \ -\frac{a + d}{2} \ = \ -\frac{3+1}{2} \ = \ -2.
\end{equation*}
Und der Eigenraum $\Eig(A; -2)$ von $A$ wird aufgespannt durch den Vektor
\begin{equation*}
\begin{pmatrix}
bc \\
-c \frac{(a-d)}{2}
\end{pmatrix}
\ = \
\begin{pmatrix}
-1\cdot 1 \\
-1 \cdot \frac{(3-1)}{2}
\end{pmatrix}
\ = \ \begin{pmatrix}
-1 \\
-1
\end{pmatrix}.
\end{equation*}
Die Matrix $A$ ist nach Satz {prf:ref}`satz:diagonalisierbarkeit` nicht diagonalisierbar, da geometrische und algebraische Vielfachheit des Eigenwerts $\lambda = -2$ nicht übereinstimmen.
\end{example}

Sollte eine quadratische Matrix $A \in \mathbb{K}^{n \times n}$ diagonalisierbar sein, so hat die reguläre Matrix $S^{-1} \in \GL(n; \mathbb{K})$ in {eq}`eq:aehnlichkeit` eine besondere Gestalt, wie das folgende Lemma zeigt.

````{prf:lemma}
:label: lem:eigenvektoren_spalten

Sei $A \in \mathbb{K}^{n \times n}$ eine diagonalisierbare Matrix.
In diesem Fall sind die Spaltenvektoren von $S^{-1}$ gerade die Eigenvektoren der zugehörigen Eigenwerte auf der Diagonalen von $D$. 
````

````{prf:proof}
Da $A$ diagonalisierbar ist existiert eine Diagonalmatrix $D \in \mathbb{K}^{n\times n}$ und eine reguläre Matrix $S \in \GL(n; \mathbb{K})$, so dass $SAS^{-1} = D$ gilt. 
Aus Lemma {prf:ref}`lem:aehnlich_polynom` wissen wir, dass die Eigenwerte $\lambda_1, \ldots, \lambda_n$ von $A$ durch die Einträge auf der Diagonalen von $D$,  gegeben sind.
Durch Multiplikation mit der Matrix $S^{-1}$ von links erhalten wir also:
\begin{equation*}
\underbrace{S^{-1} S}_{= I_n} A S^{-1} \ = \ A S^{-1} \ = \ S^{-1} D. 
\end{equation*}
Wir sehen also, dass $A S^{-1} = S^{-1} D$ gilt.
Sei nun $v_k \in \mathbb{K}^{n}$ die $k$-te Spalte von $S^{-1}$ mit $1 \leq k \leq n$, dann sieht man ein, dass gilt
\begin{equation*}
A v \ = \ \lambda_k v_k, \quad \text{ für alle } 1 \leq k \leq n.
\end{equation*}
Nach Definition {prf:ref}`def:eigenwert` ist der Vektor $v_k$ also gerade der Eigenvektor zum Eigenwert $\lambda_k$ von $A$.
````

Im folgenden Beispiel wollen wir diagonalisierbare $(2\times 2)$-Matrizen untersuchen und die Beobachtung aus Lemma {prf:ref}`lem:eigenvektoren_spalten` verifizieren.

````{prf:example}
Wir betrachten zwei Beispiele von $(2 \times 2)$-Matrizen, für die wir eine ähnliche Diagonalmatrix $D$ berechnen wollen, auf deren Hauptdiagonalen die zugehörigen Eigenwerte stehen.

* Für eine Matrix der Form
\begin{equation*}
A \ = \
\begin{pmatrix}
-1 & 6 \\
-1 & 4
\end{pmatrix}
\end{equation*}
bestimmen wir das charakteristische Polynom $P_A$ als
\begin{equation*}
P_A(t) \ = \ \det(A - tI_2) \ = \ (-1 - t)(4 - t) + 6 \ = \ t^2 - 3t + 2 \ = \ (t - 1)(t - 2).
\end{equation*}
Wir sehen also, dass das charakteristische Polynom $P_A$ in Linearfaktoren zerfällt und die Eigenwerte von $A$ gegeben sind durch $\lambda_1 = 1$ und $\lambda_2 = 2$.
Es ist auf Grund von Satz {prf:ref}`satz:diagonalisierbarkeit` klar, dass $A$ diagonalisierbar ist, d.h., dass es eine reguläre Matrix $S \in \GL(2; \mathbb{K})$ gibt, so dass $S A S^{-1} = D$ gilt.
Die Diagonalmatrix $D$ ist damit bis auf Permutation der Hauptdiagonale eindeutig bestimmt als
\begin{equation*}
D \ = \
\begin{pmatrix}
1 & 0\\
0 & 2
\end{pmatrix}.
\end{equation*}

Aus {prf:ref}`lem:eigenvektoren_spalten` wissen wir, dass die Spalten von $S^{-1}$ gerade die Eigenvektoren von $A$ sind.
Für die Bestimmung der Eigenräume $\Eig(A; \lambda_1)$ und $\Eig(A; \lambda_2)$ lösen wir die beiden homogenen Gleichungssysteme
\begin{eqnarray*}
\begin{pmatrix}
-2 & 6 \\
-1 & 3
\end{pmatrix} 
\begin{pmatrix}
v_1 \\
v_2
\end{pmatrix} \ = \ (A - \lambda_1 I_2) \vec{v} = \vec{0}, \\
\begin{pmatrix}
-3 & 6 \\
-1 & 2
\end{pmatrix} 
\begin{pmatrix}
v_1 \\
v_2
\end{pmatrix} \ = \ (A - \lambda_2 I_2) \vec{v} = \vec{0}.
\end{eqnarray*}
Wir sehen direkt, dass die jeweiligen Zeilen der beiden Matrizen linear abhängig sind und man den Eigenvektor zum Eigenwert $\lambda_1=1$ angeben kann als $v = (3, 1)^T$ bzw. den Eigenvektor zum Eigenwert $\lambda_2=2$ als $v = (2, 1)^T$.
Schreiben wir die Eigenvektoren als Spalten der Matrix $S^{-1}$, so erhalten wir
\begin{equation*}
S^{-1} \ = \
\begin{pmatrix}
3 & 2\\
1 & 1
\end{pmatrix}
\end{equation*}
Der Vollständigkeit halber bestimmen wir nun noch die Inverse $S$ zu $S^{-1}$ durch die Determinanten-Regel:
\begin{equation*}
S \ = \ (S^{-1})^{-1} \ = \
\begin{pmatrix}
3 & 2\\
1 & 1
\end{pmatrix}^{-1}
\ = \ \frac{1}{3\cdot 1 - 2\cdot 1}
\begin{pmatrix}
1 & -2\\
-1 & 3
\end{pmatrix} 
\ = \
\begin{pmatrix}
1 & -2\\
-1 & 3
\end{pmatrix}.
\end{equation*}
Wir überprüfen unsere Rechnung abschließend durch das Diagonalisieren von $A$ als
\begin{equation*}
S A S^{-1} \ = \
\begin{pmatrix}
1 & -2\\
-1 & 3
\end{pmatrix}
\begin{pmatrix}
-1 & 6 \\
-1 & 4
\end{pmatrix}
\begin{pmatrix}
3 & 2\\
1 & 1
\end{pmatrix}
\ = \
\begin{pmatrix}
1 & 0\\
0 & 2
\end{pmatrix}
\ = \ D.
\end{equation*}

* Für eine Spiegelmatrix der Form
\begin{equation*}
A \ = \
\begin{pmatrix}
\cos \alpha & \sin \alpha \\
\sin \alpha & -\cos \alpha
\end{pmatrix}
\end{equation*}
berechnen wir das charakteristische Polynom $P_A$ als
\begin{equation*}
\begin{split}
P_A(t) \ &= \ \det(A - tI_2) \ = \ - (\cos \alpha - t)(\cos \alpha + t) - \sin^2 \alpha \ = \ t^2 - \cos^2 \alpha - \sin^2 \alpha \\
&= \ t^2 - \underbrace{(\sin^2 \alpha + \cos^2 \alpha)}_{=1} \ = \ t^2 - 1 \ = \ (t - 1)(t + 1).
\end{split}
\end{equation*}
Wir sehen also, dass das charakteristische Polynom $P_A$ in Linearfaktoren zerfällt und die Eigenwerte dieser allgemeinen Spiegelmatrix unabhängig sind von der Wahl des Winkels $\alpha \in [0, 2\pi)$ immer $\lambda_1 = 1$ und $\lambda_2 = -1$.
Es ist auf Grund von Satz {prf:ref}`satz:diagonalisierbarkeit` klar, dass $A$ diagonalisierbar ist, d.h., dass es eine reguläre Matrix $S \in \GL(2; \mathbb{K})$ gibt, so dass $S A S^{-1} = D$ gilt.
Die Diagonalmatrix $D$ ist damit bis auf Permutation der Hauptdiagonale eindeutig bestimmt als
\begin{equation*}
D \ = \
\begin{pmatrix}
1 & 0\\
0 & -1
\end{pmatrix}.
\end{equation*}

Aus Lemma {prf:ref}`lem:eigenvektoren_spalten` wissen wir, dass die Spalten von $S^{-1}$ gerade die Eigenvektoren von $A$ sind.
Für die Bestimmung der Eigenräume $\Eig(A; \lambda_1)$ und $\Eig(A; \lambda_2)$ lösen wir die beiden homogenen Gleichungssysteme
\begin{eqnarray*}
\begin{pmatrix}
\cos \alpha - 1 & \sin \alpha \\
\sin \alpha & -\cos \alpha - 1
\end{pmatrix} 
\begin{pmatrix}
v_1 \\
v_2
\end{pmatrix} \ = \ (A - \lambda_1 I_2) \vec{v} = \vec{0}, \\
\begin{pmatrix}
\cos \alpha + 1 & \sin \alpha \\
\sin \alpha & -\cos \alpha + 1
\end{pmatrix} 
\begin{pmatrix}
v_1 \\
v_2
\end{pmatrix} \ = \ (A - \lambda_2 I_2) \vec{v} = \vec{0}.
\end{eqnarray*}
Durch Multiplikation der unteren Zeile mit dem ersten Eintrag der ersten Zeile sieht man, dass beide Zeilen linear abhängig sind und man kann die Eigenvektoren als Lösungen der obigen Gleichungen ablesen.
Für den Eigenwert $\lambda_1 = 1$ erhält man den zugehörigen Eigenvektor $\vec{v}_1 = (\sin^2 \alpha, \sin \alpha [1 - \cos \alpha])^T$ und für den zweiten Eigenwert $\lambda_2 = -1$ erhält man entsprechend den zugehörigen Eigenvektor $\vec{v}_2 = (\sin^2 \alpha, -\sin \alpha [1 + \cos \alpha])^T$.
Damit ist die Transformationsmatrix $S^{-1}$ gegeben durch
\begin{equation*}
S^{-1} \ = \ 
\begin{pmatrix}
\sin^2 \alpha & \sin^2 \alpha\\
\sin \alpha(1-\cos \alpha) & -\sin \alpha(1 +\cos \alpha)
\end{pmatrix}.
\end{equation*}
Das Bestimmen der Transformationsmatrix $S$ und die Überprüfung der Diagonalisierung von $A$ überlassen wir an dieser Stelle der geneigten Leserin und machen dafür folgende Beobachtung.
Die Vektoren $\vec{v}_1, \vec{v}_2 \in \mathbb{R}^2$ bilden eine Orthogonalbasis von $\mathbb{R}^2$, da gilt:
\begin{equation*}
\begin{split}
\langle \vec{v}_1, \vec{v}_2 \rangle \ &= \ \langle (\sin^2 \alpha, \sin \alpha [1 - \cos \alpha])^T,  (\sin^2 \alpha, -\sin \alpha [1 + \cos \alpha])^T \rangle \\
\ &= \ \sin^4 \alpha - \sin \alpha (1 - \cos \alpha) \cdot \sin \alpha (1 + \cos \alpha)\\
\ & = \ \sin^4 \alpha - \sin^2 \alpha \underbrace{(1 - \cos^2 \alpha)}_{= \sin^2 \alpha} \ = \ \sin^4 \alpha - \sin^4 \alpha \ = \ 0.
\end{split}
\end{equation*}
````
