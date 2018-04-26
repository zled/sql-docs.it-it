---
title: Installazione dei componenti SSMA in SQL Server (MySQLToSql) | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-mysql
ms.custom: ''
ms.date: 01/19/2017
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
- SSMA extension pack, Installation
ms.assetid: 6772d0c5-258f-4d7b-afb0-b5f810e71af1
caps.latest.revision: 9
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4d55b216e149384c38477f684f3bdddfb812141f
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="installing-ssma-components-on-sql-server-mysqltosql"></a>Installazione dei componenti SSMA in SQL Server (MySQLToSql)
Oltre a installare SSMA, è necessario installare anche i componenti nel computer in cui è in esecuzione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Questi componenti includono il pacchetto estensione SSMA, che supporta la migrazione dei dati e i provider di MySQL per abilitare la connettività di server a server.  
  
## <a name="ssma-for-mysql-extension-pack"></a>SSMA per l'estensione MySQL Pack  
Il pacchetto di estensione SSMA viene aggiunto un database, **sysdb**, per l'istanza specificata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Questo database contiene tabelle e stored procedure necessarie per la migrazione dei dati.  
  
Inoltre, quando si esegue la migrazione dei dati per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], crea SSMA [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] processi agente, quando il modulo di migrazione dei dati lato server viene utilizzato per la migrazione dei dati.  
  
### <a name="prerequisites"></a>Prerequisiti  
Prima di installare SSMA per i componenti server di MySQL in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], assicurarsi che il computer soddisfi i requisiti seguenti:  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows Installer 3.1 o versione successiva.  
  
-   Il Provider Client MySQL e la connettività al database di MySQL che si desidera eseguire la migrazione. È possibile installare i provider dal sito Web di MySQL o MySQL supporto del prodotto.  
  
-   Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] servizio Browser deve essere eseguito durante l'installazione. Viene utilizzato per popolare un elenco delle istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] nell'installazione guidata. È possibile disabilitare il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] servizio Browser dopo l'installazione.  
  
    > [!NOTE]  
    > Se il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] servizio Browser è in esecuzione, ma non ancora visualizzato un elenco di istanze nel programma di installazione, è necessario sbloccare la porta UDP 1434. È possibile utilizzare Windows Firewall per sbloccare temporaneamente la porta oppure è possibile disabilitare temporaneamente il Firewall di Windows. Potrebbe inoltre essere necessario disabilitare temporaneamente il software antivirus. Assicurarsi di attivare il software antivirus e firewall dopo l'installazione.  
  
### <a name="installing-the-extension-pack"></a>Installare il pacchetto di estensione  
È possibile installare qualsiasi momento prima di migrare i dati per il pacchetto di estensione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
> [!IMPORTANT]  
> Per installare il pacchetto di estensione, è necessario essere membro di **sysadmin** ruolo del server nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
**Per installare il pacchetto di estensione**  
  
1.  Copiare SSMA per l'estensione MySQL Pack. *n*. Install.exe, dove *n* è il numero di build, al computer in cui è in esecuzione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
2.  Fare doppio clic su SSMA per l'estensione MySQL Pack. *n*. Install.exe.  
  
3.  Nella finestra di dialogo di benvenuto, fare clic su **Avanti**.  
  
4.  Nella finestra di dialogo Contratto di licenza leggere il contratto di licenza. Se si accetta, selezionare il **accetto i termini del contratto di licenza** casella di controllo e quindi fare clic su **Avanti**.  
  
5.  Nella finestra di dialogo Selezione tipo di installazione, fare clic su **tipica**.  
  
6.  Nella schermata per la finestra di dialogo di installazione, fare clic su **installare**.  
  
7.  Scegliere la finestra di dialogo di installazione del primo passaggio di completato, **Avanti**.  
  
    Verrà visualizzata una nuova finestra di dialogo, in cui si seleziona l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] per l'installazione di Service pack di estensione.  
  
8.  Selezionare l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] in cui verrà la migrazione degli schemi di MySQL e quindi fare clic su **Avanti**.  
  
    L'istanza predefinita è lo stesso nome del computer. Le istanze denominate saranno seguite da una barra rovesciata e il nome dell'istanza.  
  
9. Nella finestra di dialogo connessione, selezionare il metodo di autenticazione e quindi fare clic su **Avanti**.  
  
    L'autenticazione di Windows utilizzerà le credenziali di Windows per tentare di accedere all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Se si seleziona [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] l'autenticazione, è necessario immettere un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] nome account di accesso e password.  
  
10. Nella successiva finestra di dialogo, selezionare **installare Database Utilities** *n*, dove *n* è il numero di versione e quindi fare clic su **Avanti**.  
  
    Il **sysdb** database viene creato con le tabelle e stored procedure necessarie per la migrazione dei dati (con modulo di migrazione dei dati lato server) vengono create in tale database.  
  
11. Per installare le utilità in un'altra istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]selezionare **Sì**, quindi fare clic su **Avanti**. Per uscire dalla procedura guidata, fare clic su **n**.  
  
## <a name="see-also"></a>Vedere anche  
[Installazione di SSMA per Client di MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/installing-ssma-for-mysql-client-mysqltosql.md)  
[Database MySQL la migrazione a SQL Server - SQL di Azure DB &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
