---
title: La migrazione dei dati di Oracle in SQL Server (OracleToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Oracle Data Migration, Client-Side Migration
- Oracle Data Migration,Server-Side Migration
ms.assetid: e23c5268-41ed-4e55-9fe7-a11376202a13
caps.latest.revision: 13
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 10c7bfea3316146924544a7c76d3bc727006b694
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="migrating-oracle-data-into-sql-server-oracletosql"></a>La migrazione dei dati di Oracle in SQL Server (OracleToSQL)
Dopo che è stato possibile sincronizzare gli oggetti convertiti con [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], è possibile migrare dati da Oracle a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
> [!IMPORTANT]  
> Se il motore in uso è modulo di migrazione dei dati lato Server, quindi, prima di migrare i dati, è necessario installare SSMA per Oracle estensione Pack e i provider Oracle nel computer in cui è in esecuzione SSMA. Il servizio SQL Server Agent deve inoltre essere in esecuzione. Per ulteriori informazioni su come installare il pacchetto di estensione, vedere [installazione dei componenti Server (OracleToSQL)](http://msdn.microsoft.com/en-us/33070e5f-4e39-4b70-ae81-b8af6e4983c5)  
  
## <a name="setting-migration-options"></a>Impostazione delle opzioni di migrazione  
Prima della migrazione di dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], esaminare le opzioni di migrazione del progetto nella **impostazioni progetto** la finestra di dialogo.  
  
-   Tramite questa finestra di dialogo è possibile impostare opzioni quali le dimensioni di batch di migrazione, il blocco di tabella, il controllo dei vincoli, la gestione dei valori null e la gestione dei valori di identità. Per ulteriori informazioni sulle impostazioni di migrazione del progetto, vedere [le impostazioni del progetto (migrazione) (OracleToSQL)](http://msdn.microsoft.com/en-us/fcd6b988-633b-4b2b-9f36-6368b5e86b60).  
  
-   Il **modulo di migrazione** nel **impostazioni progetto** della finestra di dialogo consente all'utente di eseguire il processo di migrazione sono disponibili due tipi di moduli di migrazione di dati:  
  
    1.  Modulo di migrazione dei dati sul lato client  
  
    2.  Modulo di migrazione dei dati lato server  
  
**Migrazione dei dati sul lato client:**  
  
-   Per avviare la migrazione dei dati sul lato client, selezionare il **modulo di migrazione dei dati sul lato Client** opzione il **impostazioni progetto** la finestra di dialogo.  
  
-   In **impostazioni progetto**, **modulo di migrazione dei dati sul lato Client** opzione è impostata.  
  
    > [!NOTE]  
    > Il **modulo di migrazione dei dati sul lato Client** si trova all'interno dell'applicazione di SSMA e, pertanto, non dipende dalla disponibilità del pacchetto di estensione.  
  
**Migrazione dei dati lato server:**  
  
-   Durante la migrazione dei dati lato Server, il motore si trova nel database di destinazione. Viene installata tramite il pacchetto di estensione. Per ulteriori informazioni su come installare il pacchetto di estensione, vedere [installazione dei componenti Server in SQL Server](http://msdn.microsoft.com/en-us/33070e5f-4e39-4b70-ae81-b8af6e4983c5)  
  
-   Per avviare la migrazione sul lato server, selezionare il **modulo di migrazione dei dati lato Server** opzione il **impostazioni progetto** la finestra di dialogo.  
  
## <a name="migrating-data-to-sql-server"></a>La migrazione dei dati a SQL Server  
La migrazione di dati sono un'operazione di caricamento bulk che consente di spostare le righe di dati dalle tabelle di Oracle in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tabelle nelle transazioni. Numero di righe caricate in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] in ogni transazione viene configurata nelle impostazioni del progetto.  
  
Per visualizzare i messaggi di migrazione, verificare che sia visibile il riquadro di Output. In caso contrario, dal **vista** dal menu **Output**.  
  
**La migrazione dei dati**  
  
1.  Verificare gli elementi seguenti:  
  
    -   Il provider Oracle vengono installati nel computer in cui è in esecuzione SSMA.  
  
    -   Si sono sincronizzati gli oggetti convertiti con il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database.  
  
2.  Nel Visualizzatore metadati Oracle, selezionare gli oggetti che contengono i dati che si desidera eseguire la migrazione:  
  
    -   Per eseguire la migrazione dei dati per tutti gli schemi, selezionare la casella di controllo accanto a **schemi**.  
  
    -   Per la migrazione dei dati o omettere le singole tabelle, innanzitutto espandere il nodo dello schema, **tabelle**e quindi selezionare o deselezionare la casella di controllo accanto alla tabella.  
  
3.  Per eseguire la migrazione dei dati, si verificano due casi:  
  
    **Migrazione dei dati sul lato client:**  
  
    -   Per l'esecuzione di **migrazione dei dati sul lato Client**, selezionare il **modulo di migrazione dei dati sul lato Client** opzione il **impostazioni progetto** la finestra di dialogo.  
  
    **Migrazione dei dati lato server:**  
  
    -   Prima di eseguire la migrazione dei dati sul lato server, verificare che:  
  
        1.  SSMA per Oracle estensione Pack è installato nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
        2.  Il servizio SQL Server Agent è in esecuzione nell'istanza di SQL Server.  
  
    -   Per l'esecuzione di **migrazione dei dati lato Server**, selezionare il **modulo di migrazione dei dati lato Server** opzione il **impostazioni progetto** la finestra di dialogo.  
  
4.  Fare doppio clic su **schemi** in Visualizzatore metadati Oracle e quindi fare clic su **eseguire la migrazione di dati**. È inoltre possibile migrare i dati per singoli oggetti o le categorie di oggetti: mouse l'oggetto o la cartella padre. Selezionare il **eseguire la migrazione di dati** opzione.  
  
    > [!NOTE]  
    > Se SSMA per Oracle estensione Pack non è installato nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]e se **modulo di migrazione dei dati lato Server** è selezionata, durante la migrazione dei dati al database di destinazione, viene verificato il seguente errore: ' componenti SSMA migrazione dei dati non sono stati trovati in SQL Server, non sarà possibile eseguire la migrazione dei dati lato server. Verificare se il pacchetto di estensione sia installato correttamente '. Fare clic su **Annulla** per terminare la migrazione dei dati.  
  
5.  Nel **Connect to Oracle** nella finestra di dialogo immettere le credenziali di connessione e quindi fare clic su **Connetti**. Per ulteriori informazioni sulla connessione a Oracle, vedere [OracleToSQL connettersi a Oracle &#40; &#41;](../../ssma/oracle/connect-to-oracle-oracletosql.md)  
  
    Per la connessione al database di destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], immettere le credenziali di connessione nel **Connetti al Server SQL** la finestra di dialogo e fare clic su **Connetti**. Per ulteriori informazioni sulla connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], vedere [Connetti a SQL Server](http://msdn.microsoft.com/en-us/bb8c4bde-cfc2-4636-92ae-5dd24abe9536)  
  
    I messaggi verranno visualizzati nel **Output** riquadro. Al termine, la migrazione di **Report di migrazione di dati** viene visualizzato. Se tutti i dati non sono stati migrati, fare clic sulla riga che contiene gli errori e quindi fare clic su **dettagli**. Quando si è finito di lavorare con il report, fare clic su **Chiudi**. Per ulteriori informazioni sul Report di migrazione di dati, vedere [Report di migrazione di dati (SSMA comune)](http://msdn.microsoft.com/en-us/bbfb9d88-5a98-4980-8d19-c5d78bd0d241)  
  
> [!NOTE]  
> Quando SQL Express edition viene utilizzato come database di destinazione, è consentita solo migrazione dei dati sul lato client e migrazione dei dati lato server non è supportata.  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database Oracle a SQL Server &#40; OracleToSQL &#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  

