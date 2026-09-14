---
name: guide
description: Создаёт HTML-гайд, статью, чек-лист или лендинг гайда в фирменном стиле Алены (пудрово-розовый фон, Libre Baskerville + Inter, акценты пыльной розы). Вызывай, когда Алена просит оформить текст как гайд/статью/чек-лист/лендинг.
---

# Скилл: Оформление текста в фирменный гайд Алены

## 0. Перед началом
1. Прочитай `~/.claude/brand/PROFILE.md` и `~/.claude/brand/TOV-SAMPLES.md` — голос, темы, границы.
2. Прочитай `~/.claude/brand/style-guide.md` — палитра и правила вёрстки. Ник в навбаре — `the.tsarevna`, монограмма — `Ц`.
3. Если у Алены уже есть логотип (`~/.claude/brand/logo-alena.png`) — используй его вместо монограммы (см. «Навбар»).
4. Три правила из шапки распаковки — явно: она НЕ тренер (никаких упражнений/осанки — всё человек получает лёжа и слушая); про путь к финансовой независимости пока не говорим; слово «состояние» заменять на «чувствование телом» / «ощущения в теле».
5. Границы из раздела 4 PROFILE.md абсолютны: закрытые темы (суммы дохода, отец, прошлые отношения, личное про мужа и т.д.) в гайдах не появляются, даже как пример.
6. Фильтр доказательной папки: никаких «вылечу», «уберу боль», «исцеление», гарантий и сроков; исполнение желаний — только от первого лица («у меня это работает так»).

Когда Алена просит оформить текст как гайд, статью, чек-лист, обучающий материал или лендинг — создай HTML-страницу в её фирменном стиле.

## Бренд-стиль

### Цвета (из `~/.claude/brand/style-guide.md`)
- Фон: `#FBF7F5` (тёплый пудрово-белый)
- Текст: `#332A2E` (тёмный тёпло-графитовый с розовым подтоном)
- Текст второстепенный: `#5C4F54`, `#7A6C71`, `#9B8D92`
- Акцент (пыльная роза): `#9C5F6A` — используется для: курсивных выделений в заголовках, нумерации, точек в списках, бейджей, заголовка промт-блока, кнопок
- Серые блоки: `#F4ECEA` — без закруглений, без цветных линий слева
- Карточки: `#F7F1EF` с рамкой `#E8DCD8` — квадратные углы
- Советы внутри карточек: `#EFE4E1` — квадратные углы
- Линии-разделители: `#ECE1DE`, тонкие линии навбара и списков: `#F1E8E5`
- Тёмный фон (если нужен): `#332A2E`, на нём акцент — только `#E3C2C9` (светлая пудровая роза)

### Шрифты (Google Fonts)
```html
<link href="https://fonts.googleapis.com/css2?family=Libre+Baskerville:ital,wght@0,400;0,700;1,400&family=Inter:wght@400;500;600;700;800&family=DM+Sans:ital@1&display=swap" rel="stylesheet">
```
- **Заголовки**: `Libre Baskerville`, Georgia, serif — жирный, с курсивными акцентами цветом пыльной розы
- **Основной текст**: `Inter`, sans-serif — 17px, line-height 1.75
- **Подзаголовки**: `Libre Baskerville` — 22px, жирный
- **Нумерация**: `Libre Baskerville` — курсив, цвет акцента

### Навбар
- Sticky, фон `#FBF7F5`, тонкая линия снизу `#F1E8E5`
- **Слева** — монограмма: `<span class="nav__mono">Ц</span>` (Libre Baskerville, italic, 22px, цвет акцента) — «Ц» от «Царевна»
- **Справа** — ник курсивом: `<span class="nav__logo-name">the.tsarevna</span>` (DM Sans, italic, `#9B8D92`)
- `justify-content: space-between` — монограмма и ник на разных краях
- Когда появится логотип `~/.claude/brand/logo-alena.png` — скопируй его в папку гайда как `logo.png` и замени монограмму на `<img src="logo.png" alt="Ц">` высотой 30px

### Бейдж
- Тонкая рамка 1px цвета акцента, текст капсом с разрядкой, размер 11px
- Текст бейджа зависит от контента: «ГАЙД», «УРОК», «СТАТЬЯ», «ЧЕК-ЛИСТ», «МАТЕРИАЛ»

## Структура страницы

