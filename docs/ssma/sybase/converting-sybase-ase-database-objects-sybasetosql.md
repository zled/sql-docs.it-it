---
title: La conversione di oggetti di Database ASE Sybase (SybaseToSQL) | Documenti Microsoft
ms.custom: ''
ms.date: 12/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Converting Database Objects
ms.assetid: 509cb65d-2f54-427a-83d7-37919cc4e3e3
caps.latest.revision: 8
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 94dd2dd9d2c7dab4e8c29c1bc109c5fbb7c5313c
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="converting-sap-ase-database-objects-sybasetosql"></a>La conversione di oggetti di database SAP ASE (SybaseToSQL)
Dopo avere stabilito la connessione a SAP Adaptive Server Enterprise (ASE), connesso alla [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure e imposta il progetto e le opzioni di mapping di dati, è possibile convertire oggetti di database SAP Adaptive Server Enterprise (ASE) [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure oggetti.  
  
## <a name="the-conversion-process"></a>Il processo di conversione  
La conversione di oggetti di database utilizza le definizioni degli oggetti da ASE, li converte simile [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] SQL Azure o gli oggetti e quindi carica tali informazioni nei metadati di SSMA. Impossibile caricare le informazioni nell'istanza [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. È quindi possibile visualizzare gli oggetti e le relative proprietà utilizzando il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o Visualizzatore metadati di SQL Azure.
  
Durante la conversione, SSMA Stampa messaggi di output per i messaggi di errore e riquadro di Output per il **elenco errori** riquadro. Utilizzare le informazioni di output e l'errore per determinare se è necessario modificare i database di base o il processo di conversione per ottenere i risultati di conversione desiderato.  
  
## <a name="setting-conversion-options"></a>Impostazione delle opzioni di conversione  
Prima di convertire gli oggetti, esaminare le opzioni di conversione del progetto nel **impostazioni progetto** la finestra di dialogo. Tramite questa finestra di dialogo, è possibile impostare la modalità di conversione di funzioni e variabili globali in SSMA. Per altre informazioni, vedere [impostazioni del progetto di &#40;conversione&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-conversion-sybasetosql.md).  
  
## <a name="converting-ase-database-objects"></a>La conversione di oggetti di database ASE  
Per convertire gli oggetti di database di base, selezionare innanzitutto gli oggetti che si desidera convertire e quindi chiedere di SSMA eseguire la conversione. Per visualizzare i messaggi di output durante la conversione nel **vista** dal menu **Output**.  
  
**Per convertire gli oggetti ASE alla sintassi SQL Server o SQL Azure**  
  
1.  In Visualizzatore metadati Sybase, espandere il server di base e quindi espandere **database**.  
  
2.  Selezionare gli oggetti da convertire:  
  
    -   Per convertire tutti i database, selezionare la casella di controllo accanto a **database**.  
  
    -   Per convertire o omettere un database, selezionare o deselezionare la casella di controllo accanto al nome del database.  
  
    -   Per convertire o omettere singoli schemi, espandere il database, **schemi**e quindi selezionare o deselezionare la casella di controllo accanto a schema.  
  
    -   Per convertire o omettere una categoria di oggetti, espandere lo schema, quindi selezionare o deselezionare la casella di controllo accanto alla categoria.  
  
    -   Per convertire o omettere i singoli oggetti, espandere la cartella di categoria, quindi selezionare o deselezionare la casella di controllo accanto all'oggetto.  
  
3.  Per convertire tutti gli oggetti selezionati, fare doppio clic su **database**, quindi selezionare **convertire Schema**.  
  
    È anche possibile convertire oggetti singoli o le categorie di oggetti facendo clic l'oggetto o la cartella che contiene, e quindi selezionando **convertire Schema**.  
  
> [!NOTE]  
> Alcune delle funzioni di sistema SAP ASE non corrispondono esattamente le funzioni di sistema di SQL Server equivalente nel comportamento. Per emulare il comportamento di SAP ASE, SSMA genera funzioni definite dall'utente del database di SQL Server convertito in uno schema denominato 's2ss'. A seconda delle impostazioni di progetto, alcune delle funzioni di sistema di SQL Server vengono sostituiti con queste funzioni emulate. SSMA consente di creare le funzioni definite dall'utente seguenti:  
  
||||  
|-|-|-|  
|**char_length_nvarchar**|**index_colorder**|**ssma_datepart**|  
|**char_length_varchar**|**inttohex**|**substring_nvarchar**|  
|**charindex_nvarchar**|**ssma_datediff**|**substring_varbinary**|  
|**charindex_varchar**|**hextoint**|**substring_varchar**|  
|**ulowsurr**|**to_unichar**|**ssma_current_time**|  
|**uhighsurr**|||  
  
## <a name="objects-not-supported-in-azure-sql"></a>Oggetti non supportati in SQL Azure  
Le parole chiave T-SQL seguenti vengono utilizzate da SSMA per SAP ASE durante la conversione a SQL Server locale, ma queste parole chiave non sono supportate dalla sintassi T-SQL di SQL Azure:  
  
||||  
|-|-|-|  
|CHECKPOINT|CREATE/ALTER/DROP DEFAULT|CREATE/DROP RULE|  
|DBCC TRACEOFF|DBCC TRACEON|ISTRUZIONE GRANT/REVOKE/DENY ALL|  
|KILL|READTEXT|SELECT INTO|  
|SET OFFSETS|SETUSER|SHUTDOWN|  
|WRITETEXT|||  
  
## <a name="viewing-conversion-problems"></a>Visualizzazione di problemi di conversione  
Alcuni oggetti SAP ASE potrebbero non essere convertito. È possibile determinare le percentuali di successo di conversione visualizzando il report di riepilogo di conversione.  
  
**Per visualizzare un report di riepilogo**  
  
1.  Nel Visualizzatore metadati Sybase, selezionare **database**.  
  
2.  Nel riquadro di destra, selezionare il **Report** scheda.  
  
    Questo report mostra il report di riepilogo di valutazione per tutti gli oggetti di database che sono stati valutati o convertiti. È inoltre possibile visualizzare un report di riepilogo per i singoli oggetti:  
  
    -   Per visualizzare il report per un singolo database, selezionare il database in Visualizzatore metadati Sybase.  
  
    -   Per visualizzare il report per un oggetto di database singoli, selezionare l'oggetto in Visualizzatore metadati Sybase. Gli oggetti che presentano problemi di conversione hanno un'icona di errore rossa.  
  
Per gli oggetti che non è stato possibile conversione, è possibile visualizzare la sintassi che ha generato l'errore di conversione.  
  
**Per visualizzare i problemi di conversione singoli**  
  
1.  In Esplora metadati Sybase espandere **database**.  
  
2.  Espandere il database che viene visualizzata un'icona di errore rossa.  
  
3.  Espandere il **schemi** cartella, quindi espandere lo schema che viene visualizzata un'icona di errore rossa.  
  
4.  In schema di espandere una cartella che contiene un'icona di errore rossa.  
  
5.  Selezionare l'oggetto con un'icona di errore rossa.  
  
6.  Nel riquadro di destra, selezionare il **Report** scheda.  
  
7.  Nella parte superiore del **Report** scheda è riportato un elenco a discesa. Se l'elenco Mostra **statistiche**, modificare la selezione di **origine**.  
  
    SSMA verrà visualizzato il codice sorgente e diversi pulsanti immediatamente sopra il codice.  
  
8.  Selezionare **problema successivo**, un'icona di errore rossa con una freccia rivolta verso destra.  
  
    SSMA per SAP ASE verrà evidenziati il primo codice problematico origine che trova nell'oggetto corrente.  
  
Per ogni elemento che non è stato possibile convertire, è necessario determinare ciò che si desidera eseguire con tale oggetto:  
  
-   È possibile modificare il codice sorgente per procedure e trigger nel **SQL** scheda.  
  
-   È possibile modificare l'oggetto SAP ASE per rimuovere o modificare il codice problematico. Per caricare il codice aggiornato in SSMA, è necessario aggiornare i metadati. Per altre informazioni, vedere [connessione a SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md).  
  
-   È possibile escludere l'oggetto dalla migrazione. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o Visualizzatore metadati di SQL Azure e Visualizzatore metadati Sybase, deselezionare la casella di controllo accanto all'elemento prima di caricare gli oggetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure e la migrazione dei dati da SAP ASE.  
  
## <a name="next-steps"></a>Passaggi successivi  
Il passaggio successivo del processo di migrazione è [il caricamento di convertire gli oggetti di Database in SQL Server o SQL Azure (SybaseToSQL)](http://msdn.microsoft.com/en-us/4c59256f-99a8-4351-9559-a455813dbd06).  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database SAP ASE a SQL Server - Database SQL di Azure &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
