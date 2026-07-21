# Polymarket Trading Bot | Polymarket Arbitrage Bot

**Язык / Language / 语言:** [English](README.md) | [中文](README.zh-CN.md) | Русский

Высокопроизводительный **торговый бот Polymarket** и **арбитражный бот Polymarket** для автоматизированной торговли на крипто-рынках Polymarket **5-minute** Up/Down — **BTC, ETH, SOL и XRP**.

Основная стратегия — **поздний снайп к резолюции (endcycle sniper)**: дождаться почти решённого исхода, купить фаворита по **~$0.98–$0.99** и держать до расчёта ради небольшой выплаты в каждом выигрышном цикле.

Помимо одной стратегии, на этой странице разобраны **ключевые стратегии ботов Polymarket**, которые используют серьёзные трейдеры в 2026 году — от классического комплементарного арбитража до latency-снайпа, ladder market making, stair-выходов, моментума и AI-вероятностного края.

![Polymarket Arbitrage Bot Banner](doc/banner.png)

**Живые профили со стратегией:** [**@polymarkettradingbot**](https://polymarket.com/@polymarkettradingbot) · [**@tradingbot-1**](https://polymarket.com/@tradingbot-1)

**Telegram:** [@trum3it](https://t.me/trum3it) · **Автор:** [@trum3it](https://github.com/trum3it)

---

## Возможности

- Ориентация на высоколиквидные **5-минутные crypto Up/Down** рынки Polymarket (BTC, ETH, SOL, XRP)
- **Endcycle / late-window sniper** — вход только когда фаворит уже около цены резолюции
- Мониторинг цен в реальном времени по **четырём активам** на одних и тех же 5-минутных часах
- Понятный цикл buy → redeem, согласованный с on-chain CTF Exchange и расчётом
- Малые повторяемые преимущества, которые компаундятся на многих 5-минутных окнах
- Публичные on-chain доказательства buy/redeem
- Подробный обзор основных стратегий ботов на Polymarket (без copy trading)
- База для расширения в снайп, арбитраж, маркет-мейкинг и моментум-модули

---

## Каталог стратегий (без copy trading)

CLOB Polymarket уже доминируют боты. Простые окна «YES + NO < $1» часто живут лишь секунды. Ниже — то, что реально крутят серьёзные системы: отдельно или как мультистратегийный портфель.

| # | Стратегия | Стиль | Типичный край |
|---|-----------|-------|---------------|
| 1 | **Endcycle Sniper** | Поздний направленный вход | Купить фаворита @ 0.97–0.99 → redeem @ $1.00 |
| 2 | **Complement / Sum-to-One Arb** | Рыночно-нейтральный | Купить YES+NO, когда сумма ask < $1 |
| 3 | **Latency / Oracle Arb** | Скорость | Сделка до обновления Chainlink / UI |
| 4 | **101 Cents Maker** | Предоставление ликвидности | Продажа пар YES+NO с целью ~$1.01 |
| 5 | **Ladder Market Making** | Инвентарь + спред | Лестница лимиток по уровням цены |
| 6 | **Stair Exit / Unwind** | Качество исполнения | Поэтапная ликвидация YES/NO к резолюции |
| 7 | **Dual-Side Volatility Arb** | Нейтраль / хедж | Неверные вероятности + краткосрочная вола |
| 8 | **Lost Token Sniper** | Двусторонняя позиция | Держать обе стороны, рано слить лузера |
| 9 | **High-Frequency Momentum** | Направленный | Ловить импульс order-flow / новостей |
| 10 | **Imbalance Arb** | Дисбаланс стакана | Купить дешёвую сторону при перекосе |
| 11 | **Logical / Multi-Outcome Arb** | Ограничения | Связанные рынки нарушают правила вероятностей |
| 12 | **AI Probability / Info Arb** | Информация | Модельная справедливая цена vs рынок |

---

## Контакты

У меня есть практический опыт разработки и запуска автоматизированных ботов для Polymarket, включая live endcycle-снайп на коротких крипто-рынках. Могу поделиться инсайтами, стратегиями и best practices — или обсудить кастомные решения под ваши задачи.

Если интересует сотрудничество, есть вопросы или хотите увидеть бота в деле — пишите.

| Канал | Ссылка |
|-------|--------|
| **Telegram** | [@trum3it](https://t.me/trum3it) |
| **GitHub** | [@trum3it](https://github.com/trum3it) |
| **Polymarket** | [@polymarkettradingbot](https://polymarket.com/@polymarkettradingbot) · [@tradingbot-1](https://polymarket.com/@tradingbot-1) |

Публичные аккаунты Polymarket — можно смотреть P/L бота вживую:

**https://polymarket.com/@polymarkettradingbot**

**https://polymarket.com/@tradingbot-1**

---

## Живое доказательство — циклы Buy → Redeem

Ниже реальные on-chain транзакции с живых профилей бота в Polygon. Каждая пара показывает паттерн **endcycle sniper**: **купить фаворита в конце окна → redeem по $1.00 после резолюции**.

![Polymarket Activity](doc/activity.png)

### Сделка 1 — 11 июня 2026 · вход ~$0.99

| Шаг | Время (UTC) | Детали | Polygonscan |
|-----|-------------|--------|-------------|
| **Buy** | 09:30:01 | ~**$67.32** USDC → **68 shares** @ **~$0.99** (late-window favorite) | [Смотреть buy](https://polygonscan.com/tx/0x6874a18bcd84c18a6e9d5cffd0a94eb0bdc148089a364370eb9120384bc4e21c) |
| **Redeem** | 09:31:03 | Рынок резолвится → shares redeem по **~$1.00** | [Смотреть redeem](https://polygonscan.com/tx/0x17e8fbc7ed8d995c44127da034e487733a43f18c6638cdcba9088a519b11ad63) |

**Прибл. валовая прибыль:** ~**$0.68** на ~$67 стейке (~**1%**) до комиссий, за **~62 секунды**.

### Сделка 2 — 11 июня 2026 · вход ~$0.99

| Шаг | Время (UTC) | Детали | Polygonscan |
|-----|-------------|--------|-------------|
| **Buy** | 08:55:01 | Покупка фаворита @ **~$0.98–$0.99** у конца окна | [Смотреть buy](https://polygonscan.com/tx/0x7fa58be45dc24afbc8bd135fc6a7147fb548e2c00ad2f5b6100fa7510dd58b45) |
| **Redeem** | 08:55:30 | Redeem через **~29с** после покупки | [Смотреть redeem](https://polygonscan.com/tx/0x4edaaa3a6a6d854fe6ec938280ab3cfd34d07f34fcc75c7f4757feccfc9d30dc) |

> **Как читать эти tx:** **Buy** взаимодействует с `Polymarket: CTF Exchange V2` — USDC уходит, outcome-токены приходят. **Redeem** конвертирует выигрышные shares обратно в USDC по **$1.00** за штуку после резолюции 5m-окна. Повторяйте по многим окнам — P/L компаундится. Полная история: [@polymarkettradingbot](https://polymarket.com/@polymarkettradingbot) и [@tradingbot-1](https://polymarket.com/@tradingbot-1).

### Скриншоты профиля ([@polymarkettradingbot](https://polymarket.com/@polymarkettradingbot) · [@tradingbot-1](https://polymarket.com/@tradingbot-1))

Живой дашборд Polymarket — рост портфеля и активность buy/redeem на **BTC** и **XRP** 5m-рынках около **96–99¢**:

![Polymarket profile — past day profit/loss and recent trades](doc/daily_pnl.png)

История включает повторяющиеся входы в поздней стадии крипто-prediction markets с успешными redemption после settlement.

---

## Почему стратегии ботов Polymarket важны в 2026

Короткие крипто-рынки Polymarket (особенно **BTC / ETH / SOL / XRP 5-minute Up/Down**) создали новый класс HFT-торговли на prediction markets:

- Рынки резолвятся каждые **5 минут** — сотни циклов в день
- Бинарные исходы платят ровно **$0 или $1** — жёсткая математическая структура цен
- CLOB + Polygon позволяют автоматизировать циклы **buy → merge/redeem**
- Ритейл-поток всё ещё большой; профи конкурируют по **latency, inventory и risk**

Наблюдения из исследований и bot-writeups 2026:

- Классические complement-arb окна часто длятся лишь **~2–3 секунды**
- Большую долю чистого arb забирают стеки **sub-100ms**
- Медианный сырой спред после комиссий может быть **долями цента**
- Растущая доля P/L ботов — из **non-pure-arb**: market making, momentum, endcycle sniping, correlation и information edge

Поэтому современные системы Polymarket обычно **мультистратегийные**, а не «один трюк».

---

## 1. Polymarket Endcycle Sniper Bot (основной)

**Polymarket Endcycle Sniper Bot** мониторит короткие prediction markets и исполняет высоковероятные сделки ближе к концу каждого 5-минутного эпоха.

Он ждёт большую часть окна, покупает, когда ask фаворита входит в диапазон (например **0.97–0.99**), управляет риском timed-exit’ами и закрывает выигрышные позиции после резолюции.

Это стратегия за live-активностью [@polymarkettradingbot](https://polymarket.com/@polymarkettradingbot) / [@tradingbot-1](https://polymarket.com/@tradingbot-1) выше.

### Обзор стратегии

Каждый **5-minute Up/Down** рынок (BTC, ETH, SOL, XRP) длится **300 секунд**. Все четыре актива делят одни часы окна — каждые 5 минут новый раунд.

```
0s ──────────────── 250s ─── 290s ─ 298s ─ 300s
     wait / monitor      entry      exit   close
                         window    (resolve)
```

Ближе к концу цена обычно уже ушла в одну сторону, и вероятный победитель торгуется чуть ниже **$1.00**:

1. **Мониторить все четыре рынка** (BTC, ETH, SOL, XRP) на каждом опросе
2. **Ждать** большую часть окна — без ранних входов
3. **Входить** в последние ~40с, когда Up или Down стоит **$0.97–$0.99**
4. **Купить фаворита** — до **одной позиции на актив** за окно
5. **Держать до резолюции** при **t = 298s** и сетить

| | Типичный выигрыш | Риск |
|---|------------------|------|
| **Математика** | Купить @ ~$0.98 → redeem @ **$1.00** ≈ **2%** gross на share | Разворот в последнюю секунду → почти весь стейк |
| **Край** | Малый повторяемый профит за окно | Один плохой флип съедает много побед |

### Правила стратегии

| Параметр | Значение |
|----------|----------|
| Рынки | **BTC, ETH, SOL, XRP** — 5m Up/Down |
| Позиции | До **одной сделки на актив** за 5m-окно (макс. 4 concurrent) |
| Время входа | **250–290s** после старта окна |
| Цена входа | Ask фаворита **0.97–0.99** (обычно **0.98–0.99**) |
| Выбор стороны | Сторона в диапазоне; если обе — взять **более высокую** цену |
| Выход | **t = 298s** — redeem @ **$1.00/share**, если bid ≥ 0.90, иначе выход по market bid |

Многие окна дают **0 сделок** — нормально, если ни одна сторона не попала в ценовой диапазон вовремя.

### Почему это всё ещё используют

Endcycle sniping не обязан побеждать весь рынок весь день. Нужен повторяемый late-window setup: когда фаворит уже **96–99¢**, неопределённость мала, а payout/risk математика явна. Капитал оборачивается каждые несколько минут — компаундинг идёт от **частоты**, не от огромных одиночных выигрышей.

---

## 2. Complement Arbitrage (Sum-to-One / Dump-Hedge)

Также называют **intra-market arbitrage**, **structural dump-hedge** или arb **YES+NO < $1**.

### Суть

В бинарном рынке ровно одна сторона платит **$1.00** при резолюции. Если держать **1 YES + 1 NO**, гарантированно получите **$1.00** обратно (до комиссий). Поэтому:

- Если `ask_YES + ask_NO < 1.00`, покупка обеих сторон фиксирует структурную прибыль
- Если `bid_YES + bid_NO > 1.00`, продажа обеих сторон может дать maker-край

Пример: YES ask **$0.48** + NO ask **$0.50** = **$0.98** → теоретические **$0.02** на пару shares при полном fill обеих ног.

### Как исполняют боты

1. Стримить CLOB-стаканы целевых рынков (часто 5m crypto Up/Down)
2. Ловить, когда сумма ask ниже порога (например `1.00 - fees - target_edge`)
3. Ставить почти одновременные покупки YES и NO (часто FOK/FAK/GTD)
4. Опционально **merge** matched-пары обратно в USDC при балансе инвентаря
5. Redeem остатков после резолюции при необходимости

### Reality check (2026)

- Возможности **короткоживущие** (часто секунды)
- Самые чистые принты забирают sub-100ms стеки
- Taker fees + leg risk (одна нога заполнилась, другая нет) съедают край
- Всё ещё полезно на тонких рынках, новых листингах или как secondary-модуль

**Лучше для:** market-neutral капитала, низкой направленности, automation-first трейдеров.

---

## 3. Latency / Oracle Arbitrage

### Суть

5-минутные crypto-рынки Polymarket резолвятся по oracle / reference feeds (часто обсуждают cadence в стиле **Chainlink**). Спот-площадки вроде Binance часто двигаются **раньше**, чем implied probability на Polymarket полностью обновится.

Боты смотрят спот и CLOB одновременно. Когда спот резко прыгнул, а токены ещё не переоценены, покупают сторону движения (Up/Down) и выходят по мере догона стакана — или держат до резолюции, если ход решающий.

### Типичный pipeline

1. WebSocket спот (BTC/ETH/SOL/XRP)
2. WebSocket / polling mid/asks Polymarket CLOB
3. Детект лага: спот ушёл, вероятность Polymarket ещё stale
4. Агрессивный вход с жёсткими size + slippage caps
5. Выход на reprice или hold у endcycle при высокой уверенности

### Почему сложно

- Край измеряется **сотнями миллисекунд — несколькими секундами**
- Нужны dedicated RPC, низкая latency и аккуратный учёт комиссий
- Ложные сигналы в chop убивают expectancy
- Конкурирующие latency-боты сжимают то же окно

**Лучше для:** HFT-инфры, низколатентного Polygon, команд с жёстким risk-control.

---

## 4. 101 Cents Liquidity Maker (Pair Selling)

### Суть

Вместо покупки недооценённых пар бот **создаёт** инвентарь YES+NO (split / накопление) и продаёт обе стороны так, чтобы сумма целилась около **$1.01** (101 cent) — примерно **1–2¢** на завершённую пару.

Это стратегия **liquidity-making / inventory**, не направленная ставка.

### Типичный цикл

1. Split USDC в YES + NO (или копить инвентарь)
2. Ставить сбалансированные sell-лестницы с обеих сторон
3. Требовать `sell_YES + sell_NO >= 1.01` (или динамический min pair sum)
4. Заполнять малыми парами, не дампить весь стакан
5. Перекашивать котировки при дисбалансе инвентаря
6. Повторять на многих 5m-окнах

### Почему нравится

- Много малых market-neutral циклов
- Масштабируется от uptime и качества котировок сильнее, чем от «угадай направление»
- Естественно стыкуется с inventory balancing и force-hedge

### Риски

- Инвентарь может застрять на одной стороне при сильном тренде
- Adverse selection от informed flow
- Слишком жёсткий pair sum → мало fills; слишком мягкий → край исчезает после fees

**Лучше для:** 24/7 maker-ботов на ликвидных short-interval рынках.

---

## 5. Ladder Market Making

### Суть

Вместо одного bid/ask бот ставит **лестницу** лимиток на нескольких уровнях YES и/или NO. Это:

- Собирает спред по диапазону retail fills
- Меньше impact vs один крупный ордер
- Позволяет постепенно ребалансировать инвентарь по мере заполнения ступеней

Современные ladder-боты обычно комбинируют:

- Dual-sided quoting
- Inventory skew (агрессивнее разгружать тяжёлую сторону)
- Расширение спреда при воле
- Cancel/replace циклы каждые сотни мс — секунды

### Inventory-balanced вариант

Популярный дизайн 2026 — **inventory-balanced ladder**:

1. First-leg sell, когда momentum/order-flow в пользу одной стороны
2. Хедж противоположной стороны к near-neutral
3. Force-hedge при превышении жёсткого USDC-лимита дисбаланса
4. Снятие котировок перед close / новостями

**Лучше для:** трейдеров, которым нужен стабильный maker P/L и кто умеет inventory-math.

---

## 6. Stair Exit / Stair Arbitrage (движок unwind)

### Суть

Многие боты теряют деньги на **выходах**, не на входах. Stair-логика фокусируется на финальной фазе окна: unwind YES/NO ликвидность-осознанными шагами вместо market-dump.

### Типичная stair-последовательность

1. Близко к резолюции оценить depth и качество цены обеих сторон
2. **Selective first exit** — сначала легче / лучше оценённую сторону
3. **Stair unwind** оставшейся стороны клипами по выбранным уровням
4. Опционально финальный coordinated sweep, если depth внезапно появился
5. Держать hedge / exposure caps всё время

### Почему важно

В 5m-рынках последние 30–60 секунд хаотичны. Stair-движок делает выход контролируемым: меньше slippage, меньше «продал в вакуум», лучше сохранность капитала к следующему циклу.

**Лучше для:** dual-inventory стратегий (101¢, ladder, lost-token), которым нужно чисто выходить каждый epoch.

---

## 7. Dual-Side Volatility / Probability Arbitrage

### Суть

Это семейство ботов **не** пытается предсказать победителя. Оно ищет краткосрочный mispricing между:

- Implied probabilities
- Дисбалансом стакана
- Realized short-term volatility
- Fair model value

Затем торгует **обе стороны** с хеджами, чтобы net exposure оставался под контролем, а мелкие края собирались на большом объёме.

### Частые тактики

- Купить undervalued сторону, продать/перевесить rich сторону
- Количественные пороги входа/выхода вместо «чутья»
- Хедж после первого fill, чтобы one-leg не стал naked directional
- Компаундить микро-края на высоком trade volume

**Лучше для:** quant-систем с сильным risk-модулем и непрерывным мониторингом.

---

## 8. Lost Token Sniper

### Суть

На коротких Up/Down эпохах бот может временно держать **и YES, и NO** (или получить их через split). По мере прогресса окна он определяет **проигрышный токен** и продаёт его до резолюции — оставляя победителя на redeem по $1.00.

Если суммарная стоимость входа была около или ниже $1, а лузер продан за остаточную ценность, цикл может быть прибыльным даже без идеального foresight.

### Workflow

1. Аллоцировать в YES и NO early/mid-window
2. Мониторить стаканы + momentum, чтобы оценить умирающую сторону
3. Выйти из predicted loser в оставшийся bid
4. Держать / redeem победителя на settlement
5. Повторить следующий epoch

### Риски

- Ошибка в определении лузера (классический last-second flip)
- Тонкий bid на умирающей стороне → fills по мусорной цене
- Комиссии на двух ногах режут теоретический край

**Лучше для:** тех, у кого уже dual-inventory, и нужен активный mid-window слой оптимизации.

---

## 9. High-Frequency Momentum Trading

### Суть

Когда приходит breaking news, резкий спот-ход или всплеск агрессивного CLOB-flow, цены Polymarket **трендят**, прежде чем полностью «устояться». Momentum-боты рано ловят импульс и едут на нём.

### Типичные сигналы

- Резкие всплески volume / trade-rate
- Перевороты order-book imbalance
- Подтверждение momentum со спот-бирж
- Короткие lookback-returns по YES/NO mid

### Risk-controls, которые отделяют выживших от blowup

- Trailing / time stops (эти рынки умирают каждые 5 минут)
- Circuit breakers по session drawdown
- Max position per market / per minute
- No-trade зоны в мёртвом chop

**Реальность:** сверхкороткие crypto binaries могут быть близки к random walk. Momentum работает вспышками; без жёстких фильтров бот overtrade’ит и умирает.

**Лучше для:** low-latency стеков, способных войти и выйти внутри одного окна.

---

## 10. Imbalance Arbitrage («Buy the Cheap Side»)

### Суть

Иногда одна сторона стакана временно слишком дешева относительно другой — не обязательно `YES+NO < 1`, а **относительный** mispricing vs depth, recent trades или краткосрочной fair-value модели.

Боты покупают дешёвую сторону (или продают rich сторону) и флаттят, когда стакан нормализуется.

### Почему появляется

- Панический one-sided retail sell
- Кратковременные дыры ликвидности
- Latency между связанными рынками
- Дампы инвентаря маркет-мейкеров

**Лучше для:** непрерывных сканеров по многим рынкам со строгими adverse-selection фильтрами.

---

## 11. Logical / Multi-Outcome / Correlation Arbitrage

### Суть

Помимо одиночных бинарных рынков, Polymarket содержит связанные вопросы, чьи вероятности должны подчиняться логике:

- Взаимоисключающие исходы не должны суммироваться выше $1 (после fees)
- Вложенные события («A» vs «A и B») имеют inequality constraints
- Cross-market корзины могут временно быть inconsistent

Продвинутые боты проецируют цены на valid probability simplex (в research — Bregman / Frank–Wolfe и т.п.) и торгуют нарушение.

### Reality check

- Сложнее инженерить, чем 5m Up/Down sniping
- Возможности могут быть крупнее, но реже
- Model risk реален: неверное определение constraint = ложный arb

**Лучше для:** research desks и multi-market engines, не для первого бота.

---

## 12. AI Probability / Information Arbitrage

### Суть

Рынки могут медленно переоценивать публичную информацию. AI / ensemble системы глотают headlines, polls, on-chain data или structured context, оценивают fair probability и торгуют, пока цена Polymarket ещё stale.

### Типичный стек

1. Ingest новостей / social / data
2. Несколько моделей → ensemble fair odds
3. Сравнение с Polymarket mid
4. Сделка только если edge > threshold и ликвидность реальна
5. Выход на reprice или time stop

### Важная честность

Это **не** магическая альфа. Это скорость + калибровка + исполнение. На ultra-short 5m BTC binaries live-эксперименты показывают, что directional AI-агенты могут страдать из-за огромного шума. AI чаще сияет на **information-heavy**, более длинных горизонтах — и всё равно нужны жёсткие risk limits.

**Лучше для:** event-driven рынков (политика, макро, спорт) и гибридных систем, где AI — фильтр, а не unchecked autopilot.

---

## Как эти стратегии складываются вместе

Серьёзные портфели ботов Polymarket часто комбинируют модули:

| Слой | Стратегии |
|------|-----------|
| **Structural / neutral** | Complement arb, 101¢ maker, ladder MM, dual-side hedge |
| **Execution quality** | Stair exits, inventory caps, force-hedge |
| **Speed** | Latency / oracle arb, HF momentum |
| **Late-window harvest** | Endcycle sniper |
| **Research / info** | Imbalance, logical multi-outcome, AI probability |

Система на этой странице делает акцент на **endcycle sniping** по BTC/ETH/SOL/XRP 5m — практичный, понятный и публично проверяемый стиль края — а каталог выше показывает более широкий конкурентный ландшафт.

---

## Почему этот бот

Проект помогает трейдерам понять, как на практике выглядит настоящий **арбитражный торговый бот Polymarket**:

- Торговые боты Polymarket на коротких crypto-рынках
- Автоматизация prediction markets вместо ручных кликов
- Late-window / endcycle sniper с публичными on-chain доказательствами
- Циклы buy → redeem settlement на Polygon
- Карта основных стратегий ботов, конкурирующих на Polymarket в 2026

Если хотите обсудить дизайн стратегии, кастомные боты или live-поведение — Telegram: [@trum3it](https://t.me/trum3it).

---

## Риски и дисклеймер

- **Малый край, крупные хвосты** — теоретические 1–2¢ при входе $0.98 могут исчезнуть из-за fees, slippage и одного флипа
- **Конкуренция жёсткая** — многие чистые arb-принты забирают более быстрые боты
- **Не каждое окно торгуется** — endcycle часто пропускает циклы, если никто не дошёл до 0.97–0.99
- **Прошлые результаты не гарантия будущего** — [@polymarkettradingbot](https://polymarket.com/@polymarkettradingbot) / [@tradingbot-1](https://polymarket.com/@tradingbot-1) — иллюстрация, не обещание
- **Не финансовый совет** — торговля prediction markets несёт существенный риск убытка

---

## Roadmap

- Более сильные endcycle-варианты (multi-threshold, adaptive sizing)
- Модули complement + latency arb
- Ladder / 101¢ maker + stair exit engine
- Telegram-алерты по сделкам
- Real-time analytics dashboard
- Cloud deployment automation

---

## SEO Keywords

Polymarket trading bot, Polymarket arbitrage bot, Polymarket endcycle sniper, complement arbitrage, latency arbitrage, 101 cents maker, ladder market making, stair arbitrage, lost token sniper, dual-side arbitrage, momentum trading bot, imbalance arbitrage, prediction market bot, 5-minute crypto Up/Down bot, Polymarket CLOB bot, algorithmic trading Polygon, арбитражный бот Polymarket, торговый бот Polymarket

---

## License

ISC License
