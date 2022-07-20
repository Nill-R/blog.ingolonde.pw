+++
author = "Nill Ringil"
categories = ["IT"]
date = 2020-02-03T16:04:59Z
description = ""
draft = false
slug = "wireguard-priekrasien-v-kachiestvie-vpn"
tags = ["IT"]
title = "WireGuard прекрасен в качестве VPN"

+++


WireGuard прекрасен не только тем, что на нем нет таких просадок по скорости, как бывают у OpenVPN, а прежде всего простотой настройки сервера и предельной простотой настройки для клиентов. Если у OpenVPN и прочих нужно что-то объяснять человеку куда что вводить, какой файл скормить программе и так далее, то у клиентов WireGuard для мобильных ОС есть прекрасная функция считывания конфига из QR. Человеку достаточно поставить из [Play Market](https://play.google.com/store/apps/details?id=com.wireguard.android) или [AppStore](https://apps.apple.com/us/app/wireguard/id1441195209?ls=1) официальный клиент и навести камеру смартфона на QR присланный тем кто ему VPN сделал(ну или на QR-код который он сам увидел перед собой, если он решил сам все настроить) и нажать пимпочку активировать данный конфиг в VPN-клиенте.

Написал два скрипта один из которых ставит WireGuard на сервер и делает ему необходимый конфиг, а второй добавляет пользователей когда это тебе нужно, показывать тебе в терминале QR и шлет QR, а так же файл конфига для только что добавленного клиента тебе в телеграм. Вот какой я молодец.

Если кому интересно, то скрипты [тут](https://github.com/Nill-R/wg_install_and_user_create). Скрипты рассчитаны на Ubuntu, для остальных дистрибутивов скрипт ставящий WireGuard надо слегка допилить. В принципе, если мне будет не лень, то может допилю его еще до того, что бы проверял на каком дистрибутиве запущен и в зависимости от этого запускал команды установки WireGuard.

А если кому лень самому настраивать, то он может обратиться ко мне и получить VPN с трафиком ограниченным принципом Fair Use(ну то есть не нужно качать каждый день инсталяхи игр по 50 гигов) за умеренную плату.
