***

# 📄 README.md

````markdown
# 🏆 13° Memorial Sergio Pareti 2026

Applicazione web semplice e responsive per la gestione e visualizzazione del torneo **13° Memorial Sergio Pareti** – categoria **Esordienti 1° anno (Under 12)**.

Realizzata interamente in **HTML, CSS e JavaScript vanilla**, senza framework esterni.

---

## ⚽ Struttura della pagina

La pagina è suddivisa in 4 sezioni principali:

- 🏆 **Classifica**
- 📅 **Calendario**
- 🎯 **Fasi finali**
- 👕 **Squadre**

Navigabili tramite tab sticky in alto.

---

## 🏆 Classifica automatica

La classifica viene calcolata automaticamente a partire dai risultati inseriti nel calendario.

### Logica di calcolo:

- ✅ Vittoria → 3 punti  
- ✅ Pareggio → 1 punto  
- ✅ Sconfitta → 0 punti  

### Ordinamento:

1. Punti
2. Differenza reti (DR)
3. Reti fatte (RF)
4. Ordine alfabetico

---

## 📅 Inserimento risultati

I risultati vengono inseriti **direttamente nell’HTML**, quindi:

```html
<span class="risultato-num">3</span>
<span class="risultato-sep">-</span>
<span class="risultato-num">1</span>
````

### Partite non giocate:



👉 Il trattino lungo (`–`) indica partita non disputata\
👉 Queste partite NON vengono considerate nel calcolo

***

## ⚙️ Funzionamento JavaScript

La funzione principale:

```javascript
calcolaClassifica()
```

*   Scansiona tutte le partite
*   Legge i risultati
*   Aggiorna le statistiche di ogni squadra
*   Genera dinamicamente la classifica

La classifica viene calcolata automaticamente al caricamento della pagina:

```javascript
window.addEventListener('load', calcolaClassifica);
```

***

## 🎨 UI / UX

### Layout responsive

*   Ottimizzato per **mobile e desktop**
*   Uso di `flex` e `grid` per allineamenti perfetti

### Migliorie implementate:

*   ✅ Navigazione sticky
*   ✅ Allineamento risultati stile app sportiva
*   ✅ Trattino centrato fisso tra i punteggi
*   ✅ Supporto numeri a doppia cifra senza rottura layout
*   ✅ Gestione nomi lunghi (wrap su mobile)

***

## 📊 Struttura dati squadre

Le squadre sono definite nel codice:

```javascript
const SQUADRE = [
  "PINEROLO",
  "AUTOVIP S.M.",
  ...
];
```

***

## 🚀 Come usare la pagina

1.  Aprire il file `index.html`
2.  Inserire i risultati modificando l’HTML
3.  Salvare
4.  Ricaricare la pagina

👉 La classifica si aggiorna automaticamente

***

## 🛠 Tecnologie utilizzate

*   HTML5
*   CSS3 (Flexbox + Grid)
*   JavaScript Vanilla

***

## ✨ Possibili sviluppi futuri

*   🎯 Evidenziazione automatica risultati (vittoria/sconfitta)
*   📊 Salvataggio dati (localStorage o backend)
*   📱 UI stile app (layout verticale squadre)
*   🧮 Tiebreak avanzati (scontri diretti)

***

## 📍 Autore Alessandro FAGA

Progetto realizzato per il torneo:

**A.C.D. Lucento – Torino**

***

## 🏁 Note

Questo progetto è volutamente **leggero e autonomo**, senza dipendenze esterne, per essere facilmente modificabile anche senza conoscenze avanzate di sviluppo web.



