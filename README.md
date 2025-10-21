# 📝 EdVerse Lesson Editor

> Визуальный WYSIWYG редактор HTML-контента для образовательной платформы EdVerse с интеграцией NocoDB

[![Live Demo](https://img.shields.io/badge/demo-live-success)](https://твой-username.github.io/edverse-editor/)
[![License](https://img.shields.io/badge/license-MIT-blue)](LICENSE)

![EdVerse Editor Preview](https://via.placeholder.com/800x400/2563eb/ffffff?text=EdVerse+Editor)

## ✨ Возможности

- 🎨 **Визуальное редактирование** - полноценный WYSIWYG редактор
- 💾 **Автосохранение** - локальное сохранение каждые 30 секунд  
- 🔄 **Синхронизация** - интеграция с NocoDB через n8n
- 📱 **Мобильная версия** - адаптирован для Telegram WebView
- 🎯 **Специальные блоки** - подсказки, код, спойлеры, изображения
- 🚀 **Без зависимостей** - чистый JavaScript, работает везде

## 🎬 Демо

Попробуй редактор: [https://твой-username.github.io/edverse-editor/](https://твой-username.github.io/edverse-editor/)

## 🚀 Быстрый старт

### 1. Клонируй репозиторий

```bash
git clone https://github.com/твой-username/edverse-editor.git
cd edverse-editor
```

### 2. Открой `index.html`

Просто открой файл в браузере или используй локальный сервер:

```bash
# С помощью Python
python -m http.server 8000

# Или с помощью Node.js
npx http-server
```

### 3. Настрой интеграцию

1. Настрой n8n workflow (см. [QUICK-START.md](QUICK-START.md))
2. Укажи Webhook URL в редакторе
3. Начни редактировать!

## 📖 Документация

- [🚀 Быстрый старт](QUICK-START.md) - настройка за 5 минут
- [📚 Полная документация](EDITOR-README.md) - детальное руководство
- [🔧 n8n Workflow](n8n-edverse-workflow.json) - готовый workflow для импорта

## 🎯 Использование

### Базовое редактирование

1. **Форматирование текста** - используй кнопки H1, H2, H3, жирный, курсив
2. **Списки** - нумерованные и маркированные списки
3. **Специальные блоки** - вставляй подсказки, код, спойлеры через кнопки

### Интеграция с NocoDB

```javascript
// API Endpoint
https://твой-n8n.app.n8n.cloud/webhook/edverse-save

// Формат данных
{
  "lesson_id": "m8_1",
  "content": "<h1>HTML контент</h1>"
}
```

### Открытие в Telegram

```python
# Inline кнопка
keyboard = {
  "inline_keyboard": [[{
    "text": "✏️ Редактировать",
    "url": "https://твой-username.github.io/edverse-editor/"
  }]]
}
```

## 🏗️ Архитектура

```
┌─────────────┐      ┌──────────┐      ┌──────────┐
│   Browser   │─────▶│   n8n    │─────▶│ NocoDB   │
│  / Telegram │◀─────│ Webhook  │◀─────│ Database │
└─────────────┘      └──────────┘      └──────────┘
     Editor             Proxy           Storage
```

## 📁 Структура проекта

```
edverse-editor/
├── index.html                    # Основной редактор
├── README.md                     # Этот файл
├── QUICK-START.md               # Быстрый старт
├── EDITOR-README.md             # Полная документация
├── n8n-edverse-workflow.json    # n8n workflow
└── LICENSE                      # Лицензия MIT
```

## 🛠️ Технологии

- **Frontend**: Vanilla JavaScript, ContentEditable API
- **Styling**: CSS3, CSS Variables
- **Integration**: n8n, NocoDB REST API
- **Hosting**: GitHub Pages (или любой статический хостинг)

## 🔧 Настройка n8n

1. Импортируй `n8n-edverse-workflow.json`
2. Настрой credentials для NocoDB
3. Укажи BASE_ID и TABLE_ID
4. Активируй workflow
5. Скопируй Webhook URLs

Подробнее: [EDITOR-README.md](EDITOR-README.md)

## 📊 Структура данных NocoDB

```sql
CREATE TABLE lessons (
  id              AUTO_INCREMENT PRIMARY KEY,
  lesson_id       VARCHAR(50) UNIQUE NOT NULL,
  content         TEXT NOT NULL,
  title           VARCHAR(255),
  module          VARCHAR(100),
  created_at      DATETIME DEFAULT NOW(),
  updated_at      DATETIME DEFAULT NOW()
);
```

## 🎨 Кастомизация

### Изменение цветовой схемы

```css
:root {
  --primary: #2563eb;
  --primary-hover: #1d4ed8;
  --success: #10b981;
}
```

### Добавление новых элементов

См. раздел "Кастомизация" в [EDITOR-README.md](EDITOR-README.md)

## 🤝 Вклад в проект

Contributions welcome! Пожалуйста:

1. Fork репозиторий
2. Создай feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit изменения (`git commit -m 'Add AmazingFeature'`)
4. Push в branch (`git push origin feature/AmazingFeature`)
5. Открой Pull Request

## 📝 Roadmap

- [ ] Drag & drop для изображений
- [ ] Markdown поддержка
- [ ] История изменений
- [ ] Темная тема
- [ ] Мультиязычность
- [ ] Offline режим с Service Worker
- [ ] Collaborative editing

## 🐛 Известные проблемы

- ContentEditable может вести себя по-разному в разных браузерах
- В Safari могут быть проблемы с clipboard API
- В старых версиях iOS некоторые функции недоступны

## 📄 Лицензия

MIT License - см. [LICENSE](LICENSE) для деталей

## 👤 Автор

**Eugenia**
- GitHub: [@твой-username](https://github.com/твой-username)
- Telegram: [@твой-telegram](https://t.me/твой-telegram)

## 🙏 Благодарности

- [n8n](https://n8n.io/) - за отличную платформу автоматизации
- [NocoDB](https://nocodb.com/) - за удобную работу с данными
- [Telegram](https://telegram.org/) - за WebApps API

---

⭐ Если проект был полезен - поставь звездочку на GitHub!

**Сделано с ❤️ для образования**

