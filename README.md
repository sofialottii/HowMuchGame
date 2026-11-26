# Quanto costa?
 
Un gioco multiplayer in cui si indovina il prezzo di oggetti più o meno assurdi: dal casco di Iron Man alla crescia di Urbino. Tutti i giocatori vedono lo stesso oggetto, scrivono la cifra che ritengono giusta e vince il punto chi si avvicina di più.

## Disclaimer

Il gioco è stato creato per una festa di laurea e può essere modificabile, rendendolo dinamico e creando, con poche modifiche, la possibilità di aggiungere nuovi articoli (o eliminare quelli già inseriti) direttamente dal sito web. Sentiti libero di contattarmi se ne hai la necessità.
 
## Come si gioca
 
1. **Il master crea la stanza.** Inserisce il suo nome e preme *Crea una stanza*. Compare un codice di 4 caratteri.
2. **Gli altri entrano.** Aprono il sito, scrivono il nome, inseriscono il codice e premono *Entra nella stanza*.
3. **Il master avvia la partita.** Sceglie quanti oggetti giocare (5, 10, 15, 20 o tutti) e preme *Inizia la partita*.
4. **Ogni round.** Compare un oggetto con la sua immagine. Ognuno ha 30 secondi per scrivere un prezzo in euro e premere *Fatto*.
5. **Il risultato.** Si scopre il prezzo reale e chi è andato più vicino guadagna 1 punto.
6. **Classifica finale.** Dopo l’ultimo oggetto vince chi ha più punti. Il master può far ripartire una nuova partita nella stessa stanza.
## Regole
 
- Vince il round chi ha la risposta più vicina al prezzo reale, **in valore assoluto**. Non conta se si è sbagliato per eccesso o per difetto.
- In caso di pareggio il punto va a tutti i giocatori a pari merito.
- Se tutti i giocatori premono *Fatto*, il round finisce subito, senza aspettare i 30 secondi.
- Se il tempo scade, viene inviata in automatico la cifra che il giocatore aveva scritto nel campo, anche se non aveva premuto *Fatto*. Chi non ha scritto nulla non partecipa a quel round.
- Il master gioca come tutti gli altri.
- Chi arriva a partita già iniziata non può entrare.
- Si possono usare sia il punto sia la virgola (`24,90` oppure `24.90`).

 
### Struttura del repository
 
```
.
├── index.html
├── css
├   ├── style.css
├── README.md
└── img/            # le immagini degli oggetti
    ├── ironman.png
    ├── zelda.jpg
    └── ...
```
 
## Come aggiungere nuovi oggetti
 
Gli oggetti sono nell’array `ITEMS`, all’inizio del blocco `<script>` di `index.html`. Ogni oggetto ha questo formato:
 
```js
{img:"img/zelda.jpg", name:"The Legend of Zelda", desc:"Copia originale del primo gioco", price:793065}
```
 
| Campo   | Significato                                                        |
|---------|--------------------------------------------------------------------|
| `img`   | Percorso dell’immagine, dentro la cartella `img/`                  |
| `name`  | Titolo mostrato sul cartellino                                     |
| `desc`  | Sottotitolo (può essere una stringa vuota `""`)                    |
| `price` | Prezzo reale in euro, come numero (usa il punto per i decimali: `5.5`) |
 
Per aggiungere un oggetto basta mettere l’immagine in `img/` e aggiungere una riga all’array. Il menu *Tutti* si adatta da solo al numero di oggetti presenti.
 
Altre impostazioni si trovano all’inizio dello script:
 
- `TIME`: durata di ogni round in millisecondi (30000 = 30 secondi).
- `PREFIX`: prefisso dell’identificativo delle stanze. Cambialo se vuoi evitare conflitti con altre copie del gioco.

## Tecnologie
 
HTML, CSS e JavaScript senza framework, più PeerJS caricato da CDN.
 
