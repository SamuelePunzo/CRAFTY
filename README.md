# CRAFTY: Clustering and scRAping For biTcoin deanonYmization

## Introduzione
Questo repository contiene il codice e gli strumenti necessari per condurre analisi e tecniche di deanonimizzazione sulla blockchain di Bitcoin. Il progetto fornisce un DataSet di transazioni Bitcoin raccolte tra il blocco genesis (03-01-2009, 17:15:05) e il blocco di altezza 214562 (31-12-2012, 11:52:37). Il DataSet è stato elaborato per ridurne le dimensioni e preservare la privacy degli utenti.

## DataSet
Il DataSet è composto da quattro file CSV:

1. **transactions.csv**: Contiene le informazioni principali su ogni transazione.
    - timestamp: timestamp del blocco.
    - blockId: identificatore del blocco.
    - txId: identificatore unico della transazione.
    - isCoinbase: indica se la transazione è una Coinbase.
    - fee: eventuale commissione volontaria nella transazione.

2. **inputs.csv**: Contiene informazioni sugli input di ogni transazione.
    - txId: identificatore della transazione.
    - prevTxId: identificatore della transazione di output attualmente speso.
    - prevTxpos: posizione dell'output attualmente speso nella transazione di origine.

3. **outputs.csv**: Contiene informazioni sugli output di ogni transazione.
    - txId: identificatore della transazione.
    - position: posizione dell'output nella transazione.
    - addressId: identificatore univoco dell'indirizzo (mappato tramite il file di mapping).
    - amount: valore trasferito dall'output.
    - scripttype: tipo di script contenuto nell'output.

4. **mapping.csv**: File di mapping degli indirizzi.
    - hash: hash dell'indirizzo nella blockchain di Bitcoin.
    - addressId: identificatore unico mappato sull'indirizzo reale tramite il file di mapping.

## Analisi Effettuate
### 1. Analisi generali dei dati della blockchain
- Distribuzione del numero di transazioni per blocco.
- Evoluzione dell'occupazione dei blocchi nel tempo.
- Ammontare totale degli UTXO all'ultima transazione registrata.
- Distribuzione degli intervalli di tempo tra la generazione e il consumo di un UTXO.

### 2. Clusterizzazione degli indirizzi di Bitcoin: euristica multi-input
- Implementazione di un algoritmo di clustering basato sull'euristica descritta.
- Produzione di statistiche descrittive del clustering ottenuto.

### 3. Deanonimizzazione degli indirizzi
- Utilizzo di web scraper per deanonimizzare gli indirizzi dei 10 cluster più grandi.
- Analisi su WalletExplorer e BitInfoCharts per associare indirizzi a servizi noti.

## Requisiti di Sistema
- Python 3.x
- Pacchetti Python: pandas, matplotlib, requests, BeautifulSoup
