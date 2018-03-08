---
title: Utilizzo di progetti SSMA (SybaseToSQL) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-sybase
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 11091d95-c488-48c3-891a-743cac94ac93
caps.latest.revision: "10"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4625284beb50612c276046c139f8340b1872cfc8
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="working-with-ssma-projects-sybasetosql"></a>Lavorare con progetti SSMA (SybaseToSQL)
Per eseguire la migrazione dei database Sybase Adaptive Server Enterprise (ASE) [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, creare innanzitutto un progetto SSMA. Il progetto è un file che contiene metadati sui database che si desidera eseguire la migrazione a ASE [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, i metadati sull'istanza di destinazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure che riceverà la migrazione di oggetti e i dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o informazioni di connessione di SQL Azure e le impostazioni del progetto.  
  
Quando si apre un progetto, si viene disconnessi da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. Ciò consente di lavorare offline. È possibile riconnettersi alla [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. Per ulteriori informazioni, vedere [connessione a SQL Server &#40; SybaseToSQL &#41; ](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md)  /  [La connessione al database SQL di Azure &#40; SybaseToSQL &#41; ](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md).  
  
## <a name="reviewing-default-project-settings"></a>Verificare le impostazioni di progetto predefinito  
SSMA contiene varie opzioni per la conversione e il caricamento di oggetti di database, la migrazione dei dati e la sincronizzazione di SSMA con ASE e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. Le impostazioni predefinite per queste opzioni sono appropriate per molti utenti. Tuttavia, prima di creare un nuovo progetto SSMA, si deve rivedere le opzioni e, se si desidera, modificare le impostazioni predefinite che verranno utilizzate per tutti i nuovi progetti.  
  
**Per controllare le impostazioni di progetto predefinito**  
  
1.  Nel **strumenti** dal menu **impostazioni di progetto predefinite**.  
  
2.  Selezionare il tipo di progetto in **versione di destinazione della migrazione** elenco a discesa sono necessarie da visualizzare o modificare le impostazioni e quindi fare clic su **generale** scheda.  
  
3.  Nel riquadro a sinistra, fare clic su **conversione**.  
  
4.  Nel riquadro di destra, rivedere le opzioni, modifica delle opzioni in base alle esigenze. Per ulteriori informazioni su queste opzioni, vedere [impostazioni progetto &#40; Conversione &#41; &#40; SybaseToSQL &#41; ](../../ssma/sybase/project-settings-conversion-sybasetosql.md).  
  
5.  Ripetere i passaggi da 1 a 3 per le pagine di migrazione, SQL Azure, il caricamento di oggetti, interfaccia utente grafica e Mapping dei tipi.  
  
    -   Per informazioni sulle opzioni di migrazione, vedere [impostazioni progetto &#40; La migrazione &#41; &#40; SybaseToSQL &#41; ](../../ssma/sybase/project-settings-migration-sybasetosql.md).  
  
    -   Per informazioni sulle opzioni per il caricamento di oggetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], vedere [impostazioni progetto &#40; Sincronizzazione &#41; &#40; SybaseToSQL &#41; ](../../ssma/sybase/project-settings-synchronization-sybasetosql.md).  
  
    -   Per ulteriori informazioni sulle opzioni di interfaccia utente grafica, vedere [impostazioni progetto &#40; GUI &#41; &#40; SybaseToSQL &#41; ](../../ssma/sybase/project-settings-gui-sybasetosql.md).  
  
    -   Per ulteriori informazioni sulle impostazioni di mapping dei tipi di dati, fare clic su [impostazioni progetto &#40; Mapping dei tipi di &#41; &#40; SybaseToSQL &#41; ](../../ssma/sybase/project-settings-type-mapping-sybasetosql.md).  
  
    -   Per ulteriori informazioni sulle opzioni di SQL Azure, vedere [impostazioni progetto &#40; Database SQL di Azure &#41; &#40; SybaseToSQL &#41; ](../../ssma/sybase/project-settings-azure-sql-db-sybasetosql.md).  
  
    > [!NOTE]  
    > Le impostazioni di SQL Azure verranno visualizzate solo quando si seleziona **migrazione a SQL Azure** durante la creazione di un progetto.  
  
## <a name="creating-new-projects"></a>Creazione di nuovi progetti  
La migrazione dei dati dai database ASE per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, è necessario creare innanzitutto un progetto.  
  
**Per creare un progetto**  
  
1.  Scegliere **Nuovo progetto** dal menu **File**.  
  
    Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
2.  Nel **nome** , immettere un nome per il progetto.  
  
3.  Nel **percorso** immettere o selezionare una cartella per il progetto.  
  
4.  Nel **migrazione a** elenco a discesa, selezionare la versione di destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] usato per la migrazione. Le opzioni disponibili sono:  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016  
  
    -   Database SQL di Azure  
  
E quindi fare clic su **OK**.  
  
## <a name="customizing-project-settings"></a>Personalizzazione delle impostazioni di progetto  
Inoltre, per definire impostazioni predefinite del progetto che si applicano a tutti i nuovi progetti SSMA, è possibile personalizzare le impostazioni per ogni progetto. Per ulteriori informazioni, vedere [impostazione delle opzioni progetto &#40; SybaseToSQL &#41; ](../../ssma/sybase/setting-project-options-sybasetosql.md).  
  
Quando si personalizza il mapping di tipi di dati tra database di origine e di destinazione, è possibile definire i mapping per il progetto, un database o un livello di oggetto. Per ulteriori informazioni sui mapping dei tipi, vedere [Mapping Sybase ASE e tipi di dati di SQL Server &#40; SybaseToSQL &#41; ](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).  
  
## <a name="saving-projects"></a>Il salvataggio dei progetti  
Quando si salva un progetto, SSMA mantiene le impostazioni di progetto e, facoltativamente, i metadati del database, al file di progetto.  
  
**Per salvare un progetto**  
  
-   Nel **File** dal menu **Salva progetto**.  
  
    Se i database all'interno del progetto sono state modificate o non sono stati convertiti, SSMA verrà chiesto di salvare i metadati nel progetto. Salvare i metadati consentono di lavorare offline e l'invio di un file di progetto completo ad altre persone, tra cui il personale di supporto tecnico. Se viene chiesto di salvare i metadati, eseguire le operazioni seguenti:  
  
    1.  Per ogni database che viene visualizzato lo stato **metadati mancanti**, selezionare la casella di controllo accanto al nome del database.  
  
        Salvataggio di metadati potrebbe richiedere alcuni minuti. Se non si desidera salvare i metadati a questo punto, non selezionare le caselle di controllo.  
  
    2.  Fare clic su di **salvare** pulsante.  
  
        SSMA analizzerà gli schemi di Sybase ASE e salvare i metadati del file di progetto.  
  
## <a name="opening-projects"></a>Apertura di progetti  
Quando si apre un progetto, la disconnessione da ASE e da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. Ciò consente di lavorare offline. Per aggiornare i metadati, caricare gli oggetti di database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. Per eseguire la migrazione dei dati, è necessario riconnettersi all'ASE e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure.  
  
**Per aprire un progetto**  
  
1.  Utilizzare una delle procedure riportate di seguito:  
  
    -   Nel **File** dal menu **progetti recenti**e quindi selezionare il progetto che si desidera aprire.  
  
    -   Nel **File** dal menu **Apri progetto**, individuare il file di progetto .s2ssproj, selezionare il file e quindi fare clic su **aprire**.  
  
2.  Per riconnettersi ASE, sul **File** dal menu **riconnessione per Sybase**.  
  
3.  Per riconnettersi [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, sul **File** dal menu **Riconnetti a SQL Server** / **Riconnetti a SQL Azure**.  
  
## <a name="next-step"></a>Passaggio successivo  
Il passaggio successivo del processo di migrazione consiste nel [Connetti per Sybase ASE](http://msdn.microsoft.com/en-us/a45a2330-9175-4c9e-af38-ef920e350614).  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database di Sybase ASE a SQL Server: database SQL di Azure &#40; SybaseToSQL &#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
[Connessione a Sybase ASE &#40; SybaseToSQL &#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md)  
[Connessione a SQL Server &#40; SybaseToSQL &#41;](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md)  
[Connessione a database SQL di Azure &#40; SybaseToSQL &#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md)  
  
