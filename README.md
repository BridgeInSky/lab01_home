# lab01_home
  1. Скачайте библиотеку boost с помощью утилиты wget. Адрес для скачивания https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz.
```bash
wget https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz
```
С помощью данной функции мы скачали библиотеку boost. Теперь проверим, есть ли в папке tasks наш файл.
```
ls
```
На выходе получили
boost_1_69_0.tar.gz
Архив скачан
  2. Разархивируйте скаченный файл в директорию ~/boost_1_69_0
```
tar -xzf boost_1_69_0.tar.gz -C ~/
```
Проверим, разархивировался ли файл. 
```
ls ~
```
На выходе получили такой список:
```
 a              snap        Документы     Музыка          Шаблоны
 boost_1_69_0   workspace   Загрузки      Общедоступные
 BridgeInSky    Видео       Изображения  'Рабочий стол'
```
Среди элементов списка видим название нашего файла. Значит, всё прошло успешно.
  3. Подсчитайте количество файлов в директории ~/boost_1_69_0 не включая вложенные директории.
```
 find ~/boost_1_69_0 -maxdepth 1 -type f | wc -l
```
С помощью функции *find* найдем файлы и директории, начиная с указанного пути.

*-maxdepth 1* — ограничивает поиск только текущей директорией (без вложенных).

*-type f* — ищет только файлы.

| — передаёт результат команды *find* в *wc*.

*wc -l* — подсчитывает количество строк (каждая строка соответствует одному файлу).

На выходе получим:
12

  4. Подсчитайте количество файлов в директории ~/boost_1_69_0 включая вложенные директории.
```
find ~/boost_1_69_0 -type f | wc -l
```
Воспользуемся той же функцией *find*, только не будем использовать ограничение по "глубине" поиска.
На выходе получим:
61191

  5. Подсчитайте количество заголовочных файлов, файлов с расширением .cpp, сколько остальных файлов (не заголовочных и не .cpp).
Заголовочные файлы (.h или .hpp)
```
find ~/boost_1_69_0 -type f \( -name "*.h" -o -name "*.hpp" \) | wc -l
```
На выходе получим:
15208

Подсчёт файлов с расширением .cpp
```
find ~/boost_1_69_0 -type f -name "*.cpp" | wc -l
```
На выходе получим:
13774

Подсчёт остальных файлов (не .h, не .hpp, не .cpp)
```
find ~/boost_1_69_0 -type f -not \( -name "*.h" -a -name "*.hpp" -a -name "*.cpp" \) | wc -l
```
На выходе получим:
61191

  6. Найдите полный путь до файла any.hpp внутри библиотеки boost.
```
find ~/boost_1_69_0 -name "any.hpp" 2>/dev/null
```
В данном выражении 

*2>/dev/null - подавляет ошибки доступа (например, если нет прав на чтение некоторых директорий).

Мы получили такой список:

```
/home/liza/boost_1_69_0/boost/spirit/home/support/algorithm/any.hpp
/home/liza/boost_1_69_0/boost/any.hpp
/home/liza/boost_1_69_0/boost/proto/detail/any.hpp
/home/liza/boost_1_69_0/boost/xpressive/detail/utility/any.hpp
/home/liza/boost_1_69_0/boost/hana/any.hpp
/home/liza/boost_1_69_0/boost/hana/fwd/any.hpp
/home/liza/boost_1_69_0/boost/type_erasure/any.hpp
/home/liza/boost_1_69_0/boost/fusion/algorithm/query/detail/any.hpp
/home/liza/boost_1_69_0/boost/fusion/algorithm/query/any.hpp
/home/liza/boost_1_69_0/boost/fusion/include/any.hpp
```
  7. Выведите в консоль все файлы, где упоминается последовательность boost::asio.

/home/liza/boost_1_69_0/boost/spirit/home/support/algorithm/any.hpp
/home/liza/boost_1_69_0/boost/any.hpp
/home/liza/boost_1_69_0/boost/proto/detail/any.hpp
/home/liza/boost_1_69_0/boost/xpressive/detail/utility/any.hpp
/home/liza/boost_1_69_0/boost/hana/any.hpp
/home/liza/boost_1_69_0/boost/hana/fwd/any.hpp
/home/liza/boost_1_69_0/boost/type_erasure/any.hpp
/home/liza/boost_1_69_0/boost/fusion/algorithm/query/detail/any.hpp
/home/liza/boost_1_69_0/boost/fusion/algorithm/query/any.hpp
/home/liza/boost_1_69_0/boost/fusion/include/any.hpp

  8. Скомпилирутйе boost. Можно воспользоваться инструкцией или ссылкой.

  11. Перенесите все скомпилированные на предыдущем шаге статические библиотеки в директорию ~/boost-libs.
  12. Подсчитайте сколько занимает дискового пространства каждый файл в этой директории.
  13. Найдите топ10 самых "тяжёлых".
