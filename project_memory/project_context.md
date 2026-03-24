# min-analytiker — Project Context
*Läses av styr-ai vid varje analys. Definierar projektets syfte, mål och nuläge.*

---

## Syfte
Min Analytiker är en AI-driven intradagsanalytiker kopplad till TRADESYS. Systemet levererar pre-market analys, kandidatval och trade-validering baserat på TRADESYS scanners och marknadsregim.

---

## Nuvarande prioriteringar
1. **Setup** — Supabase + Vercel deploy (scaffold i nuläge)
2. **Integration med TRADESYS** — läsa scannerdata och regimbedömning
3. **Pre-market workflow** — automatisk analys klar innan 15:30 CET

---

## Mål
- Leverera en daglig pre-market briefing med top 3–5 kandidater
- Validera trade-setups mot TRADESYS-metodologi
- Minska kognitiv last vid marknadsöppning
- Lära sig över tid från utfall — bygga en förbättrande feedback-loop

---

## Relation till andra projekt
- **TRADESYS** — primär datakälla. min-analytiker läser scanneroutput och regim
- **styr-ai** — meta-system som övervakar att min-analytiker faktiskt levererar värde

---

## Vad styr-ai ska bevaka
- Om pre-market briefing faktiskt produceras dagligen
- Kvaliteten på kandidatvalen vs faktiska utfall
- Om integrationen med TRADESYS är funktionell
- Blockers som hindrar daglig leverans

---

## Kontext för analys
- Projektet är i scaffold-läge — ingen funktionalitet byggd ännu
- Värdet realiseras bara om det faktiskt används dagligen vid marknadsöppning
- Risken är att det byggs men aldrig integreras i Gustavs faktiska workflow
