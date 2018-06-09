---
title: La migrazione dei dati di MySQL in SQL Server - database SQL di Azure (MySQLToSQL) | Documenti Microsoft
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
- Data Migration, server side data migration
- Data Migration,client side data migration
ms.assetid: a6a7f4d6-68aa-4a38-93bf-53eba0d7dc82
caps.latest.revision: 24
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: effe01a9c4201d4f579d28c003ac828e634cf6ea
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34776779"
---
# <a name="migrating-mysql-data-into-sql-server---azure-sql-db-mysqltosql"></a>La migrazione dei dati di MySQL in SQL Server - database SQL di Azure (MySQLToSQL)
Dopo che è stato possibile sincronizzare gli oggetti convertiti con [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, è possibile migrare dati da MySQL a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure.  
  
> [!IMPORTANT]  
> Se il motore in uso è modulo di migrazione dei dati lato Server, quindi, prima della migrazione di dati, è necessario installare SSMA per MySQL estensione Pack e i provider di MySQL nel computer in cui è in esecuzione SSMA. Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] servizio agente deve inoltre essere in esecuzione. Per ulteriori informazioni su come installare il pacchetto di estensione, vedere [installazione dei componenti di SSMA in SQL Server (MySQL to SQL)](http://msdn.microsoft.com/en-us/6772d0c5-258f-4d7b-afb0-b5f810e71af1)  
  
## <a name="setting-migration-options"></a>Impostazione delle opzioni di migrazione  
Prima della migrazione di dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, esaminare le opzioni di migrazione del progetto nella **impostazioni progetto** la finestra di dialogo.  
  
-   Tramite questa finestra di dialogo è possibile impostare opzioni quali le dimensioni di batch di migrazione, il blocco di tabella, il controllo dei vincoli, la gestione dei valori null e gestione di valori identity. Per ulteriori informazioni sulle impostazioni di migrazione del progetto, vedere [le impostazioni del progetto (migrazione)](http://msdn.microsoft.com/en-us/2a3cba9e-cd54-4a8b-b858-8fc4cf2580d9).  
  
    Per ulteriori informazioni sul **esteso le impostazioni di migrazione di dati**, vedere [le impostazioni di migrazione dei dati](http://msdn.microsoft.com/en-us/9c396df4-5676-4f32-9c57-70d4f15f9b7a)  
  
-   Il **modulo di migrazione** nel **impostazioni progetto** della finestra di dialogo consente all'utente di eseguire il processo di migrazione sono disponibili due tipi di moduli di migrazione di dati:  
  
    1.  Modulo di migrazione dei dati sul lato client  
  
    2.  Modulo di migrazione dei dati lato server  
  
**Migrazione dei dati lato client:**  
  
-   Per avviare la migrazione dei dati sul lato client, selezionare il **modulo di migrazione dei dati sul lato Client** opzione il **impostazioni progetto** la finestra di dialogo.  
  
-   In **impostazioni progetto**, **modulo di migrazione dei dati sul lato Client** opzione è impostata.  
  
    > [!NOTE]  
    > Il **modulo di migrazione dei dati sul lato Client** si trova all'interno dell'applicazione di SSMA e, pertanto, non dipende dalla disponibilità del pacchetto di estensione.  
  
**Migrazione dei dati lato server:**  
  
-   Durante la migrazione dei dati lato Server, il motore si trova nel database di destinazione. Viene installata tramite il pacchetto di estensione. Per ulteriori informazioni su come installare il pacchetto di estensione, vedere [installazione dei componenti di SSMA in SQL Server (MySQL to SQL)](http://msdn.microsoft.com/en-us/6772d0c5-258f-4d7b-afb0-b5f810e71af1)  
  
-   Per avviare la migrazione sul lato server, selezionare il **modulo di migrazione dei dati lato Server** opzione il **impostazioni progetto** la finestra di dialogo.  
  
> [!IMPORTANT]  
> **Migrazione dei dati lato client** opzione è disponibile per SQL Azure.  
  
## <a name="migrating-data-to-sql-server-or-sql-azure"></a>La migrazione dei dati in SQL Server o SQL Azure  
La migrazione di dati sono un'operazione di caricamento bulk che consente di spostare le righe di dati dalle tabelle di MySQL in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o tabelle di SQL Azure nelle transazioni. Numero di righe caricate in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] in ogni transazione viene configurata nelle impostazioni del progetto.  
  
Per visualizzare i messaggi di migrazione, verificare che sia visibile il riquadro di Output. In caso contrario, dal **vista** dal menu **Output**.  
  
**Per eseguire la migrazione dei dati**  
  
1.  Verificare gli elementi seguenti:  
  
    -   Il provider di MySQL sono installati nel computer in cui è in esecuzione SSMA.  
  
    -   Si sono sincronizzati gli oggetti convertiti con il database di destinazione (SQL Server o SQL Azure).  
  
2.  Nel Visualizzatore metadati MySQL, selezionare gli oggetti che contengono i dati che si desidera eseguire la migrazione:  
  
    -   Per eseguire la migrazione dei dati per tutti gli schemi, selezionare la casella di controllo accanto a **schemi**.  
  
    -   Per la migrazione dei dati o omettere le singole tabelle, innanzitutto espandere il nodo dello schema, **tabelle**e quindi selezionare o deselezionare la casella di controllo accanto alla tabella.  
  
3.  Per eseguire la migrazione dei dati, si verificano due casi:  
  
    **Migrazione dei dati lato client:**  
  
    -   Per l'esecuzione di **migrazione dei dati sul lato Client**, selezionare il **modulo di migrazione dei dati sul lato Client** opzione il **impostazioni progetto** la finestra di dialogo.  
  
    **Migrazione dei dati lato server:**  
  
    -   Prima di eseguire la migrazione dei dati sul lato server, verificare che:  
  
        1.  SSMA per il pacchetto di estensione MySQL è installato nell'istanza di SQL Server.  
  
        2.  Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] servizio dell'agente è in esecuzione nell'istanza di SQL Server  
  
    -   Per l'esecuzione di **migrazione dei dati lato Server**, selezionare il **modulo di migrazione dei dati lato Server** opzione il **impostazioni progetto** la finestra di dialogo.  
  
4.  Fare doppio clic su **schemi** in Gestione risorse MySQL metadati e quindi fare clic su **eseguire la migrazione di dati**. È inoltre possibile migrare i dati per singoli oggetti o le categorie di oggetti: mouse l'oggetto o la cartella padre. Selezionare il **eseguire la migrazione di dati** opzione.  
  
    > [!NOTE]  
    > SSMA per il pacchetto di estensione MySQL non è installato nell'istanza di SQL Server e se **modulo di migrazione dei dati lato Server** è selezionata, durante la migrazione dei dati al database di destinazione, viene verificato il seguente errore: ' componenti SSMA migrazione dei dati non sono stati trovati in SQL Server, non sarà possibile eseguire la migrazione dei dati lato server. Verificare se il pacchetto di estensione sia installato correttamente '. Fare clic su **Annulla** per terminare la migrazione dei dati.  
  
5.  Nel **connessione a MySQL** nella finestra di dialogo immettere le credenziali di connessione e quindi fare clic su **Connetti**. Per ulteriori informazioni sulla connessione a MySQL, vedere [connessione a MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/connect-to-mysql-mysqltosql.md)  
  
    Se il database di destinazione è SQL Server, quindi immettere le credenziali di connessione nel **Connetti al Server SQL** la finestra di dialogo e fare clic su **Connetti**. Per ulteriori informazioni sulla connessione a SQL Server, vedere [Connetti a SQL Server](http://msdn.microsoft.com/en-us/bb8c4bde-cfc2-4636-92ae-5dd24abe9536)  
  
    Se il database di destinazione è SQL Azure, quindi immettere le credenziali di connessione nel **Connetti a SQL Azure** la finestra di dialogo e fare clic su **Connetti**. Per ulteriori informazioni sulla connessione a SQL Azure, vedere [Connetti al database SQL di Azure &#40;MySQLToSQL&#41;](../../ssma/mysql/connect-to-azure-sql-db-mysqltosql.md)  
  
    I messaggi verranno visualizzati nel **Output** riquadro. Al termine, la migrazione di **Report di migrazione di dati** viene visualizzato. Se tutti i dati non sono stati migrati, fare clic sulla riga che contiene gli errori e quindi fare clic su **dettagli**. Quando si è finito di lavorare con il report, fare clic su **Chiudi**. Per ulteriori informazioni sul Report di migrazione dei dati, vedere [Report di migrazione dei dati (SSMA comune)](http://msdn.microsoft.com/en-us/bbfb9d88-5a98-4980-8d19-c5d78bd0d241)  
  
> [!NOTE]  
> Quando SQL Express edition viene utilizzato come database di destinazione, è consentita solo migrazione dei dati sul lato client e migrazione dei dati lato server non è supportata.  
  
## <a name="see-also"></a>Vedere anche  
[Database MySQL la migrazione a SQL Server - SQL di Azure DB &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
