# MelBet Tutorial

Этот репозиторий для обучения по проекту MelBet Landing.

## 1. Что в основном проекте

Базовая структура:

- `index.html` - главная страница;
- `contact.html` - форма заявки;
- `css/styles.css` - глобальные стили и блоки интерфейса;
- `css/contact.css` - стили формы;
- `js/main.js` - интерактив на главной;
- `js/contact.js` - интерактив формы;
- `js/i18n.js` - переключение языков и переводы;
- `assets/` - изображения и иконки.

## 2. Локальный запуск

Открыть проект локально:

```bash
cd "/Users/egorande/Documents/Melbet landing Akram/melbet-landing"
python3 -m http.server 5500
```

Открыть в браузере:

- `http://localhost:5500`

Остановить сервер:

- `Ctrl + C`

## 3. Мультиязычность

На сайте есть переключатель языков:

- `ENG`
- `ARABIC`
- `FRENCH`
- `AMHARIC`

Важно:

- переводы лежат в `js/i18n.js`;
- выбранный язык хранится в `localStorage` (`melbet_lang`);
- для арабского выставляется `dir="rtl"` и шрифт `Tajawal`;
- для остальных используется `Sarala`.

## 4. Ключевые контентные точки

### Teamcash program

Блок `Teamcash program` на главной содержит SVG-схему потоков.

Где менять:

- разметка схемы: `index.html`;
- стили схемы: `css/styles.css` (селекторы `flow-*`);
- тексты для всех языков: `js/i18n.js`.

### Контакты

Текущие ссылки:

- WhatsApp: `https://wa.me/37455256035`
- Telegram: `https://t.me/Melbetpartnerships`
- Email: `partnerships@melbet.com`

Где менять:

- `index.html` (контакт-секция);
- `index.html` и `contact.html` (floating chat dock).

## 5. Форма заявки

Текущее состояние:

- форма визуально готова;
- `action="#"` - данные пока не отправляются на сервер.

Чтобы включить отправку:

1. сделать backend endpoint, например `POST /api/lead`;
2. валидировать поля на сервере;
3. отправлять лиды в CRM/Google Sheets/Telegram;
4. вернуть статус для UI (`success/error`).

## 6. Git-процесс

Базовые команды:

```bash
git status
git add .
git commit -m "message"
git push origin main
```

Рекомендации:

- коммиты делать маленькими и логичными;
- перед пушем проверять мобильный вид и ссылки;
- не коммитить системные файлы (`.DS_Store`).

## 7. Чек-лист перед публикацией

- сайт открывается локально;
- нет дублей текста и битых ссылок;
- языки переключаются корректно;
- арабская версия не ломает верстку;
- форма и кнопки чата видны на desktop и mobile;
- `git status` чистый (кроме намеренных изменений).
