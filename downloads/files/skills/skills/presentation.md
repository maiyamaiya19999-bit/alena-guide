---
name: presentation
description: Создаёт HTML-презентацию для видеоуроков в фирменном стиле Алены (60/40 split — правые 40% под видео, пудрово-розовая палитра, 8 схемок-вариаций, экспорт в PDF). Вызывай, когда Алена просит слайды/презентацию к видеоуроку.
---

# Скилл: Оформление презентации для видеоуроков Алены

## 0. Перед началом
1. Прочитай `~/.claude/brand/PROFILE.md` и `~/.claude/brand/TOV-SAMPLES.md` — голос, темы, границы.
2. Прочитай `~/.claude/brand/style-guide.md` — палитра и правила вёрстки. Ник в навбаре — `the.tsarevna`, монограмма — `Ц`.
3. Если появился логотип `~/.claude/brand/logo-alena.png` — используй его вместо монограммы.
4. Три правила из шапки распаковки — явно: она НЕ тренер (никаких упражнений/осанки — всё лёжа и слушая); про финансовую независимость пока не говорим; слово «состояние» → «чувствование телом» / «ощущения в теле».
5. Границы из раздела 4 PROFILE.md абсолютны: закрытые темы на слайдах не появляются. Фильтр доказательной папки: без «вылечу», «уберу боль», гарантий и сроков; исполнение желаний — только от первого лица.

Когда Алена просит создать презентацию, слайды или материал для видеоурока — создай HTML-страницу со слайдами в её фирменном стиле.

## Формат

Это **презентация для видеоуроков**. Каждый слайд — отдельный экран 100vh. Макет разделён вертикально:
- **Левые 60%** — зона контента (текст, списки, карточки)
- **Правые 40%** — пустая зона под видео (туда в монтаже вставляется видео Алены)
- Между ними — тонкая вертикальная линия-разделитель `#ECE1DE`

Правая часть ВСЕГДА пустая. Никогда не размещай туда контент.

## Бренд-стиль

### Цвета (из `~/.claude/brand/style-guide.md`)
- Фон: `#FBF7F5`
- Текст: `#332A2E`
- Текст второстепенный: `#5C4F54`, `#7A6C71`, `#9B8D92`
- Акцент (пыльная роза): `#9C5F6A` — для курсивных выделений в заголовках, точек в списках, бейджей, цифр
- Серые блоки: `#F4ECEA` — без закруглений, без цветных линий
- Карточки: `#F7F1EF` с рамкой `#E8DCD8` — квадратные углы
- Советы в карточках: `#EFE4E1`
- Линии: `#ECE1DE` (разделители), `#F1E8E5` (навбар, списки)
- На тёмном фоне НИКОГДА не использовать пыльную розу — заменять на `#E3C2C9`

### Шрифты (Google Fonts)
```html
<link href="https://fonts.googleapis.com/css2?family=Libre+Baskerville:ital,wght@0,400;0,700;1,400&family=Inter:wght@400;500;600;700;800&family=DM+Sans:ital@1&display=swap" rel="stylesheet">
```
- **Заголовки**: `Libre Baskerville`, Georgia, serif — жирный, с курсивными акцентами пыльной розой
- **Основной текст**: `Inter`, sans-serif — 16px, line-height 1.75
- **Подзаголовки**: `Libre Baskerville` — 20px, жирный
- **Декоративные цифры**: `Libre Baskerville`, italic, opacity 0.3, цвет `#9C5F6A` — для нумерованных списков и метрик
- **Ник в навбаре**: `DM Sans`, italic, `#9B8D92`

### Навбар (на каждом слайде)
- Ширина = 60% (только зона контента)
- **Слева** — монограмма `<span class="nav__mono">Ц</span>` (Libre Baskerville italic 22px, цвет акцента)
- **Справа** — ник `<span class="nav__logo-name">the.tsarevna</span>` (DM Sans italic 14px, `#9B8D92`, `margin-right: 8px`)
- Тонкая линия снизу `#F1E8E5`
- Когда появится логотип — `<img src="logo.png" alt="Ц">` высотой 30px вместо монограммы

### Бейдж (на титульном слайде)
- Тонкая рамка 1px цвета акцента, текст капсом, разрядка 2px, размер 11px
- Текст: «УРОК», «ГАЙД», «КУРС» и т.п.

## Структура слайдов

