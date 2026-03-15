# Demo Projects

Коллекция интерактивных HTML-проектов, опубликованных на GitHub Pages.

**Сайт:** https://albud1978.github.io/demo/

## Как это работает

Главная страница (`index.html`) автоматически находит все `.html` файлы в подпапках через GitHub API и отображает их как карточки. Ничего не нужно обновлять вручную — добавил файл в папку, он появился на сайте.

## Структура

```
demo/
├── index.html              ← главная (автогенерация карточек)
├── mnist/
│   ├── meta.json           ← метаданные папки
│   └── mnist_explainer.html
├── QMS/
│   ├── meta.json
│   ├── Misiura_Research_Toolkit_Dashboard.html
│   ├── Misiura_Research_Methodology_Handbook_v2.html
│   ├── DONO_DataSources_Analysis_v1.html
│   └── ERM_Operating_Model_v2.html
└── README.md
```

## Как добавить новый проект

1. Создай папку (или используй существующую)
2. Положи `.html` файл
3. Добавь кнопки навигации сразу после `<body>`:

```html
<div style="position:fixed;top:14px;left:14px;z-index:9999;display:flex;gap:8px">
<a onclick="if(history.length>1){history.back()}else{location.href='../index.html'}" style="width:40px;height:40px;border-radius:50%;background:var(--blue,#2563eb);color:#fff;display:flex;align-items:center;justify-content:center;text-decoration:none;box-shadow:0 2px 8px rgba(0,0,0,.25);font-size:18px;cursor:pointer;transition:background .2s" title="Назад">&#8592;</a>
<a href="../index.html" style="width:40px;height:40px;border-radius:50%;background:var(--blue,#2563eb);color:#fff;display:flex;align-items:center;justify-content:center;text-decoration:none;box-shadow:0 2px 8px rgba(0,0,0,.25);font-size:18px;transition:background .2s" title="На главную">&#8962;</a>
</div>
```

4. (Опционально) Создай или обнови `meta.json` в папке — см. ниже
5. Закоммить и запуш — карточка появится на главной автоматически

## Формат meta.json

Файл `meta.json` в каждой папке задаёт метаданные для отображения на главной. Если файла нет — используются имена папки и файла как fallback.

```json
{
  "name": "Название проекта",
  "description": "Общее описание папки",
  "tags": ["QMS", "doc"],
  "files": {
    "my_page.html": {
      "title": "Красивое название страницы",
      "description": "Описание конкретного файла",
      "tags": ["data", "viz"]
    }
  }
}
```

### Доступные теги/категории

| Тег | Иконка | Цвет |
|-----|--------|------|
| ML | 🧠 | фиолетовый |
| data | 📊 | зелёный |
| viz | 📈 | жёлтый |
| QMS | 📋 | синий |
| doc | 📄 | розовый |

## Технические детали

- Чистый HTML/CSS/JS, без фреймворков и сборщиков
- GitHub API endpoint: `https://api.github.com/repos/albud1978/demo/git/trees/main?recursive=1`
- Адаптивная вёрстка (мобильные + десктоп)
- Тёмная тема на главной, проекты со своими стилями
- Навигация: кнопка «Назад» (← smart: `history.back()` с fallback) + кнопка «Домой» (⌂ → `../index.html`)
