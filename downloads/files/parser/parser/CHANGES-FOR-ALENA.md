# CHANGES-FOR-ALENA · Копия парсера reels-monitor под Алёну

Для Майи (или Claude): что именно поменять в копии репозитория, чтобы отдать её Алёне.
По времени — 10 минут. Секреты (.env, google_creds.json) в копию **не** попадают: они в `.gitignore`.

Исходник: `~/Desktop/клод/боты/reels-monitor/` (GitHub `maiyamaiya19999-bit/reels-monitor`, приватный).

---

## 0. Как сделать копию репозитория

Готовая фраза для Claude:

```
Сделай копию репозитория reels-monitor под Алёну по файлу
~/Desktop/клод/проекты/alena-setup/parser/CHANGES-FOR-ALENA.md:
новый приватный репо maiyamaiya19999-bit/reels-monitor-alena, примени раздел «Патч»
и правки из раздела 1, ничего из .env и google_creds.json не копируй.
```

Руками:

```bash
# 1. Свежая копия кода без секретов и без истории
cd ~/Desktop/клод/боты
git clone https://github.com/maiyamaiya19999-bit/reels-monitor.git reels-monitor-alena
cd reels-monitor-alena
rm -rf .git
rm -f _patch.py _patch3.py apply_character.py bot.log      # мусор, Алёне не нужен
# .env, google_creds.json, venv, __pycache__ в клон и так не попадают (gitignore)

# 2. Правки из разделов 1 и «Патч» ниже

# 3. Новый приватный репо и приглашение Алёны
git init && git add -A && git commit -m "Копия парсера под Алёну"
gh repo create maiyamaiya19999-bit/reels-monitor-alena --private --source=. --push
gh api -X PUT repos/maiyamaiya19999-bit/reels-monitor-alena/collaborators/<GITHUB_НИК_АЛЁНЫ> -f permission=push
```

Проверить, что секретов нет: `git ls-files | grep -E '\.env$|google_creds'` — должно быть пусто.

---

## 1. Точный список правок (без патча — «как есть»)

Если патч из раздела ниже НЕ применять, эти три константы надо править в коде вручную.
После патча их значения берутся из переменных окружения, и править код не нужно (см. раздел 2).

| # | Файл | Что | Было | Поставить |
|---|------|-----|------|-----------|
| 1 | `core.py`, строка 19 | `GOOGLE_SHEET_ID = "1ok8fN4BJeWvjsbFUgFeP-sMnuUj1htzu5nVw3ikUSmA"` | ID таблицы Майи | ID таблицы Алёны (из адреса её Google-таблицы между `/d/` и `/edit`). **Обязательно** — иначе её парсер будет писать в таблицу Майи (точнее, упадёт с 403, т.к. её service account туда не пустят). |
| 2 | `bot.py`, строка 30 | `ALLOWED_IDS = {439086150, 5076035383, 5070121776}` | Telegram ID Майи и её людей | `{<TELEGRAM_ID_АЛЁНЫ>}` — её ID из @userinfobot. **Обязательно**, иначе бот ей не отвечает. |
| 3 | `ai.py`, строки 22–30 | `DEFAULT_VOICE = """Я — Майя (@maysoulme)...` | голос Майи | текст из раздела 3 ниже. Желательно (иначе в «Мой стиль» по умолчанию будет Майя; Алёна может перезаписать через веб-интерфейс — сохраняется в `voice.txt`). |
| 4 | `bloggers.txt` | список Майи (38 англоязычных SMM/ИИ-блогеров) | — | заменить на стартовый список Алёны — список Майи её нише (тело, психосоматика, медитации) не подходит совсем. Можно оставить файл пустым: она соберёт свой по гайду (раздел 8.1 — четыре направления: тело/психосоматика, медитации и практики, выгорание/«железная леди», возвращение к себе). |
| 5 | `ai.py`, строка 21 | `CLAUDE_MODEL = os.environ.get("CLAUDE_MODEL", "claude-sonnet-5")` | — | не трогать. Claude в UI сейчас не используется (адаптация отключена, только транскрибация). |
| 6 | `web.py`, строка 25 | `WEB_PASSWORD = os.environ.get("WEB_PASSWORD", "kirill")` | — | не трогать, пароль задаётся переменной `WEB_PASSWORD`. |
| 7 | `Dockerfile`, `requirements.txt` | — | — | не трогать. |

