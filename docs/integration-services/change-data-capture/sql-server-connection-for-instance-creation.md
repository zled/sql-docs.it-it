---
title: SQL Server Connection for Instance Creation | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81d0e7e2-d8f0-4bd9-9565-218ce996f28e
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 65f20b235b6a3c4bd22ce754467f36a9b03fdaab
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="sql-server-connection-for-instance-creation"></a>Connessione di SQL Server per la creazione dell'istanza
  Uno dei primi passaggi della creazione di un'istanza di Oracle CDC consiste nella creazione di un database CDC nell'istanza [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di destinazione. Questo database CDC viene abilitato per SQL Server CDC. Questa operazione richiede un account di accesso che sia un membro del ruolo predefinito del server `sysadmin` .  
  
 Se un utente che avvia la procedura guidata **Create an Oracle CDC Instance** non è un membro del ruolo predefinito del server `sysadmin` , viene visualizzata la finestra di dialogo **Connect to SQL Server** e vengono richieste le credenziali per un membro del ruolo `sysadmin` per eseguire l'attività Enable the database for SQL Server CDC. Quando viene creato il database CDC, l'account di accesso `sysadmin` viene eliminato e viene ripreso l'account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] originale utilizzato al momento dell'accesso a Oracle Designer Console.  
  
## <a name="task-list"></a>Elenco attività  
 Immettere le informazioni riportate di seguito nella finestra di dialogo **Connect to SQL Server** .  
  
 **Nome server**  
 Digitare il nome del server in cui si trova [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Autenticazione**  
 Selezionare una delle opzioni seguenti:  
  
-   **Autenticazione di Windows**  
  
-   **Autenticazione di SQL Server**: se si seleziona questa opzione, è necessario digitare **Account utente** e **Password** per l'utente nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a cui si esegue la connessione.  
  
 L'account di accesso deve disporre di un ruolo del database che consenta l'accesso al database MSXCDCDB. L'account di accesso deve inoltre disporre dell'accesso a eventuali database aggiuntivi in uso, in caso contrario l'utente non sarà in grado di visualizzare i dati in quei database.  
  
 **Opzioni**  
 Fare clic sulla freccia per visualizzare le opzioni disponibili da configurare. È possibile scegliere di non modificare il valore predefinito per queste opzioni. Sono disponibili le opzioni seguenti:  
  
-   **Connection Timeout**: digitare il tempo, in secondi, di attesa del servizio CDC per Oracle per la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prima che si verifichi un errore di timeout. Il valore predefinito è **15**.  
  
-   **Execution Timeout**: digitare il tempo, in secondi, di attesa del servizio Windows Oracle CDC per l'esecuzione di un comando prima che si verifichi un errore di timeout. Il valore predefinito è **30**.  
  
-   **Encrypt Connection**: selezionare **Encrypt Connection** per la comunicazione tra il servizio Oracle CDC e l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di destinazione tramite una connessione crittografata.  
  
-   **Advanced**: fare clic su **Advanced** e digitare eventuali proprietà di connessione aggiuntive nella finestra di dialogo Advanced Connection Properties, se necessario.  
  
     Per informazioni sulla finestra di dialogo Advanced Connection Properties, vedere [Advanced Connection Properties](../../integration-services/change-data-capture/advanced-connection-properties.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Creare il Database SQL Server Change](../../integration-services/change-data-capture/create-the-sql-server-change-database.md)   
 [Autorizzazioni necessarie della connessione a SQL Server per la progettazione di CDC](../../integration-services/change-data-capture/sql-server-connection-required-permissions-for-the-cdc-designer.md)  
  
  
