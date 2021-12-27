# Лекция 3, часть 2

Пусть есть, для простоты, два товара. Как обычно, будем обозначать их (и их спросы) как $x,y$ а соответствующие цены как $p,q$.

## Тождество Роя

Мы хотим связать между собой три объекта: $x^{\ast}(p,q,I), y^{\ast}(p,q,I)$ и  $V^{\ast}(p,q,I)$. Для этого мы воспользуемся фундаментальным свойством, что косвенная полезность это полезность, в которую подставили спросы:

$$V(p, q, px + qy) = U(x, y),$$

Убедитесь, что это, действительно, корректная запись.

Что можно сделать с этим тождеством?

- продифференциировать по $p$
- продифференциировать по $q$

Заметим, что цены входят слева дважды, а справа не входят вообще. То есть, с точки зрения дифференциирования по ценам, справа стоит константа, а слева сложная функция. По правилам дифференциирования, полный дифференциал функции $V$ по $p$ равен:

$$ 
\begin{gather*}
\frac{d V}{d p} = \frac{\partial V}{\partial p} + \frac{\partial V}{\partial I} \cdot \frac{\partial I}{\partial p} = 0
\end{gather*}
$$

:::{seealso}
[Прочитайте, если вы не понимаете разницу между частным и полным дифференциалом.](differentials)
:::


Поскольку $\frac{\partial I}{\partial p} = x$, 

$$\frac{d V}{d p} = \frac{\partial V}{\partial p} + \frac{\partial V}{\partial I} \cdot x = 0$$

Aналогично для второй цены

$$\frac{d V}{d q} = \frac{\partial V}{\partial q} + \frac{\partial V}{\partial I} \cdot y = 0$$

Комбинируя это в векторной форме, мы получаем:

:::{prf:theorem} Тождество Роя
:class: remark
Если $\vec{x}$ - весь вектор спросов, а $\vec{p}$ - весь вектор цен то

$$\vec{x} = - \nabla_{\vec{p}} V / \nabla_I V$$

:::

Заметьте, что я меняю интерпретацию знаков $x, p$ в зависимости от контекста. К этому надо привыкать, контекст задачи важен. Например, $\nabla$ обычно означает вектор, но в знаменателе $\nabla_I = \frac{\partial V}{\partial I}$ это число, потому что $I$ это скаляр.

### Зачем оно нужно?

У тождества Роя есть две основные задачи. 

Во первых, ваши эконометрические данные могут быть в терминах косвенной полезности а не бюджетов. Например, в социальном опросе может быть вопрос: "оцените по шкале от 1 до 10 ваше благосостояние в 2010, 2011 и 2012 году", вместо "запишите ваш доход в 2010, 2011 и 2012 году". Считается, что люди неохотно сообщают свои настоящий доход, богатые занижают а бедные завышают.

Во вторых, иногда проще запомнить косвенную полезность и вывести из нее спросы, чем запоминать спросы. Также, про косвенную полезность удобно составлять задачи, чтобы потом тестировать вас на экзамене.

## Теорема об Огибающей

Это чрезвычайно важная теорема, и, в отличие от остальных, по настоящему полезная. Лично я пользуюсь этой теоремой практически каждый день.

Рассмотрим семейство опорных функций $f(x, p)$, где $x$ - переменная а $p$ - параметр. Определим огибающую $V(p)$ как результат оптимизации функции $f$ по какому-то статическому множеству $Х$: 

$$ V(p) := \max_{x \in Х} f(x, p),$$

тогда...

:::{prf:theorem} Об Огибающей
:class: remark

Функция $V(p)$ (почти всюду) дифференциируема и 

$$\frac{\partial V(p)}{\partial p} = \frac{\partial f(x, p)}{\partial p}|_{x = x^{\ast}(p)}.$$

:::

... то есть, наклон огибающей в точке касания равен наклону соответствующей опорной функции в этой точке.

### Интуиция огибающей

Представьте себе, что вы свалили в кучу какие то крупные объекты и накрыли все эластичной пленкой. 

Пленка плотно прилегла к тем объектам, которые оказались наверху. Можно сказать, что пленка - это (верхняя) огибающая вашего семейства опорных объектов, поскольку она лежит там, где находится самый высокий объект в каждой точке. 

Теперь посмотрим на нашу эластичную пленку. В точках касания с теми опорными объектами что остановили ее от падения, наклон пленки равен наклону этих объектов, так как она повторяет их форму.

Этот практиически умозрительный факт и есть основная идея Теоремы об Огибающей: **наклон огибающей функции в точке касания равен наклону (соответствующей) опорной функции**.

### Примеры

:::{prf:example}

