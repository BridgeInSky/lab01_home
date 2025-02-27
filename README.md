# lab01_home
  1. Скачайте библиотеку boost с помощью утилиты wget. Адрес для скачивания

https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz.

```bash
wget https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz
```
На выходе получим:
```
HTTP response 301  [https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz]
Adding URL: https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz/
HTTP response 301  [https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz/]
Adding URL: https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz/download
HTTP response 302  [https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz/download]
Adding URL: https://downloads.sourceforge.net/project/boost/boost/1.69.0/boost_1_69_0.tar.gz?ts=gAAAAABnu08bVTCwNGk_VeQFfggtWlYHHTTP response 302  [https://downloads.sourceforge.net/project/boost/boost/1.69.0/boost_1_69_0.tar.gz?ts=gAAAAABnu08bVTCwNGk_VeQFAdding URL: https://deac-riga.dl.sourceforge.net/project/boost/boost/1.69.0/boost_1_69_0.tar.gz?viasf=1
Saving 'boost_1_69_0.tar.gz'
HTTP response 200 OK [https://deac-riga.dl.sourceforge.net/project/boost/boost/1.87.0/boost_1_69_0.tar.gz?viasf=1]
boost_1_69_0.tar.gz  100% [=============================================================================>]  147.73M  846.15KB/s
                          [Files: 1  Bytes: 147.73M [879.96KB/s] Redirects: 4  Todo: 0  Errors: 0        ]
```
Теперь проверим содержимое
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

```
grep -rnw ~/boost_1_69_0/ -e 'boost::asio' >> ~/'Рабочий стол'/asio.txt
```
  -r — рекурсивный поиск по всем файлам в директории и её поддиректориях.

  n — выводит номер строки, где найдено совпадение.

  w — ищет точное совпадение слова (чтобы избежать частичных совпадений).

  -e 'boost::asio' — шаблон для поиска.

  Результат работы 

  https://github.com/BridgeInSky/lab01_home/blob/main/asio.txt

  8. Скомпилирутйе boost. Можно воспользоваться инструкцией или ссылкой.
```
cd ~/boost_1_69_0

./bootstrap.sh

./b2 --prefix=~/'Рабочий стол'/Boost install
```
  Воспользовались инструкцией,скомпилировали boost в папку Boost на рабочем столе
  Результат работы программы представлен в файле

  https://github.com/BridgeInSky/lab01_home/blob/main/result.txt

  9. Перенесите все скомпилированные на предыдущем шаге статические библиотеки в директорию ~/boost-libs.
```
mkdir -p ~/boost-libs
cd ./boost_1_69_0/~/'Рабочий стол'/Boost
cp lib/*.a ~/boost-libs
ls ~/ boost-libs
```
  Cоздали директорию

  Вошли в директорию, куда была скомпилирована boost

  Скопировали все скомпилированные статические библиотеки в созданную директорию

  В результате работы последней операции видим:
```
libboost_atomic.a      libboost_math_tr1l.a
libboost_chrono.a      libboost_prg_exec_monitor.a
libboost_container.a   libboost_program_options.a
libboost_context.a     libboost_random.a
libboost_contract.a    libboost_regex.a
libboost_date_time.a   libboost_serialization.a
libboost_exception.a   libboost_stacktrace_addr2line.a
libboost_fiber.a       libboost_stacktrace_backtrace.a
libboost_filesystem.a  libboost_stacktrace_basic.a
libboost_graph.a       libboost_stacktrace_noop.a
libboost_iostreams.a   libboost_system.a
libboost_locale.a      libboost_test_exec_monitor.a
libboost_math_c99.a    libboost_timer.a
libboost_math_c99f.a   libboost_unit_test_framework.a
libboost_math_c99l.a   libboost_wave.a
libboost_math_tr1.a    libboost_wserialization.a
libboost_math_tr1f.a
```
  Значит, все статические библиотеки перенесены успешно.

  10. Подсчитайте сколько занимает дискового пространства каждый файл в этой директории.
