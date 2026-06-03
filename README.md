# 🏆 13° Memorial Sergio Pareti 2026

Applicazione web **responsive e mobile-first** per la gestione e visualizzazione del torneo **13° Memorial Sergio Pareti** – categoria **Esordienti 1° anno (Under 12 / nati nel 2014)**, organizzato dall'**A.C.D. Lucento** di Torino nel maggio–giugno 2026.

Realizzata interamente in **HTML, CSS e JavaScript vanilla**, senza framework o dipendenze esterne (eccetto Google Fonts – Barlow Condensed).

---

## 📁 Struttura dei file

```
index.html                → Pagina principale del torneo
squadra.html              → Pagina di dettaglio singola squadra
risultatiCOMPLETO.json    → Calendario e risultati della fase a gironi
finali.json               → Partite e risultati delle fasi finali
```

---

## ⚽ Sezioni della pagina principale

| Tab | Contenuto |
|-----|-----------|
| 🏆 Classifica | Graduatoria automatica aggiornata in tempo reale |
| 📅 Calendario | Partite della fase a gironi, raggruppate per data |
| 🎯 Fasi Finali | Ottavi, Quarti, Semifinali, Finalissima |
| 👕 Squadre | Elenco delle 20 squadre con link al dettaglio |

---

## 🔧 Come aggiornare i risultati

### Fase a gironi → `risultatiCOMPLETO.json`

Ogni record rappresenta una partita. Campi principali:

```json
{
  "id": "match1",
  "giornata": 1,
  "data": "2026-05-16",
  "ora": "13:00",
  "casa": "NOME SQUADRA CASA",
  "trasferta": "NOME SQUADRA TRASFERTA",
  "golCasa": null,
  "golTrasferta": null
}
```

- **Partita non ancora giocata** → lasciare `"golCasa": null, "golTrasferta": null`
- **Partita giocata** → inserire i gol come numeri interi: `"golCasa": 2, "golTrasferta": 1`
- **Partita rinviata** → aggiungere `"rinviata": true` e opzionalmente `"label": "RINV."`
- **Risultato a tavolino** → aggiungere `"tavolino": true` (il risultato appare in grigio corsivo)

> ⚠️ I nomi delle squadre devono corrispondere **esattamente** (maiuscole incluse) a quelli presenti nella lista `SQUADRE` in `index.html` e nei link in `squadra.html`.

---

### Fasi finali → `finali.json`

Ogni record rappresenta una partita della fase finale. Struttura:

```json
{
  "fase": "Ottavi",
  "label": "Gara 1",
  "data": "2026-06-02",
  "ora": "15:00",
  "casa": "NOME SQUADRA CASA",
  "trasferta": "NOME SQUADRA TRASFERTA",
  "golCasa": null,
  "golTrasferta": null
}
```

- Il campo `"fase"` determina il colore del badge nella pagina squadra:

| Valore `fase` | Colore badge |
|--------------|--------------|
| `"Ottavi"` | 🔵 Blu |
| `"Quarti"` | 🟣 Viola |
| `"Semifinali"` | 🟠 Arancione |
| `"3° / 4° Posto"` | ⚫ Grigio |
| `"Finale"` | 🟡 Oro |

- **Prima della fase a gironi**: lasciare `"casa"` e `"trasferta"` con i placeholder (`"5ª classificata"` ecc.) e i gol a `null`
- **Dopo la fase a gironi**: sostituire i placeholder con i **nomi reali** delle squadre qualificate, mantenendo i gol a `null` finché non si gioca
- **Dopo ogni partita**: inserire i gol come numeri interi

> ⚠️ Anche qui i nomi devono corrispondere esattamente a quelli usati in `risultatiCOMPLETO.json` affinché la pagina squadra riconosca correttamente le partite.

---

## 🏆 Classifica automatica

La classifica viene calcolata in JavaScript a partire dai risultati in `risultatiCOMPLETO.json`. Non richiede intervento manuale.

**Punteggio:**
- Vittoria → 3 punti
- Pareggio → 1 punto
- Sconfitta → 0 punti

**Criteri di ordinamento (in ordine di priorità):**
1. Punti
2. Scontro diretto (solo tra due squadre a pari punti)
3. Differenza reti
4. Reti fatte
5. Ordine alfabetico

Le **prime 12 classificate** accedono alle fasi finali.

---

## 🎯 Fasi Finali — popolamento automatico in `index.html`

Le fasi finali si popolano **automaticamente** nella pagina principale una volta che tutti i risultati della fase a gironi sono inseriti:

**Ottavi di finale** (2 Giugno):
- Gara 1: 5ª vs 12ª
- Gara 2: 6ª vs 11ª
- Gara 3: 7ª vs 10ª
- Gara 4: 8ª vs 9ª

**Quarti di finale** (4 Giugno):
- 1ª vs Vincente Gara 4
- 2ª vs Vincente Gara 3
- 3ª vs Vincente Gara 2
- 4ª vs Vincente Gara 1

**Semifinali** (6 Giugno) e **Finalissime** (7 Giugno) si popolano dai risultati dei quarti.

> In caso di pareggio al termine dei tempi regolamentari, passa la **squadra meglio classificata** nella fase a gironi.

---

## 👤 Pagina singola squadra (`squadra.html`)

Accessibile cliccando su qualsiasi squadra (classifica, calendario o elenco squadre). Mostra:

- **📅 Fase a Gironi** — tutte le partite della squadra con data, ora, giornata e risultato colorato (🟢 vittoria / 🔴 sconfitta / 🟡 pareggio)
- **🎯 Fasi Finali** — le partite della squadra nelle fasi finali, con badge colorato per fase

I dati vengono letti rispettivamente da `risultatiCOMPLETO.json` e `finali.json`. Se `finali.json` non è ancora disponibile, la sezione mostra un messaggio neutro senza errori.

---

## 👕 Squadre partecipanti (20)

AUTOVIP S.M. · BARRIERA DI LANZO · BORGARO · CARRARA · CENTROCAMPO · CHISOLA · CIT TURIN · LASCARIS · LUCENTO BLU · LUCENTO ROSA · LUCENTO ROSSO · LUCENTO VERDE · P. BRUINESE · PINEROLO · POZZOMAINA · PRO COLLEGNO · SETTIMO · SISPORT · STS · VANCHIGLIA

---

## 🗓️ Calendario del torneo

| Fase | Date |
|------|------|
| Fase a gironi | 16 Maggio – 1 Giugno 2026 |
| Ottavi di finale | 2 Giugno 2026 |
| Quarti di finale | 4 Giugno 2026 |
| Semifinali | 6 Giugno 2026 |
| Finalissime (3°/4° e Finale) | 7 Giugno 2026 |

---

Organizzazione: **A.C.D. Lucento** – Torino

*© Al.Fa – Tutti i Diritti Riservati*
