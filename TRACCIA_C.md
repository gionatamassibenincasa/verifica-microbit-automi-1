# TRACCIA C — Verifica Pratica sui Micro:bit

**Criterio di Assegnazione:**
Svolgi questa traccia **solo se** il tuo numero di registro rispetta la condizione:

$$
\text{Numero di Registro} \pmod 3 = 0
$$

*(Esempi: studenti numero 3, 6, 9, 12, 15, 18, ...)*

## 📦 Gestione dei Progetti e Modalità di Consegna

Poiché la verifica richiede la realizzazione di **5 progetti separati**, gestirai e consegnerai il lavoro tramite un unico repository GitHub legato a Classroom50 seguendo questa procedura:

1. **Creazione Progetto in MakeCode**:
   * Per ogni esercizio, apri [makecode.microbit.org](https://makecode.microbit.org/).
   * Crea un nuovo progetto nominando ciascun lavoro in modo chiaro: `Esercizio_1`, `Esercizio_2`, `Esercizio_3`, `Esercizio_4`, `Esercizio_5`.

2. **Esportazione dei File `.hex`**:
   * Una volta completato un esercizio, fai clic sul pulsante **Salva** (icona del floppy disk in basso a sinistra) per scaricare sul computer il file del progetto con estensione `.hex` (es. `microbit-Esercizio_1.hex`).

3. **Caricamento su GitHub**:
   * Accedi al repository GitHub creato da Classroom50 per la tua verifica.
   * Fai clic su **Add file** $\rightarrow$ **Upload files**.
   * Trascina o seleziona tutti e 5 i file `.hex` scaricati nella cartella principale del repository.
   * Nel campo *Commit changes*, scrivi `"Consegna esercizi Traccia C"` e premi **Commit changes**.

4. **Conferma su Classroom50**:
   * Torna sulla scheda della verifica su **Classroom50** e fai clic sul pulsante **Consegna / Submit** per confermare l'invio finale.

---

## 📝 Esercizi da Realizzare

---

### Esercizio 1: Sistema Reattivo Istantaneo (Mappatura Evento-Uscita)
Realizza un programma per la scheda Micro:bit che risponda immediatamente agli eventi dei pulsanti senza fare uso di variabili e senza memoria storica.

* **All'avvio**: Il display LED mostra un'icona di benvenuto (Musa / Note Musicali).
* **Pressione Tasto A**: Il display mostra un'icona a forma di Farfalla (o Anatra).
* **Pressione Tasto B**: Il display mostra un'icona a forma di Fantasma.
* **Pressione Tasti A+B**: Il display mostra un'icona a forma di Pacman (o Serpente).

---

### Esercizio 2: Sistema Reattivo Istantaneo (Indicatore di Marcia Veicolo)
Realizza un secondo sistema reattivo privo di variabili di stato per indicare la direzione di marcia.

* **All'avvio**: Il display mostra un punto centrale.
* **Pressione Tasto A**: Mostra la freccia rivolta in AVANTI (Nord).
* **Pressione Tasto B**: Mostra la freccia rivolta in RETROMARCIA (Sud).
* **Pressione Tasti A+B**: Mostra l'icona di STOP (Icona NO / Crocetta).

---

### Esercizio 3: Automa con Memoria (Selettore Modalità Luce Ciclica)
Gli automi con memoria mantengono lo stato del sistema all'interno di una variabile numerica. Realizza un selettore per un sistema di illuminazione a 3 livelli ("Spento, Eco, Max"):

* **Rappresentazione dello stato** via variabile `modalita_luce`:
  * `0`: SPENTO (Display completamente spento o icona "LUMACA").
  * `1`: ECO (Mostra un quadrato piccolo al centro o icona "DIAMANTE PICCOLO").
  * `2`: MAX (Mostra un quadrato grande pieno o icona "SOLE").
* **Funzione di Transizione**: Premendo ripetutamente il **pulsante B**, il sistema avanza ciclicamente attraverso le modalità ($0 \rightarrow 1 \rightarrow 2 \rightarrow 0$).
* **Reset**: Premendo i pulsanti **A+B**, la `modalita_luce` torna immediatamente a `0`.

---

### Esercizio 4: Automa con Memoria da Tabella di Transizione (Controllo Cancello)
Realizza un automa il cui comportamento è definito esplicitamente dalla variabile `stato_cancello` e gestito tramite la seguente tabella delle transizioni di stato:

#### Specifica degli Output:
* **Stato 0 (CHIUSO)**: Il display mostra l'icona *CASA*.
* **Stato 1 (IN APERTURA)**: Il display mostra l'icona *FRECCIA NORD*.
* **Stato 2 (APERTO)**: Il display mostra l'icona *YES* (o freccia destra/aperto).

#### Tabella delle Transizioni:

| Stato Corrente | Input Tasto A | Input Tasto B | Input Tasto A+B (Reset) | Output / Display |
| :--- | :--- | :--- | :--- | :--- |
| **0 (CHIUSO)** | Rimane in **0** | Passa a **1** | Passa a **0** | Icona Casa |
| **1 (IN APERTURA)** | Passa a **2** | Rimane in **1** | Passa a **0** | Icona Freccia Nord |
| **2 (APERTO)** | Passa a **0** | Rimane in **2** | Passa a **0** | Icona YES |

*All'avvio, la variabile `stato_cancello` deve essere impostata a `0` e l'output deve mostrare lo Stato 0.*

---

### Esercizio 5: Riconoscimento di Sequenze (Attivazione Macchinario)
Realizza un automa a stati finiti in grado di avviare un macchinario industriale solo dopo aver ricevuto la sequenza ordinata **Tasto A seguito da Tasto A**.

#### Specifica del Comportamento e della Tabella di Transizione:
Usa la variabile numerica `stato` con i seguenti valori:
* `0`: Bloccato / Spento (Attesa della prima pressione di A).
* `1`: Primo Impulso Ricevuto (Attesa della seconda pressione di A).
* `2`: Macchina In Funzione (Sistema avviato).

| Stato Corrente | Input Tasto A | Input Tasto B | Input Tasto A+B (Reset) | Output / Display |
| :--- | :--- | :--- | :--- | :--- |
| **0 (Spento)** | Passa a **1** | Rimane in **0** | Passa a **0** | Icona NO / Spento |
| **1 (Standby)** | Passa a **2** | Torna a **0** | Passa a **0** | Icona Diamante / Attesa |
| **2 (Avviato)** | Rimane in **2** | Rimane in **2** | Passa a **0** | Icona Giraffa / In Funzione |

* **Regola**: Se nello `stato = 1` si preme il tasto B anziché il tasto A, la sequenza si interrompe e il sistema torna allo `stato = 0`. Una volta avviata la macchina (`stato = 2`), per spegnerla e resettarla occorre premere la combinazione **A+B**.
