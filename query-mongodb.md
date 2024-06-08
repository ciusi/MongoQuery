# Compito: Query MongoDB

## Query MongoDB per trovare risorse con criteri sui campi `eyes` e `company`.

## Query 1: Trova tutte le risorse con il dato `eyes` che sia "brown" o "blue"

```json
{ "eyes": { "$in": ["brown", "blue"] } }
```

## Query 2: Trova tutte le risorse che non presentano il dato `eyes` uguale a "green"

```json
{ "eyes": { "$ne": "green" } }
```

## Query 3: Trova tutte le risorse che non presentano il dato `eyes` uguale a "green" e neanche "blue"

```json
{ "eyes": { "$nin": ["green", "blue"] } }
```

## Query 4: Trovare tutte le risorse con il dato `company` uguale a "FITCORE" e ritornare solo l'email

```json
{ "company": "FITCORE" }
```
**Proiezione:**
```json
{ "email": 1, "_id": 0 }
```

```
{ "isActive": true } 20/97
{ "age": { "$gt": 26 } } 20/54
{ "age": { "$gt": 26, "$lte": 30 } } 1/19
{ "eyes": { "$in": ["brown", "blue"] } } 0
{ "eyes": { "$ne": "green" } } 20/97
{ "eyes": { "$nin": ["green", "blue"] } } 20/97
{ "company": "FITCORE" } 1
{ "email": 1, "_id": 0 } 1 //nella sezione project 


______________________________________________________appunti


```markdown
# 📚 Riepilogo delle Query in MongoDB e Uso di MongoDB Compass

## 🌟 Cosa Sono le Query

Le query in MongoDB sono istruzioni che permettono di cercare e manipolare i documenti all'interno di una collection. Usano la sintassi JSON per specificare i criteri di ricerca e possono includere operatori di confronto, logici e altro.

## 🔍 Operatori di Base

### 🔹 Operatore di Uguaglianza
Cerca documenti che contengono un campo specifico con un valore esatto.
```json
{ "campo": "valore" }
```

### 🔹 Operatori di Confronto
- **$gt** (greater than - maggiore di):
  ```json
  { "campo": { "$gt": valore } }
  ```
- **$gte** (greater than or equal to - maggiore o uguale a):
  ```json
  { "campo": { "$gte": valore } }
  ```
- **$lt** (less than - minore di):
  ```json
  { "campo": { "$lt": valore } }
  ```
- **$lte** (less than or equal to - minore o uguale a):
  ```json
  { "campo": { "$lte": valore } }
  ```
- **$ne** (not equal to - non uguale a):
  ```json
  { "campo": { "$ne": valore } }
  ```

### 🔹 Operatori Logici
- **$and**:
  ```json
  { "$and": [ { "campo1": "valore1" }, { "campo2": "valore2" } ] }
  ```
- **$or**:
  ```json
  { "$or": [ { "campo1": "valore1" }, { "campo2": "valore2" } ] }
  ```
- **$not**:
  ```json
  { "campo": { "$not": { "$gt": valore } } }
  ```
- **$in** (valore in una lista):
  ```json
  { "campo": { "$in": [ "valore1", "valore2" ] } }
  ```
- **$nin** (valore non in una lista):
  ```json
  { "campo": { "$nin": [ "valore1", "valore2" ] } }
  ```

## 🛠️ Uso di MongoDB Compass

### 🔹 Connetti a MongoDB
1. Apri MongoDB Compass.
2. Inserisci l'URL di connessione (ad esempio, `mongodb+srv://<username>:<password>@<cluster>.mongodb.net/`).
3. Clicca su "Connect".

### 🔹 Seleziona il Database e la Collection
1. Nella schermata principale, seleziona il database e poi la collection su cui vuoi lavorare.

### 🔹 Esegui le Query
1. Vai alla scheda "Documents".
2. Inserisci la query nel campo "Filter".

## ✨ Esempi di Query

1. **Trova tutte le risorse con `isActive` corrispondente a `true`**:
   ```json
   { "isActive": true }
   ```

2. **Trova tutte le risorse con `age` maggiore di 26**:
   ```json
   { "age": { "$gt": 26 } }
   ```

3. **Trova tutte le risorse con `age` maggiore di 26 e minore o uguale a 30**:
   ```json
   { "age": { "$gt": 26, "$lte": 30 } }
   ```

4. **Trova tutte le risorse con `eyes` che sia `brown` o `blue`**:
   ```json
   { "eyes": { "$in": ["brown", "blue"] } }
   ```

5. **Trova tutte le risorse che non presentano `eyes` uguale a `green`**:
   ```json
   { "eyes": { "$ne": "green" } }
   ```

6. **Trova tutte le risorse che non presentano `eyes` uguale a `green` e neanche `blue`**:
   ```json
   { "eyes": { "$nin": ["green", "blue"] } }
   ```

7. **Trova tutte le risorse con `company` uguale a "FITCORE" e ritorna solo l'`email`**:
   - Query:
     ```json
     { "company": "FITCORE" }
     ```
   - Proiezione:
     ```json
     { "email": 1, "_id": 0 }
     ```

## 🔢 Uso della Funzione di Aggregazione per Contare i Documenti

1. **Vai alla scheda "Aggregations"**.
2. **Aggiungi una fase $match**:
   - Clicca su "Add Stage" e seleziona `$match`.
   - Inserisci la query desiderata, ad esempio:
     ```json
     { "isActive": true }
     ```
3. **Aggiungi una fase $count**:
   - Clicca su "Add Stage" e seleziona `$count`.
   - Assegna un nome al campo di conteggio, ad esempio `"total"`.
     ```json
     { "$count": "total" }
     ```
4. **Esegui l'aggregazione**:
   - Clicca su "Run".