### Слайд 1 — Титульный
```
Навбар
Бейдж «УРОК»
Заголовок h1 (Libre Baskerville, 36px, с курсивным акцентом пыльной розой)
Описание (Inter, 17px, #7A6C71)
Мета-инфо (13px, #9B8D92, с разрядкой)
```

### Слайды 2+ — Контентные
```
Навбар
Заголовок h2 (Libre Baskerville, 28px) — БЕЗ нумерации
Контент: текст, списки, блоки, карточки, схемки
```

## Важные правила

1. **БЕЗ нумерации** — никаких 01., 02., 03. в заголовках слайдов
2. **БЕЗ номеров страниц** — никаких «1 / 21» внизу
3. **Контент только в левых 60%** — правая часть всегда пустая
4. **Каждый слайд = 100vh** — один экран
5. **Навбар на каждом слайде** — не sticky, просто повторяется
6. **Квадратные углы везде** — никаких border-radius
7. **max-width: 580px** для внутреннего контента слайда
8. **Контент вертикально по центру** слайда (flexbox align-items: center)
9. **Чередуй типы слайдов** — не делай 5 одинаковых слайдов подряд. Разбавляй базовые слайды (текст, списки) схемками (цитаты, метрики, чек-листы, формулы и т.д.). Каждый 2–3-й слайд должен быть схемкой, чтобы презентация была визуально разнообразной и интересной.
10. **Claude и reels** — слова «клод» и «рилс» ВСЕГДА пишутся латиницей: **Claude** и **reels**. Никогда кириллицей.
11. **Голос** — по разделу 8 PROFILE.md: на «ты», женский род, длинные предложения через «и»/«потому что» при коротких строках, «проги» вместо терминов, без «Вселенной», без «состояния» как термина, без инфобиз-лексики («трансформация», «прокачка»).

---

## Базовые элементы контента

### Заголовок секции
```html
<h2 class="section-heading">Тебя не сломали — <em>тебя зажали</em></h2>
```
Слово или фраза в `<em>` выделяется курсивом и цветом пыльной розы.

### Серый блок .highlight
Для ключевых мыслей, выводов, важных замечаний.
```html
<div class="highlight"><strong>Важно:</strong> чувствование телом — это не упражнения. Ты просто ложишься и слушаешь.</div>
```

### Список .guide-list
С точками цвета акцента, разделителями между пунктами.
```html
<ul class="guide-list">
  <li><strong>15 минут лёжа.</strong> Не спорт и не осанка — просто ляг и послушай.</li>
</ul>
```

### Подзаголовок .sub-heading
```html
<h3 class="sub-heading">Подзаголовок</h3>
```

### Карточка .scenario-card
Для сценариев, кейсов, примеров.
```html
<div class="scenario-card">
  <div class="scenario-card__num">ПРИМЕР</div>
  <div class="scenario-card__title">Вечер после дня на автопилоте</div>
  <div class="scenario-card__point">
    <span class="scenario-card__point-label">Шаг.</span>
    <span class="scenario-card__point-text">Легла, включила практику на 15 минут и дала плечам опуститься.</span>
  </div>
  <div class="scenario-card__tip"><strong>Совет:</strong> ничего не надо делать — надо перестать делать.</div>
</div>
```

### Завершающая фраза .footer-note
Курсивная фраза Libre Baskerville для финального слайда.
```html
<p class="footer-note">Из железной леди — <em>обратно в живую женщину</em></p>
```

---

## Схемки-вариации (8 типов)

Используй эти схемки для разнообразия. Чередуй их с базовыми слайдами — каждый 2–3-й слайд должен быть одной из этих схемок. Выбирай тип по смыслу контента.

### Схемка 1: Цитата-акцент
Для ключевых мыслей, ярких высказываний, выводов.
```html
<div class="slide__inner">
  <div class="quote-slide__label">КЛЮЧЕВАЯ МЫСЛЬ</div>
  <div class="quote-slide__mark">&ldquo;</div>
  <div class="quote-slide__text">Пока тело зажато, визуализация — <em>это просто фантазии.</em></div>
  <div class="quote-slide__divider"></div>
  <p class="quote-slide__source">О том, почему мечтать головой недостаточно — желаемое надо прожить телом.</p>
</div>
```

