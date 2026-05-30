# Domain & IP Aggregator

[Русский](#русский) | [English](#english)

---

# Русский

Этот репозиторий автоматически собирает домены, IP-адреса и подсети из правил Clash проекта BlackMatrix7 и объединяет их в единый файл `rules.txt`.

## Возможности

* Автоматическое обновление через GitHub Actions
* Ручной запуск обновления
* Обновление при изменении файла `sources.txt`
* Удаление дубликатов
* Поддержка IPv4, IPv6 и подсетей
* Поддержка комментариев в `sources.txt`

## Источник данных

Правила загружаются из репозитория:

[https://github.com/blackmatrix7/ios_rule_script](https://github.com/blackmatrix7/ios_rule_script)

## Структура репозитория

```text
.
├── sources.txt
├── rules.txt
└── .github
    └── workflows
        └── update-rules.yml
```

## Формат sources.txt

Каждая строка содержит название сервиса из каталога `rule/Clash`.

Пример:

```text
# AI
OpenAI
Claude

# Messengers
Telegram
Discord

# Disabled
# Facebook

GitHub
Google # Search
```

Поддерживаются:

* пустые строки;
* строки, начинающиеся с `#`;
* комментарии после названия сервиса.

## Что попадает в rules.txt

Из исходных правил извлекаются только:

* DOMAIN
* DOMAIN-SUFFIX
* IP-CIDR
* IP-CIDR6

Например:

```text
DOMAIN-SUFFIX,openai.com
DOMAIN,chat.openai.com
IP-CIDR,91.108.4.0/22
IP-CIDR6,2001:b28:f23d::/48
```

Преобразуется в:

```text
openai.com
chat.openai.com
91.108.4.0/22
2001:b28:f23d::/48
```

## Автоматическое обновление

Workflow запускается:

* ежедневно по расписанию;
* вручную через GitHub Actions;
* при изменении файла `sources.txt`.

## Лицензия

Данные берутся из проекта BlackMatrix7. Используйте их в соответствии с лицензией исходного проекта.

---

# English

This repository automatically collects domains, IP addresses and subnets from BlackMatrix7 Clash rules and merges them into a single `rules.txt` file.

## Features

* Automatic updates via GitHub Actions
* Manual workflow execution
* Updates when `sources.txt` changes
* Duplicate removal
* IPv4, IPv6 and subnet support
* Comment support in `sources.txt`

## Data Source

Rules are downloaded from:

[https://github.com/blackmatrix7/ios_rule_script](https://github.com/blackmatrix7/ios_rule_script)

## Repository Structure

```text
.
├── sources.txt
├── rules.txt
└── .github
    └── workflows
        └── update-rules.yml
```

## sources.txt Format

Each line contains a service name from the `rule/Clash` directory.

Example:

```text
# AI
OpenAI
Claude

# Messengers
Telegram
Discord

# Disabled
# Facebook

GitHub
Google # Search
```

Supported:

* empty lines;
* lines starting with `#`;
* inline comments after service names.

## What is included in rules.txt

Only the following rule types are extracted:

* DOMAIN
* DOMAIN-SUFFIX
* IP-CIDR
* IP-CIDR6

Example:

```text
DOMAIN-SUFFIX,openai.com
DOMAIN,chat.openai.com
IP-CIDR,91.108.4.0/22
IP-CIDR6,2001:b28:f23d::/48
```

Converted to:

```text
openai.com
chat.openai.com
91.108.4.0/22
2001:b28:f23d::/48
```

## Automatic Updates

The workflow runs:

* daily on schedule;
* manually via GitHub Actions;
* automatically when `sources.txt` is modified.

## License

Rule data originates from the BlackMatrix7 project. Please comply with the original project's license terms.
