# Deep Q-Learning, Theano

## О проекте

[GitHub](https://github.com/spragunr/deep_q_rl)

Lasagne/Theano-based реализация алгоритма описанного в:

[Playing Atari with Deep Reinforcement Learning](http://arxiv.org/abs/1312.5602)
Volodymyr Mnih, Koray Kavukcuoglu, David Silver, Alex Graves, Ioannis
Antonoglou, Daan Wierstra, Martin Riedmiller

а также:

Mnih, Volodymyr, et al. "Human-level control through deep reinforcement learning." Nature 518.7540 (2015): 529-533.

## Установка

### Зависимости

* NVIDIA GPU, CUDA v3.0 и выше
* OpenCV 
* [Theano](http://deeplearning.net/software/theano/) ([https://github.com/Theano/Theano](https://github.com/Theano/Theano))
* [Lasagne](http://lasagne.readthedocs.org/en/latest/) ([https://github.com/Lasagne/Lasagne](https://github.com/Lasagne/Lasagne))
* [Pylearn2](http://deeplearning.net/software/pylearn2/) ([https://github.com/lisa-lab/pylearn2](https://github.com/lisa-lab/pylearn2))
* [Arcade Learning Environment](http://www.arcadelearningenvironment.org/) ([https://github.com/mgbellemare/Arcade-Learning-Environment](https://github.com/mgbellemare/Arcade-Learning-Environment))

Скрипт `dep_script.sh` устанавливает все зависимости для Ubuntu, кроме NVIDIA CUDA.


## Запуск

### Обучение

Используя скрипты `run_nips.py` или `run_nature.py` можно запустить обучение сети:

`$ ./run_nips.py --rom breakout`

`$ ./run_nature.py --rom breakout`

`run_nips.py` скрипт использует параметры, описанные в
NIPS workshop статье.  Обучение займет от 2 до 4 дней.

`run_nature.py` скрипт использует параметры, описанные в
статье из Nature.  С этими параметрами сеть будет обучена лучше, но процесс займет от 6 до
10 дней.

Скрипты записывают результаты обучения в папку с именем, начинающимся с имени ROM файла игры.  Также сохраняются результаты после каждого epoch.

### Результаты
Файл `results.csv` содержит результаты тестирования сети.  Также можно построить график, используя `plot_results.py`:

`$ python plot_results.py breakout_05-28-17-09_0p00025_0p99/results.csv`

Когда обучение завершится, можно посмотреть процесс игры, используя
`ale_run_watch.py` скрипт:

`$ python ale_run_watch.py breakout_05-28-17-09_0p00025_0p99/network_file_99.pkl`