$$ 
\begin{gather*}
a = V(a) = \max_x a-(x-a)^2 \Rightarrow \\
\frac{\partial V(a)}{\partial a} = 1 + 2(x-a)|_{x = a} = 1
\end{gather*}
$$

:::

:::{prf:example}


$$ 
\begin{gather*}
a = V(a,b,c) = \max_{x,y} a-a(x-b)^2 - (y-c)^2 \Rightarrow \\
\frac{\partial V(a, b, c)}{\partial a} = 1 + 2a(x-b)|_{x = b} + 2(y-c)|_{y = c} = 1 
\end{gather*}
$$


:::

### Практическая польза

Может показаться, что дифференцирование опорной функции и подстановка это лишняя трата времени, ведь можно просто решить задачу и продифференцировать $V$ по параметру, в лоб.

Это правда, однако, если у вас абстрактная функция, вы не можете просто так ее промаксимизировать. Поэтому, эта теорема очень удобна при доказательствах, но не только. 

Зачастую, видение огибающей позволяет сэкономить время при дифференцировании, в том смысле, что вам не надо лишний раз протаскивать производную по правилу дифференциирования сложной функции.

К примеру, предположим, что у вас есть функция $F(x, y, p)$ и eще две функции $x = g(p), y = h(p)$. Если вас попросят найти полную производную $F(g(p), h(p), p)$ по $p$ то получится:

$$\frac{d}{dp} F(g(p), h(p), p) = \frac{\partial F}{\partial x} \frac{\partial g}{\partial p} + \frac{\partial F}{\partial y} \frac{\partial h}{\partial p} + \frac{\partial F}{\partial p}.$$

Теперь предположим, что нам стало известно, что $x = g(p), y = h(p)$ это, на самом деле, оптимумы функции $F$. Тогда, по Теореме об Огибающей

$$\frac{d}{dp} F(g(p), h(p), p) = \frac{\partial F}{\partial p}.$$

Получается, что Теорема об Огибающей позволяет нам **игнорировать параметр находящийся внутри оптимальной точки** при подсчете полного дифференциала. Это знание позволяет в отдельных упражнениях сэкономить 10-20 минут изнурительных вычислений.

### Как насчет косвенной полезности

Для того, чтобы активировать всю мощь Теоремы об Огибающей, вам достаточно взять любую функцию, которая является результатом оптимизации и продифференциировать ее по любому параметру.

К примеру, мы могли бы продифференциировать косвенную полезность по ценам. Тогда Теорема об Огибающей даст вам связь этих производных с производными опорной функции в точках оптимума.

:::{dropdown} Что есть опорная функция для $V(p,q,I)$?
Хочется сказать что сама полезность $U(x,y)$ но правильный ответ это Лагранжиан 

$$\mathcal{L}=U(x,y) - \lambda(px + qy - I)$$

по крайней мере он подходит формально, так как зависит от $p,q,I$.
:::

Любопытным также является факт, что теорема об огибающей позволяет найти производную косвенной полезности по бюджету. 

:::{dropdown} Чему равна $\partial V/ \partial I$?

Множителю Лагранжа $\lambda$.
:::

## Минимизация расходов

Сейчас мы перейдем к задаче, на первый взгляд, никак не связанной с максимизацией полезности. Если быть точными, мы будем минимизировать сумму расходов на все товары при минимально заданном таргетированном уровне полезности $\bar U$. Для простоты, пусть будут два товара $x, y$ с ценами $p, q$. 

$$\text{P2:} \quad p x + q y \to \min_{x,y \geqslant 0}, \quad \text{s.t.} \quad U(x,y) \geqslant 0.$$

Сравните с классической задачей максимизации полезности

$$\text{P1:} \quad U(x, y) \to \max_{x,y \geqslant 0}, \quad \text{s.t.} \quad p x + q y \leqslant 0.$$


### Условия Первого Порядка

На самом деле, эти две задачи очень близко связаны. Давайте выпишем Лагранжианы в обеих задачах, но обозначим множители Лагранжа по разному.

$$
\mathcal{L}^{1} = U(x, y) - \lambda (px + qy - I)\\
\mathcal{L}^{2} = (px + qy - I) - \gamma (\bar U - U(x,y))
$$

Поверим на слово, что обе задачи выпуклые, и выпишем УПП для поиска оптимума:

$$  
\text{P1:} \quad U'_x = \lambda p, \quad U'_y = \lambda q, \quad px + qy = I\\
\text{P2:} \quad p = \gamma U'_x, \quad q = \gamma U'_y, \quad U(x,y) = \bar U
$$

Легко видеть, что для того, чтобы решения совпали, необходимо чтобы

