```mermaid
erDiagram
  ISTRUTTORE {
    int ID
    string Nome
    string Email
  }
  CORSO {
    int ID
    string Nome
    string Disciplina
    string CodiceRegistrazione
  }
  ATTIVITA {
    int ID
    string Titolo
    string DescrizioneBreve
    string DescrizioneLunga
    int NumeroSessioni
    string Immagine1
    string Immagine2
    string Immagine3
  }
  UTENTE {
    int ID
    string Nome
    string Email
  }
  PUNTO_FITNESS {
    int ID
    int Punti
  }
  CORSO_ATTIVITA {
    int CorsoID
    int AttivitaID
  }
  UTENTE_CORSO {
    int UtenteID
    int CorsoID
  }
  UTENTE_ATTIVITA {
    int UtenteID
    int AttivitaID
  }

  ISTRUTTORE ||--o{ CORSO : crea
  CORSO ||--o{ CORSO_ATTIVITA : include
  ATTIVITA ||--o{ CORSO_ATTIVITA : parte_di
  UTENTE ||--o{ UTENTE_CORSO : si_iscrive
  CORSO ||--o{ UTENTE_CORSO : ha
  UTENTE ||--o{ UTENTE_ATTIVITA : partecipa
  ATTIVITA ||--o{ UTENTE_ATTIVITA : include
  UTENTE_ATTIVITA ||--o{ PUNTO_FITNESS : guadagna
```

#SQL

```sql
INSERT INTO ISTRUTTORE (id, nome, email) VALUES
(1, 'Marco Rossi', 'marco.rossi@palestrafit.it'),
(2, 'Anna Bianchi', 'anna.bianchi@danzaenergia.com');

INSERT INTO CORSO (id, nome, codice_iscrizione, istruttore_id) VALUES
(1, 'Pilates per principianti', 'PILATES101', 1),
(2, 'Hip Hop dance', 'HIPHOP202', 2);

INSERT INTO ATTIVITA (id, titolo, descrizione_breve, descrizione_estesa, sessioni, corso_id) VALUES
(1, 'Riscaldamento dinamico', 'Esercizi di mobilità e attivazione muscolare', 'Una serie di esercizi per preparare il corpo al Pilates', 10, 1),
(2, 'Coreografia base', 'Impara i primi passi di una coreografia hip hop', 'Creazione di una sequenza di movimenti semplici e divertenti', 12, 2);

INSERT INTO UTENTE (id, nome, email) VALUES
(1, 'Sofia Verdi', 'sofia.verdi@gmail.com'),
(2, 'Luca Neri', 'luca.neri@outlook.it');

INSERT INTO IMMAGINE (id, url, attivita_id) VALUES
(1, 'pilates_riscaldamento.jpg', 1),
(2, 'hiphop_coreografia.png', 2);

INSERT INTO DISCIPLINA (id, nome) VALUES
(1, 'Pilates'),
(2, 'Danza');

INSERT INTO ISCRIZIONE (user_id, corso_id) VALUES  -- Utilizzato il nome rinominato
(1, 1),
(2, 2);

INSERT INTO PUNTO_FITNESS (id, punti, data_assegnazione, user_id, attivita_id) VALUES
(1, 8, '2023-02-10', 1, 1),
(2, 12, '2023-02-15', 2, 2);
```
