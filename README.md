<!-- ![vue-ctk-date-time-picker](./assets/logo_sticky.png) -->

# VueCtkDateTimePicker

> Компонент vue для выбора дат (доступен режим диапазона) и времени

[![Build Status](https://circleci.com/gh/chronotruck/vue-ctk-date-time-picker/tree/master.svg?style=shield)](https://circleci.com/gh/chronotruck/vue-ctk-date-time-picker/tree/master)

Эта документация предназначена для v2.\*. Найти документацию по версии 1 [здесь](./assets/doc-v1.md)

![vue-ctk-date-time-picker](./assets/illu-animated.gif)

## Тёмный режим

![vue-ctk-date-time-picker](./assets/illu-animated-dark.gif)

# Demo

[Enjoy](https://chronotruck.github.io/vue-ctk-date-time-picker/)

# Установка

Yarn

```bash
yarn add vue-ctk-date-time-picker
```

NPM

```bash
npm i --save vue-ctk-date-time-picker
```

# Применение

## ES6 Modules / CommonJS

```js
import VueCtkDateTimePicker from 'vue-ctk-date-time-picker';
import 'vue-ctk-date-time-picker/dist/vue-ctk-date-time-picker.css';

Vue.component('VueCtkDateTimePicker', VueCtkDateTimePicker);
```

```html
<VueCtkDateTimePicker v-model="yourValue" />
```

## UMD

```html
<link
  rel="stylesheet"
  type="text/css"
  href="${YOUR_PATH}/vue-ctk-date-time-picker.css"
/>

<div id="app">
  <VueCtkDateTimePicker v-model="yourValue"></VueCtkDateTimePicker>
</div>

<script src="https://unpkg.com/vue" charset="utf-8"></script>
<script
  src="${YOUR_PATH}/vue-ctk-date-time-picker.umd.min.js"
  charset="utf-8"
></script>

<script type="text/javascript">
  Vue.component('vue-ctk-date-time-picker', window['vue-ctk-date-time-picker']);
  new Vue({
    el: '#app',
    data() {
      return {
        yourValue: null
      };
    }
  });
</script>
```

Вот пример [реализации UMD](https://codepen.io/louismazel/pen/jQWNzQ).

## Использовать настраиваемый элемент для запуска компонента

```html
<VueCtkDateTimePicker :no-value-to-custom-elem="(true|false)" />
  ...
  <input type="text" />
  ... or
  <button type="button">Метка</button>
  ...
</VueCtkDateTimePicker>
```

# Реквизит API

| Props                       | Type              | Required | Default                     |
| --------------------------- | ----------------- | -------- | --------------------------- |
| v-model                     | String            | yes      | -                           |
| format                      | String            | no       | 'YYYY-MM-DD hh:mm a'        |
| formatted                   | String            | no       | 'llll' (momentjs format)    |
| label                       | String            | no       | Select date & time          |
| hint (1)                    | String            | no       | -                           |
| error (2)                   | Boolean           | no       | false                       |
| color (3)                   | String (hex)      | no       | dodgerblue                  |
| button-color (4)            | String (hex)      | no       | #00C853                     |
| position                    | String            | no       | null                        |
| locale (5)                  | String            | no       | Browser Locale              |
| persistent                  | Boolean           | no       | false                       |
| minute-interval             | Integer           | no       | 1                           |
| output-format               | String            | no       | null                        |
| only-time                   | Boolean           | no       | false                       |
| only-date                   | Boolean           | no       | false                       |
| no-label                    | Boolean           | no       | false                       |
| no-header                   | Boolean           | no       | false                       |
| no-value-to-custom-elem (6) | Boolean           | no       | false                       |
| min-date (7)                | String            | no       | -                           |
| max-date (7)                | String            | no       | -                           |
| no-weekends-days            | Boolean           | no       | false                       |
| auto-close                  | Boolean           | no       | false                       |
| inline                      | Boolean           | no       | false                       |
| overlay                     | Boolean           | no       | false                       |
| range                       | Boolean           | no       | false                       |
| dark                        | Boolean           | no       | false                       |
| no-shortcuts                | Boolean           | no       | false                       |
| no-button                   | Boolean           | no       | false                       |
| input-size                  | String (sm or lg) | no       | null                        |
| button-now-translation      | String            | no       | 'Now'                       |
| no-button-now               | Boolean           | no       | false                       |
| first-day-of-week           | Int (0 to 7)      | no       | -                           |
| disabled-dates (8)          | Array`<string>`   | no       | []                          |
| disabled-hours (9)          | Array`<string>`   | no       | -                           |
| shortcut                    | String            | no       | -                           |
| custom-shortcuts (10)       | Array`<object>`   | no       | -                           |
| disabled-weekly (11)        | Array`<integer>`  | no       | []                          |
| no-keyboard (12)            | Boolean           | no       | false                       |
| right (13)                  | Boolean           | no       | false                       |
| noClearButton               | Boolean           | no       | false                       |
| behaviour                   | Object            | no       | [See behaviour](#Behaviour) |
| id (14)                     | String            | no       | undefined                   |

(1) hint : Текст, заменяющий метку/заполнитель (Пример: обозначение ошибки)

(2) error : Когда `true` --> Входная граница и метка красные

(3) color: Заменить цвет подсказки, границ и цвета средства выбора

(4) button-color: Заменить цвет кнопок внизу (проверка и 'now')

(5) locale : Значение по умолчанию - это локаль браузера - Пример: Установите `locale="fr"` для принудительного использования французского языка.

(6) no-value-to-custom-elem : Для вашего элемента не будет установлено никакого значения (вы можете получить отформатированное значение с помощью события @formatted-value)

(7) min-date && max-date должна быть в том же формате, что и указанный формат свойства. Если формат не задан - по умолчанию установлено значение 'YYYY-MM-DD hh:mm a'.

(8) Disabled-Dates - это массив дат в формате 'YYYY-MM-DD' (пример: `['2018-04-03', '2018-04-07', '2018-04-09']`)

(9) disabled-hours : Должен быть массивом часов в 24-часовом формате. ('00' to '23') : `['00','01','02','03','04','05','06','07','19','20','21','22','23']`

(10) custom-shortcuts - Это массив объектов. Каждый объект представляет собой один ярлык.

```js
[
  { key: 'thisWeek', label: 'На этой неделе', value: 'isoWeek' },
  { key: 'lastWeek', label: 'Прошлая неделя', value: '-isoWeek' },
  { key: 'last7Days', label: 'Последние 7 дней', value: 7 },
  { key: 'last30Days', label: 'Последние 30 дней', value: 30 },
  { key: 'thisMonth', label: 'Этот месяц', value: 'month' },
  { key: 'lastMonth', label: 'Прошлый месяц', value: '-month' },
  { key: 'thisYear', label: 'В этом году', value: 'year' },
  { key: 'lastYear', label: 'Прошлый год', value: '-year' }
];
```

Shortcut types allowed are : `['day', '-day', 'isoWeek', '-isoWeek', 'quarter', 'month', '-month', 'year', '-year', 'week', '-week']`
For each shortcut, a `key`, `label` and `value` must be specified. The `key` is a unique key for that specific shortcut.
Additional values can be passed as a `callback` function that will be called whenever the user clicks on the shortcut. The callback receives an object as first argument with the `start` and `end` values, with the `shortcut` object itself.
You can use this feature for translate existings shortcuts.
If the **value of shortcut is a number** (Integer), this number correspond to number of day (for 5 --> Last 5 days).

If the **value of shortcut is a function**, we'll use it to generate the `start` and `end` values. This function should return an object with the start & end values. Both values **must be a moment object**. The function is called when the user clicks on the shortcut button.

```js
[
  {
    key: 'customValue',
    label: 'My custom thing',
    value: () => {
      return {
        start: moment(),
        end: moment().add(2, 'days')
      }
    },
    callback: ({ start, end }) => {
      console.log('На моем ярлыке щёлкнули значения: ', start, end)
    }
  },
];
```

С помощью свойства `shortcut` вы можете указать ярлык, который выбирается по умолчанию, передав его значение `key`.

```js
  :shortcut="'thisMonth'"
```

(11) disabled-weekly : Дни недели, которые отключаются каждую неделю, в формате массива с индексом дня, воскресенье - 0, суббота - 6: `[0,4,6]`

(12) no-keyboard : Отключить доступность клавиатуры и навигацию

(13) right : добавьте этот атрибут, чтобы выровнять средство выбора справа

(14) id : назначает идентификатор, такой как 'passedstring-input', чтобы справка по вводу различалась между двумя средствами выбора даты и времени в одном компоненте.

> Любой дополнительный атрибут, переданный компоненту, будет автоматически привязан к компоненту ввода. (например. если вы передаете атрибут type, `<input>` получит его).

## Поведение

Чтобы избежать слишком большого количества свойств в компоненте, мы добавляем свойство «behavior», которое является объектом, включающим некоторые значения поведения приложения.

Значение по умолчанию для этого объекта:

```js
{
  time: {
    nearestIfDisabled: true;
  }
}
```

Чтобы переопределить эти значения, передайте новый объект со значениями, которые вы хотите переопределить:

```html
<ctk-date-time-picker
  :behaviour="{
    time: {
      nearestIfDisabled: false
    }
  }"
/>
```

| Поведение              | Описание                                                                                                                                                                                                                                                                                                                                                                       | Type    | Default |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- | ------- |
| time.nearestIfDisabled | Если `true`, он выберет ближайший доступный час в таймпикере, если текущий выбранный час отключен. Например, если час равен 12, но все часы были отключены до 14, то 14 будет выбрано по умолчанию. Установите `false`, чтобы отключить это поведение; текущий час останется выбранным, даже если он был отключен. Пользователь не может повторно выбрать его. | Boolean | true    |

# API событий

| Событие           | Возврат                                                           |
| --------------- | -------------------------------------------------                   |
| input           | значение (отформатировано с помощью реквизита 'format')             |
| formatted-value | значение (отформатировано с помощью 'отформатированных' реквизитов) |
| is-shown        | Компонент показан                                                   |
| is-hidden       | Component is hidden                               |
| validate        | Click on validate button (so component is closed) |
| destroy         | Component is destroy                              |

# Доступ с клавиатуры

| Ключ              | Действие                           |
| --------------    | --------------------------         |
| Стрелка вправо    | Следующий день                     |
| Стрелка влево     | Прошлый день                       |
| Стрелка вниз      | В тот же день на следующей неделе  |
| Стрелка вверх     | В тот же день на предыдущей неделе |
| Page Down         | В тот же день предыдущего месяца   |
| Page Up           | В тот же день следующего месяца    |
| Enter или пробел  | Выберите день                      |
| Escape            | Закрыть компонент                  |

# Предстоящие функции (Todo)

- Двойной календарь на RangeDatePicker (issue : #33)
- Ввод текста для выбора значений (issue #30)
- Поддержка секунд TimePicker (issue : #79)

# Делать вклад

## Настройка сервера разработки

### Без докера

Убедитесь, что на вашем компьютере есть Node и npm. Минимальная конфигурация:

- node >= 6.0
- npm >= 3.0

> Этот проект построен с `node@10.x`.

Установите зависимости разработки, запустив:

```bash
npm install
```

или

```bash
npm ci # Recommanded if you have node > 10.x
```

После установки ваших зависимостей запустите сервер разработки с помощью:

```bash
npm run serve
```

Это запустит сервер разработки, доступный по адресу `http://localhost:8080`.

### Docker

Чтобы легко настроить среду разработки, вы можете развернуть контейнер, содержащий приложение для разработки.
Для этого вам понадобится Docker с docker-compose на вашем компьютере.

Когда все будет запущено, вы можете просто запустить следующую команду, чтобы запустить сервер разработки:

```bash
docker-compose up -d
```

Это запустит сервер разработки внутри контейнера и будет доступен через `http://localhost:8080`.

## Компилирует и выполняет горячую перезагрузку для разработки

```bash
npm run serve
```

## Линтер

```bash
npm run lint
```

## Тесты

Работа в процессе

# Лицензия

Этот проект лицензирован в соответствии с [MIT License](http://en.wikipedia.org/wiki/MIT_License)

# Кредит

Время с открытым исходным кодом с гордостью спонсируется [Chronotruck](https://www.chronotruck.com)
