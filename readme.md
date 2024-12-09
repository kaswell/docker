# Локальная среда разработки 
[NONIUM GEEKAREA](https://www.nonium.by)


## Nginx MySQL Redis PHP Laravel
> *** Мы не претендуем на то, что это лучшая базовая сборка. Но для ускорения
начала проекта этого вполне должно хватить. :blush: ***


### Минимальные требования к стенду
* Linux (корректно поднимается на этих системах, остальные в разработке)
* Docker, Docker Compose
* CPU: 4core+, 2GHz+
* Memory: 8GB+
* Disk space: 30GB+

---

## Подготовка
1. Клонируем репозитории в домашнюю директорию в `~/apps/core`
```
    cd ~/apps
    git clone git@github.com:kaswell/docker.git core
```

2. Дополняем файл `.bashrc`

```
    nano ~/.bashrc
```

в конец файла вставляем следующий код и сохраняем. После необходимо консоль перезапустить.

```
function core {
    export HOST_UID=$(id -u)
    cd ~/apps/core && bash core $*
}
```
В дальнейшем позволит легче использовать команды

3. Перейдите в директорию проекта и инициализируйте его

```
    cd ~/apps/core && core env && core init
```

Данная команда создаст файл настроек окружения, создаст необходимые контейнеры 
и развернет базовый фреймворк Laravel (на данный момент не разворачивает). Скорее
всего сделаем выбор между классическим Laravel и Apiato

4. Дополните файл `/etc/hosts`:

```
    127.0.0.1 core.local
    127.0.0.1 api.core.local
```

---

## Список команд

```
Usage:
    core <command> [options] [arguments]

Available commands:
    artisan ................................... Run an Artisan command
    composer .................................. Run a Composer command
    destroy ................................... Remove the entire Docker environment
    init ...................................... Initialise the Docker environment and the application
    logs [container] .......................... Display and tail the logs of all containers or the specified one's
    restart ................................... Restart the containers
    start ..................................... Start the containers
    stop [-v] ................................. Stop and destroy all containers
                                                Options:
                                                    -v .................... Destroy the volumes as well
    update .................................... Update the Docker environment
    node ...................................... Run a Node Install and build front
    cert ...................................... Generate or Install ssl certificate


Usage:
    core cert <command>

Available commands:
    generate .................................. Generate a new certificate
    install ................................... Install the certificate
```