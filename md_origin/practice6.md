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
   1. Если аргумент `a1` - это строка, то остальные аргументы игнорируются, а сама строка парсится исходя из того, что она в формате: "(X,Y)", где X и Y вещественные координаты точки `x` и `y` в декартовой системе координат.
   2. Если аргумент `a1` - это число, то смотрим на аргумент `coord_system`. Он может принимать да значения: [`Cartesian`](https://ru.wikipedia.org/wiki/Прямоугольная_система_координат) и [`Polar`](https://ru.wikipedia.org/wiki/Полярная_система_координат). Если он задан как `Cartesian`, то аргументы `a1` и `a2` являются координатами `x` и `y` декартовой системы координат, если `coord_system` задан как `Polar`, то `a1` и `a2` это `r` и $\varphi$ полярной системы координат соответственно ($\varphi$ везде задаётся в радианах). По умолчанию`coord_system` задан как `Cartesian`, а `a1` и `a2` по умолчанию нули.
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
   - Если аргументы не заданы, то создаётся вектор единичной длины в направлении оси $OX$.
   - Если задан один аргумент, создаётся вектор направленный из начала координат в точку переданную в качестве параметра.
   - Если заданы оба аргумента`begin` и `end`, то создаётся вектор направленный из `begin` в `end`.
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
Все тесты должны быть пройдены (`passed`). Если хотя бы один тест не пройден (`failed`), то класс реализован не правильно.



#### <span>38</span>. Класс Рациональное число

<div id="testing" style="background-size: 40px 40px; background-image: -moz-linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); background-image: -webkit-linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); background-image: linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); box-shadow: 0 0 8px rgba(0,0,0,.3); width: 100%; margin: 0 auto; padding:15px; background-color: #4ea5cd; border-left:7px #3b8eb5 solid;">
<a href="#" style="text-decoration: none; font:16px 'Open Sans'; font-weight:600; color:#f4f0fc;">Ссылка для тренировки</a> (Скоро)
</div>

***С++***

Создайте класс `Rational` реализующий идею [рационального числа](https://ru.wikipedia.org/wiki/Рациональное_число). Внутренняя реализация класса на ваше усмотрение.

В качестве обязательных членов должны присутствовать:

1. Конструкторы:
   - Конструктор по умолчанию. Конструктор создаёт рациональное число инициализированное нулём;
   - Конструктор с двумя параметрами типа `int` . Конструктор принимает параметр `a` и `b` и создаёт рациональное число инициализированное $\frac{a}{b}$. 
2. Деструктор. По необходимости.
3. Статический член класса `gcd` принимающий два целых числа и возвращающий [наибольший общий делитель](https://ru.wikipedia.org/wiki/Наибольший_общий_делитель).
4. Оператор `==`. Сравнивает два объекта класса `Rational` на равенство. 
5. Оператор бинарный `+`. Левый и правый операнды класса `Rational`.  Возвращает рациональное число являющееся суммой левого и правого операндов.
6. Оператор бинарный `-`. Левый и правый операнды класса `Rational`.  Возвращает рациональное число являющееся разностью левого и правого операндов.
7. Оператор бинарный `*`. Левый и правый операнды класса `Rational`.  Возвращает рациональное число являющееся произведением левого и правого операндов.
8. Оператор бинарный `/`. Левый и правый операнды класса `Rational`.  Возвращает рациональное число являющееся частным левого и правого операндов.
9. Операторы преобразования к типам:
   - `double` - возвращает вещественное число соответствующее рациональному;
   - `bool` - возвращает `false` если число равно нулю и `true` в остальных случаях;
10. Метод `numerator ` - возвращающий числитель;
11. Метод `denominator` - возвращающий знаменатель;
12. Метод `isNaN` - возвращающий `true`, если число соответствует $\frac{0}{0}$ и `false` в противном случае. Обратите внимание NaN, с точки зрения математики - это неопределённое число, то есть любое. Поэтому он не равен ни чему, даже самому себе.

Используйте код представленный ниже для проверки правильности реализации класса.

```c++
#include <iostream>
#include <cmath>
  
bool equal(double a, double b, double e = 1E-10)
  
class Rational;
// Ваш код здесь
  
int main()
{
    if (Rational::gcd(91, 65) == 13 &&
        Rational::gcd(10, 3) == 1 &&
        Rational::gcd(-10, 3) == 1 &&
        Rational::gcd(10, -3) == 1 &&
        Rational::gcd(-10, -3) == 1 &&
        Rational::gcd(30, 10) == 10 &&
        Rational::gcd(10, 30) == 10 &&
        Rational::gcd(0, 10) == 10 &&
        Rational::gcd(10, 0) == 10) std::cout << "gcd test passed\n";
    else std::cout << "gcd test failed\n";
  
    if (!Rational(22, 0).isNaN() &&
        !Rational(22, 9).isNaN() &&
        !Rational(0, 9).isNaN() &&
        !Rational(-22, 9).isNaN() &&
        !Rational(-22, 0).isNaN() &&
        Rational(0, 0).isNaN() 
        ) std::cout << "isNaN test passed\n";
    else std::cout << "isNaN test failed\n";
  
    if (Rational(22, 0) == Rational(22, 0) &&
        Rational(22, 0) == Rational(9, 0) &&
        !(Rational(22, 0) == Rational(22, 9)) &&
        !(Rational(22, 0) == Rational(-22, 9)) &&
        !(Rational(22, 0) == Rational(-22, 0)) &&
        !(Rational(22, 0) == Rational(0, 9)) &&
        !(Rational(22, 0) == Rational(0, 0)) &&
  
        Rational(22, 9) == Rational(22, 9) &&
        Rational(22, 9) == Rational(-22, -9) &&
        Rational(22, 9) == Rational(110, 45) &&
        Rational(22, 9) == Rational(-110, -45) &&
        !(Rational(22, 9) == Rational(-22, 9)) &&
        !(Rational(22, 9) == Rational(22, -9)) &&
        !(Rational(22, 9) == Rational(9, 22)) &&
        !(Rational(22, 9) == Rational(22, 0)) &&
        !(Rational(22, 9) == Rational(-22, 0)) &&
        !(Rational(22, 9) == Rational(0, 9)) &&
        !(Rational(22, 9) == Rational(0, 0)) &&
  
        Rational(0, 1) == Rational(0, 1) &&
        Rational(0, 1) == Rational(0, 9)  &&
        Rational(0, 1) == Rational(0, -9)  &&
        !(Rational(0, 1) == Rational(22, 9))  &&
        !(Rational(0, 1) == Rational(-22, 9))  &&
        !(Rational(0, 1) == Rational(22, 0)) &&
        !(Rational(0, 1) == Rational(-22, 0)) &&
        !(Rational(0, 1) == Rational(0, 0)) &&
  
        Rational(-22, 9) == Rational(-22, 9) &&
        Rational(-22, 9) == Rational(22, -9) &&
        Rational(-22, 9) == Rational(-110, 45) &&
        Rational(-22, 9) == Rational(110, -45) &&
        !(Rational(-22, 9) == Rational(-22, -9)) &&
        !(Rational(-22, 9) == Rational(22, 9)) &&
        !(Rational(-22, 9) == Rational(9, -22)) &&
        !(Rational(-22, 9) == Rational(22, 0)) &&
        !(Rational(-22, 9) == Rational(-22, 0)) &&
        !(Rational(-22, 9) == Rational(0, 9)) &&
        !(Rational(-22, 9) == Rational(0, 0)) &&
  
        Rational(-22, 0) == Rational(-22, 0) &&
        Rational(-22, 0) == Rational(-9, 0) &&
        !(Rational(-22, 0) == Rational(22, 9)) &&
        !(Rational(-22, 0) == Rational(-22, 9)) &&
        !(Rational(-22, 0) == Rational(22, 0)) &&
        !(Rational(-22, 0) == Rational(0, 9)) &&
        !(Rational(-22, 0) == Rational(0, 0)) &&
  
        !(Rational(0, 0) == Rational(0, 0))
        ) std::cout << "Equality test passed\n";
    else std::cout << "Equality test failed\n";
  
    if (Rational(22, 0) + Rational(22, 0) == Rational(22, 0) &&
        Rational(22, 9) + Rational(22, 0) == Rational(22, 0) &&
        Rational(0, 9) + Rational(22, 0) == Rational(22, 0) &&
        Rational(-22, 9) + Rational(22, 0) == Rational(22, 0) &&
        (Rational(-22, 0) + Rational(22, 0)).isNaN() &&
  
        Rational(22, 0) + Rational(22, 9) == Rational(22, 0) &&
        Rational(22, 9) + Rational(22, 9) == Rational(44, 9) &&
        Rational(0, 9) + Rational(22, 9) == Rational(22, 9) &&
        Rational(-22, 9) + Rational(22, 9) == Rational(0, 9) &&
        Rational(-22, 0) + Rational(22, 9) == Rational(-22, 0) &&
  
        Rational(22, 0) + Rational(0, 1) == Rational(22, 0) &&
        Rational(22, 9) + Rational(0, 1) == Rational(22, 9) &&
        Rational(0, 9) + Rational(0, 1) == Rational(0, 9) &&
        Rational(-22, 9) + Rational(0, 1) == Rational(-22, 9) &&
        Rational(-22, 0) + Rational(0, 1) == Rational(-22, 0) &&
  
        Rational(22, 0) + Rational(-22, 9) == Rational(22, 0) &&
        Rational(22, 9) + Rational(-22, 9) == Rational(0, 9) &&
        Rational(0, 9) + Rational(-22, 9) == Rational(-22, 9) &&
        Rational(-22, 9) + Rational(-22, 9) == Rational(-44, 9) &&
        Rational(-22, 0) + Rational(-22, 9) == Rational(-22, 0) &&
  
        (Rational(22, 0) + Rational(-22, 0)).isNaN() &&
        Rational(22, 9) + Rational(-22, 0) == Rational(-22, 0) &&
        Rational(0, 9) + Rational(-22, 0) == Rational(-22, 0) &&
        Rational(-22, 9) + Rational(-22, 0) == Rational(-22, 0) &&
        Rational(-22, 0) + Rational(-22, 0) == Rational(-22, 0) &&
  
        (Rational(22, 0) + Rational(0, 0)).isNaN() &&
        (Rational(22, 9) + Rational(0, 0)).isNaN() &&
        (Rational(0, 9) + Rational(0, 0)).isNaN() &&
        (Rational(-22, 9) + Rational(0, 0)).isNaN() &&
        (Rational(-22, 0) + Rational(0, 0)).isNaN()
       ) std::cout << "Summation test passed\n";
    else std::cout << "Summation test failed\n";
  
    if ((Rational(22, 0) - Rational(22, 0)).isNaN() &&
        Rational(22, 9) - Rational(22, 0) == Rational(-22, 0) &&
        Rational(0, 9) - Rational(22, 0) == Rational(-22, 0) &&
        Rational(-22, 9) - Rational(22, 0) == Rational(-22, 0) &&
        Rational(-22, 0) - Rational(22, 0) == Rational(-22, 0) &&
  
        Rational(22, 0) - Rational(22, 9) == Rational(22, 0) &&
        Rational(22, 9) - Rational(22, 9) == Rational(0, 9) &&
        Rational(0, 9) - Rational(22, 9) == Rational(-22, 9) &&
        Rational(-22, 9) - Rational(22, 9) == Rational(-44, 9) &&
        Rational(-22, 0) - Rational(22, 9) == Rational(-22, 0) &&
  
        Rational(22, 0) - Rational(0, 1) == Rational(22, 0) &&
        Rational(22, 9) - Rational(0, 1) == Rational(22, 9) &&
        Rational(0, 9) - Rational(0, 1) == Rational(0, 9) &&
        Rational(-22, 9) - Rational(0, 1) == Rational(-22, 9) &&
        Rational(-22, 0) - Rational(0, 1) == Rational(-22, 0) &&
  
        Rational(22, 0) - Rational(-22, 9) == Rational(22, 0) &&
        Rational(22, 9) - Rational(-22, 9) == Rational(44, 9) &&
        Rational(0, 9) - Rational(-22, 9) == Rational(22, 9) &&
        Rational(-22, 9) - Rational(-22, 9) == Rational(0, 9) &&
        Rational(-22, 0) - Rational(-22, 9) == Rational(-22, 0) &&
  
        Rational(22, 0) - Rational(-22, 0) == Rational(22, 0) &&
        Rational(22, 9) - Rational(-22, 0) == Rational(22, 0) &&
        Rational(0, 9) - Rational(-22, 0) == Rational(22, 0) &&
        Rational(-22, 9) - Rational(-22, 0) == Rational(22, 0) &&
        (Rational(-22, 0) - Rational(-22, 0)).isNaN() &&
  
        (Rational(22, 0) - Rational(0, 0)).isNaN() &&
        (Rational(22, 9) - Rational(0, 0)).isNaN() &&
        (Rational(0, 9) - Rational(0, 0)).isNaN() &&
        (Rational(-22, 9) - Rational(0, 0)).isNaN() &&
        (Rational(-22, 0) - Rational(0, 0)).isNaN()
        ) std::cout << "Subtraction test passed\n";
    else std::cout << "Subtraction test failed\n";
  
    if (Rational(22, 0) * Rational(22, 0) == Rational(22, 0) &&
        Rational(22, 9) * Rational(22, 0) == Rational(22, 0) &&
        (Rational(0, 9) * Rational(22, 0)).isNaN() &&
        Rational(-22, 9) * Rational(22, 0) == Rational(-22, 0) &&
        Rational(-22, 0) * Rational(22, 0) == Rational(-22, 0) &&
  
        Rational(22, 0) * Rational(22, 9) == Rational(22, 0) &&
        Rational(22, 9) * Rational(22, 9) == Rational(22*22, 9*9) &&
        Rational(0, 9) * Rational(22, 9) == Rational(0, 9) &&
        Rational(-22, 9) * Rational(22, 9) == Rational(-22*22, 9*9) &&
        Rational(-22, 0) * Rational(22, 9) == Rational(-22, 0) &&
  
        (Rational(22, 0) * Rational(0, 1)).isNaN() &&
        Rational(22, 9) * Rational(0, 1) == Rational(0, 9) &&
        Rational(0, 9) * Rational(0, 1) == Rational(0, 9) &&
        Rational(-22, 9) * Rational(0, 1) == Rational(0, 9) &&
        (Rational(-22, 0) * Rational(0, 1)).isNaN() &&
  
        Rational(22, 0) * Rational(-22, 9) == Rational(-22, 0) &&
        Rational(22, 9) * Rational(-22, 9) == Rational(-22*22, 9*9) &&
        Rational(0, 9) * Rational(-22, 9) == Rational(0, 9) &&
        Rational(-22, 9) * Rational(-22, 9) == Rational(22*22, 9*9) &&
        Rational(-22, 0) * Rational(-22, 9) == Rational(22, 0) &&
  
        Rational(22, 0) * Rational(-22, 0) == Rational(-22, 0) &&
        Rational(22, 9) * Rational(-22, 0) == Rational(-22, 0) &&
        (Rational(0, 9) * Rational(-22, 0)).isNaN() &&
        Rational(-22, 9) * Rational(-22, 0) == Rational(22, 0) &&
        Rational(-22, 0) * Rational(-22, 0) == Rational(22, 0) &&
  
        (Rational(22, 0) * Rational(0, 0)).isNaN() &&
        (Rational(22, 9) * Rational(0, 0)).isNaN() &&
        (Rational(0, 9) * Rational(0, 0)).isNaN() &&
        (Rational(-22, 9) * Rational(0, 0)).isNaN() &&
        (Rational(-22, 0) * Rational(0, 0)).isNaN()
        ) std::cout << "Multiplication test passed\n";
    else std::cout << "Multiplication test failed\n";
  
    if ((Rational(22, 0) / Rational(22, 0)).isNaN() &&
        Rational(22, 9) / Rational(22, 0) == Rational(0, 9) &&
        Rational(0, 9) / Rational(22, 0) == Rational(0, 9) &&
        Rational(-22, 9) / Rational(22, 0) == Rational(0, 9) &&
        (Rational(-22, 0) / Rational(22, 0)).isNaN() &&
  
        Rational(22, 0) / Rational(22, 9) == Rational(22, 0) &&
        Rational(22, 9) / Rational(22, 9) == Rational(9, 9) &&
        Rational(0, 9) / Rational(22, 9) == Rational(0, 9) &&
        Rational(-22, 9) / Rational(22, 9) == Rational(-9, 9) &&
        Rational(-22, 0) / Rational(22, 9) == Rational(-22, 0) &&
  
        Rational(22, 0) / Rational(0, 1) == Rational(22, 0) &&
        Rational(22, 9) / Rational(0, 1) == Rational(22, 0) &&
        (Rational(0, 9) / Rational(0, 1)).isNaN() &&
        Rational(-22, 9) / Rational(0, 1) == Rational(-22, 0) &&
        Rational(-22, 0) / Rational(0, 1) == Rational(-22, 0) &&
  
        Rational(22, 0) / Rational(-22, 9) == Rational(-22, 0) &&
        Rational(22, 9) / Rational(-22, 9) == Rational(-9, 9) &&
        Rational(0, 9) / Rational(-22, 9) == Rational(0, 9) &&
        Rational(-22, 9) / Rational(-22, 9) == Rational(9, 9) &&
        Rational(-22, 0) / Rational(-22, 9) == Rational(22, 0) &&
  
        (Rational(22, 0) / Rational(-22, 0)).isNaN() &&
        Rational(22, 9) / Rational(-22, 0) == Rational(0, 9) &&
        Rational(0, 9) / Rational(-22, 0) == Rational(0, 9) &&
        Rational(-22, 9) / Rational(-22, 0) == Rational(0, 9) &&
        (Rational(-22, 0) / Rational(-22, 0)).isNaN() &&
  
        (Rational(22, 0) / Rational(0, 0)).isNaN() &&
        (Rational(22, 9) / Rational(0, 0)).isNaN() &&
        (Rational(0, 9) / Rational(0, 0)).isNaN() &&
        (Rational(-22, 9) / Rational(0, 0)).isNaN() &&
        (Rational(-22, 0) / Rational(0, 0)).isNaN()
        ) std::cout << "Division test passed\n";
    else std::cout << "Division test failed\n";
  
    if (equal(Rational(-22, -9), 22/9.0) &&
        equal(Rational(-9, -9), 1) &&
        equal(Rational(-6, -9), 6/9.0) &&
        equal(Rational(0, -9), 0) &&
        equal(Rational(6, -9), -6/9.0) &&
        equal(Rational(9, -9), -1) &&
        equal(Rational(22, -9), -22/9.0) &&
        std::isinf((double)Rational(-9, 0)) &&
        std::isnan((double)Rational(0, 0)) &&
        std::isinf((double)Rational(9, 0)) &&
        equal(Rational(-22, 9), -22/9.0) &&
        equal(Rational(-9, 9), -1) &&
        equal(Rational(-6, 9), -6/9.0) &&
        equal(Rational(0, 9), 0) &&
        equal(Rational(6, 9), 6/9.0) &&
        equal(Rational(9, 9), 1) &&
        equal(Rational(22, 9), 22/9.0)) std::cout << "Conversion to double test passed\n";
    else std::cout << "Conversion to double test failed\n";
  
    if (Rational(-22, -9) &&
        Rational(-9, -9) &&
        Rational(-6, -9) &&
        !Rational(0, -9) &&
        Rational(6, -9) &&
        Rational(9, -9) &&
        Rational(22, -9) &&
        Rational(-9, 0) &&
        Rational(0, 0) &&
        Rational(9, 0) &&
        Rational(-22, 9) &&
        Rational(-9, 9) &&
        Rational(-6, 9) &&
        !Rational(0, 9) &&
        Rational(6, 9) &&
        Rational(9, 9) &&
        Rational(22, 9)) std::cout << "Conversion to bool test passed\n";
    else std::cout << "Conversion to bool test failed\n";
}
  
bool equal(double a, double b, double e) {
    if (-e < a - b && a - b < e) return true;
    else return false;
}
```

***Python***

По аналогии с заданием для **С++** реализуйте класс `Rational`.

В качестве обязательных членов должны присутствовать:

1. Метод `__init__`. Кроме `self` должен принимать ещё два параметра: `numerator ` и `denominator` - целые числа:
   - Если аргументы не заданы. То создаётся рациональное число инициализированное нулём;
   - Если задан только `numerator`. То создаётся рациональное число инициализированное $\frac{numerator}{1}$. 
   - Если заданы оба аргумента. То создаётся рациональное число инициализированное $\frac{numerator}{denominator}$. 
2. Финализатор. По необходимости.
3. Статический метод `gcd` принимающий два целых числа и возвращающий [наибольший общий делитель](https://ru.wikipedia.org/wiki/Наибольший_общий_делитель).
4. Метод `__eq__` (оператор `==`). Сравнивает два объекта класса `Rational` на равенство. 
5. Метод `__add__` (бинарный `+`). Левый и правый операнды класса `Rational`.  Возвращает рациональное число являющееся суммой левого и правого операндов.
6. Метод `__sub__` (бинарный `-`). Левый и правый операнды класса `Rational`.  Возвращает рациональное число являющееся разностью левого и правого операндов.
7. Метод `__mul__` (оператор `*`). Левый и правый операнды класса `Rational`.  Возвращает рациональное число являющееся произведением левого и правого операндов.
8. Метод `__truediv__` (оператор `/`). Левый и правый операнды класса `Rational`.  Возвращает рациональное число являющееся частным левого и правого операндов.
9. Операторы преобразования к типам:
   - `__float__` - возвращает вещественное число соответствующее рациональному;
   - `__bool__` - возвращает `false` если число равно нулю и `true` в остальных случаях;
10. Метод `numerator ` - возвращающий числитель;
11. Метод `denominator` - возвращающий знаменатель;
12. Метод `isNaN` - возвращающий `True`, если число соответствует $\frac{0}{0}$ и `False` в противном случае. Обратите внимание NaN, с точки зрения математики - это неопределённое число, то есть любое. Поэтому он не равен ни чему, даже самому себе.

Используйте код представленный ниже для проверки правильности реализации класса:

```python
import math
  
class Rational:
    pass # Ваш код здесь
  
def equal(a, b, e=1E-10):
    if -e < a - b < e: return True
    else: return False
  
if (Rational.gcd(91, 65) == 13 and
    Rational.gcd(10, 3) == 1 and
    Rational.gcd(-10, 3) == 1 and
    Rational.gcd(10, -3) == 1 and
    Rational.gcd(-10, -3) == 1 and
    Rational.gcd(30, 10) == 10 and
    Rational.gcd(10, 30) == 10 and
    Rational.gcd(0, 10) == 10 and
    Rational.gcd(10, 0) == 10
    ): print('gcd test passed')
else: print('gcd test failed')
  
if (not Rational(22, 0).isNaN() and
    not Rational(22, 9).isNaN() and
    not Rational(0, 9).isNaN() and
    not Rational(-22, 9).isNaN() and
    not Rational(-22, 0).isNaN() and
    Rational(0, 0).isNaN()
    ): print('isNaN test passed')
else: print('isNaN test failed')
  
if (Rational(22, 0) == Rational(22, 0) and
    Rational(22, 0) == Rational(9, 0) and
    not(Rational(22, 0) == Rational(22, 9)) and
    not(Rational(22, 0) == Rational(-22, 9)) and
    not(Rational(22, 0) == Rational(-22, 0)) and
    not(Rational(22, 0) == Rational(0, 9)) and
    not(Rational(22, 0) == Rational(0, 0)) and
  
    Rational(22, 9) == Rational(22, 9) and
    Rational(22, 9) == Rational(-22, -9) and
    Rational(22, 9) == Rational(110, 45) and
    Rational(22, 9) == Rational(-110, -45) and
    not(Rational(22, 9) == Rational(-22, 9)) and
    not(Rational(22, 9) == Rational(22, -9)) and
    not(Rational(22, 9) == Rational(9, 22)) and
    not(Rational(22, 9) == Rational(22, 0)) and
    not(Rational(22, 9) == Rational(-22, 0)) and
    not(Rational(22, 9) == Rational(0, 9)) and
    not(Rational(22, 9) == Rational(0, 0)) and
  
    Rational(0, 1) == Rational(0, 1) and
    Rational(0, 1) == Rational(0, 9)  and
    Rational(0, 1) == Rational(0, -9)  and
    not(Rational(0, 1) == Rational(22, 9))  and
    not(Rational(0, 1) == Rational(-22, 9))  and
    not(Rational(0, 1) == Rational(22, 0)) and
    not(Rational(0, 1) == Rational(-22, 0)) and
    not(Rational(0, 1) == Rational(0, 0)) and
  
    Rational(-22, 9) == Rational(-22, 9) and
    Rational(-22, 9) == Rational(22, -9) and
    Rational(-22, 9) == Rational(-110, 45) and
    Rational(-22, 9) == Rational(110, -45) and
    not(Rational(-22, 9) == Rational(-22, -9)) and
    not(Rational(-22, 9) == Rational(22, 9)) and
    not(Rational(-22, 9) == Rational(9, -22)) and
    not(Rational(-22, 9) == Rational(22, 0)) and
    not(Rational(-22, 9) == Rational(-22, 0)) and
    not(Rational(-22, 9) == Rational(0, 9)) and
    not(Rational(-22, 9) == Rational(0, 0)) and
  
    Rational(-22, 0) == Rational(-22, 0) and
    Rational(-22, 0) == Rational(-9, 0) and
    not(Rational(-22, 0) == Rational(22, 9)) and
    not(Rational(-22, 0) == Rational(-22, 9)) and
    not(Rational(-22, 0) == Rational(22, 0)) and
    not(Rational(-22, 0) == Rational(0, 9)) and
    not(Rational(-22, 0) == Rational(0, 0)) and
  
    not(Rational(0, 0) == Rational(0, 0))
    ): print('Equality test passed')
else: print('Equality test failed')
  
if (Rational(22, 0) + Rational(22, 0) == Rational(22, 0) and
    Rational(22, 9) + Rational(22, 0) == Rational(22, 0) and
    Rational(0, 9) + Rational(22, 0) == Rational(22, 0) and
    Rational(-22, 9) + Rational(22, 0) == Rational(22, 0) and
    (Rational(-22, 0) + Rational(22, 0)).isNaN() and
  
    Rational(22, 0) + Rational(22, 9) == Rational(22, 0) and
    Rational(22, 9) + Rational(22, 9) == Rational(44, 9) and
    Rational(0, 9) + Rational(22, 9) == Rational(22, 9) and
    Rational(-22, 9) + Rational(22, 9) == Rational(0, 9) and
    Rational(-22, 0) + Rational(22, 9) == Rational(-22, 0) and
  
    Rational(22, 0) + Rational(0, 1) == Rational(22, 0) and
    Rational(22, 9) + Rational(0, 1) == Rational(22, 9) and
    Rational(0, 9) + Rational(0, 1) == Rational(0, 9) and
    Rational(-22, 9) + Rational(0, 1) == Rational(-22, 9) and
    Rational(-22, 0) + Rational(0, 1) == Rational(-22, 0) and
  
    Rational(22, 0) + Rational(-22, 9) == Rational(22, 0) and
    Rational(22, 9) + Rational(-22, 9) == Rational(0, 9) and
    Rational(0, 9) + Rational(-22, 9) == Rational(-22, 9) and
    Rational(-22, 9) + Rational(-22, 9) == Rational(-44, 9) and
    Rational(-22, 0) + Rational(-22, 9) == Rational(-22, 0) and
  
    (Rational(22, 0) + Rational(-22, 0)).isNaN() and
    Rational(22, 9) + Rational(-22, 0) == Rational(-22, 0) and
    Rational(0, 9) + Rational(-22, 0) == Rational(-22, 0) and
    Rational(-22, 9) + Rational(-22, 0) == Rational(-22, 0) and
    Rational(-22, 0) + Rational(-22, 0) == Rational(-22, 0) and
  
    (Rational(22, 0) + Rational(0, 0)).isNaN() and
    (Rational(22, 9) + Rational(0, 0)).isNaN() and
    (Rational(0, 9) + Rational(0, 0)).isNaN() and
    (Rational(-22, 9) + Rational(0, 0)).isNaN() and
    (Rational(-22, 0) + Rational(0, 0)).isNaN()
    ): print('Summation test passed')
else: print('Summation test failed')
  
if ((Rational(22, 0) - Rational(22, 0)).isNaN() and
    Rational(22, 9) - Rational(22, 0) == Rational(-22, 0) and
    Rational(0, 9) - Rational(22, 0) == Rational(-22, 0) and
    Rational(-22, 9) - Rational(22, 0) == Rational(-22, 0) and
    Rational(-22, 0) - Rational(22, 0) == Rational(-22, 0) and
  
    Rational(22, 0) - Rational(22, 9) == Rational(22, 0) and
    Rational(22, 9) - Rational(22, 9) == Rational(0, 9) and
    Rational(0, 9) - Rational(22, 9) == Rational(-22, 9) and
    Rational(-22, 9) - Rational(22, 9) == Rational(-44, 9) and
    Rational(-22, 0) - Rational(22, 9) == Rational(-22, 0) and
  
    Rational(22, 0) - Rational(0, 1) == Rational(22, 0) and
    Rational(22, 9) - Rational(0, 1) == Rational(22, 9) and
    Rational(0, 9) - Rational(0, 1) == Rational(0, 9) and
    Rational(-22, 9) - Rational(0, 1) == Rational(-22, 9) and
    Rational(-22, 0) - Rational(0, 1) == Rational(-22, 0) and
  
    Rational(22, 0) - Rational(-22, 9) == Rational(22, 0) and
    Rational(22, 9) - Rational(-22, 9) == Rational(44, 9) and
    Rational(0, 9) - Rational(-22, 9) == Rational(22, 9) and
    Rational(-22, 9) - Rational(-22, 9) == Rational(0, 9) and
    Rational(-22, 0) - Rational(-22, 9) == Rational(-22, 0) and
  
    Rational(22, 0) - Rational(-22, 0) == Rational(22, 0) and
    Rational(22, 9) - Rational(-22, 0) == Rational(22, 0) and
    Rational(0, 9) - Rational(-22, 0) == Rational(22, 0) and
    Rational(-22, 9) - Rational(-22, 0) == Rational(22, 0) and
    (Rational(-22, 0) - Rational(-22, 0)).isNaN() and
  
    (Rational(22, 0) - Rational(0, 0)).isNaN() and
    (Rational(22, 9) - Rational(0, 0)).isNaN() and
    (Rational(0, 9) - Rational(0, 0)).isNaN() and
    (Rational(-22, 9) - Rational(0, 0)).isNaN() and
    (Rational(-22, 0) - Rational(0, 0)).isNaN()
    ): print('Subtraction test passed')
else: print('Subtraction test failed')
  
if (Rational(22, 0) * Rational(22, 0) == Rational(22, 0) and
    Rational(22, 9) * Rational(22, 0) == Rational(22, 0) and
    (Rational(0, 9) * Rational(22, 0)).isNaN() and
    Rational(-22, 9) * Rational(22, 0) == Rational(-22, 0) and
    Rational(-22, 0) * Rational(22, 0) == Rational(-22, 0) and
  
    Rational(22, 0) * Rational(22, 9) == Rational(22, 0) and
    Rational(22, 9) * Rational(22, 9) == Rational(22*22, 9*9) and
    Rational(0, 9) * Rational(22, 9) == Rational(0, 9) and
    Rational(-22, 9) * Rational(22, 9) == Rational(-22*22, 9*9) and
    Rational(-22, 0) * Rational(22, 9) == Rational(-22, 0) and
  
    (Rational(22, 0) * Rational(0, 1)).isNaN() and
    Rational(22, 9) * Rational(0, 1) == Rational(0, 9) and
    Rational(0, 9) * Rational(0, 1) == Rational(0, 9) and
    Rational(-22, 9) * Rational(0, 1) == Rational(0, 9) and
    (Rational(-22, 0) * Rational(0, 1)).isNaN() and
  
    Rational(22, 0) * Rational(-22, 9) == Rational(-22, 0) and
    Rational(22, 9) * Rational(-22, 9) == Rational(-22*22, 9*9) and
    Rational(0, 9) * Rational(-22, 9) == Rational(0, 9) and
    Rational(-22, 9) * Rational(-22, 9) == Rational(22*22, 9*9) and
    Rational(-22, 0) * Rational(-22, 9) == Rational(22, 0) and
  
    Rational(22, 0) * Rational(-22, 0) == Rational(-22, 0) and
    Rational(22, 9) * Rational(-22, 0) == Rational(-22, 0) and
    (Rational(0, 9) * Rational(-22, 0)).isNaN() and
    Rational(-22, 9) * Rational(-22, 0) == Rational(22, 0) and
    Rational(-22, 0) * Rational(-22, 0) == Rational(22, 0) and
  
    (Rational(22, 0) * Rational(0, 0)).isNaN() and
    (Rational(22, 9) * Rational(0, 0)).isNaN() and
    (Rational(0, 9) * Rational(0, 0)).isNaN() and
    (Rational(-22, 9) * Rational(0, 0)).isNaN() and
    (Rational(-22, 0) * Rational(0, 0)).isNaN()
    ): print('Multiplication test passed')
else: print('Multiplication test failed')
  
if ((Rational(22, 0) / Rational(22, 0)).isNaN() and
    Rational(22, 9) / Rational(22, 0) == Rational(0, 9) and
    Rational(0, 9) / Rational(22, 0) == Rational(0, 9) and
    Rational(-22, 9) / Rational(22, 0) == Rational(0, 9) and
    (Rational(-22, 0) / Rational(22, 0)).isNaN() and
  
    Rational(22, 0) / Rational(22, 9) == Rational(22, 0) and
    Rational(22, 9) / Rational(22, 9) == Rational(9, 9) and
    Rational(0, 9) / Rational(22, 9) == Rational(0, 9) and
    Rational(-22, 9) / Rational(22, 9) == Rational(-9, 9) and
    Rational(-22, 0) / Rational(22, 9) == Rational(-22, 0) and
  
    Rational(22, 0) / Rational(0, 1) == Rational(22, 0) and
    Rational(22, 9) / Rational(0, 1) == Rational(22, 0) and
    (Rational(0, 9) / Rational(0, 1)).isNaN() and
    Rational(-22, 9) / Rational(0, 1) == Rational(-22, 0) and
    Rational(-22, 0) / Rational(0, 1) == Rational(-22, 0) and
  
    Rational(22, 0) / Rational(-22, 9) == Rational(-22, 0) and
    Rational(22, 9) / Rational(-22, 9) == Rational(-9, 9) and
    Rational(0, 9) / Rational(-22, 9) == Rational(0, 9) and
    Rational(-22, 9) / Rational(-22, 9) == Rational(9, 9) and
    Rational(-22, 0) / Rational(-22, 9) == Rational(22, 0) and
  
    (Rational(22, 0) / Rational(-22, 0)).isNaN() and
    Rational(22, 9) / Rational(-22, 0) == Rational(0, 9) and
    Rational(0, 9) / Rational(-22, 0) == Rational(0, 9) and
    Rational(-22, 9) / Rational(-22, 0) == Rational(0, 9) and
    (Rational(-22, 0) / Rational(-22, 0)).isNaN() and
  
    (Rational(22, 0) / Rational(0, 0)).isNaN() and
    (Rational(22, 9) / Rational(0, 0)).isNaN() and
    (Rational(0, 9) / Rational(0, 0)).isNaN() and
    (Rational(-22, 9) / Rational(0, 0)).isNaN() and
    (Rational(-22, 0) / Rational(0, 0)).isNaN()
    ): print('Division test passed')
else: print('Division test failed')
  
if (equal(float(Rational(-22, -9)), 22/9.0) and
    equal(float(Rational(-9, -9)), 1) and
    equal(float(Rational(-6, -9)), 6/9.0) and
    equal(float(Rational(0, -9)), 0) and
    equal(float(Rational(6, -9)), -6/9.0) and
    equal(float(Rational(9, -9)), -1) and
    equal(float(Rational(22, -9)), -22/9.0) and
    math.isinf(float(Rational(-9, 0))) and
    math.isnan(float(Rational(0, 0))) and
    math.isinf(float(Rational(9, 0))) and
    equal(float(Rational(-22, 9)), -22/9.0) and
    equal(float(Rational(-9, 9)), -1) and
    equal(float(Rational(-6, 9)), -6/9.0) and
    equal(float(Rational(0, 9)), 0) and
    equal(float(Rational(6, 9)), 6/9.0) and
    equal(float(Rational(9, 9)), 1) and
    equal(float(Rational(22, 9)), 22/9.0)
    ): print('Conversion to double test passed')
else: print('Conversion to double test failed')
  
if (bool(Rational(-22, -9)) and
    bool(Rational(-9, -9)) and
    bool(Rational(-6, -9)) and
    not bool(Rational(0, -9)) and
    bool(Rational(6, -9)) and
    bool(Rational(9, -9)) and
    bool(Rational(22, -9)) and
    bool(Rational(-9, 0)) and
    bool(Rational(0, 0)) and
    bool(Rational(9, 0)) and
    bool(Rational(-22, 9)) and
    bool(Rational(-9, 9)) and
    bool(Rational(-6, 9)) and
    not bool(Rational(0, 9)) and
    bool(Rational(6, 9)) and
    bool(Rational(9, 9)) and
    bool(Rational(22, 9))
    ): print('Conversion to bool test passed')
else: print('Conversion to bool test failed')
```

**Формат ввода**  
Ввода нет.

**Формат вывода**  
Все тесты должны быть пройдены (`passed`). Если хотя бы один тест не пройден (`failed`), то класс реализован не правильно.