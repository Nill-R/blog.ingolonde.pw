+++
author = "Nill Ringil"
categories = ["IT"]
date = 2021-10-12T14:40:18Z
description = ""
draft = false
slug = "timelapse-linux-webcam-motion-and-ffmpeg"
tags = ["IT"]
title = "Timelapse. Linux, webcam, motion and ffmpeg"

+++


Прочитал я на Хабре статью про изготовление timelapse с камеры под линухой и решил, что идея-то интересная, но реализация какая-то странная, ведь есть нормальные инструменты

В примере я использую Raspberry Pi 4B+ 8Gb, служащую мне обычным десктопом и PI camera, но так как использую при этом обращение как к `/dev/video0`, то конфиг универсальный и может использоваться с любой uvc-камерой(что я думаю использовать поставив камеру на подоконник и направив на улицу)

У меня стоит Ubuntu 21.10, но motion есть во всех Debian-based и устанавливается везде одинаково. Что бы не писать везде `sudo` я сделаю в начале `sudo su -` и буду считать, что команды даются из под рута

```
 $ sudo su -

```

```
# apt update
# apt -y install motion

```

Ставим motion из репозитория(или возьмите свежий релиз motion c [гитхаба](https://github.com/Motion-Project/motion/releases) и поставьте при помощи `gdebi`)Создаем директорию в которую motion будет писать наши ежеминутные снапшоты и делаем его владельцем пользователя от которого motion по дефолту работает

У меня в `/data` подмонтирован внешний жесткий диск, потому директорию создаю там

```
 # mkdir /data/motion
 # chown motion:motion /data/motion

```

Открываем конфиг `/etc/motion/` в нашем любимом редакторе и правим некоторые параметры, а отсутствующие прописываем

```
target_dir /data/motion
width 1920
height 1080
framerate 2
minimum_frame_time 60
snapshot_interval  60
snapshot_filename %Y%m%d/%d%m%Y-%H%M%S-snapshot
movie_output off

```

Все параметры можно найти в документации, но последний надо пояснить. Вообще motion должен бы уметь сам собирать видео из того что наснимал, но в моих экспериментах он почему-то делал видео в котором показывался только первый кадрПерезапускаем motion

```
# systemctl restart motion

```

Он начнет раз в минуту делать кадр и складывать в прописанную нами директорию

Теперь нам надо обеспечить изготовление из наших снимков видео в конце каждых суток, нам понадобится ffmpeg и небольшой скрипт

```
 # apt install ffmpeg

```

Создаем файл `/usr/local/bin/motion_snapshots_timelapse.bash` со следующим содержимым

```bash
#!/usr/bin/env bash

DATE=$(date +%Y%m%d)
cd /data/motion/$DATE
cat *.jpg | ffmpeg -f image2pipe -framerate 25 -vcodec mjpeg  -i - -c:v libx264 -r 25 -movflags +faststart $DATE-snapshots.mp4

```

и добавляем его в crontab(командой `crontab -e`) следующей строкой

```
59 23 * * * /usr/local/bin/motion_snapshots_timelapse.bash

```

В последнюю минуту каждых суток скрипт будет запускаться и делать нам в директории с датой в `/data/motion` итоговое видео `$DATE-snapshots.mp4`, где `$DATE` дата прошедшего дня

C framerate можно поиграть по своему вкусу, от этого будет зависеть сколько кадров в секунду будет показано и соответственно какой общей продолжительности будет наш итоговый ролик

