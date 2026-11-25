# Scheda dati — Festival Segnale

## Entità e campi

### Evento

| Campo | Tipo | Esempio |
|---|---|---|
| `id` | numero intero | `1` |
| `titolo` | testo | `"Lettere in movimento"` |
| `data` | data in formato `AAAA-MM-GG` | `"2026-06-12"` |
| `orario` | ora in formato `HH:MM` | `"10:00"` |
| `categoria` | testo | `"Incontro"` |
| `descrizione` | testo | `"Come cambia un messaggio quando cambiano le lettere?..."` |
| `immagine` | percorso testuale | `"assets/lettere-in-movimento.svg"` |
| `immagine_alt` | testo alternativo | `"Lettere geometriche disposte su una griglia"` |
| `sede_id` | numero intero | `1` |

### Sede

| Campo | Tipo | Esempio |
|---|---|---|
| `id` | numero intero | `1` |
| `nome` | testo | `"Officina Nord — Sede centrale"` |
| `indirizzo` | testo | `"Corso Duca degli Abruzzi 24, Torino"` |

## Chiavi e relazione

La chiave primaria di `Evento` è `id`: è numerica, univoca nell'entità e stabile.  
La chiave primaria di `Sede` è `id`: è numerica, univoca nell'entità e stabile.

Una sede può ospitare più eventi; ogni evento si svolge in una sede.  
`Evento.sede_id` fa riferimento a `Sede.id`.

## Quantità

I dati comprendono sei eventi e tre sedi.

## Aggiornamento dei dati

Chi cura il sito aggiorna i file `eventi.json` e `sedi.json` nella repository e pubblica le modifiche insieme al sito.

## Che cosa mostra la pagina

La pagina Programma mostra le schede degli eventi con data, orario, categoria, titolo, descrizione e immagine. Il nome della sede viene ricavato dai dati delle sedi attraverso `sede_id`.

## Schema Evento–Sede

```mermaid
erDiagram
    SEDE ||--o{ EVENTO : ospita
    SEDE {
        int id PK
        string nome
        string indirizzo
    }
    EVENTO {
        int id PK
        string titolo
        date data
        string orario
        string categoria
        string descrizione
        string immagine
        string immagine\_alt
        int sede\_id FK
    }