### Схемка 2: Шаги с вертикальной линией
Для пошаговых процессов, путей, последовательностей. Точки: заполненные = пройденные (`steps__item--active`), пустые = предстоящие.
```html
<div class="slide__inner">
  <div class="steps__heading">Из зажатого тела — <em>к другим выборам</em></div>
  <div class="steps__list">
    <div class="steps__item steps__item--active">
      <div class="steps__dot"></div>
      <div class="steps__item-title">Расслабила тело</div>
      <div class="steps__item-text">Лёжа и слушая, 15 минут вечером.</div>
    </div>
    <div class="steps__item">
      <div class="steps__dot"></div>
      <div class="steps__item-title">Мозг начал замечать другое</div>
      <div class="steps__item-text">В безопасности поле внимания расширяется.</div>
    </div>
  </div>
</div>
```

### Схемка 3: Нумерованный список
Для пронумерованных пунктов, анатомий, структур. Цифры — крупные, Libre Baskerville italic, полупрозрачные.
```html
<div class="slide__inner">
  <div class="numlist__heading">Четыре столпа <em>блога</em></div>
  <div class="numlist__item">
    <div class="numlist__num">1</div>
    <div class="numlist__text"><strong>Тело и расслабление</strong> <span>— зажимы, психосоматика, «шея болит не от подушки».</span></div>
  </div>
  <div class="numlist__item">
    <div class="numlist__num">2</div>
    <div class="numlist__text"><strong>Чувствование телом</strong> <span>— не визуализировать головой, а прожить телом.</span></div>
  </div>
</div>
```

### Схемка 4: Акцентная полоса слева
Для главных правил, ключевых принципов, важных мыслей с пояснением.
```html
<div class="slide__inner">
  <div class="accent-bar__label">ГЛАВНОЕ ПРАВИЛО</div>
  <div class="accent-bar__block">
    <div class="accent-bar__title">Ничего не надо делать. <em>Надо перестать делать.</em></div>
    <p class="accent-bar__text">Без дисциплины и подвигов: 15 минут, просто ляг и послушай — тело сделает остальное.</p>
    <div class="accent-bar__footer">Вход — через расслабление, а не через усилие</div>
  </div>
</div>
```

### Схемка 5: Чек-лист (Делай / Не делай)
Для сравнений, правильного и неправильного подхода, do/don't.
```html
<div class="slide__inner">
  <div class="checklist__heading">Практика — <em>без усилий</em></div>
  <div class="checklist__grid">
    <div class="checklist__col">
      <div class="checklist__col-label checklist__col-label--do">Делай</div>
      <div class="checklist__item"><span class="checklist__mark checklist__mark--do">&#x2713;</span>Просто ляг и включи практику</div>
      <div class="checklist__item"><span class="checklist__mark checklist__mark--do">&#x2713;</span>Дай себе 15 минут без телефона</div>
    </div>
    <div class="checklist__col">
      <div class="checklist__col-label checklist__col-label--dont">Не делай</div>
      <div class="checklist__item"><span class="checklist__mark checklist__mark--dont">&#x2717;</span>Ждать силы воли и «правильного» момента</div>
      <div class="checklist__item"><span class="checklist__mark checklist__mark--dont">&#x2717;</span>Превращать отдых в ещё одну задачу</div>
    </div>
  </div>
</div>
```

### Схемка 6: Три метрики
Для цифр, статистики, ключевых показателей. Цифры — Libre Baskerville italic, полупрозрачные.
```html
<div class="slide__inner">
  <div class="metrics__heading">Сколько это <em>на самом деле</em></div>
  <div class="metrics__row">
    <div class="metrics__item">
      <div class="metrics__number">15</div>
      <div class="metrics__label">минут</div>
      <div class="metrics__desc">Столько идёт практика.</div>
    </div>
    <div class="metrics__item">
      <div class="metrics__number">0</div>
      <div class="metrics__label">упражнений</div>
      <div class="metrics__desc">Всё — лёжа и слушая.</div>
    </div>
    <div class="metrics__item">
      <div class="metrics__number">1</div>
      <div class="metrics__label">вечер</div>
      <div class="metrics__desc">Чтобы попробовать сегодня.</div>
    </div>
  </div>
</div>
```

### Схемка 7: Вопрос-ответ
Для FAQ, частых вопросов, разбора сомнений. Знаки `?` — Libre Baskerville 28px italic.
```html
<div class="slide__inner">
  <div class="qa__heading">Почему у меня <em>не получается</em></div>
  <div class="qa__item">
    <div class="qa__question">Я визуализирую каждый день — где результат?</div>
    <div class="qa__answer">Мозг видит только то, что ему уже знакомо, и тянет тебя обратно в привычное болотце. Это не ты слабая — так устроен мозг.</div>
  </div>
  <div class="qa__item">
    <div class="qa__question">Мне что, придётся что-то делать телом?</div>
    <div class="qa__answer">Нет. Всё, что нужно, ты получаешь лёжа и слушая.</div>
  </div>
</div>
```

