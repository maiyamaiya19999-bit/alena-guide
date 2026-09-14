---
name: carousel
description: Создаёт карусель для Instagram (1080×1350, PNG) в фирменном стиле Алены (пудрово-розовый фон, Libre Baskerville + Inter, акценты пыльной розы) — HTML-слайды + рендер через headless Chrome. Вызывай, когда Алена просит карусель.
---

# Скилл: Карусель Алены (1080×1350)

## 0. Перед началом
1. Прочитай `~/.claude/brand/PROFILE.md` и `~/.claude/brand/TOV-SAMPLES.md` — голос, темы, границы.
2. Прочитай `~/.claude/brand/style-guide.md` — палитра и правила вёрстки. Ник — `the.tsarevna` (в навбаре) и `@the.tsarevna` (в футере), монограмма — `Ц`.
3. Если появился логотип `~/.claude/brand/logo-alena.png` — скопируй в папку карусели как `logo.png` и используй вместо монограммы (высота 46px).
4. Три правила из шапки распаковки — явно: она НЕ тренер (никаких упражнений/осанки — всё лёжа и слушая, ни в тексте, ни на фото); про финансовую независимость пока не говорим; слово «состояние» → «чувствование телом» / «ощущения в теле».
5. Границы из раздела 4 PROFILE.md абсолютны: закрытые темы (суммы дохода, отец, прошлые отношения, личное про мужа и т.д.) в карусели не появляются ни в тексте, ни на фото. Фильтр доказательной папки: без «вылечу», «уберу боль», гарантий и сроков.
6. Спроси Алену одним вопросом, если чего-то нет: фото для обложки, скрины, кодовое слово для призыва.

Когда Алена просит сделать карусель — сгенерируй HTML-слайды 1080×1350 в ФИРМЕННОМ стиле (тот же, что гайды/лендинги/презентации) и отрендери в PNG через headless Chrome. Полный шаблон слайда — ниже.

## Дизайн — фирменный стиль, как в гайдах

- Фон `#FBF7F5`, текст `#332A2E`, второстепенный `#5C4F54`/`#7A6C71`
- **Заголовки**: Libre Baskerville 700, 50–58px, курсивные акценты `<em>` пыльной розой `#9C5F6A`
- **Текст**: Inter, 29px, line-height 1.72
- Серые блоки `#F4ECEA`, квадратные углы, БЕЗ border-radius
- **Навбар на каждом слайде**: монограмма `Ц` слева (Libre Baskerville italic 34px, цвет акцента) + *ник* справа (DM Sans italic 25px `#9B8D92`), линия снизу `#F1E8E5`
- **Футер на каждом слайде**: линия сверху `#F1E8E5`, слева `@the.tsarevna` (DM Sans italic `#9B8D92`), справа *листай →* (Libre Baskerville italic, цвет акцента); на последнем слайде — *жду в комментариях →*
- Бейдж на обложке: рамка 1px цвета акцента, капс, letter-spacing 4px («ТЕЛО», «ГАЙД», «ОБЪЯСНЕНИЕ»…)
- Декоративные цифры шагов: Libre Baskerville italic, ~230px, цвет акцента, opacity .15, абсолютно справа сверху
- Лейблы («ШАГ 1», «ГЛАВНОЕ»): Inter 600, 19px, капс, letter-spacing 4px, `#9B8D92`
- Цитаты/промты: серый блок `#F4ECEA` + текст Libre Baskerville italic цветом акцента
- Фото: «полароид» — рамка padding 16px, фон `#FFFCFB`, border `#E8DCD8`, тень, наклон -2°; стикеры PNG поверх с drop-shadow и поворотом
- Скрины: карточка border `#E8DCD8` + padding 16px + лёгкая тень; высокий скрин — контейнер `flex:1 1 0; min-height:0; overflow:hidden` (обрезка снизу)
- Схемки-вариации из скилла презентаций работают и тут: цитата-акцент (кавычка 150px opacity .3 + LB italic 46px), акцентная полоса слева 3px цвета акцента, команда в рамке цвета акцента (`/post` + курсор)
- На тёмном фоне (если слайд тёмный `#332A2E`) акцент только `#E3C2C9`
- Слова Claude и reels — всегда латиницей
- Голос — по разделу 8 PROFILE.md: на «ты», женский род, длинные предложения через «и»/«потому что» при коротких строках, одна мысль на слайд, финал — одна сильная строка

## Структура типовой карусели

