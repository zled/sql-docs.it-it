---
title: Esportazione di un inventario di accesso (AccessToSQL) | Documenti Microsoft
ms.prod: sql
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
helpviewer_keywords:
- Access databases
- Access databases, exporting metadata
- exporting
- exporting Access metadata
- exporting, Access metadata
- exporting, querying exported metadata
- inventories of Access databases
- querying exported metadata
ms.assetid: 7e1941fb-3d14-4265-aff6-c77a4026d0ed
caps.latest.revision: 18
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: eb5d6e4bcd3699d99dd512ea766087a33f2adf45
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34773537"
---
# <a name="exporting-an-access-inventory-accesstosql"></a>Esportazione di un inventario di accesso (AccessToSQL)
Se si dispone di più database di Access e non si è certi di quelle per eseguire la migrazione in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], è possibile esportare un inventario di tutti i database di Access in un progetto. È possibile quindi esaminare e query sui metadati per determinare i database e gli oggetti all'interno di tali database per eseguire la migrazione di inventario. L'inventario consente rapidamente trovare risposte alle domande, ad esempio le operazioni seguenti:  
  
-   Quali sono i database più grande?  
  
-   Chi possiede la maggior parte dei database?  
  
-   I database che contengono le stesse tabelle?  
  
-   I database non sono stati modificati negli ultimi sei mesi?  
  
-   Database che contengono informazioni riservate?  
  
Alla fine di questo argomento vengono forniti esempi di query che consentono di rispondere a queste domande.  
  
## <a name="exported-metadata"></a>Metadati esportati  
SSMA consente di esportare i metadati relativi a accesso database, tabelle, colonne, indici, chiavi esterne, le query, report, form, macro e moduli. I metadati su ognuna di queste categorie di elementi vengono esportati in una tabella separata. Per gli schemi di queste tabelle, vedere [accesso inventario schemi](http://msdn.microsoft.com/en-us/fdd3cff2-4d62-4395-8acf-71ea8f17f524).  
  
## <a name="exporting-inventory-data"></a>Esportazione dei dati di inventario  
Per esportare un inventario di accesso, deve prima aprire o creare un progetto di SSMA e quindi aggiungere il database di Access che si desidera analizzare. Dopo aver aggiunto i database a un progetto SSMA, si esporta i metadati relativi a tali database in un determinato [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database e lo schema. Se necessario, SSMA vengono create tabelle per archiviare i metadati. SSMA aggiunge quindi i metadati sui database di Access per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database.  
  
> [!NOTE]  
> Un database di Access può essere diviso in più file: un database back-end che contiene le tabelle e database front-end che contengono le query, form, report, le macro, moduli e tasti di scelta rapida. Se si desidera eseguire la migrazione di un database di divisione per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], aggiungere il database front-end per SSMA.  
  
Le istruzioni seguenti descrivono come creare un progetto, aggiungere il progetto di database, connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]e quindi esportare i dati di inventario.  
  
**Per creare un progetto**  
  
1.  Aprire SSMA per l'accesso.  
  
2.  Scegliere **Nuovo progetto** dal menu **File**.  
  
    Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
3.  Nel **nome** , immettere un nome per il progetto.  
  
4.  Nel **percorso** immettere o selezionare una cartella per il progetto.  
  
5.  Nel **Esegui migrazione a** combinata, selezionare la versione di destinazione a cui si desidera eseguire la migrazione e quindi fare clic su **OK**.  
  
