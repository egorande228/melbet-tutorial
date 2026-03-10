# Codex Workflow (MelBet)

## Source of truth
Рабочий репозиторий лендинга:
`https://github.com/egorande228/melbet-landing.git`

Обучающий репозиторий:
`https://github.com/egorande228/melbet-tutorial.git`

## Ежедневный порядок работы
1. Проверить статус:
- `git status -sb`
- `git remote -v`

2. Вносить правки небольшими шагами.

3. Перед коммитом:
- проверить ключевые страницы локально;
- убедиться, что нет мусорных файлов.

4. Коммит и push:
- `git add .`
- `git commit -m "..."`
- `git push origin main`

## Доступы для настройки аналитики и деплоя

Нужны заранее:

- GitHub: `write` в `melbet-landing`;
- Cloudflare: доступ к `Workers & Pages` + домену;
- Google Analytics 4: роль `Editor` или `Administrator`;
- (опционально) Google Tag Manager: право `Publish`.

## Критерии качества
- изменения не ломают адаптив;
- навигация и ссылки работают;
- анимации не мешают чтению контента;
- форма контактов заполняется корректно.
