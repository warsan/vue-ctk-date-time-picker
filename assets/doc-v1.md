![vue-ctk-date-time-picker](./logo_sticky.png)

# vue-ctk-date-time-picker

> Documention for v1.*

## Props API

| Props      | Type       | Required | Default    |
|------------|------------|----------|------------|
| v-model    | String/Int | yes     | -          |
| label      | String     | no    | Select date & time |
| hint (1)       | text       | no       | -         |
| error-hint (2) | Boolean    | no      | false     |
| color (3)     | String (hex) | no    | dodgerblue |
| minute-interval | Int | no    | 1    |
| formatted   | string | no    | 'llll' (momentjs format) |
| format   | string | no      | - |
| time-format   | string | no  | 'H:mm a' |
| locale (4)  | string | no     | Browser Locale |
| time-zone (5)  | string | no  | Browser Time Zone |
| disable-time   | Boolean | no     | false |
| disable-date   | Boolean | no  | false |
| without-header   | Boolean | no   | false |
| id  | string | no  | CtkDateTimePicker |
| overlay | Boolean | no | true |
| min-date (6)  | string | no  | - |
| max-date (6)  | string | no  | - |
| no-weekends-days | Boolean | no | false |
| auto-close | Boolean | no | false |
| inline | Boolean | no | false |
| overlay-background | Boolean | no | false |
| disabled-dates (7) | Boolean | no | [] |
| range-mode | Boolean | no | false |
| dark | Boolean | no | false |
| without-range-shortcut | Boolean | no | false |
| shortcuts-translation (8) | Object | no | - |
| disabled-hours (9) | Array (of String) | no | - |

(1) hint : Текст, заменяющий метку/заполнитель

(2) error-hint : Когда `true` --> Входная граница и метка красные

(3) color: Заменить цвет подсказки, границ и времени, выбранных в раскрывающемся списке

(4) locale : Значение по умолчанию - локаль браузера. - Ex : Set `locale="fr"` to force to French language

(5) time-zone : Значение по умолчанию - часовой пояс браузера. - Ex : Set `Europe/Paris` to force to French TZ. Не забывайте использовать такой формат `YYYY-MM-DDTHH:mm:ssZ` чтобы получить TZ
 
(6) min-date & max-date : Must be `'YYYY-MM-DD'` format

(7) Disabled-Dates is an Array of dates in 'YYYY-MM-DD' format (ex: `['2018-04-03', '2018-04-07', '2018-04-09']`)

(8) shortcuts-translation : Должен быть такой объект

```
{
  "this_week": "This week",
  "last_7_days": "Last 7 days",
  "last_30_days": "Last 30 days",
  "this_month": "This month",
  "last_month": "Last month",
  "this_year": "This year",
  "last_year": "Last year"
}
```

(9) disabled-hours : Должен быть массивом часов в 24-часовом формате. ('00' to '23') : `['00','01','02','03','04','05','06','07','19','20','21','22','23']`