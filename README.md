# 🏆 13° Memorial Sergio Pareti 2026

Applicazione web responsive per la gestione e visualizzazione del torneo **13° Memorial Sergio Pareti** – categoria **Esordienti 1° anno (Under 12)**, organizzato dall'**A.C.D. Lucento** di Torino.

Realizzata interamente in **HTML, CSS e JavaScript vanilla**, senza framework o dipendenze esterne (eccetto Google Fonts).

---

## 📁 Struttura dei file

index.html          → Pagina principale del torneo
risultati.json      → File dati con calendario completo e risultati
squadra.html        → Pagina di dettaglio singola squadra

---

## ⚽ Sezioni della pagina

- 🏆 Classifica → Graduatoria automatica aggiornata in tempo reale
- 📅 Calendario → Calendario dinamico generato da JSON
- 🎯 Fasi Finali → Ottavi, quarti, semifinali e finalissima
- 👕 Squadre → Elenco delle 20 squadre partecipanti

---

## 🏆 Classifica automatica

La classifica viene calcolata in JavaScript a partire dai risultati caricati da `risultatiCOMPLETO.json`, senza alcun dato hardcoded.

Punteggio:
- Vittoria → 3 punti
- Pareggio → 1 punto
- Sconfitta → 0 punti

Criteri di ordinamento:
1. Punti
2. Differenza reti
3. Reti fatte
4. Ordine alfabetico

Le prime 12 squadre accedono alle fasi finali.

---

## 📅 Calendario dinamico

Il calendario viene generato automaticamente dal file `risultatiCOMPLETO.json`.

Ogni partita include:
- data
- ora
- squadra casa
- squadra trasferta
- giornata
- risultato

Se i gol sono null → partita non giocata (–)
Se presenti → partita marcata come giocata (match-done)

Vantaggi:
- nessun HTML manuale
- unica fonte dati
- aggiornamenti immediati

---

## 🎯 Fasi Finali

Le fasi finali si popolano automaticamente:

Ottavi:
- 5ª vs 12ª
- 6ª vs 11ª
- 7ª vs 10ª
- 8ª vs 9ª

Quarti:
- 1ª vs vincente ottavi
- 2ª vs vincente
- 3ª vs vincente
- 4ª vs vincente

Semifinali e Finale generate automaticamente.

Pareggio:
→ passa la meglio classificata

I risultati delle fasi finali si inseriscono direttamente nell’HTML.

---

## 🔧 Aggiornamento risultati

Gironi:
→ modificare risultati.json

Fasi finali:
→ modificare HTML

---

## 👥 Squadre

20 squadre partecipanti

---

Organizzazione: A.C.D. Lucento – Torino
