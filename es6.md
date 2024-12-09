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
 
