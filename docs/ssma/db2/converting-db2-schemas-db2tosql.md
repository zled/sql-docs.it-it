---
title: Conversione di schemi di DB2 (DB2ToSQL) | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-db2
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 7947efc3-ca86-4ec5-87ce-7603059c75a0
caps.latest.revision: 9
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 10dd76ca821303070e8856c44bafd1315ac60444
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="converting-db2-schemas-db2tosql"></a>Conversione di schemi di DB2 (DB2ToSQL)
Dopo aver connesso a DB2, connesso alla [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], e imposta il progetto e le opzioni di mapping di dati, è possibile convertire oggetti di database DB2 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oggetti di database.  
  
## <a name="the-conversion-process"></a>Il processo di conversione  
La conversione di oggetti di database utilizza le definizioni degli oggetti da DB2, li converte simile [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] degli oggetti e quindi carica tali informazioni nei metadati di SSMA. Impossibile caricare le informazioni nell'istanza [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. È quindi possibile visualizzare gli oggetti e le relative proprietà utilizzando il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati.  
  
Durante la conversione, SSMA Stampa messaggi di output nel riquadro di Output e i messaggi di errore nel riquadro elenco errori. Utilizzare le informazioni di output e l'errore per determinare se è necessario modificare i database DB2 o il processo di conversione per ottenere i risultati di conversione desiderato.  
  