### 1а. Косметика (необязательно, но приятно) — брендинг Майи → Алёны в `web.py`

Сейчас веб-страница в стиле maysoulme. Если хочется «её», по палитре из `$A/SPEC.md` (пудрово-розовая гамма «царевны») и `$A/brand/style-guide.md`:

| Где в `web.py` | Было | Стало |
|----------------|------|-------|
| строка 252 `<title>` | `Кирилл — парсер Reels` | оставить или переименовать персонажа (имя персонажа — на выбор Алёны, `[нужна деталь]`) |
| строки 363, 371 `<img src="/logo.png" alt="MS">` | логотип MS | `<span class="nav__mono">Ц</span>` (монограмма «Ц» или «А», Libre Baskerville italic 22px, цвет `#9C5F6A`), файл `logo.png` удалить |
| строка 372 `<span class="nick">maysoulme</span>`, строка 452 `<footer>maysoulme</footer>` | ник Майи | `the.tsarevna` (курсивом) |
| весь файл, CSS | `#710C04` (бордовый) — около 15 вхождений | `#9C5F6A` (пыльная роза); фон `#fff` → `#FBF7F5`, серые блоки `#f5f5f5` → `#F4ECEA`, текст → `#332A2E`; на тёмном фоне акцент `#E3C2C9` |
| `bot.py`, строки 39–72 | реплики «Кирилла» (флирт) | по желанию Алёны. Логику не трогать — только строки в списках `ANALYSIS_START`, `ADDED_PREFIX`, `ALREADY`, `REMOVED`, `NOT_FOUND`, `LIST_HEADER`, `HELP_TEXT`. |

Замена цвета одной командой: `sed -i '' 's/#710C04/#9C5F6A/g' web.py`.

---

## 2. Патч: `GOOGLE_SHEET_ID`, `ALLOWED_IDS`, `DEFAULT_VOICE` из переменных окружения

Цель: копия репозитория не требует правок кода — все личные значения в `.env` (локально) или в Variables (Railway).
Три маленьких изменения, формат «было → стало». Патч безопасен и для репозитория Майи: если переменные не заданы, поведение прежнее.

### 2.1 `core.py` — `GOOGLE_SHEET_ID`

Было (строка 19):
```python
GOOGLE_SHEET_ID = "1ok8fN4BJeWvjsbFUgFeP-sMnuUj1htzu5nVw3ikUSmA"
```

Стало:
```python
GOOGLE_SHEET_ID = os.environ.get("GOOGLE_SHEET_ID") or "1ok8fN4BJeWvjsbFUgFeP-sMnuUj1htzu5nVw3ikUSmA"
```

Для копии Алёны лучше **без запасного значения**, чтобы забытая переменная сразу давала понятную ошибку, а не тихую запись в чужую таблицу:
```python
GOOGLE_SHEET_ID = os.environ["GOOGLE_SHEET_ID"]  # ID из адреса Google-таблицы, между /d/ и /edit
```

`os` в `core.py` уже импортирован, `load_dotenv()` вызывается выше (строка 15) — `.env` подхватится.

### 2.2 `bot.py` — `ALLOWED_IDS`

Было (строка 30):
```python
ALLOWED_IDS = {439086150, 5076035383, 5070121776}
```

Стало:
```python
# Кому бот отвечает: TELEGRAM_ALLOWED_IDS="111,222" (через запятую); если пусто — только TELEGRAM_CHAT_ID
ALLOWED_IDS = {
    int(x.strip())
    for x in (os.environ.get("TELEGRAM_ALLOWED_IDS") or os.environ["TELEGRAM_CHAT_ID"]).split(",")
    if x.strip()
}
```

