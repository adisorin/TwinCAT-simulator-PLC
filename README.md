# TwinCAT-simulator-PLC
Simulator PLC cu care se poate testa: Cod PASCAL Structured Text și JavaScript.
<img width="806" height="907" alt="image" src="https://github.com/user-attachments/assets/ee7744cd-1101-4aa6-8d05-b665a846d362" />

Îți pregătesc o **prezentare publică structurată, profesională**, pe care o poți susține în fața unei clase, la licență/master sau într-o companie de automatizări.

Tema: **Simulator PLC + HMI inspirat din Beckhoff TwinCAT**

---

# 🎤 PREZENTARE PUBLICĂ

## „TwinCAT Integrated PLC & HMI Simulator”

---

## 1️⃣ Introducere

Bună ziua,

Astăzi vă prezint un **simulator PLC + HMI** inspirat din platforma industrială **Beckhoff TwinCAT**, utilizată pe scară largă în automatizări industriale.

Scopul acestui proiect este:

* Simularea unui PLC real
* Execuția ciclică a codului
* Suport pentru Structured Text (IEC 61131-3)
* Simulare I/O digitale și analogice
* Interfață HMI integrată
* Diagnostic în timp real

---

## 2️⃣ Ce este TwinCAT?

**TwinCAT** (The Windows Control and Automation Technology) este:

* Platformă software PLC
* Rulează pe PC industrial
* Respectă standardul **IEC 61131-3**
* Permite programare în:

  * Structured Text (ST)
  * Ladder Diagram
  * Function Block Diagram

Simulatorul meu reproduce parțial această logică, dar într-un mediu web.

---

## 3️⃣ Arhitectura simulatorului

Aplicația este construită în:

* HTML – structură
* CSS – interfață industrială
* JavaScript – motor PLC

Structura principală conține:

### 🔹 Panou I/O

* 4 intrări digitale (I0_0 – I0_3)
* 4 ieșiri digitale (Q0_0 – Q0_3)
* LED-uri de stare

### 🔹 Intrare analogică

* Slider nivel (0–100%)
* Simulează senzor de nivel

### 🔹 HMI

* Rezervor animat
* Mesaje de stare:

  * LOW LEVEL
  * HIGH LEVEL
  * SYSTEM RUNNING
  * READY

### 🔹 Diagnostic log

* Afișează:

  * Compilare
  * Erori
  * Evenimente sistem

---

## 4️⃣ Motorul PLC

Simulatorul implementează:

### ✔ Execuție ciclică (scan cycle)

Codul este executat la fiecare 100 ms:

```js
setInterval(() => {
   eval(compiledCode);
}, 100);
```

Exact ca un PLC real:

1. Citește intrări
2. Execută logică
3. Scrie ieșiri

---

## 5️⃣ Compilator Structured Text

Am creat un mini-compilator care:

Transformă cod IEC în JavaScript.

Exemplu:

```pascal
IF I0_0 AND I0_1 THEN
   Q0_0 := TRUE;
END_IF;
```

Devine:

```js
if(I0_0 && I0_1){
   Q0_0 = true;
}
```

Suportă:

* IF / ELSE / ELSIF
* FOR
* WHILE
* AND / OR / NOT
* MOD
* Funcții matematice
* LIMIT
* SEL

---

## 6️⃣ Function Blocks implementate

Simulatorul include blocuri IEC clasice:

### 🔹 TON – Timer On Delay

Activează ieșirea după un timp presetat.

### 🔹 TOF – Timer Off Delay

Menține ieșirea activă un timp după dezactivare.

### 🔹 R_TRIG

Detecție front crescător.

### 🔹 F_TRIG

Detecție front descrescător.

### 🔹 FLASH(ms)

Semnal intermitent.

---

## 7️⃣ Exemplu demonstrație live

Cod demonstrativ:

```pascal
IF I0_0 THEN
   Q0_0 := TRUE;
ELSE
   Q0_0 := FALSE;
END_IF;
```

Sau cu timer:

```pascal
Q0_1 := TON(t1, I0_0, 3000);
```

La apăsarea I0_0:

* după 3 secunde → Q0_1 devine activ

---

## 8️⃣ Siguranță și validare

Înainte de rulare:

```js
new Function(transformed);
```

Verifică sintaxa reală.

Dacă există eroare:

* PLC nu pornește
* Apare mesaj în diagnostic

Exact ca într-un mediu industrial.

---

## 9️⃣ Avantaje ale simulatorului

✅ Ușor de utilizat
✅ Fără instalare software
✅ Ideal pentru predare
✅ Simulare realistă ciclu PLC
✅ Vizualizare HMI integrată
✅ Diagnostic în timp real

---

## 🔟 Limitări

* Nu suportă Ladder Diagram
* Nu comunică cu hardware real
* Nu are EtherCAT
* Nu implementează task-uri multiple

---

## 1️⃣1️⃣ Aplicații educaționale

Acest simulator poate fi folosit pentru:

* Cursuri de automatizări
* Introducere în PLC
* Demonstrații IEC 61131-3
* Înțelegerea ciclului de scanare

---

## 1️⃣2️⃣ Concluzie

Proiectul demonstrează că:

* Logica PLC poate fi simulată în browser
* Structured Text poate fi interpretat dinamic
* Interfața HMI poate fi sincronizată cu logica de control

Este un exemplu de integrare între:

* Automatizări industriale
* Programare web
* Modelare sisteme în timp real

---
Vă mulțumesc pentru atenție.
Autor: Sorinescu Adrian
