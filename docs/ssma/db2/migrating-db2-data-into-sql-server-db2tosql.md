---
title: La migrazione dei dati DB2 in SQL Server (DB2ToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 86cbd39f-6dac-409a-9ce1-7dd54403f84b
caps.latest.revision: "5"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 45039e39cc04c75f0d2f92de8cf3ad95b55d8e0a
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="migrating-db2-data-into-sql-server-db2tosql"></a>La migrazione dei dati di DB2 in SQL Server (DB2ToSQL)
Dopo che è stato possibile sincronizzare gli oggetti convertiti con [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], è possibile migrare dati da DB2 a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
> [!IMPORTANT]  
> Se il motore in uso è modulo di migrazione dei dati lato Server, quindi, prima di migrare i dati, è necessario installare SSMA per DB2 estensione Pack e i provider DB2 nel computer in cui è in esecuzione SSMA. Il servizio SQL Server Agent deve inoltre essere in esecuzione. Per ulteriori informazioni su come installare il pacchetto di estensione, vedere [installazione dei componenti di SSMA in SQL Server](http://msdn.microsoft.com/en-us/cf2b724b-4ca7-470a-8dd7-fa95b1e060a4)  
  
## <a name="setting-migration-options"></a>Impostazione delle opzioni di migrazione  
Prima della migrazione di dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], esaminare le opzioni di migrazione del progetto nella **impostazioni progetto** la finestra di dialogo.  
  
-   Tramite questa finestra di dialogo è possibile impostare opzioni quali le dimensioni di batch di migrazione, il blocco di tabella, il controllo dei vincoli, la gestione dei valori null e la gestione dei valori di identità. Per ulteriori informazioni sulle impostazioni di migrazione del progetto, vedere [le impostazioni del progetto (migrazione)](http://msdn.microsoft.com/en-us/48aaa8e6-a9cb-487d-9ba5-fc3f1c4786ae).  
  
-   Il **modulo di migrazione** nel **impostazioni progetto** della finestra di dialogo consente all'utente di eseguire il processo di migrazione sono disponibili due tipi di moduli di migrazione di dati:  
  
    1.  Modulo di migrazione dei dati sul lato client  
  
    2.  Modulo di migrazione dei dati lato server  
  
**Migrazione dei dati sul lato client:**  
  
-   Per avviare la migrazione dei dati sul lato client, selezionare il **modulo di migrazione dei dati sul lato Client** opzione il **impostazioni progetto** la finestra di dialogo.  
  
-   In **impostazioni progetto**, **modulo di migrazione dei dati sul lato Client** opzione è impostata.  
  
    > [!NOTE]  
    > Il **modulo di migrazione dei dati sul lato Client** si trova all'interno dell'applicazione di SSMA e, pertanto, non dipende dalla disponibilità del pacchetto di estensione.  
  
**Migrazione dei dati lato server:**  
  
-   Durante la migrazione dei dati lato Server, il motore si trova nel database di destinazione. Viene installata tramite il pacchetto di estensione. Per ulteriori informazioni su come installare il pacchetto di estensione, vedere [installazione dei componenti di SSMA in SQL Server](http://msdn.microsoft.com/en-us/cf2b724b-4ca7-470a-8dd7-fa95b1e060a4)  
  
-   Per avviare la migrazione sul lato server, selezionare il **modulo di migrazione dei dati lato Server** opzione il **impostazioni progetto** la finestra di dialogo.  
  
## <a name="migrating-data-to-sql-server"></a>La migrazione dei dati a SQL Server  
La migrazione di dati sono un'operazione di caricamento bulk che consente di spostare le righe di dati da tabelle DB2 in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tabelle nelle transazioni. Numero di righe caricate in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] in ogni transazione viene configurata nelle impostazioni del progetto.  
  
Per visualizzare i messaggi di migrazione, verificare che sia visibile il riquadro di Output. In caso contrario, dal **vista** dal menu **Output**.  
  
**La migrazione dei dati**  
  
1.  Verificare gli elementi seguenti:  
  
    -   I provider DB2 vengono installati nel computer in cui è in esecuzione SSMA.  
  
    -   Si sono sincronizzati gli oggetti convertiti con il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database.  
  
2.  Nel Visualizzatore metadati DB2, selezionare gli oggetti che contengono i dati che si desidera eseguire la migrazione:  
  
    -   Per eseguire la migrazione dei dati per tutti gli schemi, selezionare la casella di controllo accanto a **schemi**.  
  
    -   Per la migrazione dei dati o omettere le singole tabelle, innanzitutto espandere il nodo dello schema, **tabelle**e quindi selezionare o deselezionare la casella di controllo accanto alla tabella.  
  
3.  Per eseguire la migrazione dei dati, si verificano due casi:  
  
    **Migrazione dei dati sul lato client:**  
  
    -   Per l'esecuzione di **migrazione dei dati sul lato Client**, selezionare il **modulo di migrazione dei dati sul lato Client** opzione il **impostazioni progetto** la finestra di dialogo.  
  
    **Migrazione dei dati lato server:**  
  
    -   Prima di eseguire la migrazione dei dati sul lato server, verificare che:  
  
        1.  SSMA per DB2 estensione Pack è installato nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
        2.  Il servizio SQL Server Agent è in esecuzione nell'istanza di SQL Server.  
  
    -   Per l'esecuzione di **migrazione dei dati lato Server**, selezionare il **modulo di migrazione dei dati lato Server** opzione il **impostazioni progetto** la finestra di dialogo.  
  
4.  Fare doppio clic su **schemi** in Visualizzatore metadati DB2 e quindi fare clic su **eseguire la migrazione di dati**. È inoltre possibile migrare i dati per singoli oggetti o le categorie di oggetti: mouse l'oggetto o la cartella padre. Selezionare il **eseguire la migrazione di dati** opzione.  
  
    > [!NOTE]  
    > Se SSMA per DB2 estensione Pack non è installato nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]e se **modulo di migrazione dei dati lato Server** è selezionata, durante la migrazione dei dati al database di destinazione, viene verificato il seguente errore: ' componenti SSMA migrazione dei dati non sono stati trovati in SQL Server, non sarà possibile eseguire la migrazione dei dati lato server. Verificare se il pacchetto di estensione sia installato correttamente '. Fare clic su **Annulla** per terminare la migrazione dei dati.  
  
5.  Nel **connessione a DB2** nella finestra di dialogo immettere le credenziali di connessione e quindi fare clic su **Connetti**. Per ulteriori informazioni sulla connessione a DB2, vedere [la connessione al Database DB2 &#40; DB2ToSQL &#41;](../../ssma/db2/connecting-to-db2-database-db2tosql.md)  
  
    Per la connessione al database di destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], immettere le credenziali di connessione nel **Connetti al Server SQL** la finestra di dialogo e fare clic su **Connetti**. Per ulteriori informazioni sulla connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], vedere [connessione a SQL Server](http://msdn.microsoft.com/en-us/b59803cb-3cc6-41cc-8553-faf90851410e)  
  
    I messaggi verranno visualizzati nel **Output** riquadro. Al termine, la migrazione di **Report di migrazione di dati** viene visualizzato. Se tutti i dati non sono stati migrati, fare clic sulla riga che contiene gli errori e quindi fare clic su **dettagli**. Quando si è finito di lavorare con il report, fare clic su **Chiudi**. Per ulteriori informazioni sul Report di migrazione di dati, vedere [Report di migrazione di dati (SSMA comune)](http://msdn.microsoft.com/en-us/bbfb9d88-5a98-4980-8d19-c5d78bd0d241)  
  
> [!NOTE]  
> Quando SQL Express edition viene utilizzato come database di destinazione, è consentita solo migrazione dei dati sul lato client e migrazione dei dati lato server non è supportata.  
  
## <a name="see-also"></a>Vedere anche  
[La migrazione dei dati di DB2 in SQL Server &#40; DB2ToSQL &#41;](../../ssma/db2/migrating-db2-data-into-sql-server-db2tosql.md)  
  