```
1. Навбар (sticky): монограмма Ц слева, ник справа
2. Hero: бейдж + заголовок h1 (с курсивным акцентом) + описание + мета-инфо
3. Intro: жирный тезис + обычный текст
4. Секции (01. 02. 03...): заголовок с нумерацией + контент
5. Внутри секций:
   - Серые блоки .highlight — для ключевых определений
   - Списки .guide-list — с точками цвета акцента
   - Промт-блоки .prompt-box — серый фон, заголовок цветом акцента
   - Нумерованные списки .headline-list — курсивная нумерация
   - Карточки .scenario-card — для сценариев/кейсов/уроков
   - Чек-листы .check-list — квадратные чекбоксы
6. Футер: © год · <ник> · Все права защищены
```

## Правила оформления

1. **Заголовки секций**: `<h2>` с нумерацией `<span>01.</span>` (пыльная роза) + курсивное слово `<em>` (пыльная роза)
2. **Подзаголовки**: `<h3>` в Libre Baskerville
3. **Серые блоки**: только `background: var(--block)` — БЕЗ закруглений, БЕЗ цветных линий слева
4. **Карточки**: квадратные углы, рамка `var(--card-border)`, фон `var(--card)`
5. **Советы**: фон `var(--tip)`, квадратные углы, слово «Совет:» цветом акцента
6. **Промт-блоки**: светлый фон `var(--block)` (НЕ тёмный), заголовок цветом акцента
7. **На тёмном фоне НИКОГДА не использовать пыльную розу `#9C5F6A`** — она теряется. Вместо неё `#E3C2C9`
8. **Адаптивность**: контейнер 740px, на мобильных — уменьшать шрифты
9. **Claude и reels** — слова «клод» и «рилс» ВСЕГДА пишутся латиницей: **Claude** и **reels** (reels — с маленькой буквы). Никогда кириллицей.
10. **Голос** — по разделу 8 PROFILE.md: к читательнице на «ты», женский род, длинные предложения через «и»/«потому что» при коротких строках, самоирония только на себя, «проги» вместо терминов, без «Вселенной», без «состояния» как термина, без инфобиз-лексики. Заголовки — как её фразы: «Тебя не сломали — *тебя зажали*».

## Как использовать

1. Получи текст от Алены
2. Разбей на логические секции с нумерацией 01, 02, 03...
3. Определи тип контента: списки → `.guide-list`, определения → `.highlight`, пошаговые инструкции → карточки `.scenario-card`, промты → `.prompt-box`, то, что нужно отмечать по ходу → `.check-list`, страница-обёртка с кнопками → «Лендинг гайда»
4. Собери HTML по шаблону ниже (CSS копируй целиком)
5. Сохрани как `~/Desktop/алена/гайды/<slug>/index.html` (slug — латиницей, через дефис: `vizualizacii`, `telo-bolotce`). Картинки — в ту же папку
6. Предложи Алене опубликовать на её GitHub Pages: репозиторий `<её-логин>.github.io` (или отдельный репозиторий с Pages), папка `guides/<slug>/index.html` → адрес `https://<её-логин>.github.io/guides/<slug>/`. Публиковать — только после её «да»

## Шаблон HTML

```html
<!doctype html>
<html lang="ru">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Название гайда</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Libre+Baskerville:ital,wght@0,400;0,700;1,400&family=Inter:wght@400;500;600;700;800&family=DM+Sans:ital@1&display=swap" rel="stylesheet">
<style>/* полный CSS ниже */</style>
</head>
<body>
<nav class="nav">
  <a class="nav__logo" href="#"><span class="nav__mono">Ц</span></a>
  <span class="nav__logo-name">the.tsarevna</span>
</nav>
<div class="container">
  <header class="hero">
    <div class="badge">Гайд</div>
    <h1>Почему твои визуализации <em>не работают</em></h1>
    <p class="hero__desc">Пока тело зажато, визуализация — это просто фантазии. Гайд о том, как перестать хотеть головой и начать чувствовать телом.</p>
    <p class="hero__meta">15 МИНУТ ЧТЕНИЯ &middot; ЛЁЖА И СЛУШАЯ</p>
  </header>

  <p class="intro-bold">Ничего не надо делать. Надо перестать делать.</p>
  <p class="intro-text">Здесь — объяснение без магии: почему мозг тянет тебя в привычное болотце и что с этим можно сделать за 15 минут, лёжа.</p>

  <h2 class="section-heading"><span>01.</span> Мозг тянет тебя в привычное <em>болотце</em></h2>
  <div class="highlight"><strong>Чувствование телом</strong> — это не картинка в голове. Это прожить желаемое телом: лечь, послушать и дать телу вспомнить, как это — когда хорошо.</div>
  <ul class="guide-list">
    <li><strong>Мозг видит только знакомое.</strong> Поэтому ты выбираешь одно и то же, пока внутри работает старая прога.</li>
    <li><strong>Тело — это язык.</strong> Не спорт и не осанка: всё, что нужно, ты получаешь лёжа и слушая.</li>
  </ul>

  <p class="footer-note">Из железной леди — <em>обратно в живую женщину</em>.</p>
</div>
<footer class="footer">&copy; 2026 &middot; the.tsarevna &middot; Все права защищены</footer>
</body>
</html>
```

