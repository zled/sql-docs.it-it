---
title: Preparare SQL Server per CDC | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: change-data-capture
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- prepSqlSrv
ms.assetid: 20b51dbf-a545-4234-87ae-4228268a0fb2
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6fba782c94c0499af6fe0b644c92103884da14dd
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="prepare-sql-server-for-cdc"></a>Preparare SQL Server per CDC
  Il servizio Oracle CDC richiede che tutte le istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di destinazione contengano il database MSXDBCDC. Per creare questo database utilizzare l'azione Prepare SQL Server in CDC Service Configuration Console. Verrà creato uno script speciale eseguito per creare le tabelle, le stored procedure e altri artefatti obbligatori per il database. Questa attività viene eseguita una volta sola per ogni istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di destinazione.  
  
 Per ulteriori informazioni sul database MSXDBCDC, vedere Database MSXDBCDC.  
  
 In CDC Service Configuration Console, fare clic su **Prepare SQL Server**(Prepara SQL Server). Se questa opzione non è disponibile, verificare che nel riquadro sinistro della console sia selezionata l'opzione **Local CDC Services** (Servizi CDC locali).  
  
## <a name="options"></a>Opzioni  
  
### <a name="server-name"></a>Server Name  
 Digitare il nome del server in cui si trova [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
### <a name="authentication"></a>Autenticazione  
 Selezionare una delle opzioni seguenti:  
  
-   **Autenticazione di Windows**  
  
-   **Autenticazione di SQL Server**: se si seleziona questa opzione, è necessario digitare **Nome utente** e **Password** per l'utente nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a cui si esegue la connessione.  
  
 Per preparare l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per Oracle CDC, l'account di accesso deve disporre di autorizzazioni di scrittura per il database MSXDBCDC. Immettere le credenziali per un account di accesso che dispone di autorizzazioni per il database MSXDBCDC, ad esempio un membro del ruolo `sysasmin` .  
  
### <a name="options"></a>Opzioni  
 Fare clic sulla freccia per visualizzare le opzioni disponibili da configurare. È possibile scegliere di non modificare il valore predefinito per queste opzioni. Sono disponibili le opzioni seguenti:  
  
-   **Timeout connessione**: digitare il tempo, in secondi, di attesa del servizio CDC per Oracle per la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prima che si verifichi un errore di timeout. Il valore predefinito è **15**.  
  
-   **Timeout esecuzione**: digitare il tempo, in secondi, di attesa del servizio Windows Oracle CDC per l'esecuzione di un comando prima che si verifichi un errore di timeout. Il valore predefinito è **30**.  
  
-   **Encrypt Connection**: selezionare **Encrypt Connection** per la comunicazione tra il servizio Oracle CDC e l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di destinazione tramite una connessione crittografata.  
  
-   **Advanced**: digitare eventuali proprietà di connessione aggiuntive, se necessario.  
  
### <a name="view-script"></a>View Script  
 Fare clic su **Visualizza script** per visualizzare una versione di sola lettura dello script di impostazione. Se necessario, un amministratore di sistema di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può copiare questo script nella console di gestione di SQL Server per modificarlo. Per altre informazioni sulla preparazione di SQL Server per lo script, vedere [Preparare SQL Server per lo script di visualizzazione di Oracle CDC](../../integration-services/change-data-capture/prepare-sql-server-for-oracle-cdc-view-script.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura di utilizzo dei servizi CDC](../../integration-services/change-data-capture/how-to-work-with-cdc-services.md)   
 [Procedura di preparazione di SQL Server per CDC](../../integration-services/change-data-capture/how-to-prepare-sql-server-for-cdc.md)  
  
  
