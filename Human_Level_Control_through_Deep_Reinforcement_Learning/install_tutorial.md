# Human level control paper

## Скачиваем код

[Ссылка](https://sites.google.com/a/deepmind.com/dqn/)

## Зависимости

* LuaJIT и Torch 7.0
* nngraph
* Xitari (fork of the Arcade Learning Environment (Bellemare et al., 2013))
* AleWrap (a lua interface to Xitari)

## Установка зависимостей

Linux с менеджером пакетов apt-get.

Важно: для запуска на GPU необходимо установить
NVIDIA® CUDA® (версия 5.5 и выше).

Исполняем скрипт:

`./install_dependencies.sh`

Важно: скрипт установит следующие пакеты с помощью apt-get:
`build-essential, gcc, g++, cmake, curl, libreadline-dev, git-core, libjpeg-dev,
libpng-dev, ncurses-dev, imagemagick, unzip`

## Запуск

Добавляем ROM файл в папку `roms` (проверьте название файла, обязательно все буквы в названии должны быть в lower-case).

Запуск на GPU:

`./run_gpu <game name>`

Можно указать ID GPU:

`GPU_ID=2 ./run_gpu <game name>`

Запуск на CPU:

`./run_cpu <game name>`


