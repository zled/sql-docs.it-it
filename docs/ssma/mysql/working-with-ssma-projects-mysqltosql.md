---
title: Utilizzo di progetti SSMA (MySQLToSQL) | Documenti Microsoft
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
- Working with SSMA projects, create new project
- Working with SSMA projects, customize settings
- Working with SSMA projects, Open project
- Working with SSMA projects, Save project
ms.assetid: 9e4394e9-f177-41d9-839e-5d53a9c9b840
caps.latest.revision: 20
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 44d7c381e4cc0599e24f5df1024b31b75b1598f7
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="working-with-ssma-projects-mysqltosql"></a>Lavorare con progetti SSMA (MySQLToSQL)
Per eseguire la migrazione di database MySQL a SQL Server o SQL Azure, è innanzitutto necessario creare un progetto SSMA. Il progetto è un file che contiene le informazioni seguenti:  
  
-   Metadati relativi ai database di MySQL che si desidera eseguire la migrazione a SQL Server o SQL Azure.  
  
-   Metadati relativi all'istanza di destinazione di SQL Server o SQL Azure che riceverà la migrazione di oggetti e i dati.  
  
-   Informazioni di connessione SQL Server o SQL Azure.  
  
-   Le impostazioni del progetto.  
  
Quando si apre un progetto, questo viene disconnesso da MySQL e SQL Server o SQL Azure. Che consente di lavorare offline. Per ulteriori informazioni su come connettersi a SQL Server, vedere [connessione a SQL Server &#40; MySQLToSQL &#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
## <a name="reviewing-default-project-settings"></a>Verificare le impostazioni di progetto predefinito  
SSMA contiene diverse impostazioni per la conversione e il caricamento del database, la migrazione dei dati e la sincronizzazione di SSMA con MySQL e SQL Server o SQL Azure. Le impostazioni predefinite sono appropriate per molti utenti. Tuttavia, prima di creare un nuovo progetto SSMA, è consigliabile verificare le impostazioni. Se necessario, è possibile modificare le impostazioni predefinite che verranno utilizzate per tutti i nuovi progetti.  
  
##### <a name="to-review-default-project-settings"></a>Per controllare le impostazioni di progetto predefinito  
  
1.  Selezionare **impostazioni di progetto predefinite** dal **strumenti** menu.  
  
2.  Selezionare il tipo di progetto in **versione di destinazione della migrazione** elenco a discesa per i quali impostazioni devono essere visualizzati o modificati e quindi fare clic su **generale** scheda.  
  
3.  Nel riquadro a sinistra, fare clic su **conversione**.  
  
4.  Nel riquadro di destra, esaminare e modificare le impostazioni in base alle esigenze. Per ulteriori informazioni su queste impostazioni, vedere [impostazioni progetto &#40; Conversione &#41; &#40; MySQLToSQL &#41; ](../../ssma/mysql/project-settings-conversion-mysqltosql.md) .  
  
5.  Ripetere i passaggi da 1 a 3 per le pagine di migrazione, la sincronizzazione, SQL Azure, interfaccia utente grafica e Mapping dei tipi.  
  
-   Per informazioni sulle impostazioni di migrazione, vedere [impostazioni progetto &#40; La migrazione &#41; &#40; MySQLToSQL &#41; ](../../ssma/mysql/project-settings-migration-mysqltosql.md).  
  
-   Per informazioni sulle impostazioni per la sincronizzazione con SQL Server, vedere [impostazioni progetto &#40; Sincronizzazione &#41; &#40; MySQLToSQL &#41; ](../../ssma/mysql/project-settings-synchronization-mysqltosql.md).  
  
-   Per informazioni sulle impostazioni di interfaccia utente grafica, vedere [progetto. le impostazioni (GUI) (SSMA comune)](http://msdn.microsoft.com/en-us/cf06baf1-8714-48a3-95dc-781f6ca53693).  
  
-   Per informazioni sulle impostazioni di mapping dei tipi di dati, vedere [impostazioni progetto &#40; Mapping dei tipi di &#41; &#40; MySQLToSQL &#41; ](../../ssma/mysql/project-settings-type-mapping-mysqltosql.md).  
  
-   Per informazioni sulle impostazioni di SQL Azure, vedere [impostazioni progetto &#40; Database SQL di Azure &#41; &#40; MySQLToSQL &#41; ](../../ssma/mysql/project-settings-azure-sql-db-mysqltosql.md).  
  
> [!NOTE]  
> Le impostazioni di SQL Azure verranno visualizzate solo quando si seleziona **migrazione a SQL Azure** durante la creazione di un progetto.  
  
## <a name="creating-new-projects"></a>Creazione di nuovi progetti  
Per eseguire la migrazione di dati dai database MySQL a SQL Server o SQL Azure, è necessario creare un progetto.  
  
##### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto  
  
1.  Selezionare **nuovo progetto** dal **File** menu. Verrà visualizzata la finestra di dialogo **Nuovo progetto** . Scegliere **Nuovo progetto** dal menu **File**. Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
2.  Nel **nome** , immettere un nome per il progetto.  
  
3.  Nel **percorso** immettere o selezionare una cartella per il progetto.  
  
4.  Nel **migrazione a** elenco a discesa, selezionare la versione di destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] usato per la migrazione. Le opzioni disponibili sono:  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014  
  
    -   Database SQL di Azure  
  
E quindi fare clic su **OK**  
  
SSMA consente di creare il file di progetto.  
  
## <a name="customizing-project-settings"></a>Personalizzazione delle impostazioni di progetto  
Inoltre, per definire il valore predefinito delle impostazioni di progetto che si applicano a tutti i nuovi progetti SSMA è inoltre possono personalizzare le impostazioni per ogni progetto. Per ulteriori informazioni, vedere [impostazione delle opzioni progetto &#40; MySQLToSQL &#41; ](../../ssma/mysql/setting-project-options-mysqltosql.md).  
  
Quando si personalizza il mapping di tipi di dati tra i database di origine e di destinazione, è possibile definire i mapping per il progetto, un database o un livello di oggetto. Per ulteriori informazioni, vedere [Mapping MySQL e tipi di dati di SQL Server &#40; MySQLToSQL &#41; ](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md).  
  
## <a name="saving-projects"></a>Il salvataggio dei progetti  
La funzionalità di salvataggio di progetti consente all'utente di salvare essenzialmente le impostazioni di progetto e, facoltativamente, i metadati del database per il file di progetto SSMA.  
  
##### <a name="to-save-a-project"></a>Per salvare un progetto  
  
-   Nel **File** dal menu **salvare** progetto.  
  
Se i database all'interno del progetto sono state modificate o non sono stati convertiti, SSMA verrà richiesto di caricare e salvare i metadati. Caricamento e salvataggio dei metadati consente di lavorare offline. È anche possibile inviare un file di progetto completo ad altri utenti, come il personale di supporto tecnico. Se viene chiesto di salvare i metadati, eseguire le operazioni seguenti:  
  
1.  Per ogni database che viene visualizzato lo stato **metadati mancanti**, selezionare la casella di controllo accanto al nome del database. Salvataggio di metadati potrebbe richiedere alcuni minuti. Se non si desidera salvare i metadati a questo punto, non selezionare le caselle di controllo.  
  
2.  Fare clic su **Salva**.  
  
SSMA analizzerà gli schemi di MySQL e salvare i metadati del file di progetto.  
  
## <a name="opening-projects"></a>Apertura di progetti  
Quando si apre un progetto, viene disconnesso da MySQL e SQL Server o SQL Azure. Ciò consente di lavorare offline. Per aggiornare i metadati, caricare gli oggetti di database in SQL Server o SQL Azure. Per eseguire la migrazione dei dati, è necessario riconnettersi a SQL Server o SQL Azure.  
  
##### <a name="to-open-a-project"></a>Per aprire un progetto  
  
1.  Utilizzare una delle procedure riportate di seguito:  
  
    1.  Nel **File** dal menu **progetti recenti**.  
  
    2.  Selezionare il progetto che si desidera aprire.  
  
    3.  Nel **File** dal menu **Apri progetto**, individuare il file di progetto .m2ssproj, selezionare il file e quindi fare clic su **aprire**.  
  
2.  Per ristabilire la connessione a MySQL, nel **File** dal menu **Riconnetti a MySQL**.  
  
3.  Per ristabilire la connessione a SQL Server, nel **File** dal menu **Riconnetti a SQL Server**.  
  
4.  Per ristabilire la connessione a SQL Azure, sul **File** dal menu **ristabilire la connessione a SQL Azure.**  
  
## <a name="next-step"></a>Passaggio successivo  
Il passaggio successivo del processo di migrazione è [connessione a MySQL &#40; MySQLToSQL &#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
  
## <a name="see-also"></a>Vedere anche  
[Connessione a MySQL &#40; MySQLToSQL &#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
[Migrazione di database MySQL a SQL Server: database SQL di Azure &#40; MySQLToSql &#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
[Connessione a SQL Server &#40; MySQLToSQL &#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
[Connessione a database SQL di Azure &#40; MySQLToSQL &#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md)  
  