### Схемка 8: Формула
Для визуальных формул, уравнений (A + B = C). Серые блоки для компонентов, рамка цвета акцента для результата.
```html
<div class="slide__inner">
  <div class="formula__heading">Формула <em>метода</em></div>
  <div class="formula__row">
    <div class="formula__step">
      <div class="formula__step-title">Расслабленное тело</div>
      <div class="formula__step-text">Лёжа и слушая</div>
    </div>
    <div class="formula__arrow">+</div>
    <div class="formula__step">
      <div class="formula__step-title">Чувствование телом</div>
      <div class="formula__step-text">Прожить, а не представить</div>
    </div>
    <div class="formula__arrow">=</div>
    <div class="formula__result">
      <div class="formula__step-title">Другие выборы</div>
      <div class="formula__step-text">И другая жизнь</div>
    </div>
  </div>
  <p class="formula__note">Пока тело зажато, визуализация — это просто фантазии.</p>
</div>
```

---

## Полный CSS (копировать целиком)

```css
*, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }
:root {
  --bg: #FBF7F5; --text: #332A2E; --muted: #5C4F54; --muted-2: #7A6C71; --muted-3: #9B8D92; --faint: #C3B4BA;
  --accent: #9C5F6A; --accent-dark: #E3C2C9;
  --block: #F4ECEA; --card: #F7F1EF; --card-border: #E8DCD8; --tip: #EFE4E1; --line: #ECE1DE; --nav-line: #F1E8E5;
  --split: 60%;
}

@page {
  size: 1280px 720px;
  margin: 0;
}

body {
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
  background: var(--bg);
  color: var(--text);
  font-size: 17px;
  line-height: 1.75;
  -webkit-font-smoothing: antialiased;
}

.slide {
  width: 100%;
  height: 100vh;
  display: flex;
  flex-direction: column;
  page-break-after: always;
  position: relative;
  background: var(--bg);
}

.divider {
  position: absolute;
  top: 0;
  bottom: 0;
  left: var(--split);
  width: 1px;
  background: var(--line);
}

.nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 16px 48px;
  border-bottom: 1px solid var(--nav-line);
  background: var(--bg);
  z-index: 10;
  flex-shrink: 0;
  width: var(--split);
}
.nav__logo { text-decoration: none; display: flex; align-items: center; }
.nav__logo img { height: 30px; width: auto; }
.nav__mono {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-style: italic; font-size: 22px; line-height: 30px;
  color: var(--accent);
}
.nav__logo-name {
  font-family: 'DM Sans', sans-serif;
  font-size: 14px; font-weight: 400; font-style: italic;
  color: var(--muted-3); letter-spacing: 0.5px;
  margin-right: 8px;
}

.slide__body {
  flex: 1;
  display: flex;
  align-items: center;
  width: var(--split);
  padding: 0 48px;
}

.slide__inner {
  width: 100%;
  max-width: 580px;
}

/* ===== БАЗОВЫЕ ЭЛЕМЕНТЫ ===== */

.hero { padding: 0; }
.badge {
  display: inline-block; font-size: 11px; font-weight: 600;
  color: var(--accent); border: 1px solid var(--accent);
  padding: 5px 16px; margin-bottom: 20px;
  letter-spacing: 2px; text-transform: uppercase;
}
.hero h1 {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 36px; font-weight: 700; line-height: 1.25; margin-bottom: 16px;
}
.hero h1 em { font-style: italic; color: var(--accent); }
.hero__desc { font-size: 17px; color: var(--muted-2); line-height: 1.7; }
.hero__meta { font-size: 13px; color: var(--muted-3); margin-top: 16px; letter-spacing: 1px; }

.section-heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 28px; font-weight: 700; line-height: 1.3;
  padding: 0 0 20px;
}
.section-heading em { font-style: italic; color: var(--accent); }

.highlight { background: var(--block); padding: 18px 22px; margin: 20px 0; font-size: 15px; line-height: 1.75; color: var(--muted); }
.highlight strong { color: var(--text); }

.sub-heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 20px; font-weight: 700; padding: 24px 0 10px;
}

.text { font-size: 16px; color: var(--muted); line-height: 1.75; margin-bottom: 14px; }

.guide-list { list-style: none; margin: 12px 0 20px; }
.guide-list li {
  font-size: 15px; line-height: 1.7; color: var(--muted);
  padding: 6px 0 6px 18px; position: relative;
  border-bottom: 1px solid var(--nav-line);
}
.guide-list li:last-child { border-bottom: none; }
.guide-list li::before {
  content: ''; position: absolute; left: 0; top: 14px;
  width: 5px; height: 5px; border-radius: 50%; background: var(--accent);
}
.guide-list li strong { color: var(--text); }

.scenario-card { border: 1px solid var(--card-border); padding: 24px; margin: 18px 0; background: var(--card); }
.scenario-card__num {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-style: italic; font-size: 13px;
  color: var(--accent); letter-spacing: 1px; margin-bottom: 6px;
}
.scenario-card__title {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 18px; font-weight: 700; line-height: 1.4; margin-bottom: 16px;
}
.scenario-card__point { margin-bottom: 12px; }
.scenario-card__point-label { font-weight: 600; font-size: 15px; color: var(--text); }
.scenario-card__point-text { font-size: 14px; color: var(--muted-2); line-height: 1.7; }
.scenario-card__tip {
  background: var(--tip); padding: 12px 16px; margin-top: 14px;
  font-size: 13px; color: var(--muted); line-height: 1.65;
}
.scenario-card__tip strong { color: var(--accent); }

.footer-note {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 17px; font-style: italic; color: var(--muted);
  padding: 28px 0 0;
}
.footer-note em { color: var(--accent); }

/* ===== СХЕМКА 1: ЦИТАТА-АКЦЕНТ ===== */

.quote-slide__label {
  font-size: 11px; font-weight: 600; color: var(--muted-3);
  letter-spacing: 2px; text-transform: uppercase; margin-bottom: 28px;
}
.quote-slide__mark {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 80px; color: var(--accent); line-height: 0.5;
  margin-bottom: 16px; opacity: 0.3;
}
.quote-slide__text {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 24px; font-weight: 400; font-style: italic;
  line-height: 1.5; color: var(--text); max-width: 480px; margin-bottom: 28px;
}
.quote-slide__text em { color: var(--accent); }
.quote-slide__divider { width: 40px; height: 2px; background: var(--accent); margin-bottom: 20px; }
.quote-slide__source { font-size: 14px; color: var(--muted-3); line-height: 1.6; }

/* ===== СХЕМКА 2: ШАГИ С ЛИНИЕЙ ===== */

.steps__heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 28px; font-weight: 700; line-height: 1.3; margin-bottom: 32px;
}
.steps__heading em { font-style: italic; color: var(--accent); }
.steps__list { position: relative; padding-left: 32px; }
.steps__list::before {
  content: ''; position: absolute; left: 7px; top: 8px; bottom: 8px;
  width: 1px; background: var(--line);
}
.steps__item { position: relative; padding-bottom: 24px; }
.steps__item:last-child { padding-bottom: 0; }
.steps__dot {
  position: absolute; left: -32px; top: 4px;
  width: 15px; height: 15px; border: 2px solid var(--accent);
  background: var(--bg); border-radius: 50%;
}
.steps__item--active .steps__dot { background: var(--accent); }
.steps__item-title { font-weight: 600; font-size: 16px; color: var(--text); margin-bottom: 4px; }
.steps__item-text { font-size: 14px; color: var(--muted-2); line-height: 1.6; }

/* ===== СХЕМКА 3: НУМЕРОВАННЫЙ СПИСОК ===== */

.numlist__heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 28px; font-weight: 700; line-height: 1.3; margin-bottom: 32px;
}
.numlist__heading em { font-style: italic; color: var(--accent); }
.numlist__item {
  display: flex; gap: 24px; align-items: baseline;
  padding: 16px 0; border-bottom: 1px solid var(--nav-line);
}
.numlist__item:last-child { border-bottom: none; }
.numlist__num {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-style: italic; font-weight: 400;
  font-size: 36px; color: var(--accent); opacity: 0.3;
  min-width: 48px; text-align: right; line-height: 1; flex-shrink: 0;
}
.numlist__text { font-size: 15px; color: var(--text); line-height: 1.6; }
.numlist__text strong { font-weight: 600; }
.numlist__text span { color: var(--muted-2); }

/* ===== СХЕМКА 4: АКЦЕНТНАЯ ПОЛОСА СЛЕВА ===== */

.accent-bar__label {
  font-size: 11px; font-weight: 600; color: var(--muted-3);
  letter-spacing: 2px; text-transform: uppercase; margin-bottom: 24px;
}
.accent-bar__block { border-left: 3px solid var(--accent); padding-left: 28px; }
.accent-bar__title {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 26px; font-weight: 700; line-height: 1.35; margin-bottom: 16px;
}
.accent-bar__title em { font-style: italic; color: var(--accent); }
.accent-bar__text { font-size: 15px; color: var(--muted); line-height: 1.75; margin-bottom: 20px; }
.accent-bar__footer {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 15px; font-style: italic; color: var(--muted-3);
  padding-top: 16px; border-top: 1px solid var(--nav-line);
}

/* ===== СХЕМКА 5: ЧЕК-ЛИСТ ===== */

.checklist__heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 28px; font-weight: 700; line-height: 1.3; margin-bottom: 28px;
}
.checklist__heading em { font-style: italic; color: var(--accent); }
.checklist__grid { display: grid; grid-template-columns: 1fr 1fr; gap: 0; }
.checklist__col-label {
  font-size: 11px; font-weight: 600; letter-spacing: 1.5px;
  text-transform: uppercase; padding-bottom: 14px; margin-bottom: 10px;
  border-bottom: 1px solid var(--line);
}
.checklist__col-label--do { color: var(--accent); }
.checklist__col-label--dont { color: var(--muted-3); }
.checklist__col:first-child { padding-right: 20px; border-right: 1px solid var(--nav-line); }
.checklist__col:last-child { padding-left: 20px; }
.checklist__item {
  display: flex; gap: 10px; padding: 8px 0;
  font-size: 14px; color: var(--muted); line-height: 1.6; align-items: baseline;
}
.checklist__mark { flex-shrink: 0; font-size: 14px; font-weight: 700; width: 16px; }
.checklist__mark--do { color: var(--accent); }
.checklist__mark--dont { color: var(--faint); }

/* ===== СХЕМКА 6: ТРИ МЕТРИКИ ===== */

.metrics__heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 28px; font-weight: 700; line-height: 1.3; margin-bottom: 32px;
}
.metrics__heading em { font-style: italic; color: var(--accent); }
.metrics__row { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 0; }
.metrics__item {
  text-align: center; padding: 24px 12px;
  border-right: 1px solid var(--nav-line);
}
.metrics__item:last-child { border-right: none; }
.metrics__number {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-style: italic; font-weight: 400;
  font-size: 48px; color: var(--accent); opacity: 0.3;
  line-height: 1; margin-bottom: 8px;
}
.metrics__label {
  font-size: 12px; color: var(--muted-3); text-transform: uppercase;
  letter-spacing: 1px; margin-bottom: 8px;
}
.metrics__desc { font-size: 13px; color: var(--muted-2); line-height: 1.5; }

/* ===== СХЕМКА 7: ВОПРОС-ОТВЕТ ===== */

.qa__heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 28px; font-weight: 700; line-height: 1.3; margin-bottom: 28px;
}
.qa__heading em { font-style: italic; color: var(--accent); }
.qa__item { margin-bottom: 24px; }
.qa__question {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 17px; font-style: italic; color: var(--accent);
  margin-bottom: 8px; padding-left: 32px; position: relative;
}
.qa__question::before {
  content: '?'; position: absolute; left: 0; top: -4px;
  font-family: 'Libre Baskerville', Georgia, serif;
  font-style: italic; font-weight: 400;
  font-size: 28px; color: var(--accent); opacity: 0.3;
}
.qa__answer {
  font-size: 15px; color: var(--muted); line-height: 1.7;
  padding-left: 32px; border-left: 1px solid var(--line);
}

/* ===== СХЕМКА 8: ФОРМУЛА ===== */

.formula__heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 28px; font-weight: 700; line-height: 1.3; margin-bottom: 28px;
}
.formula__heading em { font-style: italic; color: var(--accent); }
.formula__row {
  display: flex; align-items: center; gap: 16px; margin-bottom: 32px;
}
.formula__step {
  flex: 1; background: var(--block); padding: 18px 16px; text-align: center;
}
.formula__step-title {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 15px; font-weight: 700; margin-bottom: 4px;
}
.formula__step-text { font-size: 12px; color: var(--muted-2); line-height: 1.5; }
.formula__arrow { color: var(--accent); font-size: 18px; flex-shrink: 0; opacity: 0.5; }
.formula__result {
  border: 1px solid var(--accent); padding: 18px 16px; text-align: center; flex: 1;
}
.formula__result .formula__step-title { color: var(--accent); }
.formula__note { font-size: 14px; color: var(--muted-3); font-style: italic; margin-top: 8px; }

/* ===== АДАПТИВ ===== */

@media print {
  html, body { width: 1280px; }
  .slide {
    width: 1280px; height: 720px;
    page-break-after: always; page-break-inside: avoid;
  }
  .slide:last-child { page-break-after: auto; }
  body { -webkit-print-color-adjust: exact; print-color-adjust: exact; }
}

/* ВАЖНО: только screen — иначе правило течёт в print/PDF и ломает 60/40 split (навбар на всю ширину, исчезает разделитель и правая зона под видео) */
@media screen and (max-width: 768px) {
  .nav { padding: 16px 20px; width: 100%; }
  .hero h1 { font-size: 26px; }
  .section-heading { font-size: 22px; }
  .slide__body { width: 100%; padding: 0 20px; }
  .divider { display: none; }
}
```

