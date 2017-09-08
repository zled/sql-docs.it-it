---
title: Conversione di oggetti di Database di Access (AccessToSQL) | Documenti Microsoft
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
helpviewer_keywords:
- Access databases
- Access databases, converting schemas
- conversion
- conversion, converting schemas
- indexes, altering
- metadata
- metadata, altering
- metadata, converting
- migrating databases, one-click
- one-click migration
- schemas
- schemas, converting
- SQL
- SQL, converting
- syntax
- syntax, converting
- tables, altering
- translating Access to SQL Azure
- translating Access to SQL Server
ms.assetid: e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c
caps.latest.revision: 22
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 5fd1535f35afdfa53895816da2e3e32f539c04b5
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="converting-access-database-objects-accesstosql"></a>Conversione di oggetti di Database di Access (AccessToSQL)
Dopo aver aggiunto i database di Access e connesso a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, SSMA consente di visualizzare metadati per l'accesso e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o gli oggetti di database di SQL Azure. È possibile selezionare gli oggetti di database di Access e quindi eseguire la conversione degli schemi in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o degli schemi di SQL Azure.  
  
## <a name="the-conversion-process"></a>Il processo di conversione  
La conversione di oggetti di database utilizza le definizioni di oggetto di accedere ai metadati, li converte in equivalente [!INCLUDE[tsql](../../includes/tsql_md.md)] sintassi e quindi carica tali informazioni nel progetto. È quindi possibile visualizzare il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o gli oggetti di SQL Azure e le relative proprietà utilizzando [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o Visualizzatore metadati di SQL Azure.  
  
> [!IMPORTANT]  
> La conversione di oggetti non crea gli oggetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. Converte le definizioni degli oggetti solo e archivia le informazioni nel progetto SSMA.  
  
Durante la conversione, SSMA stampa lo stato sul riquadro di Output ed errore, avviso e messaggi informativi per il riquadro elenco errori. Utilizzare queste informazioni per determinare se è necessario modificare i database di Access o il processo di conversione per ottenere i risultati di conversione desiderato. È inoltre possibile utilizzare le informazioni contenute nel [preparare i database di Access per la migrazione](http://msdn.microsoft.com/en-us/9b80a9e0-08e7-4b4d-b5ec-cc998d3f5114) argomento per determinare quali verrà e non verrà convertiti.  
  
## <a name="setting-conversion-options"></a>Impostazione delle opzioni di conversione  
Prima di convertire gli oggetti, esaminare le opzioni di conversione del progetto nel **impostazioni progetto** la finestra di dialogo. Tramite questa finestra di dialogo, è possibile impostare la modalità di conversione di tabelle senza indici, chiavi primarie, vincoli di chiave esterna, timestamp e colonne indicizzate di credito in SSMA. Per ulteriori informazioni, vedere [impostazioni del progetto (conversione)](http://msdn.microsoft.com/en-us/bcebc635-c638-4ddb-924c-b9ccfef86388)  
  
## <a name="conversion-results"></a>Risultati di conversione  
Nella tabella seguente mostra gli oggetti di Access vengono convertiti e il valore risultante [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o gli oggetti di SQL Azure:  
  
|Oggetto di accesso|Oggetto risulta di SQL Server|  
|-----------------|-------------------------------|  
|table|table|  
|column|column|  
|indice|indice|  
|chiave esterna|chiave esterna|  
|Query|vista<br /><br />SELEZIONARE più query vengono convertite in viste. Altre query, ad esempio query di aggiornamento, non vengono migrate.<br /><br />Query SELECT che accettano parametri non vengono convertite, né sono query incrociati.|  
|report|non convertito.|  
|modulo|non convertito.|  
|(Macro)|non convertito.|  
|modulo|non convertito.|  
|Valore predefinito|Valore predefinito|  
|Consenti zero proprietà lunghezza della colonna|vincolo CHECK|  
|regola di convalida di colonna|vincolo CHECK|  
|regola di convalida della tabella|vincolo CHECK|  
|chiave primaria|chiave primaria|  
  
## <a name="converting-access-objects"></a>La conversione di oggetti di Access  
Per convertire gli oggetti di database di Access, è necessario selezionare gli oggetti a cui che si desidera convertire e quindi chiedere di SSMA eseguire la conversione. Per visualizzare i messaggi di output durante la conversione nel **vista** dal menu **Output**.  
  
**Per selezionare e convertire gli oggetti di database di accesso in sintassi SQL Server o SQL Azure**  
  
1.  Nel Visualizzatore metadati di accesso, espandere **accesso metabase**, quindi espandere **database**.  
  
2.  Eseguire una o più delle operazioni seguenti:  
  
    -   Per convertire tutti i database, selezionare la casella di controllo accanto a **database**.  
  
    -   Per convertire o omettere i singoli database, selezionare o deselezionare la casella di controllo accanto al nome del database.  
  
    -   Per convertire o omettere le query, espandere il database, quindi selezionare o deselezionare il **query** casella di controllo.  
  
    -   Per convertire o omettere le singole tabelle, espandere il database, **tabelle**e quindi selezionare o deselezionare la casella di controllo accanto alla tabella.  
  
3.  Eseguire una delle operazioni seguenti:  
  
    -   Per convertire gli schemi, fare doppio clic su **database** e selezionare **convertire Schema**.  
  
        È anche possibile convertire i singoli oggetti. Per convertire un oggetto, indipendentemente da quali oggetti sono selezionati, l'oggetto e scegliere **convertire Schema**.  
  
        Quando un oggetto è stato convertito, viene visualizzato in grassetto in soluzioni di accesso ai metadati.  
  
    -   Per convertire, caricare, eseguire la migrazione di schemi e dati in un unico passaggio, fare doppio clic su database e selezionare **Converti, carica ed eseguire la migrazione**.  
  
4.  Esaminare i messaggi di **Output** riquadro ed eventuali errori e avvisi nel **elenco errori** riquadro.  
  
## <a name="altering-tables-and-indexes"></a>Modifica di tabelle e indici  
Dopo la conversione di accedere ai metadati per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o i metadati di SQL Azure, e prima di caricare gli oggetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, è possibile modificare [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o indici e tabelle di SQL Azure.  
  
**Per modificare le proprietà di tabella o un indice**  
  
1.  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o Visualizzatore metadati di SQL Azure, selezionare la tabella o indice da modificare.  
  
2.  Nel **tabella** scheda, fare clic sulla proprietà che si desidera modificare e quindi immettere o selezionare la nuova impostazione. Ad esempio, modificare nvarchar (15) a nvarchar (20) oppure selezionare una casella di controllo per impostare una colonna di tabella ammette valori null.  
  
    Spostare il cursore fuori della cella della proprietà modificata. È possibile farlo facendo clic su un'altra riga o premendo il tasto Tab.  
  
3.  Fare clic su **Applica**.  
  
È ora possibile visualizzare le modifiche nel codice nel **SQL** scheda.  
  
## <a name="next-step"></a>Passaggio successivo  
Il passaggio successivo del processo di migrazione è [caricare gli oggetti di database convertito in SQL Server](http://msdn.microsoft.com/en-us/4e854eee-b10c-4f0b-9d9e-d92416e6f2ba)  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database di Access a SQL Server](http://msdn.microsoft.com/en-us/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  

