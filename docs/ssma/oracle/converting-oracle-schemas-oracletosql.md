---
title: Conversione di schemi Oracle (OracleToSQL) | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-oracle
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Conversion Results
ms.assetid: e021182d-31da-443d-b110-937f5db27272
caps.latest.revision: 14
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: a0b94e194c7d1db8dc4de0c56d3d9c37b5586d6a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="converting-oracle-schemas-oracletosql"></a>Conversione di schemi Oracle (OracleToSQL)
Dopo aver connesso a Oracle, connesso alla [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], e imposta il progetto e le opzioni di mapping di dati, è possibile convertire oggetti di database Oracle [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oggetti di database.  
  
## <a name="the-conversion-process"></a>Il processo di conversione  
La conversione di oggetti di database utilizza le definizioni degli oggetti da Oracle, li converte simile [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] degli oggetti e quindi carica tali informazioni nei metadati di SSMA. Impossibile caricare le informazioni nell'istanza [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. È quindi possibile visualizzare gli oggetti e le relative proprietà utilizzando il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati.  
  
Durante la conversione, SSMA Stampa messaggi di output nel riquadro di Output e i messaggi di errore nel riquadro elenco errori. Utilizzare le informazioni di output e l'errore per determinare se è necessario modificare i database Oracle o il processo di conversione per ottenere i risultati di conversione desiderato.  
  
## <a name="setting-conversion-options"></a>Impostazione delle opzioni di conversione  
Prima di convertire gli oggetti, esaminare le opzioni di conversione del progetto nel **impostazioni progetto** la finestra di dialogo. Tramite questa finestra di dialogo, è possibile impostare la modalità di conversione di funzioni e variabili globali in SSMA. Per altre informazioni, vedere [impostazioni del progetto di &#40;conversione&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-conversion-oracletosql.md).  
  
## <a name="conversion-results"></a>Risultati di conversione  
Nella tabella seguente mostra gli oggetti di Oracle vengono convertiti e il valore risultante [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oggetti:  
  
|||  
|-|-|  
|Oggetti di Oracle|Oggetti SQL Server risultanti|  
|Funzioni|Se la funzione può essere convertita direttamente in [!INCLUDE[tsql](../../includes/tsql_md.md)], SSMA crea una funzione.<br /><br />In alcuni casi, la funzione deve essere convertita a una stored procedure. In questo caso, SSMA crea una stored procedure e una funzione che chiama la stored procedure.|  
|Procedure|Se la procedura può essere convertita direttamente in [!INCLUDE[tsql](../../includes/tsql_md.md)], SSMA crea una stored procedure.<br /><br />In alcuni casi, una stored procedure deve essere chiamata in una transazione autonoma. In questo caso, SSMA crea due stored procedure: una che implementa la procedura e un altro che viene utilizzata per chiamare l'implementazione di stored procedure.|  
|Pacchetti|SSMA consente di creare un set di stored procedure e funzioni che sono unificate da nomi di oggetti simili.|  
|Sequenze|SSMA crea gli oggetti sequenza (SQL Server 2012 o SQL Server 2014) o emula sequenze di Oracle.|  
|Tabelle con gli oggetti dipendenti, ad esempio indici e trigger|SSMA consente di creare tabelle con gli oggetti dipendenti.|  
|Consente di visualizzare gli oggetti dipendenti, ad esempio i trigger|SSMA consente di creare visualizzazioni con gli oggetti dipendenti.|  
|Viste materializzate|**SSMA consente di creare viste indicizzate in SQL server con alcune eccezioni. Conversione non riesce se la vista materializzata include uno o più costrutti indicati di seguito:**<br /><br />Funzione definita dall'utente<br /><br />Campo non deterministica / funzione / espressione di selezione, in cui o clausole GROUP BY<br /><br />Utilizzo della colonna Float in SELECT * in o clausole GROUP BY (caso speciale di un problema precedente)<br /><br />(Inclusa nidificata tabelle) del tipo di dati personalizzati<br /><br />COUNT (distinct &lt;campo&gt;)<br /><br />FETCH<br /><br />OUTER join (LEFT, RIGHT o FULL)<br /><br />Sottoquery, altra visualizzazione<br /><br />IN, RANK, LEAD, LOG<br /><br />MIN, MAX<br /><br />UNION, SOTTRAZIONE, SI INTERSECANO<br /><br />HAVING|  
|Trigger|**SSMA consente di creare trigger in base alle regole seguenti:**<br /><br />PRIMA di convertire i trigger per trigger INSTEAD OF.<br /><br />I trigger AFTER vengono convertiti in trigger AFTER.<br /><br />I trigger INSTEAD OF vengono convertiti in trigger INSTEAD OF. Più trigger INSTEAD OF definito nella stessa operazione sono combinati in un trigger.<br /><br />I trigger a livello di riga vengono emulati utilizzano i cursori.<br /><br />Trigger di propagazione vengono convertiti in più trigger singolo.|  
|Sinonimi|**I sinonimi vengono creati per i seguenti tipi di oggetto:**<br /><br />Le tabelle e oggetto<br /><br />Viste e le viste di oggetto<br /><br />Stored procedure<br /><br />Funzioni<br /><br />**I sinonimi per gli oggetti seguenti sono risolte e sostituiti da riferimenti a oggetti direct:**<br /><br />Sequenze<br /><br />Pacchetti<br /><br />Oggetti dello schema di classe Java<br /><br />Tipi di oggetto definito dall'utente<br /><br />I sinonimi per un altro sinonimo non possono essere migrati e verranno contrassegnati come errori.<br /><br />Sinonimi non vengono creati per le viste Materialized.|  
|Tipi definiti dall'utente|**SSMA non fornisce supporto per la conversione dei tipi definiti dall'utente. Tipi definiti dall'utente, incluso il relativo utilizzo in programmi PL/SQL sono contrassegnati con errori di conversione speciali interattiva le regole seguenti:**<br /><br />Colonna della tabella di un tipo definito dall'utente viene convertita in VARCHAR(8000).<br /><br />Argomento dell'utente di tipo definito in una stored procedure o funzione viene convertita in VARCHAR(8000).<br /><br />Variabile di tipo definito dall'utente in blocco PL/SQL viene convertito in VARCHAR(8000).<br /><br />Oggetto tabella viene convertita in una tabella Standard.<br /><br />Vista dell'oggetto viene convertito in una vista Standard.|  
  
## <a name="converting-oracle-database-objects"></a>La conversione di oggetti di Database Oracle  
Per convertire gli oggetti di database Oracle, prima di selezionare gli oggetti che si desidera convertire e quindi chiedere di SSMA eseguire la conversione. Per visualizzare i messaggi di output durante la conversione nel **vista** dal menu **Output**.  
  
**Per convertire gli oggetti di Oracle per la sintassi SQL Server**  
  
1.  In Visualizzatore metadati Oracle, espandere il server Oracle e quindi espandere **schemi**.  
  
2.  Selezionare gli oggetti da convertire:  
  
    -   Per convertire tutti gli schemi, selezionare la casella di controllo accanto a **schemi**.  
  
    -   Per convertire o omettere un database, selezionare la casella di controllo accanto al nome dello schema.  
  
    -   Per convertire o omettere una categoria di oggetti, espandere uno schema, quindi selezionare o deselezionare la casella di controllo accanto alla categoria.  
  
    -   Per convertire o omettere i singoli oggetti, espandere la cartella di categoria, quindi selezionare o deselezionare la casella di controllo accanto all'oggetto.  
  
3.  Per convertire tutti gli oggetti selezionati, fare doppio clic su **schemi** e selezionare **convertire Schema**.  
  
    È anche possibile convertire oggetti singoli o le categorie di oggetti facendo l'oggetto o la relativa cartella padre, quindi **convertire Schema**.  
  
## <a name="viewing-conversion-problems"></a>Visualizzazione di problemi di conversione  
Alcuni oggetti Oracle potrebbero non essere convertiti. È possibile determinare le percentuali di successo di conversione visualizzando il report di riepilogo di conversione.  
  
**Per visualizzare un report di riepilogo**  
  
1.  Nel Visualizzatore metadati Oracle, selezionare **schemi**.  
  
2.  Nel riquadro di destra, selezionare il **Report** scheda.  
  
    Questo report mostra il report di riepilogo di valutazione per tutti gli oggetti di database che sono stati valutati o convertiti. È inoltre possibile visualizzare un report di riepilogo per i singoli oggetti:  
  
    -   Per visualizzare il report per un singolo schema, selezionare lo schema in Visualizzatore metadati Oracle.  
  
    -   Per visualizzare il report per un singolo oggetto, selezionare l'oggetto in Visualizzatore metadati Oracle. Gli oggetti che presentano problemi di conversione hanno un'icona di errore rossa.  
  
Per gli oggetti che non è stato possibile conversione, è possibile visualizzare la sintassi che ha generato l'errore di conversione.  
  
**Per visualizzare i problemi di conversione singoli**  
  
1.  In Oracle metadati Esplora espandere **schemi**.  
  
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
  
-   È possibile modificare l'oggetto nel database Oracle per rimuovere o modificare il codice problematico. Per caricare il codice aggiornato in SSMA, è necessario aggiornare i metadati. Per altre informazioni, vedere [connessione a Oracle Database &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-oracle-database-oracletosql.md).  
  
-   È possibile escludere l'oggetto dalla migrazione. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati ed Esplora i metadati di Oracle, deselezionare la casella di controllo accanto all'elemento prima di caricare gli oggetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] e la migrazione dei dati da Oracle.  
  
## <a name="next-step"></a>Passaggio successivo  
Il passaggio successivo del processo di migrazione consiste nel [caricare gli oggetti convertiti in SQL Server](http://msdn.microsoft.com/en-us/a8ae33b2-1883-4785-922b-ea0e31c0b37a).  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di Oracle database a SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