```
du -ah ~/boost-libs >> ~/'Рабочий стол'/result.txt
```
  -a — отображает размер каждого файла.

  -h — выводит размер в удобном для чтения формате (например, 1K, 234M, 2G).

  Результат работы операции записали в файл, чтобы результаты было удобно использовать

  Результат:
```
2,7M	/home/liza/boost-libs/libboost_regex.a
24K	/home/liza/boost-libs/libboost_stacktrace_addr2line.a
2,0M	/home/liza/boost-libs/libboost_locale.a
2,7M	/home/liza/boost-libs/libboost_math_tr1l.a
152K	/home/liza/boost-libs/libboost_date_time.a
232K	/home/liza/boost-libs/libboost_fiber.a
2,6M	/home/liza/boost-libs/libboost_math_tr1f.a
464K	/home/liza/boost-libs/libboost_math_c99l.a
540K	/home/liza/boost-libs/libboost_math_c99.a
4,0K	/home/liza/boost-libs/result.txt
56K	/home/liza/boost-libs/libboost_timer.a
1,2M	/home/liza/boost-libs/libboost_serialization.a
148K	/home/liza/boost-libs/libboost_container.a
1,6M	/home/liza/boost-libs/libboost_program_options.a
80K	/home/liza/boost-libs/libboost_random.a
796K	/home/liza/boost-libs/libboost_wserialization.a
848K	/home/liza/boost-libs/libboost_graph.a
16K	/home/liza/boost-libs/libboost_stacktrace_basic.a
4,0K	/home/liza/boost-libs/libboost_stacktrace_noop.a
4,0K	/home/liza/boost-libs/libboost_atomic.a
24K	/home/liza/boost-libs/libboost_context.a
236K	/home/liza/boost-libs/libboost_chrono.a
212K	/home/liza/boost-libs/libboost_prg_exec_monitor.a
416K	/home/liza/boost-libs/libboost_filesystem.a
332K	/home/liza/boost-libs/libboost_contract.a
448K	/home/liza/boost-libs/libboost_math_c99f.a
4,5M	/home/liza/boost-libs/libboost_wave.a
2,3M	/home/liza/boost-libs/libboost_test_exec_monitor.a
4,0K	/home/liza/boost-libs/libboost_system.a
20K	/home/liza/boost-libs/libboost_stacktrace_backtrace.a
172K	/home/liza/boost-libs/libboost_iostreams.a
2,3M	/home/liza/boost-libs/libboost_unit_test_framework.a
2,7M	/home/liza/boost-libs/libboost_math_tr1.a
4,0K	/home/liza/boost-libs/libboost_exception.a
30M	/home/liza/boost-libs
```

  11. Найдите топ10 самых "тяжёлых".
```
du -ah ~/boost-libs | sort -rh | head -n 11 >> ~/'Рабочий стол'/result.txt
```
-r — сортирует в обратном порядке (от большего к меньшему).

-h — учитывает человеко-читаемые размеры (например, 1K, 234M, 2G).

head -n 11 — выводит только первые 11 строк (первая строка - сама директория)

Результат:
```
30M	/home/liza/boost-libs
4,5M	/home/liza/boost-libs/libboost_wave.a
2,7M	/home/liza/boost-libs/libboost_regex.a
2,7M	/home/liza/boost-libs/libboost_math_tr1l.a
2,7M	/home/liza/boost-libs/libboost_math_tr1.a
2,6M	/home/liza/boost-libs/libboost_math_tr1f.a
2,3M	/home/liza/boost-libs/libboost_unit_test_framework.a
2,3M	/home/liza/boost-libs/libboost_test_exec_monitor.a
2,0M	/home/liza/boost-libs/libboost_locale.a
1,6M	/home/liza/boost-libs/libboost_program_options.a
1,2M	/home/liza/boost-libs/libboost_serialization.a
```
