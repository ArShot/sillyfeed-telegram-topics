# SillyFeed: замеры русскоязычного Telegram по темам

Агрегаты замеров, которые опубликованы на страницах [SillyFeed](https://sillyfeed.app/?utm_source=github&utm_medium=referral&utm_campaign=dataset) — ленты постов
из Telegram-каналов: сколько каналов пишет про тему, какой длины посты, сколько их выходит в неделю, в какой час
и день недели, сколько реакций собирают, как растёт длинное тире. Каждое число в CSV стоит на странице сайта
и совпадает с ней до знака. Та же выкладка на [Hugging Face](https://huggingface.co/datasets/Pershlab/sillyfeed-telegram-topics) — с просмотром таблиц в браузере.

## Что внутри

| Файл | Что | Строк | Выборка | Размер | Дата замера |
|---|---|---|---|---|---|
| `data/topic_channels_corpus.csv` | Сколько каналов Telegram пишет про тему и доля 18+ | 142 | корпус: собранные публичные каналы с определённой темой, без курации и без вырезания 18+ | 192884 каналов | 2026-10-22 |
| `data/topic_share_panel.csv` | Доля постов темы среди постов года и сдвиг к 2024 | 19 | панель: каналы каталога, публиковавшиеся в январе–августе каждого из 2024, 2025, 2026 | 18312 каналов | 2026-10-22 |
| `data/topic_texts_catalog.csv` | Посты темы в каталоге: сколько, какой длины, с медиа ли | 142 | каталог ленты SillyFeed: опубликованные текстовые посты видимых каналов, без 18+ | 1837893 постов, 79059 каналов | 2026-10-22 |
| `data/topic_tempo_archive.csv` | Сколько постов в неделю выпускает типичный канал темы | 142 | архив каналов каталога: последние ~500 постов канала, окно пересчёта 2026-07-17…2026-10-22 | 65834 каналов | 2026-10-22 |
| `data/topic_reactions_catalog_channels.csv` | Реакций на 1 000 просмотров у типичного канала темы | 142 | каналы каталога, у которых в архиве есть и просмотры, и реакции; медиана реакций канала, делённая на медиану его просмотров, — про каналы, а не про посты | 65864 каналов | 2026-10-22 |
| `data/topic_posting_hour.csv` | Медианный час выхода поста темы, по Москве | 20 | каталог ленты, отдельный прогон под расписание; пояс автора не хранится, все каналы посчитаны как московские | 1837893 постов | 2026-10-22 |
| `data/topic_weekday.csv` | Самый плотный и самый тихий день недели темы | 19 | каталог ленты, отдельный прогон под день недели; время публикации по Москве | 1 163 586 постов из каналов ленты SillyFeed, 19 тем | 2026-09-06 |
| `data/catalog_weekday.csv` | Доля постов каталога по дням недели | 7 | каталог ленты, отдельный прогон под день недели; время публикации по Москве | 1 163 586 постов из каналов ленты SillyFeed, 19 тем | 2026-09-06 |
| `data/catalog_posting_quarters.csv` | Доля постов каталога по четвертям суток, по Москве | 4 | каталог ленты, отдельный прогон под расписание; пояс автора не хранится | 1 163 586 постов из каналов ленты SillyFeed, 19 тем | 2026-09-06 |
| `data/reactions_by_hour.csv` | Реакций на 1 000 просмотров по часу выхода поста (часы, названные в гайде) | 6 | корпус постов авторских каналов, осень и зима; тема — одна главная у канала; время по Москве | более 20 000 000 постов за осень и зиму, 149 700 авторских каналов | 2026-08-27 |
| `data/evening_uplift_by_topic.csv` | Прибавка реакций у постов 21:00–24:00 к постам в середине дня, по теме канала | 18 | корпус постов авторских каналов, осень и зима; тема — одна главная у канала; время по Москве | более 20 000 000 постов за осень и зиму, 149 700 авторских каналов | 2026-08-27 |
| `data/reactions_by_channel_size.csv` | Реакций на 1 000 просмотров по размеру канала | 7 | корпус постов авторских каналов, осень и зима; тема — одна главная у канала; время по Москве | более 20 000 000 постов за осень и зиму, 149 700 авторских каналов | 2026-08-27 |
| `data/dash_by_ai_awareness.csv` | Плотность длинного тире по группам каналов: как часто канал пишет про нейросети | 4 | публичные каналы, разбитые на четыре группы по доле постов с упоминанием нейросетей | 13 701 487 постов, ~47 000 каналов | 2026-09-07 |
| `data/ai_text_markers.csv` | Приметы машинного текста, которые выросли сильнее коридора шума: частота на миллион знаков | 13 | одни и те же каналы в двух окнах: июль–декабрь 2024 и ноябрь 2025 – апрель 2026; в каждом окне не меньше 40 постов от 200 знаков | 7 824 530 постов, 48 242 публичных канала | 2026-10-25 |
| `data/reactions_norm_by_size.csv` | Реакций на 1 000 просмотров по числу подписчиков: четверти каналов | 7 | каналы корпуса от 40 постов за сентябрь 2025 – март 2026 и хотя бы с одной реакцией, без репостов; отклик канала — сумма реакций / сумма просмотров × 1000; подписчики на дату сбора | 239 751 канал, 47 841 670 постов | 2026-10-27 |
| `data/reactions_norm_by_topic.csv` | Реакций на 1 000 просмотров по теме канала: четверти каналов | 19 | каналы каталога SillyFeed с размеченной темой (одна главная у канала); остальное как у reactions_norm_by_size | 28 278 каналов | 2026-10-27 |
| `data/reactions_per_post_by_size.csv` | Обычный пост по числу подписчиков: серединный пост канала, затем серединный канал группы | 7 | каналы корпуса от 40 постов за сентябрь 2025 – март 2026 и хотя бы с одной реакцией, без репостов; отклик канала — сумма реакций / сумма просмотров × 1000; подписчики на дату сбора | 239 751 канал, 47 841 670 постов | 2026-10-27 |

Индекс тех же сведений машинно — `tables.csv`. Кодировка UTF-8, разделитель — запятая, десятичная точка.

## Выборки не смешиваются

- **Корпус** — все собранные публичные каналы с определённой темой, без курации и без вырезания 18+:
  «сколько такого в Telegram».
- **Каталог ленты** — то, что показывает лента SillyFeed, без 18+ и снятых с показа: «что в ленте».
- **Панель** — каналы каталога, публиковавшиеся в январе–августе каждого из трёх лет; только по ней доля темы
  внутри года. Лечит смену состава, не лечит выживаемость.
- **Архив каналов** — последние ~500 постов канала каталога: темп и отклик.
- **Корпус постов гайдов** — отдельные выборки статей, размер и метод названы в статье.

Складывать числа разных выборок нельзя: разные знаменатели и даты.

## Чего здесь нет намеренно

Текстов постов, названий и идентификаторов каналов; дат постов (только час, день недели и доля темы внутри
года — дата в таблицах это дата замера); абсолютного числа постов по годам.

## Поля

`level` — `catalog` / `topic` / `subtopic` (у подтемы `parent`); `slug` — адрес `https://sillyfeed.app/t/<slug>`;
`pct_*` — проценты, `*_pp` — процентные пункты, `*_p50` — медиана; `reactions_per_1k_views*` — реакции на тысячу
просмотров, в таблице тем — про каналы темы, а не про посты. Время московское.

## Где читать разбор

- [Лучшее время для поста: час меняет отклик, а не охват](https://sillyfeed.app/guides/luchshee-vremya-dlya-posta?utm_source=github&utm_medium=referral&utm_campaign=dataset)
- [В какой день недели публикуют в телеграме](https://sillyfeed.app/guides/den-nedeli-dlya-posta?utm_source=github&utm_medium=referral&utm_campaign=dataset)
- [Длинное тире и другие приметы машинного текста](https://sillyfeed.app/guides/dlinnoe-tire-priznak-ii?utm_source=github&utm_medium=referral&utm_campaign=dataset)
- [Как отличить текст нейросети: что выросло в постах телеграма](https://sillyfeed.app/guides/kak-otlichit-tekst-neiroseti?utm_source=github&utm_medium=referral&utm_campaign=dataset)
- [Сколько реакций нормально для телеграм-канала: ориентиры по размеру и теме](https://sillyfeed.app/guides/skolko-reakcii-normalno?utm_source=github&utm_medium=referral&utm_campaign=dataset)
- [Девятнадцать тем Telegram в одной таблице](https://sillyfeed.app/channels?utm_source=github&utm_medium=referral&utm_campaign=dataset)

Страницы тем:

- [Бизнес и финансы](https://sillyfeed.app/t/business_finance?utm_source=github&utm_medium=referral&utm_campaign=dataset)
- [Дом и стиль жизни](https://sillyfeed.app/t/home_lifestyle?utm_source=github&utm_medium=referral&utm_campaign=dataset)
- [Еда и кулинария](https://sillyfeed.app/t/food_cooking?utm_source=github&utm_medium=referral&utm_campaign=dataset)
- [Здоровье и медицина](https://sillyfeed.app/t/health_medicine?utm_source=github&utm_medium=referral&utm_campaign=dataset)
- [Игры](https://sillyfeed.app/t/gaming?utm_source=github&utm_medium=referral&utm_campaign=dataset)
- [Искусство и дизайн](https://sillyfeed.app/t/arts_design?utm_source=github&utm_medium=referral&utm_campaign=dataset)
- [Карьера и маркетинг](https://sillyfeed.app/t/careers_marketing?utm_source=github&utm_medium=referral&utm_campaign=dataset)
- [Кино и ТВ](https://sillyfeed.app/t/cinema_tv?utm_source=github&utm_medium=referral&utm_campaign=dataset)
- [Литература](https://sillyfeed.app/t/literature?utm_source=github&utm_medium=referral&utm_campaign=dataset)
- [Мода и красота](https://sillyfeed.app/t/fashion_beauty?utm_source=github&utm_medium=referral&utm_campaign=dataset)
- [Музыка](https://sillyfeed.app/t/music?utm_source=github&utm_medium=referral&utm_campaign=dataset)
- [Наука и образование](https://sillyfeed.app/t/science_education?utm_source=github&utm_medium=referral&utm_campaign=dataset)
- [Политика](https://sillyfeed.app/t/politics?utm_source=github&utm_medium=referral&utm_campaign=dataset)
- [Психология и отношения](https://sillyfeed.app/t/psychology_relationships?utm_source=github&utm_medium=referral&utm_campaign=dataset)
- [Путешествия и места](https://sillyfeed.app/t/travel_places?utm_source=github&utm_medium=referral&utm_campaign=dataset)
- [Спорт и фитнес](https://sillyfeed.app/t/sports_fitness?utm_source=github&utm_medium=referral&utm_campaign=dataset)
- [Технологии](https://sillyfeed.app/t/technology?utm_source=github&utm_medium=referral&utm_campaign=dataset)
- [Эзотерика](https://sillyfeed.app/t/esoterics?utm_source=github&utm_medium=referral&utm_campaign=dataset)
- [Юмор и мемы](https://sillyfeed.app/t/humor_memes?utm_source=github&utm_medium=referral&utm_campaign=dataset)

## Лицензия

[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) — со ссылкой на источник «SillyFeed, https://sillyfeed.app».
Автор замеров — Антон Першиков.