## Чек-лист (вариант оформления)

Для материалов, которые нужно отмечать по ходу: «что сделать до вечерней практики», «проверь, когда день прошёл на автопилоте». Бейдж — «ЧЕК-ЛИСТ». Чекбоксы — квадратные, рамка цвета акцента, без скруглений. Пункт можно пометить как уже выполненный классом `is-done` (заливка акцентом + галочка).

```html
<h2 class="section-heading"><span>02.</span> Перед вечерней <em>практикой</em></h2>
<ul class="check-list">
  <li>Выбрала один вечер на этой неделе — и не «когда будет время»</li>
  <li>Отложила телефон и легла — ничего делать не нужно</li>
  <li class="is-done">Разрешила себе 15 минут просто слушать</li>
  <li>Заметила, где в теле было напряжение и что стало после</li>
</ul>
```

Правила: одна мысль на пункт, начинать с глагола в женском роде прошедшего времени («выбрала», «легла») или с инфинитива — но не смешивать в одном списке. В конце чек-листа — одна сильная строка `.footer-note`.

## Лендинг гайда

Одностраничная обёртка: hero с кнопками + 2–3 коротких блока «что внутри» + финальная кнопка. Используется, когда гайд отдаётся по кнопке (ссылка на аудиопрактику, Telegram, другой гайд) или как страница-вход.

Кнопки — квадратные, две вариации:
- `.btn` — основная: фон акцента `#9C5F6A`, белый текст
- `.btn.btn--secondary` — вторичная: прозрачный фон, рамка 1px акцента, текст акцентом

```html
<header class="hero hero--landing">
  <div class="badge">Гайд</div>
  <h1>Тебя не сломали — <em>тебя зажали</em></h1>
  <p class="hero__desc">Гайд о том, почему тело держит тебя на автопилоте и как выйти — лёжа и слушая, без усилий и дисциплины.</p>
  <div class="hero__actions">
    <a class="btn" href="#">Забрать гайд</a>
    <a class="btn btn--secondary" href="#">Читать онлайн</a>
  </div>
  <p class="hero__meta">БЕСПЛАТНО &middot; 12 СТРАНИЦ &middot; ЧИТАТЬ 10 МИНУТ</p>
</header>

<div class="landing-grid">
  <div class="landing-card">
    <div class="landing-card__num">01.</div>
    <div class="landing-card__title">Куда прячутся эмоции</div>
    <p class="landing-card__text">Почему плечи у ушей и шея болит не от подушки.</p>
  </div>
  <div class="landing-card">
    <div class="landing-card__num">02.</div>
    <div class="landing-card__title">Привычное болотце</div>
    <p class="landing-card__text">Мозг видит только знакомое — и тянет обратно. Так устроен мозг, а не ты слабая.</p>
  </div>
  <div class="landing-card">
    <div class="landing-card__num">03.</div>
    <div class="landing-card__title">15 минут лёжа</div>
    <p class="landing-card__text">Практика, после которой легче прямо сейчас. Ничего делать не нужно.</p>
  </div>
</div>

<div class="cta">
  <p class="cta__text">Чинить нечего. <em>С тобой всё в порядке.</em></p>
  <a class="btn" href="#">Забрать гайд</a>
</div>
```

Правила лендинга: одна главная кнопка на экран (вторичная — рядом, не третья), ссылки — реальные (Telegram, файл, другой гайд), текст кнопки — глагол («Забрать», «Читать», «Открыть»), никаких «Ворваться» и «Залетай».

## Полный CSS (копировать целиком)

