# min-analytiker — Project Context
*Läses av styr-ai vid varje analys. Definierar projektets syfte, mål och nuläge.*

---

## Syfte
Min Analytiker är en AI-driven intradagsanalytiker kopplad till TRADESYS. Systemet levererar pre-market analys, kandidatval och trade-validering baserat på Gustavs regelbaserade trading-metodologi — med målet att minska kognitiv last vid marknadsöppning och förbättra beslutskvaliteten.

---

## Gustavs trading-profil
- **Fokus:** US-listade aktier, primärt semiconductors, AI infrastructure, tech. Selektivt europeiska/svenska marknader (OMXS30 på sikt)
- **Stil:** Regelbaserat, datadriven — multi-indikator confluence krävs för entry
- **Setup-typer:** [DT] daytrade, [SW] swing trade, [ANALYS] utbildande chart-review
- **Broker:** Svensk mäklare med USD-handel
- **Verktyg:** TradingView Premium, custom Pine Script, TradeSys dashboard

---

## Metodologi (inbyggd i analytikern)

### Regimklassificering (gates allt)
- **Risk-On / Risk-Off / CHOP / TRANSITION**
- Bedöms via: VIX, MOVE, HYG, LQD, SOXX/SPX, IWM/SPX, sektorrotation, pre-market intermarket dashboard
- Ogynnsamt regime = reducerad storlek eller blockerad entry

### Entry-krav (non-negotiable)
Multi-indikator confluence: pris, volym (RelVol), riktningsindikatorer (DI+/DI−, ADX) och CVD måste aligna. Single-signal setups = brus.

### Indikatorer
RSI, ADX, DI+/DI−, Relative Volume Ratio, CVD, VWAP (±1σ/±2σ), ATR-stops, multipla EMAs, Pearson R trendline, Bollinger Bands, Volume Profile

### CVD
Löpande summa av köp minus sälj-volym per bar. Divergens mot pris är nyckelsignal — men bara vid predefinerade institutionella/strukturella zoner (confluence).

### Alert-arkitektur
Invalidering sätts FÖRE entry-alert. Layered: entry trigger → strukturell bekräftelse → invalidering.

### Insider-strategi
Fyra strategier A–D baserat på kontext. Starkast signal vid Transition/crash (VIX 30+), svagast vid Risk-On (VIX under 15).

---

## Research-format
**Snapshots** — strukturerad bolagsresearch per ticker: fundamentals, värdering, analytikerkonsensus, institutionellt flöde, insider-aktivitet, trading-relevans.

---

## Nuvarande prioriteringar
1. **Setup** — Supabase + Vercel deploy (scaffold i nuläge)
2. **Integration med TRADESYS** — läsa scannerdata, regimbedömning, watchlist
3. **Pre-market workflow** — automatisk briefing klar innan 15:30 CET med top 3–5 kandidater

---

## Mål
- Daglig pre-market briefing med top 3–5 kandidater rankade efter edge-score (1–5 skala)
- Validera trade-setups mot TradeSys-metodologi innan entry
- Minska kognitiv last vid marknadsöppning
- Bygga feedback-loop: utfall → lärdomar → förbättrad kandidatrankning

---

## Relation till andra projekt
- **TRADESYS** — primär datakälla: scanneroutput, regim, watchlist, trade_log
- **styr-ai** — övervakar att min-analytiker faktiskt levererar dagligt värde

---

## Vad styr-ai ska bevaka
- Om pre-market briefing produceras dagligen (vardagar 15:00–15:30 CET)
- Om integrationen med TRADESYS är funktionell
- Om kandidatvalen korrelerar med faktiska utfall
- Blockers som hindrar daglig leverans
- Om projektet byggs men aldrig integreras i Gustavs faktiska workflow

---

## Kontext för analys
- Projektet är i scaffold-läge — ingen funktionalitet byggd ännu
- TRADESYS är fullt operativt (v37) — min-analytiker ska konsumera dess output, inte duplicera den
- Värdet realiseras bara om det används vid varje marknadsöppning
- Hög-ATR tickers (ex NBIS ~16% daglig ATR) kräver specialhantering i kandidatrankning
- Europeisk expansion (OMXS30) är på horisonten men US-baslinje prioriteras först
