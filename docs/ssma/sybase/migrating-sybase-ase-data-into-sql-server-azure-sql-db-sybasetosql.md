---
title: Eseguire la migrazione di Sybase ASE dati in SQL Server - database SQL di Azure | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
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
- Migrating data,Client Side Data Migration
- Migrating data,Server Side Data Migration
ms.assetid: 54a39f5e-9250-4387-a3ae-eae47c799811
caps.latest.revision: 15
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ab42e495eb4e76b6e9d7b6a2cca3d031eed12448
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="migrating-sybase-ase-data-into-sql-server---azure-sql-db--sybasetosql"></a>La migrazione dei dati di Sybase ASE in SQL Server - database SQL di Azure (SybaseToSQL)
Dopo aver caricato correttamente gli oggetti di database di Sybase Adaptive Server Enterprise (ASE) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure, è possibile migrare dati da ASE a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure.  
  
> [!IMPORTANT]  
> Se il motore in uso è modulo di migrazione dei dati lato Server, quindi eseguire la migrazione dei dati, è necessario installare SSMA per Sybase ASE estensione Pack e i provider di Sybase ASE nel computer in cui è in esecuzione SSMA. Il servizio SQL Server Agent deve inoltre essere in esecuzione. Per ulteriori informazioni su come installare il pacchetto di estensione, vedere [installazione dei componenti di SSMA in SQL Server (SybaseToSQL)](http://msdn.microsoft.com/en-us/5ad9e12c-2cdb-4dd2-8703-05a23242d19d)  
  
## <a name="setting-migration-options"></a>Impostazione delle opzioni di migrazione  
Prima della migrazione di dati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database SQL di Azure, esaminare le opzioni di migrazione del progetto nella **impostazioni progetto** la finestra di dialogo.  
  
-   Tramite questa finestra di dialogo è possibile impostare opzioni quali le dimensioni di batch di migrazione, il blocco di tabella, il controllo dei vincoli, la gestione dei valori null e la gestione dei valori di identità. Per ulteriori informazioni sulle impostazioni di migrazione del progetto, vedere [le impostazioni del progetto (migrazione) (Sybase)](http://msdn.microsoft.com/en-us/82f8857f-7ab1-4738-ab6e-b1e95ea94924).  
  
    Per ulteriori informazioni sul **esteso le impostazioni di migrazione di dati**, vedere [le impostazioni di migrazione dei dati](http://msdn.microsoft.com/en-us/94d7a083-2dbc-4e3d-94dd-92b7ff9d0c2d)  
  
-   Il **modulo di migrazione** nel **impostazioni progetto** della finestra di dialogo consente all'utente di eseguire il processo di migrazione sono disponibili due tipi di motori di migrazione di dati, dei quali.:  
  
    1.  Modulo di migrazione dei dati sul lato client  
  
    2.  Modulo di migrazione dei dati lato server  
  
**Migrazione dei dati lato client:**  
  
-   Per avviare la migrazione dei dati sul lato client, selezionare l'opzione **modulo di migrazione dei dati sul lato Client** nel **impostazioni progetto** la finestra di dialogo.  
  
-   In **impostazioni progetto**, **modulo di migrazione dei dati sul lato Client** opzione è impostata per impostazione predefinita.  
  
    > [!NOTE]  
    > Il modulo di migrazione dei dati sul lato Client si trova all'interno dell'applicazione di SSMA e, pertanto, non dipende dalla disponibilità del pacchetto di estensione.  
  
**Migrazione dei dati lato server:**  
  
-   Durante la migrazione dei dati lato Server, il motore si trova nel database di destinazione. Viene installata tramite il pacchetto di estensione. Per ulteriori informazioni su come installare il pacchetto di estensione, vedere [installazione dei componenti di SSMA in SQL Server (SybaseToSQL)](http://msdn.microsoft.com/en-us/5ad9e12c-2cdb-4dd2-8703-05a23242d19d)  
  
-   Per avviare la migrazione sul lato server, selezionare il **modulo di migrazione dei dati lato Server** opzione il **impostazioni progetto** finestra di dialogo.  
  
> [!NOTE]  
> Quando i database SQL di Azure viene utilizzato come database di destinazione, solo **migrazione dei dati sul lato Client** è consentito e migrazione dei dati lato server non è supportata.  
  
## <a name="migrating-data-to-sql-server-or-azure-sql-db"></a>La migrazione dei dati in SQL Server o database SQL di Azure  
La migrazione di dati sono un'operazione di caricamento bulk che consente di spostare le righe di dati dalle tabelle di base in tabelle di SQL Server nelle transazioni. Il numero di righe caricate in SQL Server o database SQL di Azure in ogni transazione viene configurato nelle impostazioni del progetto.  
  
Per visualizzare i messaggi di migrazione, verificare che sia visibile il riquadro di Output. In caso contrario, selezionare **Output** dal **vista** menu.  
  
**Per eseguire la migrazione dei dati**  
  
1.  Verificare gli elementi seguenti:  
  
    -   I provider di base vengono installati nel computer in cui è in esecuzione SSMA.  
  
    -   Gli oggetti convertiti si sono sincronizzati con il database di destinazione (SQL Server o database SQL di Azure).  
  
2.  Nel Visualizzatore metadati Sybase, selezionare gli oggetti che contengono i dati che si desidera eseguire la migrazione:  
  
    -   Per eseguire la migrazione dei dati per tutti gli schemi, selezionare la casella di controllo accanto a **schemi**.  
  
    -   Per la migrazione dei dati o omettere le singole tabelle, innanzitutto espandere il nodo dello schema, **tabelle**e quindi selezionare o deselezionare la casella di controllo accanto alla tabella.  
  
3.  Per eseguire la migrazione dei dati, si verificano due casi:  
  
    **Migrazione dei dati lato client:**  
  
    Per l'esecuzione di **migrazione dei dati sul lato Client**, selezionare il **modulo di migrazione dei dati sul lato Client** opzione il **impostazioni progetto** la finestra di dialogo.  
  
    **Migrazione dei dati lato server:**  
  
    -   Prima di eseguire la migrazione di dati lato Server, verificare che:  
  
        1.  SSMA per Sybase estensione Pack è installato nell'istanza di SQL Server.  
  
        2.  Il servizio SQL Server Agent è in esecuzione nell'istanza di SQL Server  
  
    -   Per l'esecuzione di **migrazione dei dati lato Server**, selezionare il **modulo di migrazione dei dati lato Server** opzione il **impostazioni progetto** la finestra di dialogo.  
  
4.  Fare doppio clic su **schemi** in Visualizzatore metadati Sybase e quindi fare clic su **eseguire la migrazione di dati**. È inoltre possibile migrare i dati per singoli oggetti o le categorie di oggetti: l'oggetto o la relativa cartella padre e scegliere il **eseguire la migrazione di dati** opzione.  
  
    > [!NOTE]  
    > SSMA per Sybase estensione Pack non è installato nell'istanza di SQL Server e se **modulo di migrazione dei dati lato Server** è selezionata, durante la migrazione dei dati al database di destinazione, viene verificato il seguente errore: ' componenti SSMA migrazione dei dati non sono stati trovati in SQL Server, non sarà possibile eseguire la migrazione dei dati lato server. Verificare se il pacchetto di estensione sia installato correttamente '. Fare clic su **Annulla** per terminare la migrazione dei dati.  
  
5.  Nel **Connetti per Sybase ASE** nella finestra di dialogo immettere le credenziali di connessione e quindi fare clic su **Connetti**. Per ulteriori informazioni sulla connessione per Sybase ASE, vedere [Connect per Sybase &#40;SybaseToSQL&#41;](../../ssma/sybase/connect-to-sybase-sybasetosql.md)  
  
    Se il database di destinazione è SQL Server, quindi immettere le credenziali di connessione nel **Connetti al Server SQL** la finestra di dialogo e fare clic su **Connetti**. Per ulteriori informazioni sulla connessione a SQL Server, vedere [la connessione a SQL Server(SybaseToSQL)](http://msdn.microsoft.com/en-us/dd368a1a-45b0-40e9-b4d3-5cdb48c26606)  
  
    Se il database di destinazione è il database di SQL Azure, quindi immettere le credenziali di connessione nel **Connetti al database SQL di Azure** la finestra di dialogo e fare clic su **Connetti**. Per ulteriori informazioni sulla connessione al database SQL di Azure, vedere [la connessione al database SQL di Azure &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md)  
  
    I messaggi verranno visualizzati nel **Output** riquadro. Al termine, la migrazione di **Report di migrazione di dati** viene visualizzato. Se tutti i dati non sono stati migrati, fare clic sulla riga che contiene gli errori e quindi fare clic su **dettagli**. Quando si è finito di lavorare con il report, fare clic su **Chiudi**. Per ulteriori informazioni sul Report di migrazione dei dati, vedere [Report di migrazione dei dati (SSMA comune)](http://msdn.microsoft.com/en-us/bbfb9d88-5a98-4980-8d19-c5d78bd0d241)  
  
> [!NOTE]  
> Quando SQL Express edition viene utilizzato come database di destinazione, è consentita solo migrazione dei dati sul lato client e migrazione dei dati lato server non è supportata.  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database Sybase ASE a SQL Server: SQL Azure database &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
