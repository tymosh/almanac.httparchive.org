---
#See https://github.com/HTTPArchive/almanac.httparchive.org/wiki/Authors'-Guide#metadata-to-add-at-the-top-of-your-chapters
title: CSS
description: CSS chapter of the 2020 Web Almanac covering color, units, selectors, layout, animation, media queries, and Sass usage.
authors: [LeaVerou, svgeesus, rachelandrew]
reviewers: [estelle, fantasai, j9t, mirisuzanne, catalinred, hankchizljaw]
analysts: [rviscomi, LeaVerou, dooman87]
editors: [bazzadp]
translators: [tymosh]
LeaVerou_bio: Lea <a href="https://designftw.mit.edu">викладає курс "HCI & web programming"</a> і <a href="https://mavo.io">вивчає як зробити веб-програмування простішим</a> у <a href="https://mit.edu">MIT</a>. Вона є <a href="https://www.amazon.com/CSS-Secrets-Lea-Verou/dp/1449372635?tag=leaverou-20">авторкою</a> технічних бестселлерів та досвідченою <a href="https://lea.verou.me/speaking">спікеркою</a>. У неї є жага до відкритих веб стандартів, також вона є довготривалою учасницею <a href="https://www.w3.org/Style/CSS/members.en.php3">CSS Working Group</a>. Lea започаткувала <a href="https://github.com/leaverou">кілька популярних проектів і веб-застосунків з відкритим кодом</a>, таких як <a href="https://prismjs.com">Prism</a> та <a href="https://github.com/leaverou/awesomplete">Awesomplete</a>. Вона веде твітер <a href="https://twitter.com/leaverou">@leaverou</a> і блог <a href="https://lea.verou.me">lea.verou.me</a>.
svgeesus_bio: Chris Lilley є технічним директором World Wide Web Consortium (W3C). Вважається "батьком SVG", також співавтором PNG, співредактором CSS2, очолював групу розробників <code>@font-face</code> і був співрозробником WOFF. Був у Technical Architecture Group. Chris і досі намагається отримати керування кольором у веб. Зараз працює над CSS levels 3/4/5, Web Audio та WOFF2.
rachelandrew_bio: Я є веб-розробницею, авторкою текстів, спікеркою. Співзасновницею <a href="https://grabaperch.com">Perch CMS</a> і <a href="https://noti.st">Notist</a>. Членкинею <a href="https://www.w3.org/wiki/CSSWG">CSS Working Group</a>. Головною редакторкою <a href="https://www.smashingmagazine.com/">Smashing Magazine</a>.
discuss: 2037
results: https://docs.google.com/spreadsheets/d/1sMWXWjMujqfAREYxNbG_t1fOJKYCA6ASLwtz4pBQVTw/
featured_quote: Веб більше не підліток — йому вже 30 і він поводиться відповідно. Йому більше до вподоби стабільність і простота в читанні, ніж нові забавки і складність, він воліє не відволікатися на раптові забаганки.
featured_stat_1: 72.58%
featured_stat_label_1: Відсоток значень <code>&lt;length&gt;</code>, в яких використані одиниці <code>px</code>.
featured_stat_2: 91.05%
featured_stat_label_2: Відсоток мобільних сторінок, які використовують селектори з будь-якими вендорними префіксами
featured_stat_3: <code>darken()</code>
featured_stat_label_3: Найпопулярніші функції SCSS
---

## Вступ

Каскадні таблиці стилів (Cascading Stylesheets, CSS) – це мова, яка використовується для створення візуальної структури, форматування і розмальовування веб-сторінок та інших медіа. Це одна з трьох головних мов для побудови веб-сайтів. Іншими двома є HTML, який використовується для структури, і JavaScript, який використовується для визначення поведінки.

У [минулорічному початковому Web Almanac](../2019/), ми переглянули [велику кількість CSS метрик](../2019/css), отриманих з допомогою 41 SQL-запиту до даних HTTP Archive, щоб оцінити стан технологій у 2019. Цього року ми занурилися набагато глибше, щоб отримати не тільки кількість сторінок з певним CSS правилом, але й інформацію, *як саме* воно було використане.

Загалом, ми побачили веб у двох різних видах, коли справа доходить до використання CSS. У наших дописах в блогах та інформаційних бульбашках Twitter ми загалом більше обговорюємо найновіше та найяскравіше, однак все ще існують мільйони сайтів, які використовують код минулого десятиліття. Такі речі, як [вендорні префікси з минулої ери](#vendor-prefixes), [приватні фільтри IE](#filters), а також [використання float для розміщення елементів](#layout) в усій красі свого [clearfix](#class-names). Але ми також побачили вражаюче використання багатьох нових можливостей. Навіть таких, які тільки отримали всебічну підтримку цього року, як, наприклад, [`min()` and `max()`](#feature-queries). Однак, це загалом зворотня кореляція між тим, наскільки позитивно щось сприймається і тим, як широко це використовується. Наприклад, передові можливості [Houdini](#houdini) практично не використовувалися.

Схожим чином на конференціях ми часто фокусуємося на складних, випрацюваних випадках використання, від яких вибухає мозок, і стрічках Twitter, які заповнені твітами типу "CSS вміє *таке*?!". Однак, виявляється, що у більшості випадків використання CSS на практиці досить просте. [CSS змінні загалом використовуються як константи](#complexity) і рідко посилаються на інші змінні. `calc()` [найчастіше використовується з двома CSS властивостями](#calculations), градієнти [загалом мають дві точки](#gradients) і таке інше.

Веб більше не підліток — йому вже 30 і він поводиться відповідно. Йому більше до вподоби стабільність і простота в читанні, ніж нові забавки і складність, він воліє не відволікатися на раптові забаганки.