1. Обложка: бейдж + h1 с `<em>` цвета акцента + подзаголовок + фото Алёны крупным планом или честный скрин/цитата, если фото не дано. Не подменять её формат faceless-визуалом и не использовать асаны, коврики и спортивную форму.
2. Крючок/введение
3–5. Шаги: лейбл «ШАГ N» + гигантская цифра + заголовок + текст; скрины по смыслу
6. Перелом «главное»: акцентная полоса слева
7. Результат (команда/формула)
8. Вывод: схемка-цитата
9. Призыв: плашка с кодовым словом (рамка цвета акцента, letter-spacing 7px) + скрин ТГ-канала (обрезан снизу)

Пример обложки в её теме: бейдж «ТЕЛО», h1 «Почему твои визуализации не работают — *и при чём тут тело*», подзаголовок «Объяснение без магии. Дочитай — станет понятнее». Шаг 1: «Ложишься и включаешь практику на *15 минут*» + серый блок «Ничего не надо делать — надо перестать делать». Вывод-цитата: «Пока тело зажато, визуализация — *это просто фантазии.*»

## Шаблон слайда (копировать целиком)

```html
<!doctype html><html><head><meta charset="utf-8">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Libre+Baskerville:ital,wght@0,400;0,700;1,400&family=Inter:wght@400;500;600;700;800&family=DM+Sans:ital@1&display=swap" rel="stylesheet">
<style>
*{margin:0;padding:0;box-sizing:border-box}
:root{--bg:#FBF7F5;--text:#332A2E;--muted:#5C4F54;--muted-2:#7A6C71;--muted-3:#9B8D92;
  --accent:#9C5F6A;--accent-dark:#E3C2C9;--block:#F4ECEA;--card:#F7F1EF;--card-border:#E8DCD8;--line:#ECE1DE;--nav-line:#F1E8E5}
html,body{width:1080px;height:1350px;overflow:hidden}
.canvas{width:1080px;height:1350px;position:relative;overflow:hidden;display:flex;flex-direction:column;
  font-family:'Inter',sans-serif;background:var(--bg);color:var(--text);-webkit-font-smoothing:antialiased}
.nav{flex:0 0 auto;display:flex;align-items:center;justify-content:space-between;
  padding:46px 90px 34px;border-bottom:1px solid var(--nav-line)}
.nav img{height:46px;width:auto;display:block}
.nav .mono{font-family:'Libre Baskerville',Georgia,serif;font-style:italic;font-size:34px;line-height:46px;color:var(--accent)}
.nav .name{font-family:'DM Sans',sans-serif;font-style:italic;font-size:25px;color:var(--muted-3);letter-spacing:.5px}
.frame{flex:1 1 auto;min-height:0;display:flex;flex-direction:column;padding:0 100px}
.content{flex:1 1 auto;min-height:0;display:flex;flex-direction:column;justify-content:center;position:relative}
.footer{flex:0 0 auto;display:flex;align-items:center;justify-content:space-between;
  padding:30px 0 56px;border-top:1px solid var(--nav-line)}
.footer .left{font-family:'DM Sans',sans-serif;font-style:italic;font-size:22px;color:var(--muted-3)}
.footer .right{font-family:'Libre Baskerville',Georgia,serif;font-style:italic;font-size:24px;color:var(--accent)}
.badge{display:inline-block;align-self:flex-start;font-size:19px;font-weight:600;color:var(--accent);
  border:1px solid var(--accent);padding:12px 30px;margin-bottom:44px;letter-spacing:4px;text-transform:uppercase}
h1{font-family:'Libre Baskerville',Georgia,serif;font-weight:700;font-size:56px;line-height:1.3}
h1 em{font-style:italic;color:var(--accent)}
.body{font-size:29px;color:var(--muted);line-height:1.72;margin-top:36px}
.body strong{color:var(--text)}
.steplabel{font-size:19px;font-weight:600;letter-spacing:4px;color:var(--muted-3);text-transform:uppercase;margin-bottom:30px}
.giantnum{position:absolute;top:40px;right:0;font-family:'Libre Baskerville',Georgia,serif;
  font-style:italic;font-size:230px;line-height:1;color:var(--accent);opacity:.15;user-select:none}
.highlight{background:var(--block);padding:36px 42px;margin-top:42px;font-size:28px;line-height:1.65;color:var(--muted)}
.highlight em{font-family:'Libre Baskerville',Georgia,serif;font-style:italic;color:var(--accent)}
.shot{border:1px solid var(--card-border);background:#FFFCFB;padding:16px;box-shadow:0 14px 36px rgba(51,42,46,.10)}
.shot img{display:block;width:100%}
.polaroid{background:#FFFCFB;border:1px solid var(--card-border);padding:16px 16px 20px;
  box-shadow:0 18px 44px rgba(51,42,46,.14);transform:rotate(-2deg)}
.polaroid img{display:block;width:100%}
.sticker{position:absolute;filter:drop-shadow(0 14px 30px rgba(51,42,46,.22));z-index:3}
.accent{border-left:3px solid var(--accent);padding-left:40px}
.qmark{font-family:'Libre Baskerville',Georgia,serif;font-size:150px;color:var(--accent);line-height:.5;
  opacity:.3;margin-bottom:30px}
.qtext{font-family:'Libre Baskerville',Georgia,serif;font-style:italic;font-size:46px;line-height:1.5}
.qtext em{color:var(--accent)}
.qdivider{width:64px;height:3px;background:var(--accent);margin:44px 0 32px}
.qsource{font-size:27px;color:var(--muted-2);line-height:1.7}
.cmd{display:inline-flex;align-items:center;align-self:flex-start;border:2px solid var(--accent);color:var(--accent);
  padding:30px 54px;margin-top:48px;font-weight:800;font-size:68px;letter-spacing:1px}
.cmd .cursor{display:inline-block;width:7px;height:64px;background:var(--accent);margin-left:16px;opacity:.8}
.plashka{display:inline-block;align-self:flex-start;border:1px solid var(--accent);color:var(--accent);
  padding:22px 54px;margin-top:46px;font-weight:700;font-size:32px;letter-spacing:7px}
.tgwrap{flex:1 1 0;min-height:0;overflow:hidden;margin-top:48px;margin-bottom:10px;display:flex;justify-content:center}
.tgwrap .shot{width:520px;align-self:flex-start}
</style></head><body>
<div class="canvas">
  <nav class="nav"><span class="mono">Ц</span><span class="name">the.tsarevna</span></nav>
  <div class="frame">
    <div class="content"><div class="badge">Тело</div>
    <h1>Почему твои визуализации не работают — <em>и при чём тут тело</em></h1>
    <p class="body" style="margin-top:28px;color:var(--muted-2)">Объяснение без магии. Дочитай — станет понятнее</p>
    <div style="display:flex;justify-content:center;margin-top:54px;position:relative">
      <div class="polaroid" style="width:430px"><img src="photo.jpg"></div>
      <img class="sticker" src="sticker.png" style="width:190px;right:110px;top:-30px;transform:rotate(8deg)">
    </div></div>
    <div class="footer"><span class="left">@the.tsarevna</span><span class="right">листай &rarr;</span></div>
  </div>
</div></body></html>
```

