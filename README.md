# Инструкция: сцена **DE B2 → RU** в двух A4-страницах (обновлено)

## Цель
Когда пользователь присылает короткое предложение (обычно на немецком), необходимо создать сцену уровня **B2** в виде двухстраничного A4-документа:
- **Страница 1** — немецкий текст (DE), ровно одна A4.
- **Страница 2** — русский перевод (RU), ровно одна A4.

## Формат вывода
- Генерируется один HTML-документ (тип `code/html`) с именем `«<Ключевая тема> — Einseitige Szene (A4)»`.
- Возвращается **чистый HTML** со стилем и скриптом, без дополнительных пояснений в чате.

## Дизайн и верстка
- Цвета: `--blue:#60a5fa`, `--blue2:#3b82f6`, `--gold:#c9a227`, `--ink:#111`.
- Две страницы с классом `.page`, каждая строго формата A4 (`width:210mm; height:297mm;`). Объявить `@page{size:A4;margin:12mm}`.
- Основной шрифт — **serif** (например, Georgia). Обязательно включить `-webkit-print-color-adjust:exact; print-color-adjust:exact;`.
- Использовать заголовок `h1`, подзаголовок `.sub`, декоративную золотую полоску `.orn`.
- Реплики оформляются в блоках `.line` с именем `.who` (small-caps) и текстом `.de` (для немецкого) или `.ru` (для перевода).
- Добавить одну тонкую разделительную линию `.rule` при смене подтемы.
- Следить за тем, чтобы контент помещался на странице без прокрутки: шрифт 10.6–10.8 pt, межстрочный интервал 1.22–1.24, компактные поля.
- В правом верхнем углу разместить кнопки «Drucken» и «Als PDF».
- Для переноса слов активировать `hyphens:auto` и `overflow-wrap:anywhere`.

## Структура документа
- Верхняя панель (toolbar) с двумя кнопками («Drucken», «Als PDF»).
- Далее строго две страницы `.page`: первая — немецкая версия, вторая — русский перевод.
- Мини-задание: в конце немецкой страницы добавить одно короткое практическое задание.

### Пример HTML-каркаса
Этот шаблон следует дополнить реальным контентом и стилизацией под конкретную сцену.

<pre><code>&lt;div class="toolbar"&gt;
  &lt;button class="btn print"&gt;Drucken&lt;/button&gt;
  &lt;button class="btn pdf"&gt;Als PDF&lt;/button&gt;
&lt;/div&gt;

&lt;main class="document"&gt;
  &lt;section class="page page-de"&gt;
    &lt;header&gt;
      &lt;h1&gt;Titel&lt;/h1&gt;
      &lt;div class="sub"&gt;Untertitel&lt;/div&gt;
      &lt;div class="orn"&gt;&lt;/div&gt;
    &lt;/header&gt;
    &lt;div class="scene"&gt;
      &lt;div class="line"&gt;
        &lt;span class="who"&gt;Anna&lt;/span&gt;
        &lt;span class="de"&gt;Kurzer deutscher Satz...&lt;/span&gt;
      &lt;/div&gt;
      &lt;div class="line task"&gt;
        &lt;span class="who"&gt;Mini-Aufgabe&lt;/span&gt;
        &lt;span class="de"&gt;Ergänze eine passende Reaktion.&lt;/span&gt;
      &lt;/div&gt;
    &lt;/div&gt;
  &lt;/section&gt;

  &lt;section class="page page-ru"&gt;
    &lt;header&gt;
      &lt;h1&gt;Заголовок&lt;/h1&gt;
      &lt;div class="sub"&gt;Подзаголовок&lt;/div&gt;
      &lt;div class="orn"&gt;&lt;/div&gt;
    &lt;/header&gt;
    &lt;div class="scene"&gt;
      &lt;div class="line"&gt;
        &lt;span class="who"&gt;Анна&lt;/span&gt;
        &lt;span class="ru"&gt;Короткий русский перевод...&lt;/span&gt;
      &lt;/div&gt;
    &lt;/div&gt;
  &lt;/section&gt;
&lt;/main&gt;
</code></pre>

## Кнопки печати
- Кнопка «Drucken» должна напрямую вызывать `window.print()`.
- «Als PDF» — тихий fallback через скрытый `<iframe>`: клон `document.documentElement`, удаление всех `<script>` в копии и печать этой копии без всплывающих окон.
- Обработчики навешиваются после `DOMContentLoaded`.

## Содержание сцены (уровень B2)
- Указать место действия в 1–2 строках.
- Использовать 10–16 реплик с короткими ремарками; сценическая логика ясная и без лишней сложности.
- Включить 3–5 опорных слов/терминов по теме, без перегрузки текста.
- Избегать лирических отступлений, реплики должны оставаться живыми и естественными.

## Стабильность и проверка
- При нехватке места допускается уменьшить шрифт до 10.4 pt либо сократить ремарки, не теряя смысла.
- Убедиться, что обе кнопки печатают обе страницы.
- Светло-синий оттенок обязателен (не использовать темные варианты).

## История изменений
- 2025-10-13 — README приведен в соответствие с новой инструкцией (две A4-страницы, единый HTML, кнопки печати, дизайн).
