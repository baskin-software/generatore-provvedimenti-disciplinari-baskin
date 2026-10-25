# Generatore Provvedimenti Disciplinari Baskin

Pagina HTML unica, da aprire nel browser (anche offline e da cellulare) o da usare online, che aiuta il Giudice Unico a scrivere i provvedimenti disciplinari del Baskin:

* **cerca** nel Regolamento Disciplinare (artt. 89-158 del Regolamento Tecnico Nazionale della Disciplina Baskin 2026) e tra 160 **provvedimenti tipo** già formulati sul testo del regolamento, con articolo, comma, tabella e sanzione;
* **compone** la riga del provvedimento con gara, destinatario, parti variabili e aggiunte facoltative;
* produce un **testo da copiare**, modificabile a mano, da incollare nel foglio `Provvedimenti Disciplinari` del calendario e nella mail di comunicazione.

Nulla viene salvato né inviato: vedi [Privacy](#privacy).

* **Usalo online**: <https://baskin-software.github.io/generatore-provvedimenti-disciplinari-baskin/> (versione di prova: <https://baskin-software.github.io/generatore-provvedimenti-disciplinari-baskin/beta/>)
* **Codice sorgente**: <https://github.com/baskin-software/generatore-provvedimenti-disciplinari-baskin> (organizzazione GitHub [baskin-software](https://github.com/baskin-software))

## File

| File | Contenuto |
| --- | --- |
| `Generatore_Provvedimenti_Baskin.html` | Il generatore (unico file, nessuna dipendenza) |
| `README.md` | Questo documento |
| `LICENSE` | Licenza MIT del codice e ambito delle licenze |
| `LICENSE-CC-BY-4.0.md` | Licenza CC BY 4.0 dei testi propri |
| `CITATION.cff` | Come citare il progetto |
| `.github/workflows/pages.yml` | Azione GitHub che pubblica il generatore su GitHub Pages |
| `.github/workflows/build_site.sh` | Prepara il sito con le versioni dei rami principale e `beta` |

## Uso

1. **Gara**: numero e data della gara e Massimale Ammende del campionato (preimpostato a 1.000 euro, modificabile). Restano validi per tutti i provvedimenti finché non li cambi. La casella *Inizia ogni riga con numero e data della gara* aggiunge in testa a ogni riga `Gara n. … del …`.
2. **Destinatario**: cognome, nome, Società e qualifica del tesserato; per i provvedimenti contro una Società basta il nome della Società (gli altri campi si nascondono).
3. **Cerca nel regolamento**: scrivi condotta, sanzione o numero di articolo (vedi [Ricerca](#ricerca)). Compaiono i provvedimenti tipo (`T` tesserato, `S` Società) e gli articoli che contengono le parole cercate, evidenziate. *Leggi art. N* apre il testo dell'articolo.
4. **Provvedimento**: tocca un provvedimento tipo e completa le parti variabili (scelte alternative, numero di gare, punti, descrizioni). Le **aggiunte facoltative** sono:
   * prima del riferimento normativo: *(espulso)*, *a fine gara*, *come da rapporto arbitrale* e *come da segnalazione degli Ufficiali di Campo*;
   * dopo il riferimento: recidiva (art. 110), circostanze attenuanti o aggravanti (artt. 107-108), sanzione raddoppiata (art. 112 c. 3 e art. 117 c. 6) e commutazione della squalifica (art. 100 c. 5 e art. 103 c. 2).
   
   L'anteprima si aggiorna mentre scrivi. Se scegli una squalifica per un dirigente o un altro tesserato che non sia atleta o allenatore compare l'avviso dell'art. 100 c. 2.
5. **Aggiungi e resetta** mette la riga nel testo e riporta al destinatario per il provvedimento successivo: destinatario, provvedimento, aggiunte e ricerca si azzerano, mentre gara e massimale restano. **Aggiungi senza resettare** lascia tutto com'è, per più provvedimenti simili o per lo stesso destinatario.
6. **Testo da copiare**: una riga per provvedimento, sempre modificabile a mano. **Copia** copia esattamente quello che si vede.

### Dove incollare

* **Foglio `Provvedimenti Disciplinari` del calendario** (una riga per gara): numero di gara in colonna `A`. Poi seleziona la cella in colonna `B`, premi **F2** (o doppio clic) **prima** di incollare con `Ctrl+V`: così tutte le righe restano nella stessa cella, andando a capo. Senza F2 Excel distribuisce le righe su più celle.
  * Vale anche per LibreOffice.
  * In Google Sheets: doppio clic sulla cella (o `Invio`) e poi incolla.
  * In Excel su Mac: `Ctrl+U` al posto di F2.
* **Mail di comunicazione**: incolla direttamente nel corpo del messaggio.

Ogni gara ha una sola cella: prepara insieme tutti i provvedimenti della stessa gara, poi cambia numero di gara e premi **Svuota**.

### Esempio di riga

```
Gara n. 12 del 18/10/2026 – ROSSI Mario (ASD Esempio), atleta – squalifica per 1 gara e ammenda di Euro 40,00 per comportamento offensivo nei confronti degli arbitri (espulso) [art. 117 c. 1 Tab. C n. 2 RTN]
```

## Pubblicazione online (GitHub Pages)

Il generatore si può usare anche online. L'azione GitHub `.github/workflows/pages.yml` pubblica su GitHub Pages solo `Generatore_Provvedimenti_Baskin.html`, a ogni modifica del file oppure a mano dalla scheda *Actions*:

* la versione del ramo principale (`main`, oppure `master` se `main` non c'è) all'indirizzo del sito, <https://baskin-software.github.io/generatore-provvedimenti-disciplinari-baskin/>;
* quella del ramo `beta` (se esiste) nella sottocartella `/beta/` (<https://baskin-software.github.io/generatore-provvedimenti-disciplinari-baskin/beta/>), così si può provare una versione nuova senza toccare quella in uso.

Se il ramo principale non esiste si pubblica solo `beta` e l'indirizzo del sito rimanda a `/beta/`. La preparazione del sito è nello script `.github/workflows/build_site.sh`.

Per attivarla, una sola volta: *Settings* → *Pages* → *Build and deployment* → *Source*: **GitHub Actions**.

GitHub Pages accetta pubblicazioni solo dal ramo predefinito. Un push sul ramo `beta` rilancia quindi l'azione sul ramo predefinito, che ricostruisce il sito leggendo l'HTML da tutti i rami, senza modificare le regole di protezione dell'ambiente `github-pages`. Per questo i file in `.github/workflows` devono essere presenti, aggiornati, anche nel ramo predefinito.

Anche online tutto resta nel browser: il server di GitHub registra solo i normali dati tecnici di accesso (vedi [Privacy](#privacy)).

## Ricerca

| Scrivi | Trova |
| --- | --- |
| `offese pubblico` | voci con **tutte** le parole |
| `+pivot` | parola obbligatoria (equivale a scriverla senza segno) |
| `ruolo -pivot` | voci con *ruolo* ma **senza** *pivot* |
| `"fase di gioco"` | la frase esatta |
| `avversari -"fase di gioco"` | voci con *avversari* senza la frase esatta |
| `117` | voci e testo che contengono il numero (es. art. 117) |

Maiuscole, accenti e apostrofi tipografici non contano; `Esc` svuota la ricerca. Con più di 8 articoli trovati gli articoli restano chiusi (si aprono toccandoli).

## Massimale Ammende

Le ammende del regolamento sono percentuali del Massimale Ammende stabilito ogni anno nelle Disposizioni Organizzative Annuali (art. 99). Il generatore calcola l'importo arrotondato all'euro; se la casella è vuota scrive la percentuale tra parentesi quadre (es. `Euro [4% del Massimale Ammende]`).

Il valore proposto all'apertura (1.000 euro) si cambia nel codice, all'inizio dello script, nel blocco segnalato da `MODIFICA QUI`:

```js
var MASSIMALE_AMMENDE_PREDEFINITO = 1000;
```

Con `0` la casella parte vuota.

## Formule dei provvedimenti tipo

Le formule seguono il testo del Regolamento Disciplinare così com'è, senza correzioni o interpretazioni dei refusi. La struttura è sempre:

```
[Gara n. N del gg/mm/aaaa –] DESTINATARIO – sanzione per condotta [circostanze] [riferimento RTN][, aggiunte con proprio riferimento]
```

Coprono:

* il pubblico (art. 111 Tab. A e art. 112);
* invasione e aggressione (artt. 113-115);
* le proteste (art. 116);
* i comportamenti verso arbitri, avversari e altri tesserati (art. 117 Tab. C, D, E);
* i comportamenti non regolamentari (art. 118 Tab. F1 e art. 119);
* ruoli e arruolamento degli atleti (art. 118 Tab. F2);
* le infrazioni amministrative (art. 121 Tab. G) e le attrezzature (art. 122 Tab. H);
* le altre infrazioni (artt. 123-131).

Dove una sanzione colpisce soggetti diversi (es. Tab. F2: Società e allenatore) ci sono due voci separate, una per destinatario. La valutazione dei fatti, delle circostanze, della recidiva e della sanzione resta dell'Organo di Giustizia.

## Privacy

* Tutto avviene nel browser: la pagina non invia dati e non fa richieste in rete. Una Content-Security-Policy interna (`default-src 'none'`) blocca connessioni e risorse esterne.
* Nessun cookie, localStorage, sessionStorage, IndexedDB o altro archivio del browser; nessuna statistica o tracciamento. Chiudendo o ricaricando la pagina si perde tutto.
* Completamento automatico e controllo ortografico disattivati in tutte le caselle: il browser non memorizza nomi e testi e non li invia a servizi di correzione online.
* Il testo va negli appunti solo premendo **Copia**. Può restare nella cronologia degli appunti del sistema (es. `Win+V` in Windows).
* Se la pagina è pubblicata su un sito, il server che la ospita può registrare i normali dati tecnici di accesso. Da file salvato sul computer non c'è alcun contatto con internet.
* I provvedimenti contengono dati personali: chi li inserisce, invia o pubblica ne è responsabile (GDPR).

## Licenza

* **Codice** (`Generatore_Provvedimenti_Baskin.html`, esclusi i testi del regolamento, e script e workflow in `.github`): licenza MIT, vedi `LICENSE`.
* **Testi propri** (formule dei provvedimenti tipo, istruzioni, `README.md`): licenza CC BY 4.0, vedi `LICENSE-CC-BY-4.0.md`.
* **Testo del Regolamento Disciplinare**: appartiene a EISI (Ente Italiano Sport Inclusivi) ed è riportato così com'è per sola consultazione. Non è coperto da queste licenze e fa fede la versione ufficiale pubblicata da EISI.

Nomi e loghi **Baskin** ed **EISI** appartengono ai rispettivi titolari. Progetto personale, non prodotto ufficiale di EISI né di altri enti; fornito così com'è, senza garanzie.

© 2026 Daniele Lolli (UncleDan) feat. Claude AI
