Optimierung
============================

In der Physik spielt Optimierung eine wesentliche Rolle bei der Modellierung von Energiezuständen auf unterschiedlichen Skalen:
Moleküle formieren sich in einer Art, die die Gesamtenergie des Teilchensystems unter Berücksichtigung aller wechselseitigen Kräfte minimiert.
Gleichzeitig strebt das Universum mit all seinen Planeten, Sternen und Galaxien nach einem Zustand von maximaler Verteilung, beschrieben durch die thermodynamische Größe der Entropie.
Auch hier folgt die Zunahme der Entropie dem Prinzip der Energieminimierung des Gesamtsystems.

Menschen betreiben seit jeher Optimierung in den verschiedensten Anwendungen, oft mit unterschiedlichen Motivationen. Flugzeuge werden von Ingenieuren so entworfen und gebaut, dass sie möglichst stromlinienförmig aussehen, um damit den Reibungswiderstand in der Luft zu minimieren und gleichzeitig den nötigen Auftrieb für einen sicheren Flug zu erzeugen. Fondmanager streben danach Portfolios zu erstellen, deren Gewinn möglichst maximal ist und dennoch Spekulationsrisiken vermeiden.

Im Folgenden wollen wir die mathematischen Grundlagen zur Untersuchung von allgemeinen Optimierungsproblemen einführen. 
Wir beginnen mit der Definition des allgemeinen Optimierungsproblems, welches wir im weiteren Verlauf noch näher spezifizieren werden.

````{prf:definition} definition
label: Allgemeines Optimierungsproblem

Sei $\Omega \subset \mathbb{R}^n$ eine offene, zusammenhängende Teilmenge und sei $F \colon \Omega \rightarrow \mathbb{R}$ eine reellwertige Funktion, welche wir _Zielfunktion_ nennen. Unser Ziel ist es einen unbekannten Vektor $x \in \Omega$, auch _Parametervektor_ genannt, zu finden, welcher das folgende _allgemeine Optimierungsproblem_ löst.

```{math}
:label: eq:optimierungsproblem_allgemein
\min_{x \in \Omega} F(x) \quad \text{ mit } \quad
\begin{cases}
\ c_i(x) \ = \ 0, \quad &i \in \mathcal{E},\\
\ c_j(x) \ \geq \ 0, \quad &j \in \mathcal{I}.
\end{cases}
```

Die reellwertigen Funktionen $c_i, c_j \colon \Omega \rightarrow \mathbb{R}$ bilden einen Vektor von _Nebenbedingungen_, welcher das Optimierungsproblem restringiert. Die Indexmengen $\mathcal{E}$ und $\mathcal{I}$ legen hierbei fest, ob es ich bei der jeweiligen Nebenbedingung um eine Gleichung oder eine Ungleichung handelt.
````

Zur Veranschaulichung betrachten wir ein zweidimensionales Beispiel für ein beschränktes, nichtlineares Optimierungsproblem.

````{prf:example}
:label: bsp:allgemeines_optimierungsproblem

Wir interessieren uns für das folgende Optimierungsproblem
\begin{equation*}
\min_{x \in \mathbb{R}^2}~(x_1 - 2)^2 + (x_2 - 1)^2
\end{equation*}
unter den Nebenbedingungen $x_1^2 - x_2 \leq 0$ und $x_1 + x_2 \leq 2$.
Wir können dieses Problem in die allgemeine Form des Optimierungsproblems \eqref{eq:optimierungsproblem_allgemein} umschreiben als:
\begin{equation*}
\min_{x \in \mathbb{R}^2} F(x) \ = \ \min_{x \in \mathbb{R}^2} (x_1 - 2)^2 + (x_2 - 1)^2 \quad \text{ mit } \quad
\begin{cases}
\ c_1(x) \ = \ -x_1^2 + x_2 \ \geq \ 0,\\
\ c_2(x) \ = \ -x_1 - x_2 + 2 \ \geq \ 0.
\end{cases}
\end{equation*}
Hierbei gilt für die Indexmengen $\mathcal{I} = \lbrace 1,2 \rbrace$ und $\mathcal{E} = \emptyset$.
Visualisiert man die Niveaulinien der Zielfunktion $F$ zusammen mit den Nebenbedingungen, so sieht man, dass das globale Minimum der quadratischen Funktion $F$, nämlich $x = (x_1, x_2)^T = (2,1)^T$, nicht in der erlaubten Menge der Parameter liegt, welche durch die Nebenbedingungen beschrieben ist. 
Trotzdem existiert ein eindeutiges globales Minimum des beschränkten Optimierungsproblems, nämlich $x = (x_1, x_2)^T = (1,1)^T$.
````

Neben der Unterscheidung von Optimierungsproblemen in beschränkte und unbeschränkte Formulierungen, lassen sich noch weitere Kriterien zur Charakterisierung eines Optimierungsproblems heran ziehen:

* _Anzahl der unbekannten Parameter_, z.B. groß oder klein,

* _Eigenschaften der Zielfunktion_, z.B. Linearität, Konvexität, Differenzierbarkeit,

* _Charakteristik des Optimums_, z.B. Sattelpunkt, lokales oder globales Optimum,

* _Modelleigenschaften_, z.B. stochastisch oder deterministisch,

* _Wertebereich_, z.B. diskret oder kontinuierlich
