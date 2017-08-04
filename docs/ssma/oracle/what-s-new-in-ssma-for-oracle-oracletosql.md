---
title: "Novità &#39; s di SSMA per Oracle (OracleToSQL) | Documenti Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f305ebb6-7393-4a43-abb3-6332b739d690
caps.latest.revision: 24
author: sabotta
ms.author: carlasab
manager: v-thobro
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 191fe2e11c43f4c190a87ee52df9ff87c259ea7d
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="what39s-new-in-ssma--for-oracle-oracletosql"></a>Novità &#39; s di SSMA per Oracle (OracleToSQL)
Questo argomento elenca SSMA delle modifiche Oracle in ogni versione.  

## <a name="may-2016"></a>Maggio 2016  
La versione di maggio 2016 di SSMA per Oracle sono incluse le seguenti modifiche:  

1.  Aggiunta del supporto per SQL Server 2016
2.  Aggiunta conversione delle tabelle di Oracle flashback archivio tabelle temporali di SQL Server
3.  Aggiunta di conversione del criterio VPD Oracle convertire in oggetti Criteri di SQL Server (protezione di livello di riga per Oracle)
4.  Ora una riduzione del carico iniziale per Oracle
5.  Resolver e parser migliorata
6.  Rimuovere il controllo di programma di installazione per .net 2.0
7.  Dipendenze di estensione Pack aggiornato da .net 3.5 per .net 4.0
8.  Fisso "Salva"progetto "progetto aperto" comandi e per la Console di SSMA
9.  Comando predefinito "securepassword" per la Console di SSMA
10. Fissa il conteggio di oggetti per il caricamento iniziale
11. Fissa la conversione dei tipi di dati carattere per Oracle
12. Correzione del bug nelle impostazioni globali
  
## <a name="march-2016"></a>Marzo 2016  
La versione di anteprima di marzo 2016 di SSMA per Oracle sono incluse le seguenti modifiche:  
  
1.  Supporta la migrazione a SQL Server 2016  
  
2.  Supporto per la migrazione sicurezza Oracle a livello di riga (con alcune limitazioni)  
  
3.  Supporto per la migrazione di tabelle Oracle in memoria all'archivio di colonna di SQL Server  
  
## <a name="january-2016"></a>Gennaio 2016  
Il mese di gennaio 2014 manutenzione versione di SSMA per Oracle sono incluse le seguenti modifiche:  
  
1.  Aggiunta del supporto per gli indici cluster  
  
2.  Query di schema Oracle lente (RFC 5076207) predefinito  
  
3.  Fisso connettersi ad Azure dalla console  
  
4.  Voce di Menu aggiunto visualizzazione Log di SSMA (RFC 5706203)  
  
5.  Aggiunta di dati di telemetria  
  
## <a name="july-2014"></a>Luglio 2014  
La versione di luglio 2014 di SSMA per Oracle sono incluse le seguenti modifiche:  
  
1.  Supporto per database SQL di Azure  
  
2.  Funzionalità di estensione pack spostato nello schema per il supporto di database SQL di Azure  
  
3.  Supporto per le viste materializzate Oracle  
  
4.  Le tabelle con ottimizzazione di supporto per la memoria di SQL Server 2014  
  
5.  Miglioramenti delle prestazioni testato per i database con più di 10k oggetti  
  
6.  Miglioramenti dell'interfaccia utente per la gestione con un numero elevato di oggetti  
  
7.  Evidenziazione degli schemi LOB "noti"  
  
8.  Miglioramenti di velocità di conversione  
  
9. Mostra i conteggi di oggetti nell'interfaccia utente  
  
10. Riduzione delle dimensioni di report più del 25%  
  
11. Messaggi di errore migliorati per i costrutti non analizzati.  
  
## <a name="april-2014"></a>Aprile 2014  
La versione di aprile 2014 di SSMA per Oracle sono incluse le seguenti modifiche:  
  
1.  Aggiunta del supporto di Microsoft SQL Server 2014.  
  
2.  Aggiunta del supporto di ottimizzazione di Oracle 12 e query.  
  
3.  Bug risolti sulla conversione in Azure.  
  
4.  Bug risolti per le pagine del report invisibile in Internet Explorer 10.  
  
## <a name="january-2012"></a>Gennaio 2012  
La versione di gennaio 2012 di SSMA per Oracle sono incluse le seguenti modifiche:  
  
-   Parametri di input RowType supporto e RecordType automaticamente impostati su NULL.  
  
## <a name="july-2011"></a>Luglio 2011  
La versione di luglio 2011 di SSMA per Oracle sono incluse le seguenti modifiche:  
  