- во первых, $\gamma \lambda = 1$, но это никак не ограничивает, так как мы сами выбираем множитель Лагранжа, соответственно, мы можем всегда подогнать один к другому.
- во вторых, для любого $I$ найдется $\bar U$ и наоборот.
- в третьих, при достижении таргетированной полезности обязательно расходовался весь бюджет.

Последнее условие известно как **Закон Вальраса**. Если он выполнен, и задача выпуклая, то минимизация издержек порождает абсолютно такую же систему условий первого порядка, как и максимизация полезности. 

### Закон Вальраса

Для начала приведем пример полезности, при которой Закон Вальраса не выполнен, это постоянная полезность $U(x,y) = 1$. 

Действительно, с точки зрения полезности, все бюджетное множество состоит из оптимумов. Однако, лишь одна точка $(x,y)=(0,0)$ по настоящему минимизирует издержки, при таргетированной полезности $\bar U = 0$. Что тут произошло?

Дело в том, что у полезности $U(x,y) = 1$ **толстые линии уровня**. Чтобы Закон Вальраса заработал, необходимо исключить появление таких линий уровня. Это свойство называется локальной ненасыщаемостью в $\mathbb{R}^2_{+}$.

:::{prf:definition}
Полезность **локально ненасыщаема** в $X$, если для каждой точки $x \in X$ и для любой сколько угодно малой окрестности этой точки в $X$, найдется вторая точка $y$ в этой окрестности, такая что $U(y)>U(x)$.
:::

Большинство полезностей в нашем курсе будет обладать локальной ненасыщаемостью. Теперь мы готовы сформулировать первую теорему

:::{prf:theorem} Закон Вальраса
:class: remark
Если полезность локально ненасыщаема в $\mathbb{R}^n_{+}$, то любое из решений задачи максимизации полезности всегда лежит на бюджетном ограничении.
:::

Осталось убедиться, что для любого $I$ найдется $\bar U$ и наоборот.

### Хиксианский и Маршалианский спрос

:::{prf:definition}
Назовем **Хиксианским** спрос в задаче минимизации расходов, и **Маршалианским** спрос в задаче максимизации полезности. 

Для товаров $x,y$ будем обозначать Хиксианские спросы как 

$$h_x(p,q,\bar U), \quad h_y(p,q,\bar U)$$

а Маршалианские спросы как

$$m_x(p,q,I), \quad m_y(p,q,I).$$

Разрешаю писать просто $hx, hy, mx, my$.
:::

Тогда, в для задачи максимизации полезности с параметрами $(p,q,I)$ существует 

$$ \bar U_0 := V(m_x(p,q,I), m_y(p,q,I))$$

такой что задача минимизации расходов с $(p, q, \bar U_0)$ эквивалентна ей. Аналогично, для задачи миимизации расходов с $(p, q, I)$ существует

$$ I_0 := p h_x(p,q, \bar U) + q h_y(p,q, \bar U)$$

такой что задача максимизации полезности с $(p, q, I_0)$ эквивалентна ей. 

### Функция расходов и Дуальность

Мы подошли к очень важному наблюдению.

:::{prf:theorem} Дуальность
:class: remark
Если полезность (квази-)вогнутая и локально ненасыщаемая, то любое решение задачи минимизации расходов воспроизводится как одно из решений максимизации полезности и наоборот.
:::

Это значит, что задача максимизации полезности и задача минимизации расходов, по большому счету эквивалентны. И их решения, в определенном геометрическом смысле совпадают. Есть только одна проблема - у Маршалианского и Хиксианского спросов разный набор аргументов, поэтому они не могут совпадать номинально. Для того, чтобы поправить ситуацию, нам понадобится еще одна новая функция.

:::{prf:definition}
Назовем **функцией расходов** значение целевой функции в оптимуме, в задаче минимизации расходов:

$$ E(p,q,\bar U) = p h_x(p,q,\bar U) + q h_y(p,q,\bar U).$$

:::

Это совершенно аналогично тому, как мы ввели косвенную полезность $V(p,q,I)$ через значение целевой функции в оптимуме в задаче максимизации полезности.

:::{dropdown} Так в каком смысле они совпадают?
Любой Маршалианский спроса $m_x(p,q,I)$ совпадает с Хиксианским с подставленной косвенной функцией $h_x(p,q,V(p,q,I))$. А любой Хиксианский спрос $h_x(p,q,\bar U)$ совпадает с Маршалианским с подставленной функцией расходов $m_x(p,q,E(p,q,\bar U))$.
:::

## Лемма Шепарда

Мы проходили сегодня уже Теорему об Огибающей и успешно применили ее к задаче максимизации полезности. А что произойдет, если мы применим ее к задаче минимизации расходов?

