# Das kanonische Skalarprodukt in $\mathbb{C}^n$

Bevor wir allgemeine Bilinear- und Sesquilinearformen einführen, wollen wir noch einen wichtigen Spezialfall behandeln, nämlich das kanonische Skalarprodukt in $\mathbb{C}^n$.

Wie bereits in Kapitel 2.2.7 {cite:p}`burger_2020` beschrieben, betrachten wir komplexe Zahlen $z \in \mathbb{C}$, die für $(a,b) \in \mathbb{R}^2$ dargestellt werden können als $z = a +ib$.  Das Produkt $z_1 \cdot z_2$ zweier komplexer Zahlen $z_1 = x_1 + i y_1$ und $z_2 = x_2 + i y_2$ ist definiert als

\begin{equation*}
z_1 \cdot z_2 \ = \ (x_1x_2 - y_1y_2) + i (x_1y_2 + x_2y_1).
\end{equation*}

Auch bekannt ist, dass der _Betrag_ $|z|$ von $z$ definiert ist als $|z|\coloneqq\sqrt{a^2 + b^2}$, was mit der in Definition {prf:ref}`def:norm_r` eingeführten Norm in $\mathbb{R}^2$ übereinstimmt.
Außerdem ist die komplexe Konjugation $\overline{z}$ von $z$ definiert als $\overline{z} \coloneqq a - bi$, das heißt wir vertauschen das Vorzeichen von $b \in \mathbb{R}$.

Mit diesen Eigenschaften können wir das kanonische Skalarprodukt in $\mathbb{C}^n$ einführen.

````{prf:definition} Skalarprodukt in $\mathbb{C}^n$
:label: def:skalarprodukt_c

Seien $z = (z_1, \ldots, z_n) \in \mathbb{C}^n$ und $w = (w_1, \ldots, w_n) \in \mathbb{C}^n$ zwei Vektoren.
Wir bezeichnen die Abbildung
\begin{equation*}
\begin{split}
\langle \cdot, \cdot \rangle_c \colon \mathbb{C}^n \times \mathbb{C}^n \ &\rightarrow \ \mathbb{C}, \\
(z,w) \ & \mapsto \ \langle z, w \rangle_c \ \coloneqq \ z_1\overline{w_1} + \ldots + z_n\overline{w_n} \ = \ \sum_{i=1}^n z_i \overline{w_i} 
\end{split}
\end{equation*}
als das _kanonische Skalarprodukt_ in $\mathbb{C}^n$.
Häufig wird das kanonische Skalarprodukt auch \emph{komplexes Skalarprodukt} genannt.
````

Der Index $c$ in der Notation des komplexen Skalarprodukts kann auch weggelassen werden, wenn aus dem Kontext ersichtlich ist, dass man es mit komplexen Zahlen rechnet.
Wir werden daher auch im Folgenden die vereinfachte Notation ohne den Index $c$ verwenden.

Folgende Eigenschaften des komplexen Skalarprodukts lassen sich leicht nachrechnen.

````{prf:lemma} Eigenschaften des Skalarprodukts
:label: lem:skalarprodukt_c

Das kanonische Skalarprodukt von $\mathbb{C}^n$ in Definition {prf:ref}`def:skalarprodukt_c` besitzt folgende Eigenschaften für Vektoren $z,z',w,w' \in \mathbb{C}^n$ und Skalare $\lambda \in \mathbb{C}$:

i) Sesquilinearität:
\begin{equation*}
\begin{split}
&\langle z +z', w \rangle \ = \ \langle z, w \rangle + \langle z', w \rangle, \quad \langle z, w + w' \rangle \ = \ \langle z, w \rangle + \langle z, w' \rangle, \\
& \langle \lambda z, w \rangle \ = \  \lambda \langle z, w \rangle, \quad \langle z, \lambda w \rangle \ = \  \overline{\lambda} \langle z, w \rangle.
\end{split}
\end{equation*}

ii) Hermitezität:
\begin{equation*}
\langle z, w \rangle \ = \ \overline{\langle w, z \rangle}.
\end{equation*}

