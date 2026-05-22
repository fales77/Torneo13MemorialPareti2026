# 🏆 13° Memorial Sergio Pareti 2026

Applicazione web responsive per la gestione e visualizzazione del torneo **13° Memorial Sergio Pareti** – categoria **Esordienti 1° anno (Under 12)**, organizzato dall'**A.C.D. Lucento** di Torino.

Realizzata interamente in **HTML, CSS e JavaScript vanilla**, senza framework o dipendenze esterne (eccetto Google Fonts).

---

## 📁 Struttura dei file

```
index.html          → Pagina principale del torneo
risultati.json      → File dati con i risultati delle partite
squadra.html        → (collegato) Pagina di dettaglio singola squadra
```

---

## ⚽ Sezioni della pagina

La pagina è divisa in 4 sezioni, navigabili tramite una **barra di navigazione sticky** in cima:

| Sezione | Contenuto |
|---|---|
| 🏆 Classifica | Graduatoria automatica aggiornata in tempo reale |
| 📅 Calendario | Tutte le partite del girone con orari e risultati |
| 🎯 Fasi Finali | Ottavi, quarti, semifinali e finalissima |
| 👕 Squadre | Elenco delle 20 squadre partecipanti |

---

## 🏆 Classifica automatica

La classifica viene calcolata in JavaScript a partire dai risultati caricati da `risultati.json`, senza alcun dato hardcoded.

**Punteggio:**
- Vittoria → **3 punti**
- Pareggio → **1 punto**
- Sconfitta → **0 punti**

**Criteri di ordinamento (in caso di parità):**
1. Punti
2. Differenza reti (RF − RS)
3. Reti fatte (RF)
4. Ordine alfabetico

Le **prime 12 classificate** accedono alle fasi finali (evidenziate con bordo verde).

---

## 📅 Calendario e risultati

Le partite coprono **6 giornate** (dal 16 maggio al 31 maggio 2026), con partite distribuite su sabati, domeniche e qualche lunedì e venerdì.

I risultati vengono caricati da `risultati.json`. Ogni voce ha questa struttura:

```json
{
  "casa": "LASCARIS",
  "trasferta": "CIT TURIN",
  "golCasa": 5,
  "golTrasferta": 0
}
```

Se `golCasa` o `golTrasferta` sono `null`, la partita viene mostrata come non ancora disputata (`–`).

Le partite con risultato vengono marcate con la classe CSS `match-done`, che cambia il colore del punteggio in oro.

**Navigazione intelligente al Calendario:** cliccando su "Calendario" nella nav, la pagina scorre automaticamente alla prima partita non ancora disputata, evidenziata con un bordo dorato lampeggiante (`.partita-attiva`).

---

## 🎯 Fasi Finali — logica di popolamento automatico

Le fasi finali si popolano **dinamicamente** al termine del girone, seguendo questa catena:

### Ottavi di Finale (2 Giugno)
- Si attivano solo **quando tutte le partite del calendario sono state giocate**
- Gli accoppiamenti sono: 5ª vs 12ª, 6ª vs 11ª, 7ª vs 10ª, 8ª vs 9ª

### Quarti di Finale (5 Giugno)
- Le teste di serie (1ª–4ª) affrontano le vincitrici degli ottavi
- Abbinamenti: 1ª vs Vinc. Gara 4, 2ª vs Vinc. Gara 3, 3ª vs Vinc. Gara 2, 4ª vs Vinc. Gara 1

### Semifinali (6 Giugno)
- Vinc. 1° Quarto vs Vinc. 4° Quarto
- Vinc. 2° Quarto vs Vinc. 3° Quarto

### Finalissima (7 Giugno)
- Finale 3°/4° posto tra i perdenti delle semifinali
- **Finalissima** tra i vincitori delle semifinali (con animazione glow dorata)

**Regola pareggi nelle fasi finali:** in caso di parità al 90', passa la squadra **meglio classificata nel girone**.

---

## 🎨 Design e stile

- Tema **dark** con palette blu navy e oro, ispirata alla Champions League
- Font: **Barlow Condensed** (titoli/numeri) e **Barlow** (testo), via Google Fonts
- Completamente **responsive** con breakpoint a 480px per schermi mobile
- Animazione `glow` sulla card della Finalissima
- I nomi squadra in classifica sono **link** verso la pagina di dettaglio (`squadra.html?team=NOME`)

---

## 📋 Pagina dettaglio squadra (`squadra.html`)

Ogni squadra in classifica è un link cliccabile che apre la pagina di dettaglio della singola squadra:

```
squadra.html?team=NOME_SQUADRA
```

### Funzionamento

La pagina legge il parametro `team` dall'URL, poi esegue un `fetch("index.html")` per estrarre dinamicamente tutte le partite che coinvolgono quella squadra, senza duplicare dati.

Per ogni partita vengono mostrati:
- Orario e avversario
- Giornata di riferimento
- Risultato **colorato** in base all'esito per quella squadra:
  - 🟢 Verde → vittoria
  - 🔴 Rosso → sconfitta
  - 🟡 Giallo → pareggio
  - Trattino `—` → partita non ancora disputata

### Navigazione

Un pulsante **"← Torna"** fisso in alto a sinistra riporta alla pagina precedente (`history.back()`), compatibile sia con la navigazione da classifica che da qualsiasi altra origine.

---

## 🔧 Come aggiornare i risultati

1. Aprire `risultati.json`
2. Aggiungere o modificare una voce con i gol della partita
3. Salvare — la classifica e le fasi finali si aggiornano automaticamente al caricamento della pagina

Non è necessario modificare `index.html` per inserire risultati.

---

## 👥 20 Squadre partecipanti

Pinerolo · Autovip S.M. · Chisola · Vanchiglia · STS · Lucento Rosso · Lascaris · Borgaro · Pozzomaina · Sisport · Cit Turin · Pro Collegno · P. Bruinese · Lucento Verde · Lucento Blu · Carrara · Centrocampo · Barriera di Lanzo · Settimo · Lucento Rosa

---

*Organizzazione: A.C.D. Lucento · Torino · Maggio–Giugno 2026*
