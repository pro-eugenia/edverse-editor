# 🚀 Быстрый старт EdVerse Editor

## За 5 минут до работающего редактора

### Шаг 1: Загрузи на GitHub (2 мин)

```bash
# 1. Создай новый репозиторий на github.com
# Название: edverse-editor
# Public, без README

# 2. Локально
cd ~/Desktop
mkdir edverse-editor
cd edverse-editor

# 3. Скопируй файл редактора
cp "/Users/pro_eugenia/Desktop/Eugenia Bots/EDVERSE/lesson-editor-full.html" index.html

# 4. Инициализируй и загрузи
git init
git add index.html
git commit -m "Add editor"
git branch -M main
git remote add origin https://github.com/ТвойUsername/edverse-editor.git
git push -u origin main
```

### Шаг 2: Включи GitHub Pages (1 мин)

1. Открой репозиторий на GitHub
2. Settings → Pages
3. Source: Deploy from a branch
4. Branch: `main` / `root`
5. Save

✅ Редактор доступен: `https://ТвойUsername.github.io/edverse-editor/`

### Шаг 3: Настрой n8n (2 мин)

1. Открой n8n
2. Create new workflow
3. Import from file → выбери `n8n-edverse-workflow.json`
4. Замени:
   - `YOUR_BASE_ID` → твой Project ID из NocoDB
   - `YOUR_TABLE_ID` → ID таблицы `lessons`
5. Добавь credentials для NocoDB (API Token)
6. Activate workflow

✅ Webhook URL скопируй из n8n (например: `https://твой-n8n.app.n8n.cloud/webhook/edverse-save`)

### Шаг 4: Используй редактор (30 сек)

1. Открой `https://ТвойUsername.github.io/edverse-editor/`
2. Вставь Webhook URL в "API Endpoint"
3. Укажи lesson_id (например: `m8_1`)
4. Нажми "Загрузить" или начни редактировать
5. Нажми "Сохранить"

✅ Готово!

---

## Добавление в Telegram бота

### Вариант 1: Inline кнопка

```python
keyboard = {
  "inline_keyboard": [[
    {
      "text": "✏️ Редактировать урок",
      "url": "https://ТвойUsername.github.io/edverse-editor/?lesson_id=m8_1"
    }
  ]]
}
```

### Вариант 2: Mini App

```python
keyboard = {
  "inline_keyboard": [[
    {
      "text": "✏️ Открыть редактор",
      "web_app": {
        "url": "https://ТвойUsername.github.io/edverse-editor/"
      }
    }
  ]]
}
```

---

## Структура таблицы NocoDB

Создай таблицу `lessons`:

| Поле | Тип | Обязательное |
|------|-----|--------------|
| lesson_id | SingleLineText | ✅ |
| content | LongText | ✅ |
| updated_at | DateTime |  |
| title | SingleLineText |  |

---

## Troubleshooting

### ❌ "Ошибка соединения"
- Проверь, что n8n workflow активен
- Проверь CORS в n8n (должен быть `*`)
- Проверь webhook URL

### ❌ "Контент не найден"
- Убедись, что lesson_id существует в NocoDB
- Проверь фильтр в n8n node "NocoDB Get"

### ❌ "Не сохраняется"
- Проверь credentials NocoDB в n8n
- Проверь, что поля lesson_id и content заполнены
- Посмотри логи в n8n (Executions)

---

## Полезные ссылки

- [Полная документация](./EDITOR-README.md)
- [NocoDB Docs](https://docs.nocodb.com/)
- [n8n Docs](https://docs.n8n.io/)

---

**Нужна помощь?** Проверь логи:
- Браузер: F12 → Console
- n8n: Executions → Последний запуск
- NocoDB: Activity → Recent changes

