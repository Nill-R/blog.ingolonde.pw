+++
author = "Nill Ringil"
categories = ["FB October 2021 Outage tribute Google May 2005 Outage", "IT"]
date = 2021-10-05T15:55:13Z
description = ""
draft = false
slug = "bgp-i-pizdietsy"
tags = ["FB October 2021 Outage tribute Google May 2005 Outage", "IT"]
title = "BGP и пиздецы"

+++


Начал искать в новостях про аварию похожую на FBшную которую помню у Яндекса. Точно помнил, что она была недавно, я уже тут жил…

Нашел про то, как в 2011 году они маршруты из BGP фиганули во внутренний OSPF и прилегли на несколько часов

Ну не может же моя память ТАК сбоить, что я считал недавней аварию случившуюся 19 августа 2011 года

Еще нашел(и вспомнил ее), как Пакистан(в 2008 году) пытался заблочить у себя YouTube и вместо того что бы внутри страны послать анонсы подсетей YouTube в задницу случайно разослали их во внешний мир, от чего у всего мира пути к YouTube оказались через задницу. Проблему быстро устранили заткнув фонтан, весь кавардак продолжался больше двух часов суммарно(там вообще все было хитро, Пакистан что бы убить у себя YouTube анонсировал /24, это пролезло наружу и получило приоритет над YouTubeвским анонсом /22, когда YouTube это заметил он сначала начал анонсировать тоже /24, что бы перебить, потом перешел на /25, но многие провайдеры считают /25 слишком мелкой нарезкой и игнорировали, но все это уже подробности которые у меня тут мало кому интересны)

Google’s May 2005 Outage я пропустил, как ни странно. Тоже хуйня с BGP, но на этот раз у Гугла. Тоже бодро и весело, судя по описанию было, даже жаль, что я был занят другими вещами.

Бразильскую аварию в 2008 тоже вспомнил начав читать о ней.Ну, то есть по этому краткому обзору вы можете видеть, что оно случается периодически, просто обычно реагирование идет быстрей или масштабы бедствия не такие.

И не смотря на все эти пиздецы ФБ умудрился себе сам организовать такой же, видать, что бы походить на Гугл


