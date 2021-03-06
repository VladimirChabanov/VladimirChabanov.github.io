[TOC]

#### <span>23</span>. Заголовочные файлы

<div id="testing" style="background-size: 40px 40px; background-image: -moz-linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); background-image: -webkit-linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); background-image: linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); box-shadow: 0 0 8px rgba(0,0,0,.3); width: 100%; margin: 0 auto; padding:15px; background-color: #4ea5cd; border-left:7px #3b8eb5 solid;">
<a href="https://www.classmarker.com/online-test/start/?quiz=tq95fb245c2c0c31" style="text-decoration: none; font:16px 'Open Sans'; font-weight:600; color:#f4f0fc;">Ссылка для тренировки</a>
</div>
**C++**

Создайте 3 **заголовочных** файла, имена придумайте самостоятельно.  В каждом файле предусмотрите защиту от повторного включения: в одном используйте директиву `pragma`, в двух других реализуйте защиту через директиву `ifndef`.

В первом файле реализуйте функцию принимающую одно целое число $n \in[1...10]$ и возвращающую факториал этого число $n!$.

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/0613b26bbfc65ef7ae0142723f8251988cc70ba0)

Во втором файле реализуйте функцию принимающую два аргумента: $x$ - вещественное число и $k\in[1... 10]$ - количество членов в разложении функции синус в ряд Тейлора:

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/b89940045b13c9bcd33512a3051b8869086947ed)

В третьем файле реализуйте функцию принимающую два целых числа $k$ и $n$ ($k, n\in[1... 10]$)и возвращающую количество сочетаний $C_{n}^{k}$ из $n$ по $k$:

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/a73cf8428fc85510cade14325f0d8a3f460ed0c6)

Второй и третий файлы должны включать (include) первый. Расчёт синуса и сочетаний $C_{n}^{k}$ **обязательно** реализовать с использованием функции расчёта факториала из первого файла.

Все три файла подключите к .cpp файлу вашего проекта. Воспользуйтесь написанными функциями и выведите:

- таблицу факториалов в диапазоне $[1..10]$;
- таблицу синуса угла в диапазоне $x\in[0...\frac{\pi}4]$ c шагом $\frac{\pi}{180}$. Количество членов разложения $k=5$;
- таблицу сочетаний для $n = 10$ и $k$ в диапазоне $[1...10]$.

**Формат ввода**   
Нет ввода

**Формат вывода**   
В первой строке выходных данных выведите строку "n", затем табуляция и "n!". В последующих 10 строках выведите значение $n$ и через табуляцию $n!$. Закончите вывод таблицы пустой строкой. 

