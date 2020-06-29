Лабораторная работа №2 по ТиМП

Работу выполнил: Сакулин Даниил

Клонируем репозиторий:

```
$ git clone https://github.com/tp-labs/lab03-1
Cloning into 'lab03-1'...
remote: Enumerating objects: 15, done.
remote: Counting objects: 100% (15/15), done.
remote: Compressing objects: 100% (13/13), done.
remote: Total 88 (delta 7), reused 4 (delta 2), pack-reused 73
Unpacking objects: 100% (88/88), done.
```

Задание 1

Переходим в директорию formatter_lib:

```
$ cd lab03-1/formatter_lib
```

Указываем минимальную версию CMake и название проекта:

```
$ cat > CMakeLists.txt <<EOF
> cmake_minimum_required(VERSION 3.4)
> project(formatter)
> EOF
```

Устанавливаем стандарт С++11, делаем его обязательным:

```
$ cat >> CMakeLists.txt <<EOF
> set(CMAKE_CXX_STANDARD 11)
> set(CMAKE_CXX_STANDARD_REQUIRED ON)
> EOF
```

Создаем статическую библиотеку:

```
$ cat >> CMakeLists.txt  << EOF
> add_library(formatter STATIC \${CMAKE_CURRENT_SOURCE_DIR}/formatter.cpp)
> EOF
```

Указываем в каких директориях необходимо искать заголовочные файлы:

```
$ cat >> CMakeLists.txt <<EOF
> include_directories(\${CMAKE_CURRENT_SOURCE_DIR}/)
> EOF
```

Задание 2

Переходим в директорию formatter_ex_lib:

```
$ cd .. $ cd formatter_ex_lib/
```

Указываем минимальную версию CMake и название проекта:

```
$ cat > CMakeLists.txt <<EOF
> cmake_minimum_required(VERSION 3.4)
> project(formatter_ex)
> EOF
```

Устанавливаем стандарт С++11 и делаем его обязательным

```
$ cat >> CMakeLists.txt <<EOF
> set(CMAKE_CXX_STANDARD 11)
> set(CMAKE_CXX_STANDARD_REQUIRED ON)
> EOF
```

Создаем статическую библиотеку:

```
$ cat >> CMakeLists.txt  << EOF
> add_library(formatter_ex STATIC \${CMAKE_CURRENT_SOURCE_DIR}/formatter_ex.cpp)
> EOF
```

Указываем, в каких директориях необходимо искать заголовочные файлы

```
$ cat >> CMakeLists.txt <<EOF
> include_directories(\${CMAKE_CURRENT_SOURCE_DIR}/ lab03-1/formatter_lib/)
> EOF
```

Задание 3 - 1

Переходим в нужную директорию:

```
$ cd ..
$ mkdir hello_world
$ cd hello_world/
```

Указываем минимальную версию CMake и название проекта:

```
$ cat > CMakeLists.txt <<EOF
> cmake_minimum_required(VERSION 3.4)
> project(hello_world)
> EOF
```

Устанавливаем стандарт С++11 и делаем его обязательным:

```
$ cat >> CMakeLists.txt <<EOF
> set(CMAKE_CXX_STANDARD 11)
> set(CMAKE_CXX_STANDARD_REQUIRED ON)
> EOF
```

Создаем статическую библиотеку:

```
$ cat >> CMakeLists.txt  << EOF
> add_library(formatter_ex STATIC lab03-1/formatter_ex_lib/formatter_ex.cpp)
> EOF
```

Указываем в каких директориях необходимо искать заголовочные файлы

```
$ cat >> CMakeLists.txt <<EOF
> include_directories(lab03-1/formatter_ex_lib/)
> EOF
```

Добавляем цель для сборки:

```
$ cat >> CMakeLists.txt <<EOF
> add_executable(program \${CMAKE_CURRENT_SOURCE_DIR}/program.cpp)
> EOF
```

Подключаем библиотеку к исполняемому файлу:

```
$ cat >> CMakeLists.txt <<EOF
> target_link_libraries(program hello_world)
> EOF 
```

Задание 3 - 2

Переходим в нужную директорию:
```
$ cd ..
$ mkdir solver
$ cd solver/
```

Указываем минимальную версию CMake и название проекта:

```
$ cat > CMakeLists.txt <<EOF
> cmake_minimum_required(VERSION 3.4)
> project(solver)
> EOF
```

Устанавливаем стандарт С++11 и делаем его обязательным:

```
$ cat >> CMakeLists.txt <<EOF
> set(CMAKE_CXX_STANDARD 11)
> set(CMAKE_CXX_STANDARD_REQUIRED ON)
> EOF
```

Создаем статические библиотеки:

```
$ cat >> CMakeLists.txt  << EOF
> add_library(formatter_ex STATIC lab03-1/formatter_ex_lib/formatter_ex.cpp)
> add_library(solver_lib STATIC lab03-1/solver_lib/solver.cpp)
> EOF
```

Указываем в каких директориях необходимо искать заголовочные файлы:

```
$ cat >> CMakeLists.txt <<EOF
> include_directories(lab03-1/formatter_ex_lib/)
> include_directories(lab03-1/solver_lib/)
> EOF
```

Добавляем цель для сборки:

```
$ cat >> CMakeLists.txt <<EOF
> add_executable(program \${CMAKE_CURRENT_SOURCE_DIR}/program.cpp)
> EOF
```

Подключаем библиотеки к исполняемому файлу

```
$ cat >> CMakeLists.txt <<EOF
> target_link_libraries(program solver_lib)
> target_link_libraries(program formatter_ex)
> EOF 
```
