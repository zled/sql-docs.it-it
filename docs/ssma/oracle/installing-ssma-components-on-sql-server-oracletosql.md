---
title: Installazione dei componenti SSMA in SQL Server (OracleToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-oracle
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Installign the Extension Pack
- SQL Server Database Objects
ms.assetid: 33070e5f-4e39-4b70-ae81-b8af6e4983c5
caps.latest.revision: "7"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: 76880266efb8c38bffdaa4223e49822c6d3b0778
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="installing-ssma-components-on-sql-server-oracletosql"></a>Installazione dei componenti SSMA in SQL Server (OracleToSQL)
Oltre a installare SSMA, è necessario installare anche i componenti nel computer in cui è in esecuzione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Questi componenti includono il pacchetto estensione SSMA, che supporta la migrazione dei dati e il provider Oracle per abilitare la connettività di server a server.  
  
## <a name="ssma-for-oracle-extension-pack"></a>SSMA per Oracle estensione Pack  
Il pacchetto di estensione SSMA aggiunge i database, **sysdb** e **ssmatesterdb**, per l'istanza specificata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Il database **sysdb** contiene le tabelle e stored procedure necessarie per la migrazione dei dati e le funzioni definite dall'utente che simulano le funzioni di sistema Oracle. Il **ssmatesterdb** database contiene le tabelle e le procedure necessari per il componente di Tester.  
  
Inoltre, quando si esegue la migrazione dei dati per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], crea SSMA [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] agente dei processi quando il modulo di migrazione dei dati lato server viene utilizzato per la migrazione dei dati.  
  
### <a name="prerequisites"></a>Prerequisites  
Prima di installare SSMA per i componenti server Oracle in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], assicurarsi che il sistema soddisfi i requisiti seguenti:  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]è installata l'istanza. SSMA non supporta SQL Server 2008 Express Edition.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows Installer 3.1 o versione successiva.  
  
-   Il Provider Client Oracle o il provider OLE DB per Oracle e la connettività al database Oracle che si desidera eseguire la migrazione. È possibile installare i provider dal supporto del prodotto Oracle o sito Web Oracle.  
  
-   Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] servizio Browser deve essere eseguito durante l'installazione. Viene utilizzato per popolare un elenco delle istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] nell'installazione guidata. È possibile disabilitare il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] servizio Browser dopo l'installazione.  
  
    > [!NOTE]  
    > Se il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] servizio Browser è in esecuzione, ma non ancora visualizzato un elenco di istanze nel programma di installazione, è necessario sbloccare la porta UDP 1434. È possibile utilizzare Windows Firewall per sbloccare temporaneamente la porta oppure è possibile disabilitare temporaneamente il Firewall di Windows. Potrebbe inoltre essere necessario disabilitare temporaneamente il software antivirus. Assicurarsi di attivare il software antivirus e firewall dopo l'installazione.  
  
### <a name="installing-the-extension-pack"></a>Installare il pacchetto di estensione  
È possibile installare qualsiasi momento prima di migrare i dati per il pacchetto di estensione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
> [!IMPORTANT]  
> Per installare il pacchetto di estensione, è necessario essere membro di **sysadmin** ruolo del server nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
**Per installare il pacchetto di estensione**  
  
1.  Se non è già stato fatto, estrarre tutti i file dal file Zip SSMA.  
  
    A seconda della versione di WinZip si dispone, è possibile fare doppio clic sul file, o il file e selezionare **Estrai tutto** o **aperto in WinZip**. Seguire le istruzioni nell'interfaccia utente WinZip per estrarre i file.  
  
2.  Copiare SSMA per Oracle estensione Pack. *n*. Install.exe, in cui  *n*  è il numero di build, al computer in cui è in esecuzione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
3.  Fare doppio clic su SSMA per Oracle estensione Pack. *n*. Install.exe.  
  
4.  Nella pagina di benvenuto fare clic su **Avanti**.  
  
5.  Nella pagina Contratto di licenza leggere il contratto di licenza. Se si accetta, selezionare il **accetto i termini del contratto di licenza** casella di controllo e quindi fare clic su **Avanti**.  
  
6.  Nella pagina Selezione tipo di installazione, fare clic su **tipica**.  
  
7.  Scegliere la pagina Inizio installazione, **installare**.  
  
8.  Nella pagina Installazione del primo passaggio di completato, fare clic su **Avanti**.  
  
    Verrà visualizzata una nuova finestra di dialogo, in cui si seleziona l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] per l'installazione di Service pack di estensione.  
  
9. Selezionare l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] in cui verrà la migrazione degli schemi di Oracle e quindi fare clic su **Avanti**.  
  
    L'istanza predefinita è lo stesso nome del computer. Le istanze denominate saranno seguite da una barra rovesciata e il nome dell'istanza.  
  
10. Nella pagina connessione selezionare il metodo di autenticazione e quindi fare clic su **Avanti**.  
  
    L'autenticazione di Windows utilizzerà le credenziali di Windows per tentare di accedere all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Se si seleziona [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] l'autenticazione, è necessario immettere un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] nome account di accesso e password.  
  
11. Nella pagina successiva, selezionare **installare Database utilità**  *n* , dove  *n*  è il numero di versione e quindi fare clic su **Avanti**.  
  
    Il **sysdb** database viene creato e le funzioni definite dall'utente e una stored procedure vengono create in tale database.  
  
    Se **installare Database Tester** opzione è selezionata il tester **ssmatesterdb** database verrà creato.  
  
12. Per installare le utilità in un'altra istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]selezionare **Sì**, quindi fare clic su **Avanti**. Per uscire dalla procedura guidata, fare clic su **n**.  
  
13. In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] o tramite l'utilità sqlcmd, eseguire lo script seguente per abilitare CLR:  
  
    ```  
    sp_configure 'clr enabled', 1  
    GO  
    RECONFIGURE  
    GO  
    ```  
    Se CLR non è abilitato, viene visualizzato l'errore seguente quando si connette SSMA a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]:  
  
    SSMA Impossibile recuperare le informazioni sulla versione di assembly di pacchetto di estensione. Reinstallare il pacchetto di estensione nel server di database.  
  
### <a name="sql-server-database-objects"></a>Oggetti di Database SQL Server  
Dopo aver installato il pacchetto di estensione, sarà possibile vedere un **ssma_oracle.bcp_migration_packages** tabella, un **ssma_oracle.db_storage** tabella e un **ssma_oracle.db_error_list** tabella il **sysdb** database. Si verifica anche molte stored procedure e funzioni definite dall'utente nel **ssma_oracle** dello schema.  
  
Ogni volta che si esegue la migrazione di dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], SSMA crea un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] processo dell'agente. Questi processi sono denominati **pacchetto di migrazione di dati ssma_oracle {GUID}**e sono visibili nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] nodo agenti di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] nella cartella processi.  
  
## <a name="see-also"></a>Vedere anche  
[Installazione di SSMA per Client Oracle &#40; OracleToSQL &#41;](../../ssma/oracle/installing-ssma-for-oracle-client-oracletosql.md)  
[Migrazione di database Oracle a SQL Server &#40; OracleToSQL &#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
