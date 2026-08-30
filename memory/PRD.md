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

## Обновление (2026-08-25)
- Добавлена статья «Выездное обслуживание принтеров: как организовать без простоев»
  (slug `vyezdnoe-obsluzhivanie-printerov-bez-prostoev`, dzen https://dzen.ru/a/aorGd__jWlrMU0nV).
  8 фото скачаны из Google Doc в public/images/analytics/ (vyezd-*.jpg). Показывается первой.
- Добавлены перекрёстные ссылки между статьями (ролики/тонер/рынок/TCO) для удержания и SEO.
- SEO-аудит и доработка всех статей аналитики:
  * AnalyticsArticle.jsx: html lang, robots max-image-preview:large, полный Open Graph
    (site_name, locale, image:alt), Twitter Card, article:modified_time/section,
    JSON-LD FAQPage (для статей с полем `faq`).
  * Analytics.jsx (список): og:image, Twitter Card, og:locale/site_name, html lang.
  * В data/articles.js добавлено структурированное поле `faq` для статей TCO и «Выездное».
  * routes.mjs: маршрут новой статьи добавлен (prerender + sitemap с image).
- Проверено: компиляция без ошибок, все страницы и 8 изображений — HTTP 200,
  битых картинок и ошибок в консоли нет; список показывает новую статью первой.

## Обновление (2026-08-28)
- Добавлена статья «Почему ваш московский офис переплачивает за печать: 7 ошибок»
  (slug `moskovskiy-ofis-pereplachivaet-za-pechat-7-oshibok`, dzen https://dzen.ru/a/apQT7LdIiUjcEckN).
  По просьбе — стоит ТРЕТЬЕЙ в списке (index 2), перед «Резиновые убийцы».
- Источник (Google Doc) отдавал картинки в base64 (обрезаны), Dzen — JS-рендер без CDN-ссылок,
  поэтому 8 иллюстраций СГЕНЕРИРОВАНЫ (image_generation, gemini) под каждую секцию и сохранены
  как public/images/analytics/msk-*.jpg. Точные цифры вынесены в подписи (текст на картинках не рисуется).
  ЗАМЕТКА: если пользователь пришлёт оригинальные фото из статьи — заменить msk-*.jpg на них.
- Таблицы (сравнение принтеров, без/с договором, итоговые потери), FAQ (поле `faq` → FAQPage JSON-LD),
  перекрёстные ссылки на статьи TCO/выездное/тонер.
- Маршрут добавлен в scripts/routes.mjs (prerender + sitemap с image).
- Проверено: компиляция без ошибок, /analytics и статья — HTTP 200, все 8 картинок 200,
  список показывает новую статью третьей, битых изображений нет.
