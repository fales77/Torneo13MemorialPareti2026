🏆 13° Memorial Sergio Pareti 2026
Applicazione web responsive per la gestione e visualizzazione del torneo 13° Memorial Sergio Pareti – categoria Esordienti 1° anno (Under 12), organizzato dall'A.C.D. Lucento di Torino.
Realizzata interamente in HTML, CSS e JavaScript vanilla, senza framework o dipendenze esterne (eccetto Google Fonts).

📁 Struttura dei file
index.html          → Pagina principale del torneo
risultati.json      → File dati con calendario completo e risultati
squadra.html        → Pagina di dettaglio singola squadra


⚽ Sezioni della pagina
La pagina è divisa in 4 sezioni, navigabili tramite una barra di navigazione sticky in cima:

























SezioneContenuto🏆 ClassificaGraduatoria automatica aggiornata in tempo reale📅 CalendarioCalendario dinamico generato da JSON🎯 Fasi FinaliOttavi, quarti, semifinali e finalissima👕 SquadreElenco delle 20 squadre partecipanti

🏆 Classifica automatica
La classifica viene calcolata in JavaScript a partire dai risultati caricati da risultati.json, senza alcun dato hardcoded.
Punteggio:

Vittoria → 3 punti
Pareggio → 1 punto
Sconfitta → 0 punti

Criteri di ordinamento (in caso di parità):

Punti
Differenza reti (RF − RS)
Reti fatte (RF)
Ordine alfabetico

Le prime 12 classificate accedono alle fasi finali (evidenziate con bordo verde).

📅 Calendario dinamico e risultati
Il calendario delle partite non è più presente staticamente nell’HTML, ma viene generato dinamicamente tramite JavaScript a partire dal file risultati.json.
✅ Struttura dati
Ogni partita è definita nel JSON con questo formato:
JSON{  "data": "2026-05-16",  "ora": "13:00",  "casa": "CIT TURIN",  "trasferta": "PRO COLLEGNO",  "giornata": 1,  "golCasa": null,  "golTrasferta": null}Mostra più linee
✅ Funzionamento


Le partite vengono:

✅ raggruppate automaticamente per data
✅ ordinate per orario
✅ renderizzate nel DOM con lo stesso layout grafico originale



Se golCasa o golTrasferta sono null:

la partita viene mostrata come non giocata (–)



Se entrambe hanno un valore:

la partita viene marcata con la classe CSS match-done




✅ Vantaggi del nuovo sistema

✅ Nessun calendario manuale in HTML
✅ Unica fonte dati → risultati.json
✅ Nessun rischio di inconsistenza tra calendario e risultati
✅ Aggiornamenti immediati modificando solo il JSON


🧭 Navigazione intelligente
Cliccando su “Calendario” nella navbar:

la pagina scorre automaticamente alla prima partita non disputata
questa viene evidenziata con un bordo dorato (.partita-attiva)


🎯 Fasi Finali — logica automatica
Le fasi finali si popolano dinamicamente seguendo la classifica.

✅ Ottavi di Finale (2 Giugno)

Si attivano solo quando tutte le partite del girone sono concluse
Accoppiamenti:

5ª vs 12ª
6ª vs 11ª
7ª vs 10ª
8ª vs 9ª




✅ Quarti di Finale (5 Giugno)

Le prime 4 classificate entrano direttamente
Accoppiamenti:

1ª vs Vinc. Gara 4
2ª vs Vinc. Gara 3
3ª vs Vinc. Gara 2
4ª vs Vinc. Gara 1




✅ Semifinali (6 Giugno)

Vinc. Quarto 1 vs Vinc. Quarto 4
Vinc. Quarto 2 vs Vinc. Quarto 3


✅ Finali (7 Giugno)

Finale 3° / 4° posto
Finalissima tra i vincitori delle semifinali


⚠️ Regola pareggi
In caso di parità:
👉 passa la squadra meglio classificata nel girone

✏️ Inserimento risultati fasi finali
A differenza del calendario:
👉 i risultati di ottavi, quarti, semifinali e finale vengono inseriti direttamente nell’HTML, modificando i valori:
HTML<span class="risultato-num">2</span><span class="risultato-num">1</span>Mostra più linee
Il sistema aggiorna automaticamente le fasi successive.

🎨 Design e stile

Tema dark stile Champions League (blu navy + oro)
Font: Barlow Condensed (titoli) e Barlow (testo)
Layout completamente responsive
Animazione glow sulla finalissima
Squadre cliccabili → link a squadra.html


📋 Pagina dettaglio squadra (squadra.html)
La pagina mostra tutte le partite della squadra selezionata:
squadra.html?team=NOME_SQUADRA

✅ Funzionamento

Legge il parametro team
Filtra dinamicamente le partite dal DOM del calendario

✅ Colori risultato

🟢 Vittoria
🔴 Sconfitta
🟡 Pareggio
– Non giocata


🔧 Come aggiornare i risultati
✅ Fase a gironi

Modificare risultati.json
Inserire i gol
Salvare

👉 calendario e classifica si aggiornano automaticamente

✅ Fasi finali

Modificare direttamente l’HTML
Inserire i risultati nella partita

👉 le fasi successive si aggiornano automaticamente

👥 20 Squadre partecipanti
Pinerolo · Autovip S.M. · Chisola · Vanchiglia · STS · Lucento Rosso · Lascaris · Borgaro · Pozzomaina · Sisport · Cit Turin · Pro Collegno · P. Bruinese · Lucento Verde · Lucento Blu · Carrara · Centrocampo · Barriera di Lanzo · Settimo · Lucento Rosa

Organizzazione: A.C.D. Lucento · Torino · Maggio–Giugno 2026
