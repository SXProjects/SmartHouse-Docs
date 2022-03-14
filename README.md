# Не сильно умный дом

## Содержание
- Сеть вещей
  - [Описание](Сеть%20вещей/Описание)
  - [Интерфейсы](Сеть%20вещей/Интерфейсы)
  - [Требования](Сеть%20вещей/Требования)
  - [Функциональный анализ](Сеть%20вещей/Функциональный%20анализ)
  - [Анализ применения](Сеть%20вещей/Анализ%20применения)
- CV
  - [Описание](CV/Описание)
- Сервер
  - [Описание](Сервер/Описание)

## О отделе
![image](https://user-images.githubusercontent.com/36124495/156545800-7dca4fd9-09e1-4aeb-8b5e-0071efb4692c.png)
Проект отдела IT разделён на 6 обязательных систем. Задачи сверху таблицы считаются наиболее важными, потому что без их реализации затруднено дальнейшее продвижение проекта. Поддержку пользователя реализовать будет возможно только в конце проекта, когда точно будет определена реализация.

![image](https://user-images.githubusercontent.com/48065080/155875155-f5a687af-1038-43b4-aff4-ab0b0ccffc91.png)
Таймлайны в диаграмме Ганта определены оценочно и участники отдела жестко не привязаны к системам. После выполнения задачи, необходимо переключиться на помощь сокомандникам, потому что объём работы в задачах не равный.

## Интересы целевой аудитории

Поддержка и просмотр комфортных параметров среды в доме.
- Температура.
- Влажность.
- Освещение.
- Вентиляция.

Упрощение или автоматизация рутинных бытовых задач.
- О которых легко забыть.
  - Управление закрытием дверей и окон.
  - Управление отключением воды.
  - Управление выключение/включением света.
  - Управление умной фермой.
- Обязательные, но занимающие много времени без пользы.
  - Управление домом, не отрывая от дела голосом
- Опциональные, но на которые не хватает времени.
  - Посмотреть новости, прогноз погоды и т.д.
- Дополнительные приятные мелочи, quality of life features.
  - Мультимедиа + Дискотека
  - Голосовой помощник

Safety.
- Уведомление и реагирование на неисправности оборудования.
  - Оповещение о неполадках или поломках датчиков или управляющих устройств
- Оповещения о бытовых происшествиях в доме.
  - Оповещение о месте утечки воды
  - Оповещение о месте возгорания
- Защита от возможных бактерий и вирусов. Особенно актуальна дезинфекция пола.

Security.
- Уведомления о проникновении.
- Запуск в дом по опознаванию человека по камере
- Защищенность личных данных и систем в доме.

Модификация.
- Самостоятельное добавление и замены оборудования в доме. Свобода от ограничений производителя позволит выбирать и добавлять лучшее оборудование на рынке для конкретной ситуации.
  - Умные шторы
  - Умная светодиодная лента
  - Замена ламп в доме
- Самостоятельная настройка сценариев поведения систем в умном доме. Кастомизация систем под нужды пользователя в зависимости от его пожеланий. Например,
  - Адекватные идеи
     - Уличные свет включается/выключается в зависимости от времени или уровня освещения.
     - Система вентиляции переключается между обычным или интенсивным проветриванием.
     - Систему отопления, если все уедут из дома, можно перевести в режим экономии энергии.
  - Больные идеи
    - Плавно разбудить с помощью музыки и света и послушать умную колонку, включение чайника
    - Выключать/включать освещение при заданном уровне освещения. Уличное ночью, обычное днём.
    - Режим дискотеки/чилла - гаснет свет, задвигаются шторы, запускается аудиосистема
    - Режим готовки - включается музыка, вытяжка
    - Сценарий Зайцева с холодильником и весами

Удалённый мониторинг и управление дома
- Подключение с мобильного устройства для управления
  - Из дома - Не вставая с дивана
  - Вне дома - Находясь на работе или еще где-то

Демонстрация работоспособности и крутости дома
- Просмотр динамики изменений температуры, влажности
- Хаб

## Общая функциональная диаграмма
![image](https://user-images.githubusercontent.com/48065080/156381076-5321bcb4-0a66-4bca-88fc-956d4da8817f.png)

Система умного дома разделена на управляющие подсистемы, выделенные красным, обрабатывающие всю информацию, поступающую с систем переферии или программных компонентов, выделенных зелёным, а девайс - логический элемент, служащий связующим звеном. Системы переферии имеют строго определеные способы получения и передачи параметров, изменяет только режим работы, выполняющий обработку. Девайс реализует способ передачи данных, настройки физического или программного компонента со стороны, не зависимо от его физической реализации, патформы.

Программную часть, даже фактически находящуюся на сервере, очень удобно рассматривать подобным образом, потому что часть программных модулей не способно выполняться на физических устройствах из-за ограничений производительностии и они могут предустанавливаться на сервер - примером могут послужить алгоритмы распознавания лиц.

Для разнородных физических устройств необходимо лишь реализовать этот уровень, а дальше общаться с сервером как обычно. Если планируется поддержка различных способов связи между устройствами, то изменив реализацию функции получения и отправки команд на сервере, можно будет добавить необходимые стандарты.

Модульное решение обусловлено невозможностью жестко определить образ системы умного дома, из-за постоянно изменяющихся потребностей пользователя, а также в связи с разнообразием и постоянным изменением физических устройств. К тому же, это решение позволит создать гибкую архитектуру, снижающую связанность кода и служащую стандартом для всех программистов.

## Сервер & Сеть вещей & Устройства

### Запуск сети вещей
Можно запустить в режиме сервера или в режиме клиента.
Можно указать либо поле server, либо пол client, но не два сразу.

```json
{
  "server": 9002,
  "client": "ws://127.0.0.1:9002"
}
```

### JSON для передачи данных с датчика на сеть вещей. (Перед тем как попасть в сеть вещей, JSON попадает на сервер.)
```json
  {
    "device_id": 0,
    "command_name": "transmit_data",
    "time": "2022-03-09T13:54:02",
    "data": [
      {
        "name": "temperature",
        "value": 24.5
      }
    ],
    "error": "Тут напишу возможные сообщения о ошибках"
  }
```

Ответ точно такого формата, но с указанием параметров других устройств, а не только индикаторов

### JSON для получение истории показаний (для ГУИ по большей части.)
```json
{
    "device_id": 1312413123123123123123,
    "command_name": "history",
    "start_date": "date",
    "end_date": "date",
    "interval": "hours/days/minutes",
    "approx": "min/max/first/last/avg",
    "parameter": ["temperature"]
}
```

Ответ, который, в лучшем случае, получает устройство.
```json
{
    "device_id": 42,
    "command_name": "history",
    "data": [
        {
            "time": "stroka vremeni",
            "temprature": 24
        },
        {
            "time": "stroka vremeni",
            "temprature": 24
        }

    ],
    "error": "Тут напишу возможные сообщения о ошибках"
}
```

### Добавить новый тип устсройства в сеть вещей
```json
{
    "command_name": "add_device_type",
    "name": "thermometer"
    "work_modes": [
        {
            "name":"send_on_time",
            "indicators":[{"name":"themperature", "type":"float"}],
            "parameters":[{"name":"send_seconds", "type":"int"}]
        },
        {
            "name":"send_on_command",
            "indicators":[{"name":"themperature", "type":"float"}],
            "parameters":[{"name":"send", "type":"bool"}],
        }
    ]
}
```
Ответ
```json
{
    "command_name": "add_device_type",
    "error": "Тут напишу возможные сообщения о ошибках"
}
```

### Удалить тип устройства
Тип удлится только если в системе нет устройств с этим типом
```json
{
    "command_name": "remove_device_type",
    "device_type": "thermometer",
}
```
Ответ
```json
{
    "command_name": "remove_device_type",
    "error": "invalid device type/device type is used by thermometer"
}
```

### Запросить информацию о типах устройства
```json
{
    "command_name": "device_type_info",
}
```

Ответ
```json
{
    "command_name": "device_type_info",
    "device_types": [
        {
            "name": "thermometer",
            "work_modes": [
                {
                    "name":"send_on_time",
                    "indicators":[{"name":"themperature", "type":"float"}],
                    "parameters":[{"name":"send_seconds", "type":"int"}]
                },
                {
                    "name":"send_on_command",
                    "indicators":[{"name":"themperature", "type":"float"}],
                    "parameters":[{"name":"send", "type":"bool"}],
                }
            ]
        }
    ],
    "error": "Тут напишу возможные сообщения о ошибках"
}
```

### Добавить устройство
```json
{
    "command_name": "add_device",
    "location": "home/kitchen/thermometer1",
    "device_type": "thermometer",
    "work_mode": "send_on_time"
}
```
Ответ
```json
{
    "command_name": "add_device",
    "device_id": 42,
    "error": "Тут напишу возможные сообщения о ошибках"
}
```

### Запросить информцию о устройствах
```json
{
    "command_name": "device_info",
}
```
Ответ
```json
{
    "command_name": "device_info",
    "devices": [
        {
            "device_id": 42
            "location": "home/kitchen/thermometer1",
            "device_type": "thermometer",
            "work_mode": "send_on_time",
        }
    ],
    "error": "Тут напишу возможные сообщения о ошибках"
}
```

### Найти устройство
match - true - ищем устройства по точному совпадинию, найдёт при "home/*/thermometer1"
metch - false - ищем по частичному совпадению, найдёт даже при "ome/*/therm"
```json
{
    "command_name": "find_device",
    "match": false,
    "location": "home/*/thermometer"
}
```
Ответ
```json
{
    "command_name": "find_device",
    "device_id": [42, 43],
    "error": "Тут напишу возможные сообщения о ошибках"
}
```

### Удалить устройство
```json
{
    "command_name": "remove_device",
    "device_id": 42
}
```
Ответ
```json
{
    "command_name": "remove_device",
    "error": "Тут напишу возможные сообщения о ошибках"
}
```

### Установить режим работы
```json
{
    "command_name": "set_work_mode",
    "device_id": 42,
    "work_mode": "send_on_time"
}
```
Ответ
```json
{
    "command_name": "set_work_mode",
    "error": "Тут напишу возможные сообщения о ошибках"
}
```

### Установить путь до устройства
```json
{
    "command_name": "set_location",
    "device_id": 42,
    "location": "home/bedroom/lamp"
}
```
Ответ
```json
{
    "command_name": "set_location",
    "error": "Тут напишу возможные сообщения о ошибках"
}
```

### Связть устройства
Отвязть устройства - тоже самое, но unlink вместо link

```json
{
    "command_name": "link",
    "transmitter": 42,
    "indicator": "themperature"
    "receiver": 43,
    "parameter": "max_working_temperature"
}
```
Ответ
```json
{
    "command_name": "link",
    "error": "Тут напишу возможные сообщения о ошибках"
}
```
