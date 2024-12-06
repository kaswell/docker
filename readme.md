Все команды прописаны в ./core

В файл ~/.bashrc добавить следующий код:

`
function core {
    export HOST_UID=$(id -u)
    cd ~/apps/core && bash core $*
}
`