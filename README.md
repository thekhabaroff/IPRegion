# ipregion

`ipregion` — это production-ready Bash-скрипт для проверки того, как ваш IP определяется GeoIP-базами, популярными интернет-сервисами и CDN-узлами.[1][2]

## Возможности

- Проверка через GeoIP-сервисы: MaxMind, RIPE, ipinfo, ipregistry, ipapi, Cloudflare, ipquery, ipwho.is и другие.[3]
- Проверка через популярные сервисы: Google, YouTube, Twitch, ChatGPT, Netflix, Spotify, Reddit, Amazon Prime, Apple, Steam, PlayStation, TikTok, Bing.[3]
- Проверка CDN-маршрутизации: Cloudflare CDN, YouTube CDN, Netflix CDN.[3]
- Поддержка IPv4 и IPv6.[3]
- Вывод в JSON.[3]
- Поддержка SOCKS5-прокси и выбора сетевого интерфейса.[3]
- Цветной вывод в терминале.[3]
- GitHub Actions-проверка через ShellCheck для push и pull request.[4]

## Зачем нужен скрипт

Скрипт полезен, если вы хотите понять, как ваш IP видят разные базы геолокации и сервисы: как страну IP, как регион CDN, как регион аккаунта или как зону доступности конкретного продукта.[3]

Это особенно полезно для VPN, прокси, мобильных операторов, серверов, residential IP и нестандартной маршрутизации, когда разные сервисы показывают разные страны.[3]

## Установка

Требования:

- `bash`
- `curl`
- `jq`
- `column` из `util-linux`[3]

Сделайте файл исполняемым и запустите его:

```bash
sudo curl -fsSL https://raw.githubusercontent.com/thekhabaroff/IPRegion/main/ipregion.sh -o /usr/local/bin/ip
sudo chmod +x /usr/local/bin/ip && ip
```

```bash
chmod +x ipregion.sh
./ipregion.sh
```

## Использование

Базовый запуск:

```bash
./ipregion.sh
```

Примеры:

```bash
./ipregion.sh -h
./ipregion.sh -g primary
./ipregion.sh -g custom
./ipregion.sh -g cdn
./ipregion.sh -4
./ipregion.sh -6
./ipregion.sh -j
./ipregion.sh -p 127.0.0.1:1080
./ipregion.sh -i eth0
./ipregion.sh --version
```

## Параметры

- `-h, --help` — показать справку.[3]
- `-v, --verbose` — включить подробный лог.[3]
- `-j, --json` — вывести результат в JSON.[3]
- `-g, --group GROUP` — запустить только одну группу: `primary`, `custom`, `cdn` или `all`.[3]
- `-t, --timeout SEC` — задать таймаут запросов.[3]
- `-4, --ipv4` — проверять только IPv4.[3]
- `-6, --ipv6` — проверять только IPv6.[3]
- `-p, --proxy ADDR` — использовать SOCKS5-прокси.[3]
- `-i, --interface IF` — использовать указанный сетевой интерфейс.[3]
- `--version` — показать версию скрипта.[3]

## Структура вывода

Скрипт может выводить до трёх логических блоков:[3]

- `Popular services` — как ваш IP/регион видят крупные сервисы.[3]
- `CDN services` — через какие CDN-узлы и страны проходит доставка контента.[3]
- `GeoIP services` — что возвращают классические IP geolocation API и базы.[3]

В конце выводится `Legend` с процентным распределением стран по IPv4/IPv6 среди результатов сервисов.[3]

## Пример вывода

```text
ipregion.sh v1.0.0
https://github.com/Davoyan/ipregion

IPv4: 217.177.*.*
ASN: AS50053 Anton Levin

Popular services
Service                 |IPv4
Google                  |KG
Netflix                 |LV
...

CDN services
Service                 |IPv4
Cloudflare CDN          |DE (FRA)
YouTube CDN             |DE (FRA)
Netflix CDN             |LV
```

## CI / Lint

В репозитории настроен GitHub Actions workflow, который запускает ShellCheck на каждый `push` и `pull request`, что помогает находить типовые ошибки shell-скриптов до публикации изменений.[4][5]

## Ограничения

Скрипт опирается на внешние сервисы и частично на неофициальные эндпоинты, поэтому отдельные результаты могут меняться со временем, попадать под rate limit или отражать не только IP-геолокацию, но и регион аккаунта, маршрутизации или продуктовой доступности.[3]

Иными словами, результат `Google`, `YouTube`, `Netflix`, `ChatGPT` или `CDN` не всегда означает именно «официальную страну IP в RIPE/MaxMind» — иногда это прикладная логика конкретного сервиса.[3]

## Лицензия

Проект распространяется под лицензией MIT.[3]
