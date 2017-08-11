---
title: Servizio Windows ReportServer (MSSQLServer) 107 | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSSQLServer 107 error
ms.assetid: 52b5704b-27f9-400a-a821-d8fa0786afe4
caps.latest.revision: 20
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 55aaa75882e5fdad4ffcad603e5edaef86226d48
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="report-server-windows-service-mssqlserver-107"></a>Servizio Windows ReportServer (MSSQLServer) 107
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|107|  
|Origine evento|Servizio Windows ReportServer|  
|Componente|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|Testo del messaggio|Il servizio Windows ReportServer (MSSQLSERVER) non è in grado di connettersi al database del server di report.|  
  
## <a name="explanation"></a>Spiegazione  
 Il servizio del server di report di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è in grado di connettersi al database del server di report. Questo errore si verifica durante un riavvio del servizio se non è possibile stabilire una connessione al database del server di report. Di seguito vengono riportate le condizioni in presenza delle quali si verifica l'errore:  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)] servizio non è in esecuzione all'avvio del servizio Server di Report.  
  
-   Non è possibile eseguire la connessione al servizio [!INCLUDE[ssDE](../../includes/ssde-md.md)] perché le connessioni remote o il protocollo TCP/IP non è abilitato.  
  
-   Il database del server di report non è configurato in modo corretto.  
  
-   L'account di servizio non è configurato correttamente o l'account non dispone più di autorizzazioni sul database del server di report. Questa situazione può verificarsi se non si utilizza lo strumento di configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] per configurare l'account o il database del server di report.  
  
## <a name="user-action"></a>Azione dell'utente  
 Avviare il servizio [!INCLUDE[ssDE](../../includes/ssde-md.md)] se non è in esecuzione e verificare che le connessioni remote siano abilitate per il protocollo TCP/IP.  
  
 Utilizzare lo strumento di configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] per configurare il database del server di report e l'account di servizio.  
  
## <a name="internal-only"></a>Solo interno  
  
## <a name="see-also"></a>Vedere anche  
 [Configurare Account di servizio del Server di Report &#40; Gestione configurazione SSRS &#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Reporting Services di Configuration Manager &#40; Modalità nativa &#41;](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)   
 [Avviare e arrestare il servizio Server di Report](../../reporting-services/report-server/start-and-stop-the-report-server-service.md)  
  
  