Per ulteriori informazioni sulla creazione di progetti, vedere [creazione e gestione dei progetti](http://msdn.microsoft.com/en-us/f2d1f0b0-5394-4adb-b3f3-abd71eb68ca7).  
  
**Per trovare e aggiungere database**  
  
1.  Nel **File** menu, fare clic su **trovare database**.  
  
2.  Nella creazione guidata database di ricerca, immettere l'unità, percorso del file o percorso UNC che si desidera cercare. In alternativa, fare clic su **Sfoglia** per selezionare la cartella di rete o unità.  
  
3.  Fare clic su **Aggiungi** aggiungere il percorso nella casella di riepilogo.  
  
    Ripetere i due passaggi precedenti per aggiungere percorsi di ricerca aggiuntive.  
  
4.  Facoltativamente, aggiungere criteri di ricerca per filtrare l'elenco dei database che vengono restituiti.  
  
    > [!IMPORTANT]  
    > Il **tutto o parte del nome file** casella di testo non supporta caratteri jolly.  
  
5.  Fare clic su **analisi**.  
  
    Viene visualizzata la pagina di analisi. Mostra i database che sono stati trovati e lo stato di avanzamento di ricerca. Per interrompere la ricerca, fare clic su **arrestare**.  
  
6.  Nella pagina Seleziona file, selezionare ogni database che si desidera aggiungere al progetto.  
  
    È possibile utilizzare il **Seleziona tutto** e **Cancella tutto** pulsanti nella parte superiore dell'elenco per selezionare o deselezionare tutti i database. È anche possibile tenere premuto il tasto CTRL per selezionare più righe o tenere premuto il tasto MAIUSC per selezionare un intervallo di righe.  
  
7.  Scegliere **Avanti**.  
  
8.  Nella pagina verifica, fare clic su **fine**.  
  
Per ulteriori informazioni sull'aggiunta di database per i progetti, vedere [aggiunta e rimozione di file di Database di Access](http://msdn.microsoft.com/en-us/e944c740-4c8a-4bc1-b0ed-be57bc06dced).  
  
**Per connettersi a SQL Server**  
  
1.  Nel **File** dal menu **Connetti al Server SQL**.  
  
2.  Nella finestra di dialogo connessione, immettere o selezionare il nome dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
    -   Se ci si connette all'istanza predefinita nel computer locale, è possibile immettere **localhost** o un punto (**.**).  
  
    -   Se ci si connette all'istanza predefinita in un altro computer, immettere il nome del computer.  
  
    -   Se ci si connette a un'istanza denominata, immettere il nome del computer, una barra rovesciata e il nome dell'istanza. Ad esempio: MyServer\MyInstance.  
  
3.  Nel **Database** , immettere il nome del database di destinazione per i metadati esportati.  
  
4.  Se l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] è configurato per accettare le connessioni su una porta non predefinito, immettere il numero di porta utilizzato per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] connessioni nel **porta Server** casella. Per l'istanza predefinita di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], il numero di porta predefinito è 1433. Per le istanze denominate, SSMA tenta di ottenere il numero di porta dal [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] servizio Browser.  
  
5.  Nel **autenticazione** -menu a discesa, seleziona il tipo di autenticazione da utilizzare per la connessione. Per utilizzare l'account di Windows, selezionare **l'autenticazione di Windows**. Per utilizzare un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] account di accesso, selezionare **autenticazione di SQL Server**, quindi specificare un nome utente e una password.  
  