## Шаблон HTML-слайда

```html
<!-- Титульный слайд -->
<div class="slide">
<div class="divider"></div>
<nav class="nav">
  <a class="nav__logo" href="#"><span class="nav__mono">Ц</span></a>
  <span class="nav__logo-name">the.tsarevna</span>
</nav>
<div class="slide__body">
  <div class="slide__inner">
    <div class="hero">
      <div class="badge">УРОК</div>
      <h1>Почему твои визуализации <em>не работают</em></h1>
      <p class="hero__desc">Пока тело зажато, визуализация — это просто фантазии.</p>
      <p class="hero__meta">ТЕЛО &middot; ЧУВСТВОВАНИЕ &middot; 15 МИНУТ</p>
    </div>
  </div>
</div>
</div>

<!-- Контентный слайд -->
<div class="slide">
<div class="divider"></div>
<nav class="nav">
  <a class="nav__logo" href="#"><span class="nav__mono">Ц</span></a>
  <span class="nav__logo-name">the.tsarevna</span>
</nav>
<div class="slide__body">
  <div class="slide__inner">
    <h2 class="section-heading">Тебя не сломали — <em>тебя зажали</em></h2>
    <p class="text">Текст слайда.</p>
  </div>
</div>
</div>
```

## Как использовать

1. Получи текст/тему от Алены
2. Разбей на логические слайды (один экран = одна мысль)
3. Первый слайд — титульный с бейджем, заголовком, описанием
4. Остальные слайды — чередуй базовые и схемки:
   - **Цитата** — для ключевых мыслей и выводов
   - **Шаги** — для процессов и последовательностей
   - **Нумерованный список** — для структур и анатомий
   - **Акцентная полоса** — для главных правил и принципов
   - **Чек-лист** — для сравнений (делай / не делай)
   - **Метрики** — для цифр и статистики
   - **Вопрос-ответ** — для FAQ и разбора сомнений
   - **Формула** — для визуальных уравнений (A + B = C)
5. Каждый 2–3-й слайд должен быть схемкой — так интереснее смотреть
6. Не перегружай слайд — контент должен поместиться в 60% экрана по центру
7. Сохрани как `index.html` в `~/Desktop/алена/презентации/<slug>/`

## Экспорт в PDF

Генерировать строго с размером страницы 1280×720px (16:9), иначе вёрстка ломается:

```bash
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless --disable-gpu \
  --no-pdf-header-footer --print-to-pdf="presentation.pdf" --no-margins \
  --paper-width=13.333 --paper-height=7.5 "file://$(pwd)/index.html"
```

(13.333×7.5 дюйма = 1280×720px при 96dpi.)

**ОБЯЗАТЕЛЬНО проверить сам PDF в print-режиме, а не скриншот экрана** (на экране баг не виден):

```bash
sips -s format png presentation.pdf --out _check.png   # стр. 1
```

Посмотреть глазами: есть ли вертикальный разделитель на 60%, пустые ли правые 40% под видео, стоит ли ник у разделителя (а не у правого края), тёплый ли фон (не белый). После проверки удалить `_check.png`.
