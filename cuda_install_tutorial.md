# Установка CUDA

## Проверка совместимости видеокарты и просмотр версии CUDA

[CUDA GPUs](https://developer.nvidia.com/cuda-gpus)

## Действия перед установкой на Ubuntu

[Ссылка на скачивание CUDA Toolkit](https://developer.nvidia.com/cuda-downloads)

Удаляем предыдущие драйвера NVIDIA (можно пропустить если нет необходимости устанавливать последнюю версию):

`sudo apt-get remove nvidia*`

`sudo apt-get autoremove`

Пререквизиты:

`sudo apt-get update`

`sudo apt-get install dkms build-essential linux-headers-generic`

Следующие действия исправляют ошибку, при которой при установке постоянно требуется перезагрузка. Добавляем `nouveau` в черный список:

`sudo nano /etc/modprobe.d/blacklist-nouveau.conf`

и записываем в этот файл следующие строки:

```
blacklist nouveau
blacklist lbm-nouveau
options nouveau modeset=0
alias nouveau off
alias lbm-nouveau off
```

Отключаем `nouveau`:

`echo options nouveau modeset=0 | sudo tee -a /etc/modprobe.d/nouveau-kms.conf`

`sudo update-initramfs -u`

## Установка

Перезагружаем компьютер и на экране приветствия нажимаем `CTRL + ALT + F1` (для возвращения в обычный режим `CTRL + ALT + F7`). Вводим свой логин и пароль.

Переходим в папку с скаченным пакетом, допустим его имя `nvidia-linux.run`, и добавляем права запуска:

`chmod +x nvidia-linux.run`

Отключаем X-сервер:

`sudo /etc/init.d/lightdm stop`

Запускаем установку и следуем её инструкциям:

`sudo ./nvidia-linux.run`

После установки перезагружаем компьютер:

`reboot`

Если выбирается другая видеокарта пишем:

`sudo nvidia-xconfig`

и перезагружаемся снова.

## Использование CUDA

Для использования CUDA нужно прописать новые пути в переменные окружения, например следующими командами (если вы использовали директории, отличающиеся от стандартных, используйте их):

`export PATH=/usr/local/cuda/bin:$PATH`

`export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH`

## Настройка Theano

Настраиваем Theano использовать gpu по умолчанию. Создаем `.theanorc` в домашней директории и прописываем в нем:

```
[global]
floatX = float32
device = gpu
```