```css
*, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }
:root {
  --bg: #FBF7F5; --text: #332A2E; --muted: #5C4F54; --muted-2: #7A6C71; --muted-3: #9B8D92; --faint: #C3B4BA;
  --accent: #9C5F6A; --accent-dark: #E3C2C9;
  --block: #F4ECEA; --card: #F7F1EF; --card-border: #E8DCD8; --tip: #EFE4E1; --line: #ECE1DE; --nav-line: #F1E8E5;
}

body {
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
  background: var(--bg);
  color: var(--text);
  font-size: 17px;
  line-height: 1.75;
  -webkit-font-smoothing: antialiased;
}

.nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 16px 48px;
  border-bottom: 1px solid var(--nav-line);
  position: sticky;
  top: 0;
  background: var(--bg);
  z-index: 100;
}
.nav__logo {
  text-decoration: none;
  display: flex;
  align-items: center;
}
.nav__logo img { height: 30px; width: auto; }
.nav__mono {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-style: italic;
  font-size: 22px;
  line-height: 30px;
  color: var(--accent);
}
.nav__logo-name {
  font-family: 'DM Sans', sans-serif;
  font-size: 14px;
  font-weight: 400;
  font-style: italic;
  color: var(--muted-3);
  letter-spacing: 0.5px;
}

.container { max-width: 740px; margin: 0 auto; padding: 0 24px; }

.hero { padding: 60px 0 48px; }
.badge {
  display: inline-block;
  font-size: 11px;
  font-weight: 600;
  color: var(--accent);
  border: 1px solid var(--accent);
  padding: 5px 16px;
  margin-bottom: 20px;
  letter-spacing: 2px;
  text-transform: uppercase;
}
.hero h1 {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 38px;
  font-weight: 700;
  line-height: 1.25;
  margin-bottom: 16px;
}
.hero h1 em { font-style: italic; color: var(--accent); }
.hero__desc { font-size: 18px; color: var(--muted-2); line-height: 1.7; }
.hero__meta { font-size: 14px; color: var(--muted-3); margin-top: 16px; letter-spacing: 1px; }

.intro-bold {
  font-size: 18px;
  font-weight: 700;
  line-height: 1.65;
  color: var(--text);
  padding: 40px 0 16px;
}
.intro-text {
  font-size: 17px;
  color: var(--muted);
  line-height: 1.75;
  padding-bottom: 48px;
}

.section-heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 30px;
  font-weight: 700;
  line-height: 1.3;
  padding: 56px 0 24px;
  border-top: 1px solid var(--line);
}
.section-heading span { color: var(--accent); margin-right: 8px; }
.section-heading em { font-style: italic; color: var(--accent); }

.highlight {
  background: var(--block);
  padding: 20px 24px;
  margin: 24px 0;
  font-size: 16px;
  line-height: 1.75;
  color: var(--muted);
}
.highlight strong { color: var(--text); }

.sub-heading {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 22px;
  font-weight: 700;
  padding: 36px 0 16px;
}

.text { font-size: 17px; color: var(--muted); line-height: 1.75; margin-bottom: 16px; }

.guide-list { list-style: none; margin: 16px 0 24px; }
.guide-list li {
  font-size: 16px; line-height: 1.75; color: var(--muted);
  padding: 8px 0 8px 20px; position: relative;
  border-bottom: 1px solid var(--nav-line);
}
.guide-list li:last-child { border-bottom: none; }
.guide-list li::before {
  content: ''; position: absolute; left: 0; top: 16px;
  width: 6px; height: 6px; border-radius: 50%; background: var(--accent);
}
.guide-list li strong { color: var(--text); }

.prompt-box {
  background: var(--block);
  padding: 36px;
  margin: 32px 0;
}
.prompt-box__title {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 20px; font-weight: 700;
  color: var(--accent);
  margin-bottom: 6px;
}
.prompt-box__subtitle { font-size: 13px; color: var(--muted-3); margin-bottom: 20px; }
.prompt-box__text { font-size: 15px; line-height: 1.8; color: var(--muted); }

.headline-list { list-style: none; margin: 16px 0 32px; }
.headline-list li {
  display: flex; gap: 16px; padding: 16px 0;
  border-bottom: 1px solid var(--nav-line); align-items: baseline;
}
.headline-list li:first-child { border-top: 1px solid var(--nav-line); }
.headline-num {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-style: italic; font-size: 15px;
  color: var(--accent); min-width: 28px; flex-shrink: 0;
}
.headline-text { font-size: 17px; line-height: 1.6; color: var(--text); font-weight: 500; }

.scenario-card {
  border: 1px solid var(--card-border);
  padding: 32px; margin: 24px 0; background: var(--card);
}
.scenario-card__num {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-style: italic; font-size: 14px;
  color: var(--accent); letter-spacing: 1px; margin-bottom: 8px;
}
.scenario-card__title {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 20px; font-weight: 700; line-height: 1.4; margin-bottom: 20px;
}
.scenario-card__point { margin-bottom: 14px; }
.scenario-card__point-label { font-weight: 600; font-size: 16px; color: var(--text); }
.scenario-card__point-text { font-size: 15px; color: var(--muted-2); line-height: 1.7; }
.scenario-card__ending {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 17px; font-style: italic; color: var(--text);
  padding-top: 16px; margin-top: 16px; border-top: 1px solid var(--card-border);
}
.scenario-card__tip {
  background: var(--tip); padding: 14px 18px; margin-top: 16px;
  font-size: 14px; color: var(--muted); line-height: 1.65;
}
.scenario-card__tip strong { color: var(--accent); }

/* ===== ЧЕК-ЛИСТ ===== */
.check-list { list-style: none; margin: 16px 0 32px; }
.check-list li {
  font-size: 16px; line-height: 1.75; color: var(--text);
  padding: 12px 0 12px 36px; position: relative;
  border-bottom: 1px solid var(--nav-line);
}
.check-list li:last-child { border-bottom: none; }
.check-list li::before {
  content: ''; position: absolute; left: 0; top: 17px;
  width: 16px; height: 16px;
  border: 1.5px solid var(--accent); background: var(--bg);
}
.check-list li.is-done { color: var(--muted-2); }
.check-list li.is-done::before { background: var(--accent); }
.check-list li.is-done::after {
  content: ''; position: absolute; left: 5px; top: 20px;
  width: 5px; height: 9px;
  border-right: 2px solid var(--bg); border-bottom: 2px solid var(--bg);
  transform: rotate(45deg);
}

/* ===== ЛЕНДИНГ: КНОПКИ, HERO, КАРТОЧКИ, CTA ===== */
.btn {
  display: inline-block;
  font-family: 'Inter', sans-serif;
  font-size: 14px; font-weight: 600;
  letter-spacing: 1px; text-transform: uppercase;
  text-decoration: none;
  padding: 14px 28px;
  background: var(--accent); color: #fff;
  border: 1px solid var(--accent);
  transition: background .15s ease;
}
.btn:hover { background: #84505A; border-color: #84505A; }
.btn--secondary { background: transparent; color: var(--accent); }
.btn--secondary:hover { background: var(--block); border-color: var(--accent); }

.hero--landing { padding: 80px 0 56px; }
.hero--landing h1 { font-size: 44px; }
.hero__actions { display: flex; gap: 12px; flex-wrap: wrap; margin-top: 28px; }

.landing-grid {
  display: grid; grid-template-columns: repeat(3, 1fr); gap: 16px;
  margin: 24px 0 48px;
}
.landing-card { background: var(--card); border: 1px solid var(--card-border); padding: 24px; }
.landing-card__num {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-style: italic; font-size: 14px; color: var(--accent); margin-bottom: 10px;
}
.landing-card__title {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 17px; font-weight: 700; line-height: 1.4; margin-bottom: 10px;
}
.landing-card__text { font-size: 14px; color: var(--muted-2); line-height: 1.65; }

.cta {
  background: var(--block); padding: 48px 32px; margin: 48px 0 0; text-align: center;
}
.cta__text {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 22px; font-style: italic; color: var(--text); margin-bottom: 24px; line-height: 1.5;
}
.cta__text em { color: var(--accent); }

.footer {
  text-align: center; padding: 64px 24px;
  border-top: 1px solid var(--line); margin-top: 64px;
  color: var(--muted-3); font-size: 14px;
}
.footer .tiny {
  font-size: 12.5px; color: var(--faint); max-width: 52ch;
  margin: 12px auto 0; line-height: 1.6; letter-spacing: 0;
}
.footer-note {
  font-family: 'Libre Baskerville', Georgia, serif;
  font-size: 18px; font-style: italic; color: var(--muted);
  text-align: center; padding: 48px 24px 0;
}
.footer-note em { color: var(--accent); }

/* только screen — чтобы мобильные правила не текли в print/PDF */
@media screen and (max-width: 768px) {
  .nav { padding: 16px 20px; }
  .hero h1, .hero--landing h1 { font-size: 28px; }
  .section-heading { font-size: 24px; }
  .scenario-card { padding: 20px; }
  .prompt-box { padding: 24px; }
  .landing-grid { grid-template-columns: 1fr; }
  .hero__actions .btn { width: 100%; text-align: center; }
}
```
