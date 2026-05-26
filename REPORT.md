# Лабораторная работа 11

Студент: Rzaev Emil
Группа: ИУ8-24
Дата: 20.05.2026

## Tutorial

```shell
$ cd ~
$ mkdir install
$ mkdir tmp
$ export HOME_PREFIX=`pwd`/install
$ echo $HOME_PREFIX
/home/emilrzaev28/install
$ export USERNAME=`whoami`
$ echo $USERNAME
emilrzaev28
```

```shell
$ cd tmp
```

```shell
$ wget https://github.com/libevent/libevent/releases/download/release-2.1.8-stable/libevent-2.1.8-stable.tar.gz
$ tar -xvzf libevent-2.1.8-stable.tar.gz
$ cd libevent-2.1.8-stable
$ ./configure --prefix=${HOME_PREFIX}
$ make && make install
$ cd ..
```

```shell
$ wget http://invisible-island.net/datafiles/release/ncurses.tar.gz
$ tar -xvzf ncurses.tar.gz
$ cd ncurses-5.9
$ ./configure --prefix=${HOME_PREFIX}
$ make && make install
$ cd ..
```

```shell
$ wget https://github.com/tmux/tmux/releases/download/2.5/tmux-2.5.tar.gz
$ tar -xvzf tmux-2.5.tar.gz
$ cd tmux-2.5
$ ./configure --prefix=${HOME_PREFIX} CFLAGS="-I${HOME_PREFIX}/include -I${HOME_PREFIX}/include/ncurses" LDFLAGS="-L${HOME_PREFIX}/lib"
$ make && make install
$ cd ..
```

```shell
$ wget https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-linux-amd64.zip
$ unzip ngrok-stable-linux-amd64.zip
$ mv ngrok ${HOME_PREFIX}/bin
```

```shell
$ export LD_LIBRARY_PATH=${HOME_PREFIX}/lib
$ export PATH="${HOME_PREFIX}/bin:${PATH}"
$ tmux -V
tmux 3.4
$ ngrok version
ngrok version 3.39.2
```

```shell
$ tmux new -d -s session_with_group
$ tmux ls
session_with_group: 1 windows (created Wed May 20 11:47:30 2026)
```

```shell
# Alisa:
$ open https://ngrok.com/signup
$ export NGROK_TOKEN=<токен>
$ ngrok config add-authtoken ${NGROK_TOKEN}
Authtoken saved to configuration file: /home/emilrzaev28/.config/ngrok/ngrok.yml
$ ngrok tcp 22
ngrok                                                          (Ctrl+C to quit)

Session Status                online
Account                       Emil2007emka (Plan: Free)
Version                       3.39.2
Region                        Europe (eu)
Latency                       75ms
Web Interface                 http://127.0.0.1:4040
Forwarding                    tcp://0.tcp.eu.ngrok.io:XXXXX -> localhost:22

Connections                   ttl     opn     rt1     rt5     p50     p90
                              0       0       0.00    0.00    0.00    0.00
```

```shell
# Bob:
$ ssh ${USERNAME}@0.tcp.eu.ngrok.io -p<порт_ngrok_сервера>
<пароль_от_учетной_записи>
$ tmux a -t session_with_group
$ <C-B>"
```

```shell
$ tmux kill-session -t session_with_group
$ tmux ls
no server running on /tmp/tmux-1000/default
```

```shell
$ cd ~
$ rm -rf tmp install
```

## Report

```shell
$ cd ~/workspace/
$ export LAB_NUMBER=11
$ git clone https://github.com/tp-labs/lab${LAB_NUMBER}.git tasks/lab${LAB_NUMBER}
$ mkdir reports/lab${LAB_NUMBER}
$ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md
$ cd reports/lab${LAB_NUMBER}
$ edit REPORT.md
$ gist REPORT.md
```