Строка 29 (`CHAT_ID = int(os.environ["TELEGRAM_CHAT_ID"])`) остаётся как есть. Для Майи в Railway: `TELEGRAM_ALLOWED_IDS=439086150,5076035383,5070121776`.

### 2.3 `ai.py` — `DEFAULT_VOICE`

Было (строки 22–30):
```python
DEFAULT_VOICE = """Я — Майя (@maysoulme). Веду блог про блогинг и ИИ: ...
...
и без выгорания."""
```

Стало:
```python
_REPO_VOICE = Path(__file__).parent / "voice.default.txt"
DEFAULT_VOICE = (
    os.environ.get("DEFAULT_VOICE")
    or (_REPO_VOICE.read_text(encoding="utf-8").strip() if _REPO_VOICE.exists() else "")
    or """Я — Майя (@maysoulme). Веду блог про блогинг и ИИ: ...(прежний текст без изменений)..."""
)
```

Порядок: переменная `DEFAULT_VOICE` → файл `voice.default.txt` в корне репо → зашитый текст. `Path` и `os` в `ai.py` уже импортированы.
В копию Алёны кладём файл `voice.default.txt` с текстом из раздела 3 — тогда переменная не нужна, а многострочный текст не надо запихивать в env.

Напоминание: рабочий голос всё равно живёт в `DATA_DIR/voice.txt` (раздел «06 Мой стиль» на странице). `DEFAULT_VOICE` — только значение по умолчанию, пока `voice.txt` не создан.

### 2.4 Итог для `.env` / Railway Variables после патча

```
GOOGLE_SHEET_ID=...              # новая
TELEGRAM_ALLOWED_IDS=...         # новая, необязательная
DEFAULT_VOICE=...                # новая, необязательная (есть voice.default.txt)
```
Шаблон целиком — `env.example` рядом.

Проверка после патча (в папке репо, с заполненным `.env`):
```bash
./venv/bin/python -c "import core, ai; print(core.GOOGLE_SHEET_ID); print(ai.DEFAULT_VOICE[:60])"
./venv/bin/python -c "import bot; print(bot.ALLOWED_IDS)"
```

---

## 3. Текст `DEFAULT_VOICE` для Алёны (файл `voice.default.txt`)

Собрано из `$A/brand/PROFILE.md` (разделы 1, 2, 4, 7, 8). Ник — `the.tsarevna`.

```
Я — Алёна (@the.tsarevna), Царевна. Специалист по осознанному расслаблению: помогаю женщинам расслаблять тело и благодаря этому исполнять свои желания. Блог про тело и психосоматику простым языком: подавленные эмоции → зажимы → автопилот → та же жизнь. Всё, что я даю, человек получает лёжа и слушая — я НЕ тренер, никаких упражнений и осанки.

Тон: подруга, которая старше не годами, а километражем, — без надрыва и без позиции сверху. Длинные предложения через «и» и «потому что», короткие строки, самоирония только над собой, «проги» вместо терминов, эмодзи вместо интонации (🤡 😢 🤷🏼‍♀️). Не «состояние», а «чувствование телом». Слова «Claude» и «reels» пишу латиницей.

Аудитория: женщины 30–45, уставшие «железные леди» на автопилоте — хотят, чтобы их оставили в покое, и вернуть саму способность хотеть.

Границы: никаких медицинских обещаний («вылечу», «уберу боль»), без гарантий и сроков, про финансовую независимость не говорю.
```

---

## 4. Чек-лист перед передачей Алёне

- [ ] В репо нет `.env`, `google_creds.json`, `bot.log`, `venv/` (`git ls-files` проверить)
- [ ] Патч 2.1–2.3 применён, `voice.default.txt` добавлен
- [ ] `bloggers.txt` — стартовый список (или пустой файл: пустой список даст ошибку «Список блогеров пуст» до первого добавления — это нормально)
- [ ] `env.example` из этой папки скопирован в корень репо
- [ ] Алёна приглашена в репо (collaborator) или репо перенесён на её GitHub
- [ ] Ей отправлен `PARSER-GUIDE.md`
