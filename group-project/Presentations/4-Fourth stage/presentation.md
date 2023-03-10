---
## Front matter
lang: ru-RU
title: "Групповой проект. Этап 3"
subtitle: "Рост дендритов"
author: |
	Дорук Мерич, 
	Мухамедиар Адиль,
	Яссин Мохамад Аламин,
	Акуленко Максим


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

---

# Цели и задачи группового проекта

**Цель проекта:** На основе построения модели роста
дендритов, изучить принципы математического
моделирования. 

## Цели и задачи группового проекта 

**Задачи проекта:**   
1. изучить теоретическую информацию о дендритах и о
моделях их роста;
2. разработать алгоритмы
3. написать программу, взяв в основу разработанные ранее алгоритмы;
4. проанализировать полученные результаты.

# Что есть дендриды?

**Дендриты** (*от гр. $\tau o$ $\delta\varepsilon\nu\delta\rho o\nu$* - *дерево*) - термин широкого употребления, которым обозначаются различные древовидные ветвистые образования.

# Формирование дендрида

**Дендрит** - ветвящееся и расходящееся в стороны образование, возникающее при ускоренной или стеснённой кристаллизации в неравновесных условиях, когда кристалл расщепляется по определённым законам.

**Дендритный рост** -  процесс образования дендрита. 

**Свойства дендриов:**   
- шороховатая поверхность(микроуровень)    
- выраженая структура(Большой масштаб)  
- отсутсвие четко выраженных граней

## Формирование дендрида

![Физические фрактальные кластеры: осаждение металла при электролизе, «вязкие пальцы», электрический разряд](1.png)

## Формирование дендрида

![Дендриты в зольнхофенском известняке (мрамор)](3.jpg)

## Формирование дендрида

![Кристалы йода](2.jpg)

# Основные понятия и уравнения

## Физические свойства вещества

- $\rho$ - плотность  
- $L$ - удельная теплота плавления на единицу массы  
- $c_\mathit{p}$ - теплоемкость при постоянном давление (также на единицу массы)  
- $k$ - коэфицент теплопроводности  
- $T_m$ - температура плавления   
- $T_\infty < T_m$  

**Симметричная модель** - теплопроводность и плотность на зависят от температуры и одинаковы как для твердой, так и для житкой фазы. 

## Основные уравнения

**Безразмерное переохлаждение**

$$S = c_p(T_m-T_\infty)$$

- $S \geq 1$  - затвердивает весь расплав  
- $S < 1$ - затвердевает часть расплава 

**Уравнение теплопроводности**

$$\rho c_p \frac{\delta T}{\delta t } = \nabla^2T \equiv k\bigg(\frac{\delta^2T}{\delta x^2 }+\frac{\delta^2T}{\delta y^2 } \bigg) $$

# Скорость движения границы кристализации

$V$ - скорость кристализации

Масса вещества, затвердевающая за время  $\Delta t$ на участке польщадью $s$:  
$$\Delta m = \rho sV \Delta t$$

При кристализации выдкляется теплота:  
$$\Delta Q = \Delta m L$$

Суммарный поток тепла на границе:  
$$q = -k(\nabla T \mid_l-\nabla T \mid_s )$$

- $\nabla$ - *градиент*
- $l$ и $s$ относятся к жидкой (liquid) и твердой (solid) фазам

## Скорость движения границы кристализации

Должно выполнятся равенство:  
$$qs\Delta t = \Delta Q$$

Тогда выражение для скорости - **Условие Стефана**:

$$nV = \frac{k}{\rho L}n\big( \nabla T\mid_s - \nabla T \mid_l\big)$$,

*где*  
  **n** - вектор единичной длинны, перпендикулярный границе (вектор нормали)

# Изменение положения и формы границы затвердевания со временем. 

## Механизм, связанный с поверхностным натяжением 

**$T_b$** - температура на границе 

Добавка потенциальной энергии пропорциональна площади поверхности: $\Delta E_p = \gamma s$

где **$\gamma$** - коэффицент поверхности натяжения.

*Условие Гиббса - Томсона*:

$$T_b = T_m\bigg(1 - \frac{\gamma T_m}{\rho L^2R} \bigg)$$

**R** -  радиус кривзны в данной точке границы (для плоской поверхности $R = \infty$)

*Капилярный радиус*: $d_0 = \gamma T_m c_p/(\rho L^2)$

## Механизм замедления роста выступов

Влияние на температуру границы: $\Delta T_b =  - T_m\beta V$

**$\beta$** -кинетический коэфицент

Введем безразмерную температуру $\tilde{T} = c_p(T-T\infty)/L$. Тогда уравнение для $\tilde{T}$:

$$\frac{\delta \tilde{T}}{\delta t} = \chi \nabla^2 \tilde{T}$$

$\tilde{T} = 0$ везде, кроме затравки

$\chi = k/\rho c_p$ - *коэффицент температуропроводности*.

При затвердевании всего вещества $\tilde{T}$ повысится на единицу. В дальнейшем опустим ~ у $\tilde{T}$.

# Модель роста дендритов

Пусть у нас есть квадратная область размера $N * N$ узлов, в центре которой задана некоторая затравка.

$h = 1$ - расстояние между узлами по горизонтали и вертикал

$\Delta t = 1$ - шаг по времени

## Уравнение теплопроводности 

$$\nabla^2T\approx\frac{\langle T_{(i, j)}\rangle-T_{i,j}}{(4+4w)(1+2w)h^2}$$ 

где $0\leq w<1$ - коэффициент, учитывает влияние диагональных соседей

Общая формула для вычисления среднего значения температуры в соседних узлах: $\langle T_{(i, j)}\rangle=(T_{i+1,j}+T_{i-1,j}+T_{i,j+1}+T_{i,j-1}+w(T_{i+1,j+1})+T_{i+1,j-1}+T_{i-1,j+1}+T_{i-1,j-1}))/(4+4w)$

Новое значение температуры после каждого шага: $\hat{T}_{i,j}=T_{i,j}+\chi\Delta t\nabla^2T/m$, что устойчиво при $\chi\Delta t/(mh^2)<1/4$. 

## Рост дендритов 

Состояния каждого узла $n$:  
- $n=0$ - жидкая фаза  
- $n=1$ - твердая фаза  
- промежуточные состояния не учитываются

Всего может быть четыре ближайших соседа и четыре диагональных. 

$n=1$ у пяти соседей - *граница плоская*:

$$1/R\approx s_{i,j}=\displaystyle\sum_{1}^{}n_{i,j}+w_n\displaystyle\sum_{2}^{}n_{i,j}-(\frac{5}{2}+\frac{5}{2}w_n),$$

где **первая сумма** - по ближайшим соседям, **вторая** - по диагональным, **$0\leq w_n\leq1$** - коэффициент, учитывает ослабление влияния соседей с ростом расстояния.

## Рост дендритов

Также необходимо учитывать **тепловой шум**. 

В простейшем случае можно прибавлять к температуре в узле некоторую случайную добавку $n_{i,j}\delta$, где $n_{i,j}$ - случайное число, равномерно распределенное в интервале $[-1,1]$, а $\delta$ - величина флуктаций температуры.

Узел, расположенный на границе, меняет свое состояние с жидкого на твердое, если 

$$T\leq\tilde{T}_m(1+\eta_{i,j}\delta)+\lambda s_{i,j},$$

где $T_{m}$ - температура плавления, $\tilde{T}_m$ - безразмерное начальное переохлаждение, $\lambda$ - капиллярный радиус.
