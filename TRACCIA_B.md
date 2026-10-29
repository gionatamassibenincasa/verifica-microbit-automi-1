# TRACCIA B — Verifica Pratica sui Micro:bit

**Criterio di Assegnazione:**
Svolgi questa traccia **solo se** il tuo numero di registro rispetta la condizione:
$$\text{Numero di Registro} \pmod 3 = 2$$
*(Esempi: studenti numero 2, 5, 8, 11, 14, 17, ...)*

---

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
   * Nel campo *Commit changes*, scrivi `"Consegna esercizi Traccia B"` e premi **Commit changes**.
4. **Conferma su Classroom50**:
   * Torna sulla scheda della verifica su **Classroom50** e fai clic sul pulsante **Consegna / Submit** per confermare l'invio finale.

---

## 📝 Esercizi da Realizzare

---

### Esercizio 1: Sistema Reattivo Istantaneo (Mappatura Evento-Uscita)
Realizza un programma per la scheda Micro:bit che risponda immediatamente agli eventi dei pulsanti senza fare uso di variabili e senza memoria storica.
* **All'avvio**: Il display LED mostra un'icona di benvenuto (Cuore).
* **Pressione Tasto A**: Il display mostra un'icona a forma di Stella (o Tartaruga).
* **Pressione Tasto B**: Il display mostra un'icona a forma di Casa.
* **Pressione Tasti A+B**: Il display mostra un'icona a forma di Teschio (o Dito in su).

---

### Esercizio 2: Sistema Reattivo Istantaneo (Indicatore di Temperatura Percepita)
Realizza un secondo sistema reattivo privo di variabili di stato per indicare visivamente lo stato termico.
* **All'avvio**: Il display mostra un punto centrale.
* **Pressione Tasto A**: Mostra l'icona Freddo/Neve (Fiocco di neve o Diamante piccolo).
* **Pressione Tasto B**: Mostra l'icona Caldo/Sole (Sole o Quadrato grande).
* **Pressione Tasti A+B**: Mostra l'icona Temperatura Normale (Icona Spunta / YES).

---

### Esercizio 3: Automa con Memoria (Selettore Livello Volume Ciclico)
Gli automi con memoria mantengono lo stato del sistema all'interno di una variabile numerica. Realizza un selettore di volume a 3 livelli ("Basso, Medio, Alto"):
* **Rappresentazione dello stato** via variabile `livello_volume`:
  * `0`: BASSO (Mostra una sola riga/punto di LED o icona "LUMACA").
  * `1`: MEDIO (Mostra tre righe/punti di LED o icona "TARTARUGA").
  * `2`: ALTO (Mostra display pieno di LED o icona "CONIGLIO").
* **Funzione di Transizione**: Premendo ripetutamente il **pulsante A**, il sistema avanza ciclicamente attraverso i livelli ($0 \rightarrow 1 \rightarrow 2 \rightarrow 0$).
* **Reset**: Premendo i pulsanti **A+B**, il `livello_volume` torna immediatamente a `0`.

---

### Esercizio 4: Automa con Memoria da Tabella di Transizione (Selettore di Modalità)
Realizza un automa il cui comportamento è definito esplicitamente dalla variabile `modalita` e gestito tramite la seguente tabella delle transizioni di stato:

#### Specifica degli Output:
* **Stato 0 (OROLOGIO)**: Il display mostra l'icona *SVEGLIA*.
* **Stato 1 (CRONOMETRO)**: Il display mostra l'icona *GIRAFFA*.
* **Stato 2 (ALLARME)**: Il display mostra l'icona *LUMACA*.

#### Tabella delle Transizioni:

| Stato Corrente | Input Tasto A | Input Tasto B | Input Tasto A+B (Reset) | Output / Display |
| :--- | :--- | :--- | :--- | :--- |
| **0 (OROLOGIO)** | Passa a **1** | Rimane in **0** | Passa a **0** | Icona Sveglia |
| **1 (CRONOMETRO)** | Rimane in **1** | Passa a **2** | Passa a **0** | Icona Giraffa |
| **2 (ALLARME)** | Rimane in **2** | Passa a **0** | Passa a **0** | Icona Lumaca |

*All'avvio, la variabile `modalita` deve essere impostata a `0` e l'output deve mostrare lo Stato 0.*

---

### Esercizio 5: Riconoscimento di Sequenze (Sistema d'Allarme)
Realizza un automa a stati finiti in grado di armare e attivare un allarme dopo la sequenza ordinata **Tasto B seguito da Tasto A**.

#### Specifica del Comportamento e della Tabella di Transizione:
Usa la variabile numerica `stato` con i seguenti valori:
* `0`: Disarmato (Attesa del tasto B).
* `1`: Pre-Allarme (Attesa del tasto A).
* `2`: Allarme Attivo (Intrusione/Allarme scattato).

| Stato Corrente | Input Tasto A | Input Tasto B | Input Tasto A+B (Reset) | Output / Display |
| :--- | :--- | :--- | :--- | :--- |
| **0 (Disarmato)** | Rimane in **0** | Passa a **1** | Passa a **0** | Icona Casa / Disarmato |
| **1 (Pre-Allarme)** | Passa a **2** | Rimane in **1** | Passa a **0** | Icona Diamante / Attesa A |
| **2 (Allarme)** | Rimane in **2** | Rimane in **2** | Passa a **0** | Icona Teschio / Sirena |

* **Regola**: Premere A prima di B mantiene il sistema disarmato in `stato = 0`. Una volta scattato l'allarme (`stato = 2`), il sistema si resetta allo stato disarmato `0` solo premendo **A+B**.