-   Supporto per la conversione della sequenza di Oracle da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] generatore di sequenza "Denali".  
  
-   Una migliore segnalazione errori durante la migrazione dei dati.  
  
-   Conversione miglioramento dell'istruzione di utilizzo di parole riservate.  
  
-   Migliorate conversione implicita del valore di data in una funzione.  
  
## <a name="april-2011"></a>Aprile 2011  
La versione di aprile 2011 di SSMA per Oracle sono incluse le seguenti modifiche:  
  
-   Singolo prodotto "SSMA per Oracle", che supporta [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008 e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] "Denali".  
  
-   Supporto per la connessione e la migrazione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] "Denali".  
  
-   Enhanced client side dati modulo di migrazione, supporto della migrazione parallela dei dati.  
  
-   Prestazioni migrazione di dati migliorate con semplici e di massa registrato i modelli di recupero.  
  
-   Compatibilità con le versioni precedenti dei progetti creati con versioni precedenti di SSMA (v 4.0 e v 4.2).  
  
-   SSMA per Oracle v 5.0 prodotto può essere installato affiancata (SxS) con le versioni precedenti di SSMA (v 4.0 e v 4.2).  
  
-   Supporto per i tipi definiti dall'utente (include sottotipo, VARRAY, tabella nidificata, tabella oggetti e visualizzazione di oggetti) e relativo utilizzo in blocchi PL/SQL con messaggi di errore speciale di reporting.  
  
## <a name="july-2010"></a>Luglio 2010  
La versione di luglio 2010 di SSMA per Oracle sono incluse le seguenti modifiche:  
  
-   Supporto per la migrazione a SQL Server 2008 R2  
  
-   Nuova applicazione Console di SSMA per l'esecuzione della riga di comando  
  
-   Supporto per la migrazione dei dati tramite motori di migrazione dei dati lato Client e lato Server  
  
-   Supporto per l'istruzione "SELECT personalizzata" nella migrazione dei dati  
  
-   Supporto per la migrazione da Oracle 11g R2  
  
## <a name="june-2008"></a>Giugno 2008  
La versione di giugno 2008 di SSMA per Oracle sono incluse le seguenti modifiche:  
  
-   Miglioramenti nel Report di valutazione è sono completati. Include informazioni aggiuntive per sinonimi, origine file non elaborato per oggetti analizzabili, pannelli e rimozione di logo di SQL Server e la persistenza del layout.  
  
-   Miglioramenti nella conversione di oggetti:  
  
    -   Pacchetti DBMS_LOB, conversione DBMS_SQL aggiunto.  
  
    -   Crea un join conversione rivista.  
  
    -   Modifica di record e le raccolte di conversione, ora di conversione di record nei casi più semplici rilasciati mediante variabili separate per ogni campo.  
  
    -   Miglioramenti dell'implementazione di record e raccolte.  
  
    -   Funzioni di aggregazione di windowing aggiunte.  
  
    -   Clausola ROLLUP o CUBE aggiunto.  
  
    -   Analisi utilizzo software per NEXTVAL/CURVAL.  
  
    -   Sono state aggiunte colonne nella clausola SET di raggruppamento, Grouping sets e ID di raggruppamento.  
  
    -   MERGE-istruzione aggiunto.  
  
    -   Supporto di nuovi tipi datetime e la conversione di record e le raccolte come tipi di dati CLR aggiunti.  
  
-   Sono state aggiunte nuove funzionalità di Tester. Tabelle possono ora essere testate come oggetti con Tester, è possibile modificare un ordine di chiamata di diversi oggetti testabili nel test case, utente eseguire il test di procedure e funzioni di record e le raccolte come parametri e restituire valori e un dipendenze analizzatore è stato aggiunto al controllo solo tabelle utilizzate.  
  
## <a name="august-2007"></a>Agosto 2007  
La versione di agosto 2007 di SSMA per Oracle sono incluse le seguenti modifiche:  
  
-   Un nuovo componente TESTER consente di creare, gestire ed eseguire i test case per verificare il codice SQL convertito.  
  
-   Conversione di sottotipi Oracle, raccolte e moduli locali sono stati aggiunti al convertitore di tipi SQL.  
  
-   Una nuova funzionalità di sincronizzazione consente di sincronizzare oggetti specifici con database di SQL Server.  
  
-   Aggiunte nuove opzioni di conversione.  
  
## <a name="april-2007"></a>Aprile 2007  
La versione di aprile 2007 di SSMA per Oracle è la versione iniziale.  
  