Варианты `.content` для других слайдов:
- Шаг: `<div class="giantnum">1</div><div class="steplabel">Шаг 1</div><h1>Ложишься и включаешь практику на <em>15 минут</em></h1><div class="highlight"><em>«Ничего не надо делать — надо перестать делать»</em></div><p class="body">Не спорт и не осанка — просто лёжа и слушая</p>`
- Главное: `<div class="accent"><div class="steplabel">Главное</div><h1>Мозг видит только знакомое — <em>и тянет тебя в привычное болотце</em></h1><p class="body">…</p></div>`
- Вывод-цитата: `<div class="qmark">&ldquo;</div><div class="qtext">Пока тело зажато, визуализация — <em>это просто фантазии.</em></div><div class="qdivider"></div><p class="qsource">…</p>`
- Призыв: `<h1 style="font-size:50px">Хочешь практику, после которой <em>легче прямо сейчас?</em></h1><p class="body">Напиши в комментариях слово «ТЕЛО» — скину в директ</p><div class="plashka">«ТЕЛО»</div><div class="tgwrap"><div class="shot"><img src="tg.jpg"></div></div>` + футер *жду в комментариях →*

## Рендер

Папка: `~/Desktop/алена/карусели/карусель-<тема>/`. Материалы (фото, скрины, стикеры, `logo.png`) скопировать в неё с ASCII-именами.

```bash
for i in 1 2 3 ...; do
  "/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless --disable-gpu \
    --hide-scrollbars --force-device-scale-factor=1 --window-size=1080,1350 \
    --virtual-time-budget=10000 --screenshot="слайд-$i.png" "file://$(pwd)/slide-$i.html"
done
```

ОБЯЗАТЕЛЬНО посмотреть готовые PNG глазами: слайд может отрендериться пустым (перезапустить с sleep 1 между слайдами), футер не должен уезжать за край (`min-height:0` на flex-контейнерах), фон должен быть тёплым пудрово-розовым, а не белым (если белый — шрифты/CSS не подгрузились, перезапустить).
