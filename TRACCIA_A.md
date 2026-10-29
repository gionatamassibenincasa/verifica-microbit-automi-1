# TRACCIA A — Verifica Pratica sui Micro:bit

**Criterio di Assegnazione:**
Svolgi questa traccia **solo se** il tuo numero di registro rispetta la condizione:


$$\text{Numero di Registro} \pmod 3 = 1$$


*(Esempi: studenti numero 1, 4, 7, 10, 13, 16, ...)*

---

## 📦 Gestione dei Progetti e Modalità di Consegna

Poiché la verifica richiede la realizzazione di **5 progetti separati**, gestirai e consegnerai il lavoro tramite un unico repository GitHub legato a Classroom50 seguendo questa procedura:

1. **Creazione Progetto in MakeCode**:
* Per ogni esercizio, apri [makecode.microbit.org](https://makecode.microbit.org/).
* Crea un nuovo progetto nominando ciascun lavoro in modo chiaro: `Esercizio_1`, `Esercizio_2`, `Esercizio_3`, `Esercizio_4`, `Esercizio_5`.


2. **Esportazione dei File `.hex**`:
* Una volta completato un esercizio, fai clic sul pulsante **Salva** (icona del floppy disk in basso a sinistra) per scaricare sul computer il file del progetto con estensione `.hex` (es. `microbit-Esercizio_1.hex`).


3. **Caricamento su GitHub**:
* Accedi al repository GitHub creato da Classroom50 per la tua verifica.
* Fai clic su **Add file** $\rightarrow$ **Upload files**.
* Trascina o seleziona tutti e 5 i file `.hex` scaricati nella cartella principale del repository.
* Nel campo *Commit changes*, scrivi `"Consegna esercizi Traccia A"` e premi **Commit changes**.


4. **Conferma su Classroom50**:
* Torna sulla scheda della verifica su **Classroom50** e fai clic sul pulsante **Consegna / Submit** per confermare l'invio finale.



---

## 📝 Esercizi da Realizzare

---

### Esercizio 1: Sistema Reattivo Istantaneo (Mappatura Evento-Uscita)

Realizza un programma per la scheda Micro:bit che risponda immediatamente agli eventi dei pulsanti senza fare uso di variabili e senza memoria storica.

* **All'avvio**: Il display LED deve mostrare un'icona di benvenuto (Smile).


* **Pressione Tasto A**: Il display mostra una faccina triste (Sad).


* **Pressione Tasto B**: Il display mostra una faccina felice (Happy).


* **Pressione Tasti A+B**: Il display mostra un'icona di sorpresa (Surprised).



---

### Esercizio 2: Sistema Reattivo Istantaneo (Segnalatore di Direzione)

Realizza un secondo sistema reattivo privo di variabili di stato per indicare la direzione di un veicolo.

* **All'avvio**: Il display mostra un punto centrale.
* **Pressione Tasto A**: Mostra la freccia rivolta a SINISTRA (Ovest).
* **Pressione Tasto B**: Mostra la freccia rivolta a DESTRA (Est).
* **Pressione Tasti A+B**: Mostra l'icona di arresto (Icona NO / Crocetta).



---

### Esercizio 3: Automa con Memoria (Contatore Ciclico a 3 Fasi)

Gli automi con memoria mantengono lo stato del sistema all'interno di una variabile numerica. Realizza una sequenza ciclica di partenza per una gara ("Pronti, Partenza, Via!"):

* **Rappresentazione dello stato** via variabile `stato`:


* `0`: PRONTI (Mostra testo `"PRONTI"` o icona di attesa).


* `1`: PARTENZA (Mostra testo `"PARTENZA"` o icona intermedia).


* `2`: VIA! (Mostra testo `"VIA!"` o icona Spunta/Yes).




* **Funzione di Transizione**: Premendo ripetutamente il **pulsante B**, il sistema avanza ciclicamente attraverso le fasi ($0 \rightarrow 1 \rightarrow 2 \rightarrow 0$).


* **Reset**: Premendo i pulsanti **A+B**, lo `stato` torna immediatamente a `0`.

---

### Esercizio 4: Automa con Memoria da Tabella di Transizione (Semaforo)

Realizza un automa il cui comportamento è definito esplicitamente dalla variabile `stato` e gestito tramite la seguente tabella delle transizioni di stato:

#### Specifica degli Output:

* **Stato 0 (ROSSO)**: Il display mostra l'icona *NO* (o quadrato pieno).


* **Stato 1 (GIALLO)**: Il display mostra l'icona *DIAMANTE PICCOLO*.


* **Stato 2 (VERDE)**: Il display mostra l'icona *YES*.



#### Tabella delle Transizioni:

| Stato Corrente | Input Tasto A | Input Tasto B | Input Tasto A+B (Reset) | Output / Display |
| --- | --- | --- | --- | --- |
| **0 (ROSSO)** | Passa a **1** | Rimane in **0** | Passa a **0** | Icona NO

 |
| **1 (GIALLO)** | Rimane in **1** | Passa a **2** | Passa a **0** | Icona Diamante Piccolo

 |
| **2 (VERDE)** | Passa a **0** | Rimane in **2** | Passa a **0** | Icona YES

 |

*All'avvio, la variabile `stato` deve essere impostata a `0` e l'output deve mostrare lo Stato 0*.

---

### Esercizio 5: Riconoscimento di Sequenze (Cassaforte Digitale)

Realizza un automa a stati finiti in grado di riconoscere la sequenza di sblocco ordinata **Tasto A seguito da Tasto B**.

#### Specifica del Comportamento e della Tabella di Transizione:

Usa la variabile numerica `stato` con i seguenti valori:

* `0`: Bloccato (Attesa del tasto A).


* `1`: Cifra 1 Corretta (Attesa del tasto B).


* `2`: Sbloccato (Cassaforte aperta).



| Stato Corrente | Input Tasto A | Input Tasto B | Input Tasto A+B (Reset) | Output / Display |
| --- | --- | --- | --- | --- |
| **0 (Bloccato)** | Passa a **1** | Rimane in **0** | Passa a **0** | Icona NO / Chiuso

 |
| **1 (Attesa B)** | Rimane in **1** | Passa a **2** | Passa a **0** | Icona Diamante / Attesa

 |
| **2 (Sbloccato)** | Rimane in **2** | Rimane in **2** | Passa a **0** | Icona YES / Aperto

 |

* **Regola**: Qualsiasi pressione errata (es. premere B prima di A) mantiene il sistema bloccato in `stato = 0`. Una volta sbloccata, la cassaforte si riarma solo premendo la combinazione **A+B**.
