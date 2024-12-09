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
 ```sql
CREATE TABLE ISTRUTTORE (
  id INT PRIMARY KEY,
  nome VARCHAR(255),
  email VARCHAR(255)
);

CREATE TABLE CORSO (
  id INT PRIMARY KEY,
  nome VARCHAR(255),
  codice_iscrizione VARCHAR(255),
  istruttore_id INT,
  FOREIGN KEY (istruttore_id) REFERENCES ISTRUTTORE(id)
);

CREATE TABLE ATTIVITA (
  id INT PRIMARY KEY,
  titolo VARCHAR(255),
  descrizione_breve VARCHAR(160),
  descrizione_estesa TEXT,
  sessioni INT,
  corso_id INT,
  FOREIGN KEY (corso_id) REFERENCES CORSO(id)
);

CREATE TABLE UTENTE (
  id INT PRIMARY KEY,
  nome VARCHAR(255),
  email VARCHAR(255)
);

CREATE TABLE IMMAGINE (
  id INT PRIMARY KEY,
  url VARCHAR(255),
  attivita_id INT,
  FOREIGN KEY (attivita_id) REFERENCES ATTIVITA(id)
);

CREATE TABLE DISCIPLINA (
  id INT PRIMARY KEY,
  nome VARCHAR(255)
);

CREATE TABLE ISCRIZIONE (  -- Rinominata per chiarezza
  user_id INT,
  corso_id INT,
  PRIMARY KEY (user_id, corso_id),
  FOREIGN KEY (user_id) REFERENCES UTENTE(id),
  FOREIGN KEY (corso_id) REFERENCES CORSO(id)
);

CREATE TABLE PUNTO_FITNESS (
  id INT PRIMARY KEY,
  punti INT,
  data_assegnazione DATE,
  user_id INT,
  attivita_id INT,
  FOREIGN KEY (user_id) REFERENCES UTENTE(id),
  FOREIGN KEY (attivita_id) REFERENCES ATTIVITA(id)
);
```

#SQL

```sql
INSERT INTO ISTRUTTORE (id, nome, email) VALUES
(1, 'John Smith', 'john.smith@example.com'),
(2, 'Jane Doe', 'jane.doe@example.com');

INSERT INTO CORSO (id, nome, codice_iscrizione, istruttore_id) VALUES
(1, 'Yoga Base', 'YOGA101', 1),
(2, 'Calcio Avanzato', 'SOCCER201', 2);

INSERT INTO ATTIVITA (id, titolo, descrizione_breve, descrizione_estesa, sessioni, corso_id) VALUES
(1, 'Yoga del mattino', 'Posizioni base dello yoga per principianti', 'Descrizione dettagliata delle posizioni yoga...', 10, 1),
(2, 'Allenamento di calcio', 'Esercitazioni e tecniche di calcio', 'Programma dettagliato di allenamento di calcio...', 12, 2);

INSERT INTO UTENTE (id, nome, email) VALUES
(1, 'Alice Johnson', 'alice@example.com'),
(2, 'Bob Wilson', 'bob@example.com');

INSERT INTO IMMAGINE (id, url, attivita_id) VALUES
(1, 'yoga1.jpg', 1),
(2, 'soccer1.jpg', 2);

INSERT INTO DISCIPLINA (id, nome) VALUES
(1, 'Yoga'),
(2, 'Calcio');

INSERT INTO ISCRIZIONE (user_id, corso_id) VALUES  -- Utilizzato il nome rinominato
(1, 1),
(2, 2);

INSERT INTO PUNTO_FITNESS (id, punti, data_assegnazione, user_id, attivita_id) VALUES
(1, 10, '2023-01-10', 1, 1),
(2, 15, '2023-01-15', 2, 2);
```