## <a name="setting-conversion-options"></a>Impostazione delle opzioni di conversione  
Prima di convertire gli oggetti, esaminare le opzioni di conversione del progetto nel **impostazioni progetto** la finestra di dialogo. Tramite questa finestra di dialogo, è possibile impostare la modalità di conversione di funzioni e variabili globali in SSMA. Per altre informazioni, vedere [impostazioni del progetto di &#40;conversione&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-conversion-db2tosql.md).  
  
## <a name="conversion-results"></a>Risultati di conversione  
La tabella seguente mostra gli oggetti di DB2 vengono convertiti e il valore risultante [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oggetti:  
  
|Oggetti di DB2|Oggetti SQL Server risultanti|  
|-----------|----------------------------|  
|Tipi di dati|**SSMA esegue il mapping di ogni tipo, ad eccezione di quanto segue elencati di seguito:**<br /><br />Oggetto CLOB: Alcune funzioni native per lavoro con questo tipo non sono supportati (ad esempio CLOB_EMPTY())<br /><br />BLOB: Alcune funzioni native per lavoro con questo tipo non sono supportati (ad esempio BLOB_EMPTY())<br /><br />DBLOB: Alcune funzioni native per lavoro con questo tipo non sono supportati (ad esempio DBLOB_EMPTY())|  
|Tipi definiti dall'utente|**SSMA viene eseguito il mapping seguente definito dall'utente:**<br /><br />Tipo distinto<br /><br />Tipo strutturato<br /><br />Tipi di dati SQL PL-Nota: il tipo di cursore vulnerabili non sono supportati.|  
|Registri speciali|**SSMA esegue il mapping solo registri elencati di seguito:**<br /><br />TIMESTAMP CORRENTE<br /><br />DATA CORRENTE<br /><br />ORA CORRENTE<br /><br />FUSO ORARIO CORRENTE<br /><br />UTENTE CORRENTE<br /><br />SESSION_USER e utente<br /><br />SYSTEM_USER<br /><br />CLIENT_APPLNAME CORRENTE<br /><br />CLIENT_WRKSTNNAME CORRENTE<br /><br />TIMEOUT DI BLOCCO CORRENTE<br /><br />SCHEMA CORRENTE<br /><br />SERVER CORRENTE<br /><br />ISOLAMENTO CORRENTE<br /><br />Altri registri speciali non sono mappati a semantica di SQL server.|  
|CREATE TABLE|**SSMA viene eseguito il mapping CREATE TABLE con le eccezioni seguenti:**<br /><br />Tabelle di clustering (MDC) multidimensionali<br /><br />Tabelle cluster intervallo (RCT)<br /><br />Tabelle partizionate<br /><br />Tabella disconnessa<br /><br />Clausola di acquisizione dei dati<br /><br />Opzione IMPLICITLY NASCOSTE<br /><br />Opzione VOLATILE|  
|CREATE VIEW|SSMA mappe CREATE VIEW con 'WITH locale CHECK OPTION', ma le altre opzioni non sono mappati alla semantica SQL server|  
|CREATE INDEX|**SSMA viene eseguito il mapping CREATE INDEX con le eccezioni seguenti:**<br /><br />Indice XML<br /><br />Opzione BUSINESS_TIME senza SOVRAPPOSIZIONI<br /><br />Clausola PARTIZIONATA<br /><br />Specifica solo l'opzione<br /><br />Opzione utilizzando EXTEND<br /><br />Opzione MINPCTUSED<br /><br />Opzione di suddivisione di pagina|  
|Trigger|**SSMA viene eseguito il mapping la semantica di trigger seguente:**<br /><br />Dopo aver / per i trigger di ogni riga<br /><br />Dopo aver /FOR ogni istruzione attiva<br /><br />PRIMA di / per ogni riga e anziché per ogni riga trigger|  
|Sequenze|Viene eseguito il mapping.|  
|Istruzione SELECT|**Mappe SSMA selezionare con le eccezioni seguenti:**<br /><br />Clausola di riferimento nella tabella di modifica dati – parzialmente mappato, ma le tabelle finale non supportato<br /><br />Clausola di riferimento alla tabella – parzialmente mappato, ma solo tabella di riferimento, riferimento di tabella esterna, analyze_table-expression, tabella derivata insieme, xmltable espressione non viene eseguito il mapping alla semantica SQL server<br /><br />Specifica del periodo di clausola: non è stato eseguito il mapping.<br /><br />Clausola del gestore continuare: non è stato eseguito il mapping.<br /><br />Clausola di correlazione tipizzato: non è stato eseguito il mapping.<br /><br />Clausola simultanee-accesso-risoluzione: non è stato eseguito il mapping.|  
|Istruzione di valori|Viene eseguito il mapping.|  
|INSERT-istruzione|Viene eseguito il mapping.|  
|Istruzione UPDATE|S**SMA esegue il mapping di aggiornamento con le eccezioni seguenti:**<br /><br />Clausola di riferimento alla tabella – solo tabella di riferimento non è stato eseguito il mapping alla semantica SQL server<br /><br />Clausola periodo: non è mappato.|  
|Istruzione MERGE|**SSMA esegue il mapping di tipo MERGE con le eccezioni seguenti:**<br /><br />Singolo vs più occorrenze di ogni clausola - è stato eseguito il mapping alla semantica SQL server per le occorrenze limitate di ogni clausola<br /><br />Clausola di segnale: non eseguire il mapping alla semantica di SQL Server<br /><br />Misto aggiornamento e le clausole DELETE: non eseguire il mapping alla semantica di SQL Server<br /><br />Periodo-clausola, non esegue il mapping alla semantica di SQL Server|  
|DELETE-istruzione|**Mappe SSMA eliminare con le eccezioni seguenti:**<br /><br />Clausola di riferimento alla tabella – solo tabella di riferimento non è stato eseguito il mapping alla semantica SQL server<br /><br />Clausola periodo: non eseguire il mapping alla semantica di SQL Server|  
|Livello di isolamento e il tipo di blocco|Viene eseguito il mapping.|  
|Procedure (SQL)|Viene eseguito il mapping.|  
|Procedure (esterna)|Richiedono l'aggiornamento manuale.|  
|Procedure (originate)|Non eseguire il mapping alla semantica di SQL Server.|  
|Istruzione di assegnazione|Viene eseguito il mapping.|  
|Istruzione CALL per una stored Procedure|Viene eseguito il mapping.|  
|Istruzione CASE|Viene eseguito il mapping.|  
|Istruzione FOR|Viene eseguito il mapping.|  
|GOTO - istruzione|Viene eseguito il mapping.|  
|Istruzione IF|Viene eseguito il mapping.|  
|L'istruzione di ITERAZIONE|Viene eseguito il mapping.|  
|LASCIARE l'istruzione|Viene eseguito il mapping.|  
|Istruzione di ciclo|Viene eseguito il mapping.|  
|Ripetere l'istruzione|Viene eseguito il mapping.|  
|Istruzione RESIGNAL|Le condizioni non sono supportate. I messaggi possono essere facoltativi.|  
|Istruzione RETURN|Viene eseguito il mapping.|  
|Istruzione di segnale|Le condizioni non sono supportate. I messaggi possono essere facoltativi.|  
|WHILE (istruzione)|Viene eseguito il mapping.|  
|GET (istruzione) diagnostica|**SSMA viene eseguito il mapping ottenere diagnostica con le eccezioni seguenti:**<br /><br />ROW_COUNT – viene eseguito il mapping.<br /><br />DB2_RETURN_STATUS – viene eseguito il mapping.<br /><br />Testo_Messaggio – viene eseguito il mapping.<br /><br />DB2_SQL_NESTING_LEVEL - non esegue il mapping alla semantica di SQL Server<br /><br />DB2_TOKEN_STRING - non esegue il mapping alla semantica di SQL Server|  
|Cursori|**SSMA viene eseguito il mapping dei CURSORI con le eccezioni seguenti:**<br /><br />Istruzione di cursore ALLOCARE - non esegue il mapping alla semantica di SQL Server<br /><br />Istruzione di ASSOCIARE i LOCALIZZATORI - non esegue il mapping alla semantica di SQL Server<br /><br />Istruzione DECLARE CURSOR - clausola Returnability non è stato eseguito il mapping alla semantica SQL server<br /><br />Istruzione FETCH-mapping parziale. Le variabili come destinazione sono supportate solo. DESCRITTORE SQLDA non è stato eseguito il mapping alla semantica SQL server|  
|Variabili|Viene eseguito il mapping.|  
|Eccezioni, i gestori e condizioni|**SSMA esegue il mapping di "eccezioni" con le eccezioni seguenti:**<br /><br />Uscire da gestori: viene eseguito il mapping.<br /><br />ANNULLARE i gestori: viene eseguito il mapping.<br /><br />I gestori di continuare – non è stato eseguito il mapping.<br /><br />-Condizioni non eseguire il mapping alla semantica SQL server.|  
|SQL dinamica|Non è mappato.|  
|Alias|Viene eseguito il mapping.|  
|Nomi alternativi|Mapping parziale. L'elaborazione manuale è necessaria per l'oggetto sottostante|  
|Sinonimi|Viene eseguito il mapping.|  
|Funzioni standard in DB2|SSMA esegue il mapping di funzioni standard di DB2 quando una funzione equivalente è disponibile in SQL Server:|  
|Autorizzazione|Non è mappato.|  
|Predicati|Viene eseguito il mapping.|  
|SELECT INTO - istruzione|Non è mappato.|  
|I valori nell'istruzione.|Non è mappato.|  
|Controllo delle transazioni|Non è mappato.|  
  
## <a name="converting-db2-database-objects"></a>La conversione di oggetti di Database DB2  
Per convertire gli oggetti di database DB2, prima di selezionare gli oggetti che si desidera convertire e quindi chiedere di SSMA eseguire la conversione. Per visualizzare i messaggi di output durante la conversione nel **vista** dal menu **Output**.  
  
**Per convertire gli oggetti di DB2 in sintassi SQL Server**  
  
1.  In Visualizzatore metadati DB2, espandere il server DB2 e quindi espandere **schemi**.  
  
2.  Selezionare gli oggetti da convertire:  
  
    -   Per convertire tutti gli schemi, selezionare la casella di controllo accanto a **schemi**.  
  
    -   Per convertire o omettere un database, selezionare la casella di controllo accanto al nome dello schema.  
  
    -   Per convertire o omettere una categoria di oggetti, espandere uno schema, quindi selezionare o deselezionare la casella di controllo accanto alla categoria.  
  
    -   Per convertire o omettere i singoli oggetti, espandere la cartella di categoria, quindi selezionare o deselezionare la casella di controllo accanto all'oggetto.  
  
3.  Per convertire tutti gli oggetti selezionati, fare doppio clic su **schemi** e selezionare **convertire Schema**.  
  
    È anche possibile convertire oggetti singoli o le categorie di oggetti facendo l'oggetto o la relativa cartella padre, quindi **convertire Schema**.  
  
## <a name="viewing-conversion-problems"></a>Visualizzazione di problemi di conversione  
Alcuni oggetti DB2 potrebbero non essere convertiti. È possibile determinare le percentuali di successo di conversione visualizzando il report di riepilogo di conversione.  
  
**Per visualizzare un report di riepilogo**  
  
1.  Nel Visualizzatore metadati DB2, selezionare **schemi**.  
  
2.  Nel riquadro di destra, selezionare il **Report** scheda.  
  
    Questo report mostra il report di riepilogo di valutazione per tutti gli oggetti di database che sono stati valutati o convertiti. È inoltre possibile visualizzare un report di riepilogo per i singoli oggetti:  
  
    -   Per visualizzare il report per un singolo schema, selezionare lo schema in Visualizzatore metadati DB2.  
  
    -   Per visualizzare il report per un singolo oggetto, selezionare l'oggetto in Visualizzatore metadati DB2. Gli oggetti che presentano problemi di conversione hanno un'icona di errore rossa.  
  
Per gli oggetti che non è stato possibile conversione, è possibile visualizzare la sintassi che ha generato l'errore di conversione.  
  
**Per visualizzare i problemi di conversione singoli**  
  
1.  In DB2 metadati Esplora espandere **schemi**.  
  
2.  Espandere lo schema che viene visualizzata un'icona di errore rossa.  
  
3.  In schema di espandere una cartella che contiene un'icona di errore rossa.  
  
4.  Selezionare l'oggetto con un'icona di errore rossa.  
  
5.  Nel riquadro di destra, fare clic su di **Report** scheda.  
  
6.  Nella parte superiore del **Report** scheda è riportato un elenco a discesa. Se l'elenco Mostra **statistiche**, modificare la selezione di **origine**.  
  
    SSMA verrà visualizzato il codice sorgente e diversi pulsanti immediatamente sopra il codice.  
  
7.  Fare clic su di **problema successivo** pulsante. Si tratta di un'icona di errore rossa con una freccia rivolta verso destra.  
  
    SSMA verrà evidenziati il primo codice problematico origine che trova nell'oggetto corrente.  
  
Per ogni elemento che non è stato possibile convertire, è necessario determinare ciò che si desidera eseguire con tale oggetto:  
  
-   È possibile modificare il codice sorgente per le procedure nel **SQL** scheda.  
  
-   È possibile modificare l'oggetto nel database di DB2 per rimuovere o modificare il codice problematico. Per caricare il codice aggiornato in SSMA, è necessario aggiornare i metadati. Per altre informazioni, vedere [la connessione al Database DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/connecting-to-db2-database-db2tosql.md).  
  
-   È possibile escludere l'oggetto dalla migrazione. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati ed Esplora i metadati di DB2, deselezionare la casella di controllo accanto all'elemento prima di caricare gli oggetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] e la migrazione dei dati da DB2.  
  
## <a name="next-step"></a>Passaggio successivo  
Il passaggio successivo del processo di migrazione consiste nel [caricare gli oggetti convertiti in SQL Server](http://msdn.microsoft.com/en-us/f4ea1ced-9f9f-4a9d-88ab-81dbab64adc3).  
  
## <a name="see-also"></a>Vedere anche  
[La migrazione dei dati DB2 in SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-data-into-sql-server-db2tosql.md)  
  