Per ulteriori informazioni sulla connessione al [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], vedere [ci si connette a SQL Server &#40;AccessToSQL&#41;](../../ssma/access/connecting-to-sql-server-accesstosql.md).  
  
**Per esportare le informazioni di inventario**  
  
1.  In Esplora metadati accesso espandere **accesso metabase**.  
  
2.  Selezionare la casella di controllo accanto a **database**.  
  
    Per omettere i singoli database o oggetti di database, espandere il **database** cartella e quindi deselezionare la casella di controllo accanto al database o di un oggetto di database.  
  
3.  Fare doppio clic su **database** e selezionare **Esporta Schema**.  
  
4.  Nel **selezionare uno Schema per l'esportazione** la finestra di dialogo, selezionare lo schema di destinazione per i metadati esportati e quindi fare clic su **OK**.  
  
Ogni volta che si esporta i metadati, SSMA aggiunge i dati per l'inventario. I dati esistenti nell'inventario non viene aggiornati o eliminati.  
  
## <a name="querying-the-exported-metadata"></a>L'esecuzione di query i metadati esportati  
Dopo aver esportato i metadati relativi a database di Access, è possibile eseguire una query di metadati. Le istruzioni seguenti viene descritto come per utilizzare la finestra dell'Editor di Query in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] per eseguire query.  
  
**Per eseguire query sui metadati**  
  
1.  Dal **avviare** dal menu **tutti i programmi**, scegliere **Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005** o **Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008** o **Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012**e quindi fare clic su **SQL Server Management Studio**.  
  
2.  Nel **Connetti al Server** la finestra di dialogo, verificare le impostazioni e quindi fare clic su **Connetti**.  
  
3.  Sulla barra degli strumenti Management Studio, fare clic su **nuova Query** per aprire l'Editor di Query.  
  
4.  Nella finestra dell'Editor di Query, immettere una query. Nella sezione seguente vengono illustrati alcuni esempi.  
  
5.  Premere il tasto F5 per eseguire la query.  
  
## <a name="query-examples"></a>Esempi di query  
Prima di eseguire le query seguenti, è consigliabile eseguire un utilizzo *database_name* query per assicurarsi che le query vengono eseguite nel database che contiene i metadati esportati. Ad esempio, se è stata esportata in un database denominato MyAccessMetadata metadati, aggiungere quanto segue all'inizio del [!INCLUDE[tsql](../../includes/tsql_md.md)] codice:  
  
```  
USE MyAccessMetadata;  
GO  
```  
I seguenti esempi utilizzano tutti la **dbo** dello schema. Se è stato esportato i metadati in un altro schema, assicurarsi di modificare lo schema quando si eseguono queste query.  
  
### <a name="what-tables-and-columns-are-in-these-databases"></a>Le tabelle e le colonne si trovano in questi database?  
La query seguente crea un join tra le tabelle che contengono i metadati del database, tabelle e colonna e quindi restituisce i nomi di tutti i database, tabelle e colonne, ordinati in base al nome di colonna:  
  
```  
SELECT DatabaseName, TableName, ColumnName   
FROM dbo.SSMA_Access_InventoryColumns C  
JOIN dbo.SSMA_Access_InventoryTables T  
ON C.TableId = T.TableId  
JOIN dbo.SSMA_Access_InventoryDatabases D  
ON T.DatabaseId = D.DatabaseId  
ORDER BY ColumnName;  
```  
  
### <a name="what-are-the-largest-databases"></a>Quali sono i database più grande?  
La query seguente restituisce il nome del database, dimensioni del file e numero di tabelle in ogni database di Access, ordinati per dimensioni del file:  
  
```  
SELECT DatabaseName, FileSize, TablesCount  
FROM dbo.SSMA_Access_InventoryDatabases  
ORDER BY FileSize DESC;  
```  
  
### <a name="who-is-the-owner-of-most-of-the-databases"></a>Chi è il proprietario della maggior parte dei database?  
La query seguente restituisce il nome del database e ogni database di Access, ordinati in base a proprietario.  
  
```  
SELECT DatabaseName, FileOwner  
FROM dbo.SSMA_Access_InventoryDatabases  
ORDER BY FileOwner;  
```  
  
### <a name="which-databases-contain-the-same-tables"></a>I database che contengono le stesse tabelle?  
La query seguente utilizza una sottoquery per trovare tutti i nomi di tabella che vengono visualizzati più volte nell'elenco di tabelle e quindi utilizza l'elenco delle tabelle per ottenere il nome del database. I risultati vengono restituiti come il nome del database e quindi il nome della tabella e vengono ordinati in base al nome della tabella.  
  
```  
SELECT DatabaseName, TableName   
FROM dbo.SSMA_Access_InventoryTables T  
JOIN dbo.SSMA_Access_InventoryDatabases D  
ON D.DatabaseId = T.DatabaseId  
WHERE TableName IN (  
SELECT TableName   
FROM dbo.SSMA_Access_InventoryTables  
GROUP BY TableName   
HAVING count(*)>1  
)  
ORDER BY TableName;  
```  
  
### <a name="which-databases-were-not-modified-in-the-last-six-months"></a>I database non sono stati modificati negli ultimi sei mesi?  
La query seguente ottiene la data corrente, ottiene il valore del mese per sei mesi e quindi restituisce un elenco di database con una data di modifica di maggiore di 6 mesi.  
  
```  
SELECT DatabaseName, DateModified  
FROM dbo.SSMA_Access_InventoryDatabases  
WHERE DATEDIFF(month, DateModified, GETDATE()) > 6  
ORDER BY DateModified;  
```  
  
### <a name="which-databases-contain-private-information"></a>Database che contengono informazioni riservate?  
Database di Access potrebbero contenere informazioni riservate o personali. È consigliabile spostare i database [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] per sfruttare le funzionalità di sicurezza. Se si conosce che hanno un nome specifico, le colonne che contengono dati sensibili o contengono caratteri specifici, è possibile utilizzare una query per trovare tutte le colonne che contengono tali informazioni. Ad esempio, è possibile trovare tutte le colonne che includono la stringa "salary".  La query restituisce quindi il nome del database, nome della tabella e il nome di colonna.  
  
```  
SELECT DatabaseName, TableName, ColumnName   
FROM dbo.SSMA_Access_InventoryColumns C  
JOIN dbo.SSMA_Access_InventoryTables T  
ON C.TableId = T.TableId  
JOIN dbo.SSMA_Access_InventoryDatabases D  
ON T.DatabaseId = D. DatabaseId  
WHERE ColumnName LIKE '%salary%';  
```  
Se non si conosce il nome della colonna, è possibile scrivere una query per restituire tutte le colonne. A tale scopo, rimuovere la clausola WHERE dalla query precedente.  
  
## <a name="see-also"></a>Vedere anche  
[Preparazione dei database di Access per la migrazione](http://msdn.microsoft.com/en-us/9b80a9e0-08e7-4b4d-b5ec-cc998d3f5114)  
  
