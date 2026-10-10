# Данные к ДЗ 1 по рекомендательным системам: Amazon Reviews 2018, Digital Music

Данные к домашнему заданию 1 курса «Рекомендательные системы». Ноутбук с решением читает их отсюда по прямым ссылкам, поэтому запускается сразу, без ручного скачивания файлов.

## Файлы

| Файл | Что внутри | Источник |
|---|---|---|
| `Digital_Music.csv.gz` | Все оценки категории Digital Music, 1 584 082 строки. Заголовка нет, колонки по порядку: `item` (ASIN, код товара на Amazon), `user` (reviewerID, автор отзыва), `rating` (оценка от 1 до 5), `timestamp` (время отзыва в unix time, с точностью до дня). | [Amazon Review Data (2018)](https://cseweb.ucsd.edu/~jmcauley/datasets/amazon_v2/), раздел «Small» subsets for experimentation, строка Digital Music, файл ratings only (`Digital_Music.csv`) |
| `Digital_Music_5.json.gz` | Официальный 5-core той же категории: 169 781 отзыв, по одному JSON-объекту на строку (поля `reviewerID`, `asin`, `overall`, `unixReviewTime`, `style`, `summary`, `reviewText` и другие). В ноутбуке нужен только для сверки k-core и подсказок о товарах. | там же, файл 5-core (`Digital_Music_5.json.gz`) |

Оба файла скачаны 9 октября 2026 года и больше не меняются. CSV сжат gzip, 5-core пересжат; содержимое файлов не менялось. pandas читает сжатые файлы напрямую.

Данные принадлежат авторам датасета и выложены здесь только для воспроизводимости учебного ноутбука. Статья, на которую нужно ссылаться:

> Jianmo Ni, Jiacheng Li, Julian McAuley. Justifying recommendations using distantly-labeled reviews and fine-grained aspects. EMNLP 2019.

## Как загрузить

```python
import pandas as pd

DATA_URL = 'https://raw.githubusercontent.com/Alya-F/recsys-hw1-digital-music/main/'

raw = pd.read_csv(DATA_URL + 'Digital_Music.csv.gz', header=None,
                  names=['item', 'user', 'rating', 'timestamp'])
core5 = pd.read_json(DATA_URL + 'Digital_Music_5.json.gz', lines=True)
```