$$ E(p,q,\bar U) = p h_x(p,q,\bar U) + q h_y(p,q,\bar U), \quad \frac{\partial E}{\partial p} = ?$$

Прежде всего, мы должны ответить на следующий вопрос:

:::{dropdown} Что есть опорная функция для $E(p,q,I)$?
Хочется сказать что расходы $p x + q y$ но правильный ответ это Лагранжиан 

$$\mathcal{L}=px + qy - I - \lambda(\bar U - U(x,y)).$$

Правда, это ничего не меняет, так как прибавка не зависит от параметров.
:::

Теперь, когда мы знаем чему равна опорная функция, мы можем сформулировать следующую теорему:

:::{prf:theorem} Лемма Шепарда
:class: remark
Если $\vec{h}$ - весь вектор спросов, а $\vec{p}$ - весь вектор цен то

$$\vec{h} = \nabla_{\vec{p}} E$$

то есть, Хиксианский спрос является градиентом функции расходов.

:::

Лемма Шепарда это первая манифестация Теоремы об Огибающей в нашем курсе, которых будет очень, очень много. 

## Как не запутаться?

Подводя итог, у нас было две задачи: максимизации полезности и минимизации расходов. Каждая задача имела свой набор параметров: первая $(p,q,I)$ а вторая $(p,q,\bar U)$. Каждая задача произвела три обьекта:

- оптимальные $m_x(p,q,I), m_y(p,q,I)$ и косвенная полезность $V(p,q,I)$ в первой задаче
- оптимальные $h_x(p,q,\bar U), h_y(p,q,\bar U)$ и функция расходов $E(p,q,\bar U)$ во второй задаче

Если вы решали задачу максимизации полезности и нашли маршалианский спрос, который зависит от $\bar U$ то правильным ответом это быть не может, поскольку вам разрешено только пользоваться $(p,q,I)$. Это значит, что вы недоподставили где то, недоиспользовали Дуальность.

Можно изобразить "схему перемещений" между объектами:

... тут будет схема ...

Косвенная полезность и функция расходов тривиально выводятся из соответствующих спросов, это будет "подъем наверх".

Далее, при помощи дуальности и спросов вы можете свободно перемещаться "горизонтально" между $V$ и $E$. И наоборот, при помощи дуальности и $V$, $E$ вы можете свободно перемещаться "горизонтально" между спросами.

Наконец, Лемма Шепарда и Тождество Роя позволяют вам "спускаться вниз" от косвенной полезности и функции расходов к маршалианским и хиксианским спросам соответственно. 

## Примеры

### Полезность Кобб-Дуглас

При работе с Кобб-Дугласом, приятнее всего начинать с задачи максимизации прибыли. Как мы помним, расходы на каждый из товаров делятся в пропорциях, которые не зависят ни от цен, ни от доходов. Пусть есть два товара $x,y$, $\alpha + \beta = 1$ тогда

$$m_x = \alpha\frac{I}{p}, \quad m_y = \beta\frac{I}{q},$$

лучше всего запомнить это наизусть. Также можно запомнить (с точностью до константы $C$) неявную полезностъ в логарифмической форме с весами суммирующимися в единицу:

$$V(p,q,I) = \log I - \alpha \log p - \beta \log q + C$$

Нам осталось найти хиксианские спросы и функцию расходов. Но давайте не торопиться, а сначала рассмотрим наши опции. Один способ - сфомулировать задачу минимизации расходов, решить ее, и затем, чисто механически, вычислить функцию расходов. Другой способ - пройти горизонтально от косвенной полезности к функции расходов, а затем спуститься вниз по Лемме Шепарда.

:::{dropdown} В какой последовательности лучше делать?

Вывести функцию расходов по дуальности, а затем спуститься по Лемме Шепарда. 

:::{prf:proof}
Используем дуальность, тобы перейти от $(p,q,I)$ к $(p,q,\bar U)$:

$$\bar U = V(p,q,Е(p,q,\bar U)) = \log Е(p,q,\bar U) - \alpha \log p - \beta \log q - C
$$

Применяя экспоненту к правой и левой части, получаем:

$$
Е(p,q,\bar U) = e^{\bar U + C} p^{\alpha} q^{\beta}
$$

И прямо таки дифференциируем ее по ценам.

$$ h_x = \frac{\alpha}{p} e^{\bar U + C} p^{\alpha} q^{\beta}, \quad h_y = \frac{\beta}{q} e^{\bar U + C} p^{\alpha} q^{\beta}.$$

Обратите внимание, что понижение степени, к которому вы привыкли в курсах матанализа, равносильно делению. Это удобно.

:::


### Леонтьевская полезность

### Линейная полезность

