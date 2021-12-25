---
# Титульный лист
title: |
    Отчёт по лабораторной работе №7  
    Дискретное логарифмирование в конечном поле
author:
- "Студент: Агеева Анастасия Сергеевна, 1032212304"
- "Группа: НФИмд-02-21"
- "Преподаватель: Кулябов Дмитрий Сергеевич,"
- "д-р.ф.-м.н., проф."
date: "Москва 2021"

# Generic otions
lang: ru-RU
toc-title: "Содержание"

# Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

# Pdf output format
toc: true # Содержание
toc_depth: 2
lof: true # Список изображений
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
### Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric

## Misc options
indent: true
header-includes:
  - \linepenalty=10 # the penalty added to the badness of each line within a paragraph (no associated penalty node) Increasing the value makes tex try to have fewer lines in the paragraph.
  - \interlinepenalty=0 # value of the penalty (node) added after each line of a paragraph.
  - \hyphenpenalty=50 # the penalty for line breaking at an automatically inserted hyphen
  - \exhyphenpenalty=50 # the penalty for line breaking at an explicit hyphen
  - \binoppenalty=700 # the penalty for breaking a line at a binary operator
  - \relpenalty=500 # the penalty for breaking a line at a relation
  - \clubpenalty=150 # extra penalty for breaking after first line of a paragraph
  - \widowpenalty=150 # extra penalty for breaking before last line of a paragraph
  - \displaywidowpenalty=50 # extra penalty for breaking before last line before a display math
  - \brokenpenalty=100 # extra penalty for page breaking after a hyphenated line
  - \predisplaypenalty=10000 # penalty for breaking before a display
  - \postdisplaypenalty=0 # penalty for breaking after a display
  - \floatingpenalty = 20000 # penalty for splitting an insertion (can only be split footnote in standard LaTeX)
  - \raggedbottom # or \flushbottom
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text

  - \usepackage{titling}
  - \setlength{\droptitle}{-9em}
  - \pretitle{\begin{center}
      \textbf{РОССИЙСКИЙ УНИВЕРСИТЕТ ДРУЖБЫ НАРОДОВ}\\
      \textbf{Факультет физико-математических и естественных наук}\\
      \textbf{Кафедра прикладной информатики и теории вероятностей}
      \vspace{9cm}
      \LARGE\\}
  - \posttitle{\vskip 1em \Large \emph{\textit{Дисциплина$:$ Математические основы защиты информации и информационной безопасности}} \end{center}}
  - \preauthor{\vskip 3em \begin{flushright} \large \begin{tabular}[t]{c}}
  - \postauthor{\end{tabular}\par\end{flushright} \vfill \vskip 5em}
---

# Цель работы

Цель данной лабораторной работы изучение задачи и алгоритмов дискретного логарифмирования в конечном поле.

# Задание

1.  Реализовать программно алгоритм, реализующий p-метод Полларда для задач дискретного логарифмирования.

# Теоретическое введение

## $\rho$-алгоритм Полларда

**$\rho$-алгоритм ($\rho$-алгоритм)** — предложенный Джоном Поллардом в 1975 году алгоритм, служащий для факторизации (разложения на множители) целых чисел. Данный алгоритм основывается на алгоритме Флойда поиска длины цикла в последовательности и некоторых следствиях из парадокса дней рождения. Алгоритм наиболее эффективен при факторизации составных чисел с достаточно малыми множителями в разложении [@rho]. 

Сложность алгоритма оценивается как $O(N^{1/4})$.

$\rho$-алгоритм Полларда строит числовую последовательность, элементы которой образуют цикл, начиная с некоторого номера n, что может быть проиллюстрировано, расположением чисел в виде греческой буквы $\rho$, что послужило названием семейству алгоритмов.

### Современная версия

Пусть $N$ составное целое положительное число, которое требуется разложить на множители. Алгоритм выглядит следующим образом:
Случайным образом выбирается небольшое число $x_{0}$ и строится последовательность $\{x_{n}\},n=0,1,2,...$, определяя каждое следующее как $x_{n+1}=F(x_{n})\,(\mathrm {mod} \,\,N)$.

Одновременно на каждом i-ом шаге вычисляется $d=\mathrm {GCD} (N,|x_{i}-x_{j}|)$ для каких-либо $i$, $j$ таких, что $j<i$, например, $i=2j$.
Если $d>1$, то вычисление заканчивается, и найденное на предыдущем шаге число $d$ является делителем $N$. Если $N/d$ не является простым числом, то процедуру поиска делителей продолжается, взяв в качестве $N$ число $N'=N/d$.

На практике функция $F(x)$ выбирается не слишком сложной для вычисления (но в то же время не линейным многочленом), при условии того, что она не должна порождать взаимно однозначное отображение. Обычно в качестве $F(x)$ выбираются функции $F(x)=x^{2}\pm 1(\mathrm {mod} \,N)$ или $F(x)=x^{2}\pm a(\mathrm {mod} \,N)$. Однако функции $x^{2}-2$ и $x^{2}$ не подходят.

Если известно, что для делителя $p$ числа $N$ справедливо $p\equiv 1\,(\mathrm {mod} \,k)$ при некотором $k>2$, то имеет смысл использовать $F(x)=x^{k}+b$.

Существенным недостатком алгоритма в такой реализации является необходимость хранить большое число предыдущих значений $x_{j}$.

## Алгоритмы для дискретного логарифмирования

Существуют три различных категории алгоритмов для вычисления дискретных логарифмов [@categories]:

1. Алгоритмы, которые работают для произвольных групп, т.е. они не используют какие-либо специфические свойства групп. К этой категории относятся метод «шаги младенца – шаги гиганта» Шэнкса, $\rho$-метод Полларда (аналог метода $\rho$-факторизации Полларда) и $\lambda$-метод (также известный как «дикие и ручные кенгуру»).
2. Алгоритмы, которые хорошо работают в конечных группах, для которых порядок групп не имеет больших простых множителей. Хорошо известный алгоритм Сильвера – Поляга – Хеллмана, основанный на китайской теореме об остатках, относится к этой категории.
3. Алгоритмы, которые используют методы представления групповых элементов как продуктов элементов из относительно небольшого набора (также используя китайскую теорему об остатках); типичными алгоритмами в этой категории являются алгоритм исчисления индекса Адлемана и алгоритм NFS Гордона.

# Выполнение лабораторной работы

1. **Реализация p-метода Полларда**

   1. Задам функцию $f()$, обладающую сжимающими свойствами, в которую буду передавать числа $c$, $u$ и $v$.

      ![Сжимающая функция f](image/f_x.jpg){#fig:001 width="70%"}

   2. Задам функцию $discrlog()$, в которую буду передавать параметры, необходимые для вычисления . По алгоритму, реализующему p-метода Полларда для задач дискретного логарифмирования, осуществляется нахождение показателя $x$, для которого верно $a^{x}\equiv b{\pmod {p}}$. В качестве результата возвращается показатель степени $x$. Вызову функцию для чисел $p = 107$, $a = 10$, $r = 53$, $b = 64$, $u = 2$ и $v = 2$. Алгоритм верно находит показатель степени $x = 20$.

      ![Результаты p-метода Полларда](image/discrlog.jpg){#fig:002 width="70%"}
      
      

# Выводы

В ходе данной лабораторной работы я реализовала программно $/rho$-метод Полларда для задач дискретного логарифмирования.

# Список литературы {#список-литературы .unnumbered}

::: {#refs}
:::
