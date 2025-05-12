# EMit Emotion Detection con Fine-Tuning di LLM

Questo repository contiene il codice, i dati e le risorse per la sperimentazione di fine tuning su un modello volto al riconoscimento automatico di emozioni in testi provenienti dai social media.

L'obiettivo principale di questa fase è prendere familiarità con tecniche di fine-tuning di LLM e affrontare le sfide comuni del processo.

## Obiettivi

* Acquisire esperienza pratica nel fine-tuning di modelli Transformer per task di classificazione multilabel.
* Affrontare e risolvere difficoltà tipiche come sbilanciamento delle classi, selezione e calibrazione della loss, tuning di iperparametri, ecc...
* Impostare una pipeline riproducibile e documentata per estensioni future.

## Struttura

* `Emit_finetuning.ipynb`: notebook Jupyter che contiene l'intera pipeline di fine-tuning.
* `data/`: directory contenente i dataset EMit utilizzati.
* `fine_tuned_umberto_emotions.zip`: archivio con i file del modello fine-tunato.
* `.requirements.txt`: file con la lista delle dipendenze.

## Passaggi della pipeline

### 1. Setup e preparazione dell'ambiente

* Installazione delle dipendenze principali (`transformers`, `datasets`, `wandb`, ecc.).
* Configurazione di WandB per il monitoraggio esperimenti.

### 2. Preprocessing e analisi dati

* Caricamento dataset e analisi iniziale della distribuzione delle classi.
* Pulizia minima dei testi specifica per social media italiani (gestione URL, menzioni, hashtag ed emoji).

### 3. Split stratificato multilabel

* Divisione del dataset in train e validation mantenendo distribuzioni multilabel coerenti (90/10).

### 4. Baseline: TF-IDF + Logistic Regression

* Implementazione di una baseline per avere un punto di riferimento iniziale (macro-F1).

### 5. Preparazione dataset Hugging Face

* Tokenizzazione dei dati e conversione in formato compatibile con Hugging Face datasets.

### 6. Fine-tuning del modello UmBERTo

* Selezione e inizializzazione di UmBERTo (`Musixmatch/umberto-commoncrawl-cased-v1`).
* Impostazione iniziale del bias del classificatore con prevalenza delle classi per migliorare la convergenza.
* Uso di BCE pesata (`pos_weight`) per gestire lo sbilanciamento.
* Configurazione iperparametri.

### 7. Calibrazione delle soglie

* Tuning delle soglie post-training sulla validation set per massimizzare la Macro-F1.

### 8. Valutazione finale

* Calcolo delle metriche finali (Macro-F1 e classification report dettagliato per classe).

## Difficoltà incontrate

* **Gestione del multilabel imbalance**: Risolta utilizzando `pos_weight` e inizializzando opportunamente il bias.
* **Type e device mismatch**: Risolto adattando custom Trainer e gestione esplicita dei tensori (CPU/GPU).
* **Calibrazione delle soglie**: Necessaria per massimizzare la performance reale sul test set.

## Risultati ottenuti

Dopo il fine-tuning con i parametri ottimizzati, abbiamo ottenuto:

* Macro-F1 iniziale TF-IDF+LR: 0.16 (baseline)
* Macro-F1 dopo fine-tuning UmBERTo senza calibrazione soglie: \~0.47
* Macro-F1 finale dopo calibrazione soglie: \~0.51

Questi risultati evidenziano come il fine-tuning di LLM su task multilabel possa fornire notevoli miglioramenti rispetto ad approcci tradizionali, ma sottolineano anche l'importanza della gestione fine di soglie, loss e regolarizzazioni.

## Prossimi passi

* Implementare ulteriori tecniche di regolarizzazione (dropout, focal loss).
* Data augmentation per classi rare.
* Valutare architetture più grandi per ulteriori miglioramenti.
