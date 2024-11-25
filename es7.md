erDiagram
    PAZIENTE ||--o{ PRENOTAZIONE : effettua
    MEDICO ||--o{ VISITA : esegue
    PAZIENTE ||--o{ VISITA : prenota
    MEDICO ||--o{ CARTELLACLINICA : aggiorna
    PAZIENTE ||--o{ CARTELLACLINICA : possiede
    MEDICO ||--o{ SPECIALIZZAZIONE : possiede
    RISORSACLINICA ||--o{ VISITA : utilizza
    PRENOTAZIONE ||--o{ DOCUMENTO : allega
    
    MEDICO { 
        int ID_Medico PK
        string Nome
        string Cognome
        string Email
        string Specializzazioni
    }

    PAZIENTE {
        int ID_Paziente PK
        string Nome
        string Cognome
        string Email
        string Indirizzo
    }

    VISITA {
        int ID_Visita PK
        int ID_Medico FK
        int ID_Paziente FK
        date DataVisita
        string TipoVisita
        int Durata
        string Descrizione
    }

    SPECIALIZZAZIONE {
        int ID_Specializzazione PK
        string NomeSpecializzazione
    }

    CARTELLACLINICA {
        int ID_Cartella PK
        int ID_Paziente FK
        int ID_Medico FK        
        string Diagnosi
        string Trattamento
        date DataAggiornamento
    }

    PRENOTAZIONE {
        int ID_Prenotazione PK
        int ID_Medico FK
        int ID_Paziente FK
        date DataPrenotazione
        string MotivoVisita
    }

    RISORSACLINICA {
        int ID_Risorsa PK
        string NomeRisorsa
        string Tipo
        string Disponibilita
    }

    DOCUMENTO {
        int ID_Documento PK
        int ID_Prenotazione FK
        string TipoDocumento
        string Descrizione
        date DataAllegato
    }
