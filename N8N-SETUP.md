# Настройка n8n за 3 минуты

## Шаг 1: Добавь NocoDB credentials
1. n8n: Settings → Credentials → Add Credential
2. Выбери NocoDB API
3. Заполни Host и API Token из NocoDB
4. Save

## Шаг 2: Импортируй workflow
1. n8n: Import from File → n8n-workflow-simple.json

## Шаг 3: Настрой nodes
В каждом NocoDB node:
- Credentials: выбери созданный
- Project: выберется автоматом из списка!
- Table: выбери lessons

## Шаг 4: Активируй
Переключатель Active → скопируй Webhook URL

## Ссылка на редактор:
https://pro-eugenia.github.io/edverse-editor/?api=ТВОЙ_WEBHOOK_URL&lesson=m8_1
