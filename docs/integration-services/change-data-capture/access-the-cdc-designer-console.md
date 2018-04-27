---
title: Accedere a CDC Designer Console | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: change-data-capture
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- accMsDes
ms.assetid: b168c64e-c1b5-42d4-a92a-84de1dd0324e
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ed9d343d4fd33a4eee7be1b6b49caa3516d444c9
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="access-the-cdc-designer-console"></a>Accedere a CDC Designer Console
  È possibile accedere a CDC Designer Console dal computer in cui è stata installata la console. Per ulteriori informazioni sull'installazione, vedere Installazione.  
  
 Quando si apre CDC Designer Console, verrà visualizzata la finestra di dialogo Connect to SQL Server.  
  
 L'account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che accede alla finestra di progettazione di CDC deve disporre delle autorizzazioni UPDATE per il database MSXDBCDC. Deve inoltre disporre del ruolo predefinito del server `dbcreator` per creare nuove istanze di Oracle CDC. L'account di accesso dovrebbe inoltre disporre dell'accesso SELECT ai database CDC utilizzati, in caso contrario l'utente non sarà in grado di visualizzare lo stato di questi database.  
  
 Immettere le informazioni riportate di seguito nella finestra di dialogo Connect to SQL Server.  
  
### <a name="server-name"></a>Server Name  
 Digitare il nome del server in cui si trova [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
### <a name="authentication"></a>Autenticazione  
 Selezionare una delle opzioni seguenti:  
  
-   **Autenticazione di Windows**  
  
-   **Autenticazione di SQL Server**: se si seleziona questa opzione, è necessario digitare **Account utente** e **Password** per l'utente nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a cui si esegue la connessione.  
  
 L'account di accesso deve disporre di un ruolo del database che consenta l'accesso al database MSXCDCDB. L'account di accesso deve inoltre disporre dell'accesso a eventuali database aggiuntivi in uso, in caso contrario l'utente non sarà in grado di visualizzare i dati in quei database.  
  
### <a name="options"></a>Opzioni  
 Fare clic sulla freccia per visualizzare le opzioni disponibili da configurare. È possibile scegliere di non modificare il valore predefinito per queste opzioni. Sono disponibili le opzioni seguenti:  
  
 **Connection Timeout**  
 Digitare il tempo, in secondi, di attesa del servizio CDC per Oracle per la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prima che si verifichi un errore di timeout. Il valore predefinito è **15**.  
  
 **Execution Timeout**  
 Digitare il tempo, in secondi, di attesa del servizio Windows Oracle CDC per l'esecuzione di un comando prima che si verifichi un errore di timeout. Il valore predefinito è **30**.  
  
 **Encrypt Connection**  
 Selezionare **Encrypt Connection** per la comunicazione tra il servizio Oracle CDC e l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di destinazione usando una connessione crittografata.**Advanced**: fare clic su **Advanced** e digitare eventuali proprietà di connessione aggiuntive nella finestra di dialogo Advanced Connection Properties.  
  
 **Advanced**  
 Fare clic su **Advanced** e digitare eventuali proprietà di connessione aggiuntive nella finestra di dialogo Advanced Connection Properties.  
  
 Per informazioni sulla finestra di dialogo Advanced Connection Properties, vedere [Advanced Connection Properties](../../integration-services/change-data-capture/advanced-connection-properties.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Autorizzazioni necessarie della connessione di SQL Server per la finestra di progettazione di CDC](../../integration-services/change-data-capture/sql-server-connection-required-permissions-for-the-cdc-designer.md)  
  
  