Затем выведите строку "x", табуляция и "sin(x)". В последующих 46 строках выведите значение $x$ и через табуляцию $sin(x, 5)$ с точностью 4 значащих цифры. Для указания точности воспользуйтесь манипулятором [setprecision](https://www.cplusplus.com/reference/iomanip/setprecision/). Закончите вывод таблицы пустой строкой.  

Выведите строку "k", табуляция и "C(k, 10)". В последующих 10 строках выведите значение $k$ и через табуляцию $C_{n}^{k}$.

**Пример** 

<details style="border: 1px solid #dfe2e5;"><table>
<thead><tr><td width="50%"><b>Ввод</b></td><td width="50%"><b>Вывод</b></td></tr></thead>
<tr><td></td><td><pre>n       n!
1       1
2       2
3       6
4       24
5       120
6       720
7       5040
8       40320
9       362880
10      3628800<br>
x       sin(x)
0       0
0.01745 0.01745
0.03491 0.0349
0.05236 0.05234
0.06981 0.06976
0.08727 0.08716
0.1047  0.1045
0.1222  0.1219
0.1396  0.1392
0.1571  0.1564
0.1745  0.1736
0.192   0.1908
0.2094  0.2079
0.2269  0.225
0.2443  0.2419
0.2618  0.2588
0.2793  0.2756
0.2967  0.2924
0.3142  0.309
0.3316  0.3256
0.3491  0.342
0.3665  0.3584
0.384   0.3746
0.4014  0.3907
0.4189  0.4067
0.4363  0.4226
0.4538  0.4384
0.4712  0.454
0.4887  0.4695
0.5061  0.4848
0.5236  0.5
0.5411  0.515
0.5585  0.5299
0.576   0.5446
0.5934  0.5592
0.6109  0.5736
0.6283  0.5878
0.6458  0.6018
0.6632  0.6157
0.6807  0.6293
0.6981  0.6428
0.7156  0.6561
0.733   0.6691
0.7505  0.682
0.7679  0.6947
0.7854  0.7071<br>
k       C(k, 10)
1       10
2       45
3       120
4       210
5       252
6       210
7       120
8       45
9       10
10      1</pre></td></tr>
</table></details>



#### <span>24</span>. Работа с json

<div id="testing" style="background-size: 40px 40px; background-image: -moz-linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); background-image: -webkit-linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); background-image: linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); box-shadow: 0 0 8px rgba(0,0,0,.3); width: 100%; margin: 0 auto; padding:15px; background-color: #4ea5cd; border-left:7px #3b8eb5 solid;">
<a href="https://www.classmarker.com/online-test/start/?quiz=ep75fb48783cb77a" style="text-decoration: none; font:16px 'Open Sans'; font-weight:600; color:#f4f0fc;">Ссылка для тренировки</a>
</div>


Дан файл `in.json` в формате json содержащий массив объектов следующего вида:

```json
{
  "userId": 1,
  "id": 1,
  "title": "delectus aut autem",
  "completed": false
}
```

Где поле `userId` - это целое число, идентификатор пользователя $[1...2\cdot10^9]$; `id` - целое число, идентификатор (номер) записи в массиве $[1...2\cdot10^9]$; `title` - название задачи, строка состоящая символов латинского алфавита; `completed` - логическое значение, указывает выполнена ли задача (true - выполнена, false - не выполнена).

Для каждого пользователя посчитайте количество выполненных задач и результат сохраните в файл `out.json` в формате json. Данные должны быть представлены в виде массива объектов вида: 

```json
{
  "userId": 1,
  "task_completed": 10
}
```

Где поле `userId` - это целое число, идентификатор пользователя $[1...2\cdot10^9]$; `task_completed` - целое число, количество выполненных пользователем задач $[1...2\cdot10^9]$.

**Для ознакомления с форматом json:**

- Структура json сущностей: https://www.json.org/json-ru.html  
  Внизу страницы есть список языков и библиотек для работы с json.

- Видео пояснение к предыдущей ссылке: https://youtu.be/Wqmcj1IhDFM  
  В видео есть оговорка. Корневой сущностью может быть не только объект, но и просто массив.
- Json валидатор: https://codebeautify.org/jsonvalidator  
  Входит в состав довольно большого числа инструментов https://codebeautify.org/

**С++: **

Для задания используйте библиотеку JSON for Modern C++: https://github.com/nlohmann/json. Для этого скачайте и подключите к проекту заголовочный файл `json.hpp` расположенный в репозитории в каталоге [single_include](https://github.com/nlohmann/json/tree/develop/single_include).

Чтение/запись из/в файла показаны в разделе [To/from streams (e.g. files, string streams)](https://github.com/nlohmann/json#user-content-tofrom-streams-eg-files-string-streams) во втором блоке кода. Но дополнительно нужно подключить библиотеку для работы с файлами `#include <fstream>`.

Несколько примеров от автора библиотеки: [итерирование по массиву и объекту](https://wandbox.org/permlink/ScW4gbehjRyjHyPZ), [создание и заполнение массива](https://wandbox.org/permlink/Ptk2BoNyGfrZfxRU). При работе с массивами можно использовать push_back, size и остальные методы стандартных контейнеров std.

**Python: **

Для задания используйте стандартный модуль json. Описание модуля на английском языке приведено в [документации](https://docs.python.org/3/library/json.html).

Про базовые способы работы с модулем json на руссом языке можно почитать тут: https://python-scripts.com/json.

Видео пример работы с модулем json: https://youtu.be/rIhygmw9HZM и https://youtu.be/Wt4WAcqEje8

**Формат ввода**   
Ввод данных в программу осуществляется при помощи файла с названием `in.json`. Гарантируется, что этот файл существует, располагается в том же каталоге, что и программа и содержит валидный json.

**Формат вывода**   
Ввод данных из программы осуществляется в файл с названием `out.json`. Файл должен создаваться в том же каталоге, что и программа и должен содержать валидный json. Визуальное форматирование, порядок объектов в массиве и порядок полей в объекте могут быть произвольными.

**Пример** 

<table>
<thead><tr><td width="50%"><b>Входной файл</b></td><td width="50%"><b>Выходной файл</b></td></tr></thead>
    <tr><td valign="top"><a href="./resources/files/task24/in.json">in.json</a></td><td valign="top"><a href="./resources/files/task24/out.json">out.json</a></td></tr>
</table> 

