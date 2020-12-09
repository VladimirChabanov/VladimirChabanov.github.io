[TOC]

#### <span>25</span>. BozoSort

<div id="testing" style="background-size: 40px 40px; background-image: -moz-linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); background-image: -webkit-linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); background-image: linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); box-shadow: 0 0 8px rgba(0,0,0,.3); width: 100%; margin: 0 auto; padding:15px; background-color: #4ea5cd; border-left:7px #3b8eb5 solid;">
<a href="#" style="text-decoration: none; font:16px 'Open Sans'; font-weight:600; color:#f4f0fc;">Ссылка для тренировки (скоро)</a>
</div>

***С++ и Python***

Реализуйте сортировку методом [BozoSort](https://habr.com/ru/post/198114/). Данную сортировку реализуйте в виде трёх отдельных функций для следующих случаев:

1. Массива целых чисел (std::vector<int\> для С++ и list для Python);
2. Двумерного массива целых чисел (std::vector\<std::vector<int\>> для С++ и список из списков для Python). Количество строк и столбцов одинаковое;
3. Трёх отдельных целых чисел.

*Примечание 1*: в Python параметр *args использовать запрещено.

*Примечание 2*: использовать одну функцию в другой можно.

Для всех трёх случаев:

- Имя функции одинаковое **BozoSort**;
- Исходные данные не изменяются;
- Функция возвращает одномерный вектор/лист отсортированных значений;
- Кроме данных требующих сортировки функция должна принимать, последним параметром, порядок сортировки. Порядок сортировки задаётся параметром булевого типа:
  - значение параметра **Истина** устанавливает порядок сортировки по возрастанию;
  - значение параметра **Ложь** устанавливает порядок сортировки по убыванию.  

- По умолчанию все функции должны сортировать данные по возрастанию. О параметрах со значениями по умолчанию можно почитать: [C++](https://ravesli.com/urok-103-parametry-po-umolchaniyu/), [Python (3 пункт)](https://habr.com/ru/company/ruvds/blog/515678).

Продемонстрируйте работу функций отсортировав входные данные сначала по возрастанию, затем по убыванию.

**Формат ввода**  
В первой строке задаётся одно целое число $n$ — количество чисел требующий сортировки $4\leq n\leq 100$, при этом корень из $n$ - целое число. В следующей строке через пробел задаются сам числа. Для функций принимающих двумерный массив количество столбцов и строк определяется как $\sqrt n$. Для функций принимающих три числа ввод всегда ограничен первыми тремя числами. 

**Формат вывода**  
В отдельных строках выведите числа отсортированные сначала по возрастанию, затем по убыванию. И так для каждой функции. 

**Пример 1**

<table>
<thead><tr><td width="50%"><b>Ввод</b></td><td width="50%"><b>Вывод</b></td></tr></thead>
<tr><td valign="top">4<br/>2 1 7 -3</td><td valign="top">-3 1 2 7<br/>7 2 1 -3<br/>-3 1 2 7<br/>7 2 1 -3<br/>1 2 7<br/>7 2 1</td></tr>
</table> 


#### <span>26</span>. Шаблон BozoSort

<div id="testing" style="background-size: 40px 40px; background-image: -moz-linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); background-image: -webkit-linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); background-image: linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); box-shadow: 0 0 8px rgba(0,0,0,.3); width: 100%; margin: 0 auto; padding:15px; background-color: #4ea5cd; border-left:7px #3b8eb5 solid;">
<a href="#" style="text-decoration: none; font:16px 'Open Sans'; font-weight:600; color:#f4f0fc;">Ссылка для тренировки (скоро)</a>
</div>

***С++***

Реализуйте шаблоны функций описанных в задании 25. Продемонстрируйте работу на примере: чисел: `double` и сток: `std::string`.

**Формат ввода**  
В первой строке задаётся одно целое число $n$ — количество значений требующий сортировки $4\leq n\leq 100$, при этом корень из $n$ - целое число. В следующей строке через пробел задаются сам значения. Для функций принимающих двумерный массив количество столбцов и строк определяется как $\sqrt n$. Для функций принимающих три значения ввод всегда ограничен первыми тремя значениями. Далее ввод повторяется.  
В первом случае требуется считать данные как вещественные числа, во втором случае как строки.

**Формат вывода**  
В отдельных строках выведите значения отсортированные сначала по возрастанию, затем по убыванию. И так для каждой функции. 

**Пример 1 (double)**

<table>
<thead><tr><td width="50%"><b>Ввод</b></td><td width="50%"><b>Вывод</b></td></tr></thead>
<tr><td valign="top">4<br/>2 1 7 -3<br/>4<br/>2 1 7 -3</td><td valign="top">-3 1 2 7<br/>7 2 1 -3<br/>-3 1 2 7<br/>7 2 1 -3<br/>1 2 7<br/>7 2 1<br>-3 1 2 7<br/>7 2 1 -3<br/>-3 1 2 7<br/>7 2 1 -3<br/>1 2 7<br/>7 2 1</td></tr>
</table> 



#### <span>27</span>. TOP — 5 минимальных
<div id="testing" style="background-size: 40px 40px; background-image: -moz-linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); background-image: -webkit-linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); background-image: linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); box-shadow: 0 0 8px rgba(0,0,0,.3); width: 100%; margin: 0 auto; padding:15px; background-color: #9f9f9f; border-left:7px #8f8f8f solid;">
<a href="#" style="text-decoration: none; font:16px 'Open Sans'; font-weight:600; color:#f4f0fc;">Задача без теста</a>
</div>

***С++ и Python***

Вам известна последовательность $a_i$ поступления $n$ сигналов с устройства.  
После каждого поступившего сигнала необходимо вывести 5 самых минимальных сигналов от начала наблюдений. Если сигналов было меньше, то нужно вывести все имеющиеся сигналы.   
Выводите сигналы в порядке убывания.

**Формат ввода**   
В первой строке записано одно целое число $n$ ($1\leq n\leq 100\:000$) — количество сигналов. Во второй строке записаны $n$ целых чисел $a_i$ ($-1\:000\:000\leq a_i\leq 1\:000\:000$).

**Формат вывода**  
Выведите $n$ строк, в каждой из которых будут записаны, в порядке убывания, самые минимальные 5 сигналов (или все, если наблюдений было меньше 5).

**Пример 1**

<table>
<thead><tr><td width="50%"><b>Ввод</b></td><td width="50%"><b>Вывод</b></td></tr></thead>
<tr><td valign="top">3<br/>3 1 2</td><td valign="top">3<br/>3 1<br/>3 2 1</td></tr>
</table> 

**Пример 2**

<table>
<thead><tr><td width="50%"><b>Ввод</b></td><td width="50%"><b>Вывод</b></td></tr></thead>
<tr><td valign="top">8<br/>1 2 3 4 5 6 7 0</td><td valign="top">1<br/>2 1<br/>3 2 1<br/>4 3 2 1<br/>5 4 3 2 1<br/>5 4 3 2 1<br/>5 4 3 2 1<br/>4 3 2 1 0</td></tr>
</table> 


#### <span>28</span>. Факторизация натурального числа
<div id="testing" style="background-size: 40px 40px; background-image: -moz-linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); background-image: -webkit-linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); background-image: linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); box-shadow: 0 0 8px rgba(0,0,0,.3); width: 100%; margin: 0 auto; padding:15px; background-color: #9f9f9f; border-left:7px #8f8f8f solid;">
<a href="#" style="text-decoration: none; font:16px 'Open Sans'; font-weight:600; color:#f4f0fc;">Задача без теста</a>
</div>

***С++ и Python***

Факторизацией натурального числа называется его разложение в произведение простых множителей.  
Реализуйте функцию выполняющую факторизацию и отображающую на экран разложение переданного ей числа на простые множители.

Прототип функции:

```C++
void print_factorization(unsigned int n);
```

```python
print_factorization(n: int) -> None
```

**Формат ввода**  
В единственной строке вводится натуральное число $n$ ($1\leq n\leq 10^9$).

**Формат вывода**  
Простые множители без повторения разделённые знаком умножения `*`, если есть несколько одинаковых сомножителей, то кол-во повторений записывается как показатель степени у этого сомножителя.

**Пример 1**

<table>
<thead><tr><td width="50%"><b>Ввод</b></td><td width="50%"><b>Вывод</b></td></tr></thead>
<tr><td valign="top">10</td><td valign="top">2*5</td></tr>
</table> 

**Пример 2**

<table>
<thead><tr><td width="50%"><b>Ввод</b></td><td width="50%"><b>Вывод</b></td></tr></thead>
<tr><td valign="top">999</td><td valign="top">3^3*37</td></tr>
</table> 

<details style="box-sizing: inherit; display: block;"><summary style="box-sizing: inherit; display: block;">Тестовые данные</summary><table border="0" cellpadding="3" cellspacing="0">
<tbody><tr>
<td style="border: 0 solid #fff;"><table><caption>1 − 20</caption><tbody><tr><td>1</td><td>—</td></tr><tr><td>2</td><td>2</td></tr><tr><td>3</td><td>3</td></tr><tr><td>4</td><td>2<sup>2</sup></td></tr><tr><td>5</td><td>5</td></tr><tr><td>6</td><td>2·3</td></tr><tr><td>7</td><td>7</td></tr><tr><td>8</td><td>2<sup>3</sup></td></tr><tr><td>9</td><td>3<sup>2</sup></td></tr><tr><td>10</td><td>2·5</td></tr><tr><td>11</td><td>11</td></tr><tr><td>12</td><td>2<sup>2</sup>·3</td></tr><tr><td>13</td><td>13</td></tr><tr><td>14</td><td>2·7</td></tr><tr><td>15</td><td>3·5</td></tr><tr><td>16</td><td>2<sup>4</sup></td></tr><tr><td>17</td><td>17</td></tr><tr><td>18</td><td>2·3<sup>2</sup></td></tr><tr><td>19</td><td>19</td></tr><tr><td>20</td><td>2<sup>2</sup>·5</td></tr></tbody></table></td>
<td style="border: 0 solid #fff;"><table><caption>21 − 40</caption><tbody><tr><td>21</td><td>3·7</td></tr><tr><td>22</td><td>2·11</td></tr><tr><td>23</td><td>23</td></tr><tr><td>24</td><td>2<sup>3</sup>·3</td></tr><tr><td>25</td><td>5<sup>2</sup></td></tr><tr><td>26</td><td>2·13</td></tr><tr><td>27</td><td>3<sup>3</sup></td></tr><tr><td>28</td><td>2<sup>2</sup>·7</td></tr><tr><td>29</td><td>29</td></tr><tr><td>30</td><td>2·3·5</td></tr><tr><td>31</td><td>31</td></tr><tr><td>32</td><td>2<sup>5</sup></td></tr><tr><td>33</td><td>3·11</td></tr><tr><td>34</td><td>2·17</td></tr><tr><td>35</td><td>5·7</td></tr><tr><td>36</td><td>2<sup>2</sup>·3<sup>2</sup></td></tr><tr><td>37</td><td>37</td></tr><tr><td>38</td><td>2·19</td></tr><tr><td>39</td><td>3·13</td></tr><tr><td>40</td><td>2<sup>3</sup>·5</td></tr></tbody></table></td>
<td style="border: 0 solid #fff;"><table><caption>41 − 60</caption><tbody><tr><td>41</td><td>41</td></tr><tr><td>42</td><td>2·3·7</td></tr><tr><td>43</td><td>43</td></tr><tr><td>44</td><td>2<sup>2</sup>·11</td></tr><tr><td>45</td><td>3<sup>2</sup>·5</td></tr><tr><td>46</td><td>2·23</td></tr><tr><td>47</td><td>47</td></tr><tr><td>48</td><td>2<sup>4</sup>·3</td></tr><tr><td>49</td><td>7<sup>2</sup></td></tr><tr><td>50</td><td>2·5<sup>2</sup></td></tr><tr><td>51</td><td>3·17</td></tr><tr><td>52</td><td>2<sup>2</sup>·13</td></tr><tr><td>53</td><td>53</td></tr><tr><td>54</td><td>2·3<sup>3</sup></td></tr><tr><td>55</td><td>5·11</td></tr><tr><td>56</td><td>2<sup>3</sup>·7</td></tr><tr><td>57</td><td>3·19</td></tr><tr><td>58</td><td>2·29</td></tr><tr><td>59</td><td>59</td></tr><tr><td>60</td><td>2<sup>2</sup>·3·5</td></tr></tbody></table></td>
<td style="border: 0 solid #fff;"><table><caption>61 − 80</caption><tbody><tr><td>61</td><td>61</td></tr><tr><td>62</td><td>2·31</td></tr><tr><td>63</td><td>3<sup>2</sup>·7</td></tr><tr><td>64</td><td>2<sup>6</sup></td></tr><tr><td>65</td><td>5·13</td></tr><tr><td>66</td><td>2·3·11</td></tr><tr><td>67</td><td>67</td></tr><tr><td>68</td><td>2<sup>2</sup>·17</td></tr><tr><td>69</td><td>3·23</td></tr><tr><td>70</td><td>2·5·7</td></tr><tr><td>71</td><td>71</td></tr><tr><td>72</td><td>2<sup>3</sup>·3<sup>2</sup></td></tr><tr><td>73</td><td>73</td></tr><tr><td>74</td><td>2·37</td></tr><tr><td>75</td><td>3·5<sup>2</sup></td></tr><tr><td>76</td><td>2<sup>2</sup>·19</td></tr><tr><td>77</td><td>7·11</td></tr><tr><td>78</td><td>2·3·13</td></tr><tr><td>79</td><td>79</td></tr><tr><td>80</td><td>2<sup>4</sup>·5</td></tr></tbody></table></td>
<td style="border: 0 solid #fff;"><table><caption>81 − 100</caption><tbody><tr><td>81</td><td>3<sup>4</sup></td></tr><tr><td>82</td><td>2·41</td></tr><tr><td>83</td><td>83</td></tr><tr><td>84</td><td>2<sup>2</sup>·3·7</td></tr><tr><td>85</td><td>5·17</td></tr><tr><td>86</td><td>2·43</td></tr><tr><td>87</td><td>3·29</td></tr><tr><td>88</td><td>2<sup>3</sup>·11</td></tr><tr><td>89</td><td>89</td></tr><tr><td>90</td><td>2·3<sup>2</sup>·5</td></tr><tr><td>91</td><td>7·13</td></tr><tr><td>92</td><td>2<sup>2</sup>·23</td></tr><tr><td>93</td><td>3·31</td></tr><tr><td>94</td><td>2·47</td></tr><tr><td>95</td><td>5·19</td></tr><tr><td>96</td><td>2<sup>5</sup>·3</td></tr><tr><td>97</td><td>97</td></tr><tr><td>98</td><td>2·7<sup>2</sup></td></tr><tr><td>99</td><td>3<sup>2</sup>·11</td></tr><tr><td>100</td><td>2<sup>2</sup>·5<sup>2</sup></td></tr></tbody></table></td>
</tr></tbody></table>
</details>
