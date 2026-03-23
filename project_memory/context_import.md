# Min Analytiker — Context Import

*Importerad från Claude.ai-chattar 2026-03-23. Källa för all historisk kontext.*

---

## Projektbeskrivning

Gustav (f. 1984, Stockholm) är en aktiv retail-trader. Claude fungerar som **intradagsanalytiker och systemutvecklare** för hans trading-system TradeSys — ett regelbaserat, data-drivet system för daytrading och swing trading i amerikanska (och selektivt svenska) aktier.

---

## TradeSys — Systemets kärna

Tre pelare:
1. **Makroregim-klassificering** — Risk-On / Risk-Off / Rotation / Chop / Transition
2. **Multi-timeframe teknisk analys** med specificerad indikatorstack
3. **Intermarket-hierarki** som gate innan kandidatval

**Regler:** Edge-rating under 3 = ingen trade. CHOP/TRANSITION = ingen trade. Inga undantag.

---

## Indikatorstack (TradeSys standard)

RSI, ADX, DI+/DI-, Relative Volume Ratio, CVD, VWAP (+/-1s/+/-2s), ATR-stopp, EMA 10/20/50/100/200, Pearson's R trendlinje, Bollinger Bands, Volume Profile

---

## Analysramverk

- **Pre-market** (15:00-15:20 CET): regim, sektorer, max 2 kandidater
- **Post-session**: outcome, plan-avvikelse, lärdom
- **Intradag**: bekräftelse vid uppladdad chart

---

## Byggda moduler

| Modul | Beskrivning |
|-------|-------------|
| Watchlist Insider | HTML-modul, insider-transaktioner per ticker (A/B/C/D-strategi), SEC EDGAR + OpenInsider |
| Regime Pressure Score (0-10) | VIX, SPY RelVol, IWM/SPY, HYG, SPY drawdown |
| CVD Pine Script | TradingView-indikator for CVD-divergens och institutionella zoner |
| NBIS alert-framework | Fyra nivaer: fundamental + strukturell + intradag + makro |

---

## Gjorda analyser (urval)

- **MU** — post-earnings sell-the-news, HL-formation, VIX-filter
- **NBIS** — konvertibel-obligationserbjudande $4B, delta-hedge-tryck, triangelkomprimering
- **MRVL, TER, ASX** — CSV-baserad strukturanalys med DI+/DI-, CVD, RelVol
- **HIMX** — Hunterbrook-rapport, CPO-tesen, kallkritik
- **LUMI, ETN, PWR** — teknisk analys inkl. Pearson's R, VWAP, ADX
- **GLDD** — pagaende uppkop $17/aktie, radet att tendera istallet for salja

---

## Portfoljbeslut

- Stang Enthusiast Gaming + Hamlet BioPharma (off-thesis)
- GLDD: tendera via broker innan 31 mars 2026

---

## Kopplade API:er

| API | Namn i Claude | Syfte |
|-----|--------------|-------|
| Polygon.io | `Massive Market Data` | OHLCV, volym, quotes. Krav: `tool_search("financial market data")` forst |
| Gmail | Gmail MCP | E-post |
| Google Calendar | GCal MCP | Kalender |
| MT Newswires | MT Newswires MCP | Nyhetsfeed |
| Supabase | Supabase MCP | Databas |
| GitHub | GitHub MCP | Repo-hantering |

**Kritisk notering om Polygon:** `Massive Market Data` syns INTE direkt for Claude — kraver alltid `tool_search` forst. Gustav ska aldrig behova forklara detta.

---

## Systemprompt-gap att fylla

| Aspekt | Saknas i prompt |
|--------|----------------|
| Polygon API | Central datakalla, ej dokumenterad |
| CVD som signal | Central indikator i verkligheten |
| Insider-modul | Watchlist Insider ar aktiv modul |
| Snapshot-format | Ej dokumenterat |
| Bollinger/Volume Profile | Saknas i indikatorlistan |

---

## Koppling till tradesys1337

TradeSys dashboard-repot (`gustavkall/tradesys1337`) ar den tekniska plattformen — single-file HTML dashboard med Polygon API, scanners, chart-analys. Min Analytiker ar den analytiska sidan: daglig regim, kandidatval, trade-beslut, post-session-review.
