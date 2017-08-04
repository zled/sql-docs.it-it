---
title: "Novità &#39; s di SSMA per MySQL (MySQLToSql) | Documenti Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 1451a0b0-6713-4d0c-954f-ea3d8fce1d31
caps.latest.revision: 21
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 42706f2ce71fc540d8538f9614f1db17b4f70ea7
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="what39s-new-in-ssma-for-mysql-mysqltosql"></a>Novità &#39; s di SSMA per MySQL (MySQLToSql)
Questo argomento elenca SSMA per le modifiche di MySQL in ogni versione.  

## <a name="may-2016"></a>Maggio 2016  
La versione di maggio 2016 di SSMA per MySQL contiene le seguenti modifiche:.

1.  Aggiunta del supporto per SQL Server 2016
2.  Resolver e parser migliorata
3.  Rimuovere il controllo di programma di installazione per .net 2.0
4.  Dipendenze di estensione Pack aggiornato da .net 3.5 per .net 4.0
5.  Typemapping BigInt predefinito fisso per MySql
6.  Fisso "Salva"progetto "progetto aperto" comandi e per la Console di SSMA
7.  Comando predefinito "securepassword" per la Console di SSMA
8.  Fissa il conteggio di oggetti per il caricamento iniziale
9.  Oggetti MsSql fissi durante il caricamento
10. Correzione del bug nelle impostazioni globali 
 
## <a name="march-2016"></a>Marzo 2016  
La versione di anteprima di marzo 2016 di SSMA per MySQL contiene le seguenti modifiche:  
  
1.  Supporta la migrazione a SQL Server 2016  
  
## <a name="january-2016"></a>Gennaio 2016  
La versione di gennaio 2016 manutenzione di SSMA per MySQL contiene le seguenti modifiche:  
  
1.  Voce di Menu aggiunto visualizzazione Log di SSMA (RFC 5706203)  
  
2.  Aggiunta di dati di telemetria  
  
## <a name="july-2014"></a>Luglio 2014  
La versione di luglio 2014 di SSMA per MySQL contiene le seguenti modifiche:  
  
1.  Conversione del codice di database SQL di Azure migliorata  
  
2.  Funzionalità di estensione pack spostato nello schema per il supporto di database SQL di Azure  
  
3.  Miglioramenti delle prestazioni testato per i database con più di 10k oggetti  
  
4.  Miglioramenti dell'interfaccia utente per la gestione con un numero elevato di oggetti  
  
5.  Evidenziazione degli schemi LOB "noti" (in modo che può essere ignorati nella conversione)  
  
6.  Miglioramenti di velocità di conversione  
  
7.  Mostra i conteggi di oggetti nell'interfaccia utente  
  
8.  Riduzione delle dimensioni di report più del 25%  
  
9. Messaggi di errore migliorati per i costrutti non analizzati.  
  
## <a name="april-2014"></a>Aprile 2014  
La versione di luglio 2011 di SSMA per MySQL contiene le seguenti modifiche:  
  
1.  Aggiunta del supporto di Microsoft SQL Server 2014.  
  
2.  Bug risolti sulla conversione in Azure  
  
3.  Bug risolti per le pagine del report invisibile in Internet Explorer 10.  
  
## <a name="july-2011"></a>Luglio 2011  
La versione di luglio 2011 di SSMA per MySQL contiene le seguenti modifiche:  
  
-   Supporto per la conversione del limite per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] OFFSET "Denali".  
  
-   Una migliore segnalazione errori durante la migrazione dei dati.  
  
## <a name="april-2011"></a>Aprile 2011  
La versione di aprile 2011 di SSMA per MySQL contiene le seguenti modifiche:  
  
-   Singolo Installable di "SSMA per MySQL", che supporta [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] "Denali" e SQL Azure.  
  
-   La possibilità di connettersi [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] "Denali".  
  
-   Enhanced client side dati modulo di migrazione, supporto della migrazione parallela dei dati.  
  
-   Prestazioni migrazione di dati migliorate con semplici e di massa registrato i modelli di recupero.  
  
-   SSMA per MySQL Console versione supporta la compatibilità con le versioni precedenti. Sarà in grado di aprire i progetti creati con versioni precedenti a v 5.0 SSMA.  
  
-   SSMA per MySQL v 5.0 prodotto può essere installato affiancata (SxS) con le versioni precedenti del prodotto SSMA.  
  
## <a name="july-2010"></a>Luglio 2010  
La versione di luglio 2010 di SSMA per MySQL contiene le seguenti funzionalità:  
  
1.  **Miglioramenti all'interfaccia utente:**  
  
    -   Scheda 'Modalità di SQL' per gli oggetti di MySQL Database  
  
    -   Scheda 'Impostazioni' per gli oggetti di MySQL Database  
  
    -   Scheda 'Data' per le tabelle di MySQL  
  
    -   Impostazioni di progetto aggiornato nelle pagine di migrazione e di conversione  
  
    -   'Impostazioni di migrazione di dati' a livello di tabella  
  
2.  **Miglioramenti per la connessione a MySQL e SQL Server:**  
  
    -   Connettività SSL di MySQL  
  
    -   Connettività crittografata in SQL Server  
  
3.  **Miglioramenti alla Metabase MySQL Explorer:**  
  
    -   Durante il caricamento di tutti gli oggetti di Database MySQL e le rispettive schede.  
  
4.  **Miglioramenti per la conversione degli oggetti:**  
  
    -   Conversione di oggetti della Metabase di MySQL: procedure, funzioni, viste, trigger e le istruzioni.  
  
    -   Supporto limitato per i tipi di dati spaziali nelle tabelle.  
  
    -   Opzione per convertire le funzioni di MySQL in Stored procedure di SQL Server  
  
    -   Opzione per applicare il mapping di modalità di SQL e set di caratteri durante la conversione degli oggetti  
  
5.  **Miglioramenti alla migrazione dei dati:**  
  
    -   Supporto per la migrazione dei dati tramite motori di migrazione dei dati lato Client e lato Server  
  
    -   Supporto per la migrazione di dati spaziali  
  
    -   SQL personalizzata per la migrazione dei dati per le tabelle  
  
6.  **SSMA per la Console di MySQL:**  
  
    -   Supporto di funzionalità della Console per SSMA per MySQL  
  
    -   Supporto per l'interfaccia a livello di Script  
  
## <a name="january-2010"></a>Gennaio 2010  
La versione di gennaio 2010 di SSMA per MySQL è la versione iniziale. Contiene le seguenti funzionalità:  
  
-   Migrazione a locale SQL Server e SQL Azure sono supportati.  
  
-   **Funzionalità Snapshot:** migrazione di schemi e dati di tabelle/indici o vincoli di MySQL.  
  

