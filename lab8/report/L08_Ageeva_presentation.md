---
## Front matter
lang: ru-RU
title: |
    Отчёт по лабораторной работе №8  
    Целочисленная арифметика многократной точности
author: |
    *Дисциплина: Математические основы защиты информации*  
    *и информационной безопасности*  
    \vspace{2pt}  
    **Студент:** Агеева Анастасия Сергеевна, 1032212304  
		**Группа:** НФИмд-02-21  
		**Преподаватель:** д-р.ф.-м.н., проф. Кулябов Дмитрий Сергеевич  
    \vspace{2pt}
date: 30 декабря, 2021, Москва

## Formatting
toc: false
slide_level: 2
theme: metropolis
header-includes:
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
 - '\makeatletter'
 - '\beamer@ignorenonframefalse'
 - '\makeatother'
aspectratio: 43
section-titles: true
linestretch: 1.25

mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.7
---

# Прагматика

## Прагматика данной лабораторной работы

- В рамках дисциплины "Математические основы защиты информации и информационной безопасности" нам необходимо изучить ее разделы. 
- Данная работа необходима для более глубоко и детального понимания работы алгоритмов шифрования.


# Цель

## Цель выполнения данной лабораторной работы

- Цель данной лабораторной работы изучение алгоритмов целочисленной арифметики многократной точности.

# Задачи

## Задачи выполнения данной лабораторной работы

1. Реализовать программно алгоритм сложения неотрицательных чисел;
2. Реализовать программно алгоритм вычитания неотрицательных чисел;
3. Реализовать программно алгоритм умножения неотрицательных целых чисел столбиком;
4. Реализовать программно алгоритм умножения "быстрый столбик";
5. Реализовать программно алгоритм деления многоразрядных целых чисел.

# Результаты выполнения данной лабораторной работы

## Вспомогательные функции (1)

![Импорт библиотеки math](image/import.jpg){#fig:001 width="90%"}

![Описание словарей](image/dicts.jpg){#fig:002 width="90%"}

![Перевод в десятичную систему счисления](image/to_10.jpg){#fig:003 width="90%"}

## Вспомогательные функции (2)

![Перевод в систему счисления с основанием $b$](image/to_b.jpg){#fig:004 width="90%"}

![Удаление/добаввление нулей](image/zeros.jpg){#fig:005 width="90%"}

## Сложение неотрицательных чисел

![Сложение](image/addition.jpg){#fig:006 width="90%"}

## Вычитание неотрицательных чисел

![Вычитание](image/substraction.jpg){#fig:007 width="90%"}

## Умножение неотрицательных целых чисел столбиком

![Умножение столбиком](image/column.jpg){#fig:008 width="90%"}

## Умножение  неотрицательных чисел быстрым столбиком

![Быстрый столбик](image/quick.jpg){#fig:009 width="90%"}

## Деление многоразрядных целых

![Деление](image/division.jpg){#fig:010 width="90%"}

## Выводы

- Исходя из теоретических сведений, программа выполнена без ошибок, чему свидетельствуют полученные результаты.
- В ходе данной лабораторной работы я реализовала программно 5 алгоритмов целочисленной арифметики многократной точности..