iii) Positive Definitheit:
\begin{equation*}
\langle z, z \rangle \ = \ |z_1|^2 + \ldots + |z_n|^2 \ \in \mathbb{R}^+_0, \quad \langle z, z \rangle \ = \ 0 \ \Leftrightarrow \ z = \vec{0}.
\end{equation*}
````

Die dritte Eigenschaft von {prf:ref}`lem:skalarprodukt_c` erlaubt es uns den Begriff der Norm eines komplexwertigen Vektors in der folgenden Definition einzuführen.

````{prf:definition} Norm in $\mathbb{C}^n$
\labeldef:norm_c

Sei $z \in \mathbb{C}^n$ ein Vektor.
Dann definieren wir die Abbildung
\begin{align*}
||\cdot|| \ \colon \ \mathbb{C}^n \ &\rightarrow \ \mathbb{R}_0^+, \\
z \ &\to \ ||z|| \ \coloneqq \ \sqrt{\langle z, z \rangle} \ = \ \sqrt{|z_1|^2 + \ldots + |z_n|^2}
\end{align*}
als _Norm_ von $z$ in $\mathbb{C}^n$.
````

Besonders interessant ist die Beziehung zum kanonischen Skalarprodukt in $\mathbb{R}^n$.
Bezüglich der natürlichen Inklusion $\mathbb{R} \subset \mathbb{C}$ mit $x = x + i\cdot 0$ gibt es kein Problem.
Daher können wir $\mathbb{R}^n \subset \mathbb{C}^n$ betrachten und es wird klar, dass $\langle \cdot, \cdot \rangle_c$ eine natürliche Fortsetzung des kanonischen Skalarprodukts $\langle \cdot, \cdot \rangle$ in $\mathbb{R}^n$ ist.

Betrachten wir jedoch die Darstellung

```{math}
:label: eq:komplexe_abbildung

\begin{split}
\mathbb{R}^{2n} \ &\rightarrow \ \mathbb{C}^n, \\
v \ = \ (x_1, y_1, \ldots, x_n, y_n) \ & \mapsto \ (x_1 + i y_1, \ldots, x_n + i y_n) \ = \ z,
\end{split}
```

so können wir das komplexe Skalarprodukt in $\mathbb{C}^n$ in Relation zum kanonischen Skalarprodukt in $\mathbb{R}^{2n}$ wie folgt setzen.
Seien $v, v' \in \mathbb{R}^{2n}$ zwei Vektoren, denen die komplexen Vektoren $z, z' \in \mathbb{C}^n$ mit Abbildung {eq}`eq:komplexe_abbildung` entsprechen.
Dann können wir schreiben:
\begin{equation*}
\langle z, z' \rangle_c \ = \ \sum_{j=1}^n z_j \overline{z'_j} \ = \ \sum_{j=1}^n (x_jx'_j + y_jy'_j) - i \underbrace{\sum_{j=1}^n \det
\begin{pmatrix}
x_j & y_j\\
x'_j & y'_j
\end{pmatrix}}_{\eqqcolon \omega(v, v')}
\ = \ \langle v, v' \rangle - i \, \omega(v,v').
\end{equation*}
Auf Grund der Determinante innerhalb der Summe ist klar, dass $\omega(v, v') = - \omega(v',v)$ und $\omega(v,v) = 0$ gilt.

Wir erkennen also, dass das kanonische Skalarprodukt in $\mathbb{R}^{2n}$ gerade der Realteil des komplexen Skalarprodukts in $\mathbb{C}^n$ ist, zu dem noch ein alternierender Imaginärteil hinzukommt.
Da die Abbildung $\omega \colon \mathbb{R}^{2n} \times \mathbb{R}^{2n} \rightarrow \mathbb{R}$ für gleiche Vektoren verschwindet, stellen wir fest, dass das kanonische Skalarprodukt in $\mathbb{R}^{2n}$ und das komplexe Skalarprodukt in $\mathbb{C}^n$ die gleiche Norm induzieren.
