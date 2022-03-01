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
![image](https://user-images.githubusercontent.com/48065080/155874875-0d28365d-f7ad-4dc7-a25b-3a63ec29ff15.png)
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
![image](https://user-images.githubusercontent.com/48065080/156154018-61250be9-2aa4-45cc-b458-9e2c3828b54b.png)

Система умного дома разделена на управляющие подсистемы, выделенные красным, обрабатывающие всю информацию, поступающую с систем переферии или программных компонентов, выделенных зелёным, а девайс - логический элемент, служащий связующим звеном. Системы переферии имеют строго определеные способы получения и передачи параметров, изменяет только режим работы, выполняющий обработку. Девайс реализует способ передачи данных, настройки физического или программного компонента со стороны, не зависимо от его физической реализации, патформы.

Программную часть, даже фактически находящуюся на сервере, очень удобно рассматривать подобным образом, потому что часть программных модулей не способно выполняться на физических устройствах из-за ограничений производительностии и они могут предустанавливаться на сервер - примером могут послужить алгоритмы распознавания лиц.

Для разнородных физических устройств необходимо лишь реализовать этот уровень, а дальше общаться с сервером как обычно. Если планируется поддержка различных способов связи между устройствами, то изменив реализацию функции получения и отправки команд на сервере, можно будет добавить необходимые стандарты.

Модульное решение обусловлено невозможностью жестко определить образ системы умного дома, из-за постоянно изменяющихся потребностей пользователя, а также в связи с разнообразием и постоянным изменением физических устройств. К тому же, это решение позволит создать гибкую архитектуру, снижающую связанность кода и служащую стандартом для всех программистов.
