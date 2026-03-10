# MelBet Tutorial

Практическая инструкция по проекту `melbet-landing`:
`https://github.com/egorande228/melbet-landing.git`

## 1. Структура проекта

- `index.html` - главная страница;
- `contact.html` - страница формы;
- `css/styles.css` - общие стили и анимации;
- `css/contact.css` - стили формы;
- `js/main.js` - интерактив главной;
- `js/contact.js` - логика отправки формы;
- `js/i18n.js` - все переводы и переключение языков;
- `assets/` - логотипы, иконки, изображения.

## 2. Локальный запуск

```bash
cd "/Users/egorande/Documents/Melbet landing Akram/melbet-landing"
python3 -m http.server 5500
```

Проверка в браузере: `http://localhost:5500`

## 3. Языки и RTL

Поддерживаемые языки:

- English (`eng`)
- العربية (`arab`)
- Français (`franch`)
- Español (`esp`)
- فارسی (`farsi`)
- Монгол хэл (`mongol`)
- Af-Soomaali (`somali`)
- Português (`portug`)
- አማርኛ (`amharic`)
- Türkçe (`turk`)
- Русский (`russian`)

Важно:

- все тексты лежат в `js/i18n.js`;
- текущий язык хранится в `localStorage` (`melbet_lang`);
- для RTL-языков включается `dir="rtl"`;
- цифры в RTL-статистике принудительно отображаются слева-направо (`.stat-num`).

## 4. Форма заявок и лиды

Форма на `contact.html` отправляет данные в Google Apps Script через:

- `data-sheet-endpoint="https://script.google.com/macros/s/.../exec"`

Минимальный поток:

1. Пользователь отправляет форму.
2. `js/contact.js` валидирует поля.
3. Данные уходят в Apps Script endpoint.
4. Скрипт пишет лид в Google Sheets.

Что нужно держать актуальным:

- URL `data-sheet-endpoint` в `contact.html`;
- названия полей и валидация в `js/contact.js`;
- доступ sales-менеджеров к Google Sheet (роль Viewer/Editor).

## 5. Деплой в Cloudflare Pages

Рекомендуемая настройка для этого лендинга:

- Framework preset: `None`
- Build command: пусто
- Build output directory: `/`
- Production branch: `main`

После первого деплоя:

1. Добавить кастомные домены:
   - `melbetcollaborations.com`
   - `www.melbetcollaborations.com`
2. Проверить статус `Active` и `SSL enabled` для обоих доменов.
3. Включить редирект `www -> root` (301).
4. В SSL/TLS выбрать `Full (strict)` (если origin-сертификаты валидны).

## 6. Подключение Google Analytics 4

### Что нужно получить заранее

- `GA4 Measurement ID` вида `G-XXXXXXXXXX`.
- Доступ в Google Analytics:
  - минимум `Editor`;
  - лучше `Administrator` на Property.

### Какие доступы нужны для внедрения

- GitHub `write` к `melbet-landing` (чтобы внести код и запушить).
- Cloudflare Pages доступ (чтобы проконтролировать деплой).
- Google Analytics доступ (`Editor`/`Administrator`).

### Варианты подключения

1. Напрямую `gtag.js` в `index.html` и `contact.html`.
2. Через Google Tag Manager (`GTM-XXXXXXX`), если планируется много тегов.

### Базовые события для старта

- `page_view` (автоматически);
- `generate_lead` при успешной отправке формы;
- `click_contact` для кликов по Telegram/WhatsApp.

## 7. Перформанс (без удаления функций)

Что уже применялось и стоит сохранять:

- throttled scroll на `requestAnimationFrame`;
- оптимизация инициализации `i18n` (без лишней перерисовки на `eng`);
- `content-visibility` для секций;
- отключение тяжелых анимаций только для `prefers-reduced-motion`.

## 8. Git-процесс

```bash
git status -sb
git add .
git commit -m "Short clear message"
git push origin main
```

Практика:

- не коммитить `.DS_Store`;
- пушить маленькими логичными коммитами;
- после пуша проверять сайт на mobile.

## 9. Быстрый чек-лист перед релизом

- сайт открывается и скролл не тормозит на телефоне;
- все 11 языков переключаются;
- RTL-верстка и цифры отображаются корректно;
- форма отправляет лид в таблицу;
- домены `root` и `www` активны, SSL зеленый;
- редирект `www -> root` работает (301);
- в аналитике идут события.
