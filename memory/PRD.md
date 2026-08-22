# ComplexPrint — сайт сервисного центра (React SPA, /app root)

## Раздел «Аналитика»
Статьи-данные: `/app/src/data/articles.js` (массив `articles`, поиск по slug).
Список: `/app/src/pages/Analytics.jsx` (grid карточек, порядок = порядок в массиве).
Статья: `/app/src/pages/AnalyticsArticle.jsx` (роут `/analytics/:slug`).
Рендерер параграфов поддерживает типы: string, `quote`, `list`, `image`, `subheading` (h3), `table` (headers+rows, inline-разметка в ячейках).
Маршруты для prerender/sitemap: `/app/scripts/routes.mjs`.

## Реализовано (2026-08-22)
- Добавлена статья «Сколько стоит содержать парк принтеров в офисе: полный расчёт TCO»
  (slug `skolko-stoit-soderzhat-park-printerov-tco`, dzen: https://dzen.ru/a/aomeYCPmOUPCQ_XF).
  Отображается первой в списке (новейшая).
- Добавлены рендереры `table` и `subheading` в AnalyticsArticle.jsx.
- Фото из `public/images/analytics/` (сделаны ASCII-копии файлов с пробелами/кириллицей:
  tco-cover-infographic.png, tco-office-messy-hp.jpeg, tco-office-clean-kyocera.jpeg,
  tco-thermofilm-worn.jpg, tco-chart-20people.png, tco-chart-toner-vs-original.png,
  tco-cartridge-disassembled.png, combined_rubber_parts.png).
- Маршрут статьи добавлен в scripts/routes.mjs (prerender + sitemap).

## Проверено
- yarn install + dev server (craco) компилируется без ошибок.
- Страница статьи и все 8 изображений возвращают HTTP 200. Ошибок в консоли нет.
