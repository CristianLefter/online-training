# Aplicație To-Do

## Scop
O aplicație în care utilizatorii își pot gestiona sarcinile zilnice: adăugare, modificare, marcare ca finalizate și ștergere.

## Tipuri de date
- **Task**: ID, Titlu, Descriere, Dată, Status
- **Comentarii**: Structurate ca obiecte JSON atașate fiecărui task
- **Fișiere atașate**: Imagini, PDF-uri sau documente

## Propunere de stocare în Azure

| Tip de date       | Soluție Azure         | Motivare                                 |
|-------------------|------------------------|------------------------------------------|
| Task              | Azure SQL Database     | Structurat, relațional, ușor de interogat |
| Comentarii        | Azure Cosmos DB        | Semi-structurat, stocare flexibilă JSON  |
| Fișiere atașate   | Azure Blob Storage     | Ideal pentru imagini și documente        |

## Model de entități

### Task

| Atribut   | Tip      | Descriere                    |
|-----------|----------|------------------------------|
| ID        | int      | Identificator unic           |
| Titlu     | text     | Titlul sarcinii              |
| Descriere | text     | Detalii opționale            |
| Dată      | date     | Data limită pentru task      |
| Status    | text     | Exemplu: „nou”, „făcut”      |

### Exemplu JSON pentru un task cu comentarii

```json
{
  "id": 1,
  "titlu": "Cumpără pâine",
  "descriere": "De la magazinul din colț",
  "data": "2025-07-15",
  "status": "nou",
  "comentarii": [
    { "autor": "Maria", "text": "Nu uita bonul!" },
    { "autor": "Alex", "text": "Poți lua și lapte?" }
  ]
}
```

## Întrebări de analiză

- Câte taskuri sunt finalizate pe zi?
- Care este procentul de sarcini nefinalizate?
- Cine are cele mai multe taskuri?

## Fișier CSV de test (opțional)

```csv
ID,Titlu,Descriere,Data,Status
1,Cumpără pâine,De la magazin,2025-07-15,nou
2,Trimite e-mail,Răspunde clientului,2025-07-15,finalizat
3,Fă curat,,2025-07-16,nou
```

## Autori
Acest proiect este creat ca parte a cursului **DP-900: Azure Data Fundamentals**.
