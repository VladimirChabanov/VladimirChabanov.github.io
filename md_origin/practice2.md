[TOC]

#### <span>23</span>. Название

<div id="testing" style="background-size: 40px 40px; background-image: -moz-linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); background-image: -webkit-linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); background-image: linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); box-shadow: 0 0 8px rgba(0,0,0,.3); width: 100%; margin: 0 auto; padding:15px; background-color: #4ea5cd; border-left:7px #3b8eb5 solid;">
<a href="#" style="text-decoration: none; font:16px 'Open Sans'; font-weight:600; color:#f4f0fc;">Ссылка для тренировки (скоро)</a>
</div>

Скоро



#### <span>24</span>. Работа с json

<div id="testing" style="background-size: 40px 40px; background-image: -moz-linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); background-image: -webkit-linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); background-image: linear-gradient(135deg, rgba(255, 255, 255, .05) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, .05) 50%, rgba(255, 255, 255, .05) 75%, transparent 75%, transparent); box-shadow: 0 0 8px rgba(0,0,0,.3); width: 100%; margin: 0 auto; padding:15px; background-color: #4ea5cd; border-left:7px #3b8eb5 solid;">
<a href="#" style="text-decoration: none; font:16px 'Open Sans'; font-weight:600; color:#f4f0fc;">Ссылка для тренировки (скоро)</a>
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

Где поле `userId` - это целое число, идентификатор пользователя [1, ...]; `id` - целое число, идентификатор (номер) записи в массиве [1, ...]; `title` - название задачи, строка состоящая символов латинского алфавита; `completed` - логическое значение, указывает выполнена ли задача (true - выполнена, false - не выполнена).

Для каждого пользователя посчитайте количество выполненных задач и результат сохраните в файл `out.json` в формате json. Данные должны быть представлены в виде массива объектов вида: 

```json
{
  "userId": 1,
  "task_completed": 10
}
```

Где поле `userId` - это целое число, идентификатор пользователя [1, ...]; `task_completed` - целое число, количество выполненных пользователем задач [0, ...].

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

