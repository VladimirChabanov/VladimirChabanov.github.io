[TOC]

#### <span>36</span>. Класс Точка на плоскости

<div id="testing" style="background-size: 40px 40px; background-image: -moz-linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); background-image: -webkit-linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); background-image: linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); box-shadow: 0 0 8px rgba(0,0,0,.3); width: 100%; margin: 0 auto; padding:15px; background-color: #4ea5cd; border-left:7px #3b8eb5 solid;">
<a href="https://www.classmarker.com/online-test/start/?quiz=nfn605be02b62f42" style="text-decoration: none; font:16px 'Open Sans'; font-weight:600; color:#f4f0fc;">Ссылка для тренировки</a>
</div>

***С++***

Создайте класс `Point` реализующий идею [точки](https://ru.wikipedia.org/wiki/Точка_(геометрия)) на плоскости. Внутренняя реализация класса на ваше усмотрение.

В качестве обязательных членов должны присутствовать:

1. Конструкторы:
   - Конструктор с тремя параметрами `a1` и `a2` типа `double` и `coord_system` типа перечисление состоящее из двух значений: [`Cartesian`](https://ru.wikipedia.org/wiki/Прямоугольная_система_координат) и [`Polar`](https://ru.wikipedia.org/wiki/Полярная_система_координат). Если третий параметр задан как `Cartesian`, то параметры `a1` и `a2` являются координатами `x` и `y` декартовой системы координат, если третий параметр задан как `Polar`, то `a1` и `a2` это `r` и $\varphi$ полярной системы координат соответственно ($\varphi$ везде задаётся в радианах). Параметр `coord_system` имеет значение по умолчанию `Cartesian`, а `a1` и `a2` по умолчанию нули.
2. Деструктор. Т.к. класс динамически нечего не создаёт деструктор можно не объявлять.
3. Операторы `==` и `!=`. Сравнивает два объекта класса `Point` на равенство/не равенство, при этом не играет роли в какой системе координат задавались координаты точки при создании. Если отклонение по каждой координате не превышает 10<sup>-10</sup>, то считается что это одна и та же точка. 
4. Оператор `<<`. Выводит координаты точки в поток в виде строки в формате: "(X,Y)", где X и Y заменяются на значение координат точки `x` и `y` в декартовой системе координат.
5. Оператор `>>`. Считывает координаты точки из потока в виде строки в формате: "(X,Y)", где X и Y координаты точки `x` и `y` в декартовой системе координат.
6. Методы `get_x` и `get_y` возвращающие координаты точки в декартовой системе координат;
7. Методы `get_r` и `get_phi` возвращающие координаты точки в полярной системе координат;
8. Методы `set_x` и `set_y` устанавливающие новое значение соответствующей координаты точки в декартовой системе координат;
9. Методы `set_r` и `set_phi` устанавливающие новое значение  соответствующей координаты точки в полярной системе координат;

Используйте код представленный ниже и [этот файл](./resources/files/task36/data.txt) для проверки правильности реализации класса и операторов. Класс можно описать тут же или подключить как отдельный файл (он пригодится в следующем задании).

```c++
#include <iostream>
#include <string>
#include <fstream>
#include <vector>
#include <algorithm>
  
const auto PI = 3.141592653589793;
  
class Point;
// Ваш код здесь
  
int main() {
	std::vector<Point> original;
	std::ifstream fin("data.txt");
	if (!fin.is_open()) { 
		std::cout << "Can't open file" << std::endl;
		return 1; 
	} else {
		while (!fin.eof()) {
			Point p;
			fin >> p;
			fin.ignore(2); // Точки разделены двумя символами ", "
			original.push_back(p);
		}
		fin.close();
	}
  
	std::vector<Point> simulacrum(original);
	for (auto& p : simulacrum) {
		std::cout << p;
		p.set_x(p.get_x() + 10);
		p.set_phi(p.get_phi() + 180*PI/180);
		p.set_y(-p.get_y());
		p.set_x(-p.get_x() - 10);
		std::cout << p << std::endl;
	}
  
	if (std::equal(original.begin(), original.end(), simulacrum.begin()))
		std::cout << "\nIt works!\n";
	else 
		std::cout << "\nIt not works!\n";
}
```

***Python***

По аналогии с заданием для **С++** реализуйте класс `Point`.

В качестве обязательных членов должны присутствовать:

1. Метод `__init__`. Кроме `self` должен принимать ещё три параметра: `a1` и `a2` и `coord_system`:
   1. Если параметр `a1` - это строка, то остальные параметры игнорируются, а сама строка парсится исходя из того, что она в формате: "(X,Y)", где X и Y вещественные координаты точки `x` и `y` в декартовой системе координат.
   2. Если параметр `a1` - это число, то смотрим на параметр `coord_system`. Он может принимать да значения: [`Cartesian`](https://ru.wikipedia.org/wiki/Прямоугольная_система_координат) и [`Polar`](https://ru.wikipedia.org/wiki/Полярная_система_координат). Если он задан как `Cartesian`, то параметры `a1` и `a2` являются координатами `x` и `y` декартовой системы координат, если `coord_system` задан как `Polar`, то `a1` и `a2` это `r` и $\varphi$ полярной системы координат соответственно ($\varphi$ везде задаётся в радианах). По умолчанию`coord_system` задан как `Cartesian`, а `a1` и `a2` по умолчанию нули.
2. Финализатор. Можно не объявлять.
3. Операторы `==` (метод `__eq__`) и `!= ` (метод `__ne__`). Сравнивает два объекта класса `Point` на равенство/не равенство, при этом не играет роли в какой системе координат задавались координаты точки при создании. Если отклонение по каждой координате не превышает 10<sup>-10</sup>, то считается что это одна и та же точка. 
4. Методы `__repr__` и `__str__`. Преобразуют объект класса `Point` в строку в формате: "(X,Y)", где X и Y заменяются на значение координат точки `x` и `y` в декартовой системе координат.
6. Методы `get_x` и `get_y` возвращающие координаты точки в декартовой системе координат;
7. Методы `get_r` и `get_phi` возвращающие координаты точки в полярной системе координат;
8. Методы `set_x` и `set_y` устанавливающие новое значение соответствующей координаты точки в декартовой системе координат;
9. Методы `set_r` и `set_phi` устанавливающие новое значение  соответствующей координаты точки в полярной системе координат;

Используйте код представленный ниже и [этот файл](./resources/files/task36/data.txt) для проверки правильности реализации класса и операторов. Класс можно описать тут же или подключить как отдельный файл (он пригодится в следующем задании).

```python
import math
import copy
  
class Point:
    pass # Ваш код здесь
  
  
with open('data.txt') as fin:
    original = [Point(p) for p in fin.readline().split(', ')]
  
simulacrum = copy.deepcopy(original)
for p in simulacrum:
    print(p, end='')
    p.set_x(p.get_x() + 10)
    p.set_phi(p.get_phi() + 180*math.pi/180)
    p.set_y(-p.get_y())
    p.set_x(-p.get_x() - 10)
    print(p)
  
print('\nIt works!\n' if simulacrum == original else '\nIt not works!\n')
```

**Формат ввода**  
[Файл с данными](./resources/files/task36/data.txt) в формате: набор Точек разделённые двумя символами: запятая и пробел. Каждая точка задана в ПДСК в формате: открывающая круглая скобка, координата X, запятая, координата Y, закрывающая круглая скобка. Точки образуют [фигуру](https://www.desmos.com/calculator/pylclig6jz).

**Формат вывода**  
Вывод должен заканчиваться на "It works!",  что свидетельствует о том, что класс написан правильно. Если вывод заканчивается на "It not works!", значите в классе есть ошибки.



#### <span>37</span>. Класс Вектор на плоскости

<div id="testing" style="background-size: 40px 40px; background-image: -moz-linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); background-image: -webkit-linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); background-image: linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); box-shadow: 0 0 8px rgba(0,0,0,.3); width: 100%; margin: 0 auto; padding:15px; background-color: #4ea5cd; border-left:7px #3b8eb5 solid;">
<a href="#" style="text-decoration: none; font:16px 'Open Sans'; font-weight:600; color:#f4f0fc;">Ссылка для тренировки</a> (Скоро)
</div>

***С++***

Создайте класс `Vector` реализующий идею [вектора](https://ru.wikipedia.org/wiki/Вектор_(геометрия)) на плоскости. Внутренняя реализация класса на ваше усмотрение.

В качестве обязательных членов должны присутствовать:

1. Конструкторы (НЕ совмещать):
   - Конструктор по умолчанию. Конструктор создаёт вектор единичной длины в направлении оси $OX$.
   - Конструктор с одним параметром. Параметр `end` - это объект класса `Point` (задание 36). Конструктор создаёт вектор направленный из начала координат в точку `end`.
   - Конструктор с двумя параметрами. Параметры - `begin` и `end` - это объекты класса `Point`. Конструктор создаёт вектор направленный из `begin` в `end`.
2. Деструктор. Т.к. класс динамически нечего не создаёт можно не объявлять свой деструктор.
4. Оператор `==`. Сравнивает два объекта класса `Vector` на равенство. Точность сравнения 10<sup>-10</sup>. 
6. Оператор унарный `-`. Возвращает новый вектор направление которого противоположно направлению вектора к которому применяется оператор.
7. Оператор бинарный `+`. Левый и правый операнды класса `Vector`.  Возвращает новый вектор являющийся покомпонентной суммой левого и правого операндов.
8. Оператор бинарный `-`. Левый и правый операнды класса `Vector`.  Возвращает новый вектор являющийся покомпонентной разностью левого и правого операндов.
9. Оператор бинарный `*`. Левый операнд класса `Vector`, правый типа `double`.  Возвращает новый вектор компоненты которого умножены на правый операнд.
8. Метод `length`. Метод не принимает параметров и возвращает длину вектора;
9. Оператор бинарный `*`. Левый и правый операнды класса `Vector`.  Возвращает вещественное число вычисляющееся как скалярное произведение векторов-операндов.

Используйте код представленный ниже для проверки правильности реализации класса. Рекомендуется закомментировать все тесты и "открывать" их по одному, по мере выполнения задания.

```c++
#include <iostream>
using namespace std;
 
double sqr(double a);
bool equal(double a, double b, double e = 1E-10);
 
class Point;
// Класс Point из задания 36
 
class Vector;
// Ваш код здесь
 
int main()
{
    Vector a(Point(1, 2)), b(Point(-2, 0), Point(-1, 2));
    if (a == b && b == a) cout << "Equality test passed\n";
    else cout << "Equality test failed\n";
 
    Vector na(Point(-1, -2)), ox(Point(1, 0)), nox(Point(-1, 0)), oy(Point(0, 1)), noy(Point(0, -1));
    if (a == -na && na == -a && -ox == nox && -oy == noy) cout << "Invert test passed\n";
    else cout << "Invert test failed\n";
 
    if (ox + oy + oy == a && -ox == -a + oy + oy) cout << "Summation test passed\n";
    else cout << "Summation test failed\n";
 
    if (-ox + oy == oy - ox && -oy + ox == ox - oy) cout << "Subtraction test passed\n";
    else cout << "Subtraction test failed\n";
 
    if (ox * 3 == ox + ox + ox &&
        oy * 3 == oy + oy + oy &&
        ox * (-3) == -ox - ox - ox &&
        oy * (-3) == -oy - oy - oy) cout << "Multiplication by number test passed\n";
    else cout << "Multiplication by number test failed\n";
 
    if (equal(ox.length(), 1) &&
        equal(oy.length(), 1) &&
        equal((ox * 3 + oy * 4).length(), 5)) cout << "Length test passed\n";
    else cout << "Length test failed\n";
 
    if (equal(ox*ox, sqr(ox.length())) &&
        equal(oy*oy, sqr(oy.length())) &&
        equal((ox*3 + oy*4)*(ox*3 + oy*4), sqr((ox*3 + oy*4).length()))) cout << "Multiplication by Vector test passed\n";
    else cout << "Multiplication by Vector test failed\n";
}
 
bool equal(double a, double b, double e) {
    if (-e < a - b && a - b < e) return true;
    else return false;
}
 
double sqr(double a) {
    return a * a;
}
```

***Python***

По аналогии с заданием для **С++** реализуйте класс `Vector`.

В качестве обязательных членов должны присутствовать:

1. Метод `__init__`. Кроме `self` должен принимать ещё два параметра: `begin` и `end` - экземпляры класса `Point` из задания 36:
   - Если параметры не заданы, то создаётся вектор единичной длины в направлении оси $OX$.
   - Если задан один параметр, создаётся вектор направленный из начала координат в точку переданную в качестве параметра.
   - Если заданы оба параметра `begin` и `end`, то создаётся вектор направленный из `begin` в `end`.
2. Финализатор. Можно не объявлять.
5. Метод `__eq__` (оператор `==`). Сравнивает два объекта класса `Vector` на равенство. Точность сравнения 10<sup>-10</sup>. 
6. Метод `__neg__` (унарный `-`). Возвращает новый вектор направление которого противоположно направлению вектора к которому применяется оператор.
7. Метод `__add__` (бинарный `+`). Левый и правый операнды класса `Vector`.  Возвращает новый вектор являющийся покомпонентной суммой левого и правого операндов.
8. Метод `__sub__` (бинарный `-`). Левый и правый операнды класса `Vector`.  Возвращает новый вектор являющийся покомпонентной разностью левого и правого операндов.
7. Метод `__mul__` (бинарный `*`). Левый операнд класса `Vector`, правый типа `double`.  Возвращает новый вектор компоненты которого умножены на правый операнд.
8. Метод `length`. Метод не принимает параметров и возвращает длину вектора;
9. Метод `__mul__` (бинарный `*`). Левый и правый операнды класса `Vector`.  Возвращает вещественное число вычисляющееся как скалярное произведение векторов-операндов.

Используйте код представленный ниже для проверки правильности реализации класса. Рекомендуется закомментировать все тесты и "открывать" их по одному, по мере выполнения задания.

```python
import math
  
def equal(a, b, e=1E-10):
    if -e < a - b < e: return True
    else: return False
  
  
class Point:
    pass # Класс Point из задания 36
  
class Vector:
    pass # Ваш код здесь
  
  
a = Vector(Point(1, 2))
b = Vector(Point(-2, 0), Point(-1, 2))
if a == b and b == a: print('Equality test passed')
else: print('Equality test failed')
  
na  = Vector(Point(-1, -2))
ox  = Vector(Point( 1,  0))
nox = Vector(Point(-1,  0))
oy  = Vector(Point( 0,  1))
noy = Vector(Point( 0, -1))
if a == -na and na == -a and -ox == nox and -oy == noy: print('Invert test passed')
else: print('Invert test failed')
  
if ox + oy + oy == a and -ox == -a + oy + oy: print('Summation test passed')
else: print('Summation test failed')
  
if -ox + oy == oy - ox and -oy + ox == ox - oy: print('Subtraction test passed')
else: print('Subtraction test failed')
  
if (ox * 3 == ox + ox + ox and
    oy * 3 == oy + oy + oy and
    ox * (-3) == -ox - ox - ox and
    oy * (-3) == -oy - oy - oy): print('Multiplication by number test passed')
else: print('Multiplication by number test failed')
  
if (equal(ox.length(), 1) and
    equal(oy.length(), 1) and
    equal((ox * 3 + oy * 4).length(), 5)): print('Length test passed')
else: print('Length test failed')
  
if (equal(ox*ox, ox.length()**2) and
    equal(oy*oy, oy.length()**2) and
    equal((ox*3 + oy*4)*(ox*3 + oy*4), (ox*3 + oy*4).length()**2)): print('Multiplication by Vector test passed')
else: print('Multiplication by Vector test failed')
```

**Формат ввода**  
Ввода нет.

**Формат вывода**  
Все тесты должны быть пройдены (`passed`). Если хотя бы один тест не пройден, то класс реализован не правильно (`failed`).



#### <span>38</span>. Класс Рациональное число

<div id="testing" style="background-size: 40px 40px; background-image: -moz-linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); background-image: -webkit-linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); background-image: linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); box-shadow: 0 0 8px rgba(0,0,0,.3); width: 100%; margin: 0 auto; padding:15px; background-color: #4ea5cd; border-left:7px #3b8eb5 solid;">
<a href="#" style="text-decoration: none; font:16px 'Open Sans'; font-weight:600; color:#f4f0fc;">Ссылка для тренировки</a> (Скоро)
</div>

***С++***

Создайте класс `Rational` реализующий идею [рационального числа](https://ru.wikipedia.org/wiki/Рациональное_число). Внутренняя реализация класса на ваше усмотрение.

В качестве обязательных членов должны присутствовать:

1. Конструкторы:
   - Конструктор по умолчанию. Конструктор создаёт рациональное число инициализированное нулём.
   - Конструктор с параметром типа `int`. Конструктор принимает параметр `a` и создаёт рациональное число инициализированное $\frac{a}{1}$.
   - Конструктор с параметром типа `double`. Конструктор принимает параметр `a` и создаёт рациональное число инициализированное:
     - `a`, если `a` точно представимо в рациональной форме;
     - `r` удовлетворяющим выражению: $|r-a| = min$, если `a` НЕ представимо точно в рациональной форме. То есть `r` должно быть ближайшим к `a` вещественным числом точно представимым в рациональной форме.
2. Деструктор. По необходимости.
4. Оператор `==`. Сравнивает два объекта класса `Rational` на равенство. 
4. Оператор бинарный `+`. Левый и правый операнды класса `Rational`.  Возвращает рациональное число являющееся суммой левого и правого операндов.
5. Оператор бинарный `-`. Левый и правый операнды класса `Rational`.  Возвращает рациональное число являющееся разностью левого и правого операндов.
6. Оператор бинарный `*`. Левый и правый операнды класса `Rational`.  Возвращает рациональное число являющееся произведением левого и правого операндов.
7. Оператор бинарный `/`. Левый и правый операнды класса `Rational`.  Возвращает рациональное число частным суммой левого и правого операндов.
8. Операторы преобразования к типам:
   - `double` - возвращает вещественное число соответствующее рациональному;
   - `bool` - возвращает `false` если число равно нулю и `true` в остальных случаях;
9. Метод `numerator ` - возвращающий числитель;
10. Метод `denominator` - возвращающий знаменатель;
11. Статический член класса `gcd` принимающий два целых числа и возвращающий [наибольший общий делитель](https://ru.wikipedia.org/wiki/Наибольший_общий_делитель).

Используйте код представленный ниже для проверки правильности реализации класса.

```c++
// Тут код ля проверки
```

***Python***

По аналогии с заданием для **С++** реализуйте класс `Rational`.

```python
# Тут код ля проверки
```

**Формат ввода**  
Ввода нет.

**Формат вывода**  
Все тесты должны быть пройдены (`passed`). Если хотя бы один тест не пройден, то класс реализован не правильно (`failed`).