---
title: Database (modalità nativa SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.databasesetup.F1
ms.assetid: 8c9bb3b3-ea77-4a5b-ba35-7451ed11083d
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: d79b50e70f3eae3d9183ae220002136b39717e46
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48102491"
---
# <a name="database-ssrs-native-mode"></a>Database (modalità nativa SSRS)
  Utilizzare la pagina Database per creare e configurare i database del server di report che forniscono spazio di archiviazione interno per una o più istanze del server di report. Se si configura un server di report per l'uso di un database del server di report remoto, è necessario usare il [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager per creare il database.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Il processo per la creazione del database di un server di report e la configurazione della connessione include più passaggi. Per semplificare l'esecuzione dei passaggi necessari, in questa pagina sono disponibili procedure guidate per ogni tipo di attività. Le autorizzazioni e gli account di accesso vengono creati o aggiornati automaticamente. È possibile controllare lo stato di ogni passaggio nella pagina Stato. Se si verifica un errore, è possibile fare clic sull'errore per visualizzare informazioni su come risolverlo.  
  
 Il database del server di report deve supportare una modalità server specifica. La modalità predefinita è la modalità nativa, ma è anche possibile creare un database del server di report per la modalità integrata SharePoint, se si esegue il server di report in una distribuzione più ampia che include un prodotto o una tecnologia SharePoint. Per altre informazioni, vedere [Creare un database del server di report in modalità nativa &#40;Gestione configurazione SSRS&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md).  
  
 Per aprire questa pagina, avviare il [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager e fare clic su **Database** nel riquadro di spostamento. Per altre informazioni, vedere [Gestione configurazione Reporting Services &#40;modalità nativa&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
## <a name="options"></a>Opzioni  
 **Nome del Server SQL**  
 Nel Database di Server di Report corrente **SQL Server nome in** specifica il nome del [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] che esegue il database del server di report. È possibile utilizzare un'istanza predefinita o denominata su un computer locale o remoto.  
  
 **Database Name**  
 Consente di specificare il nome del database del server di report in cui sono archiviati i dati del server.  
  
 **Modalità Server di report**  
 Indica se il database del server di report supporta la modalità nativa o la modalità integrata SharePoint. Per altre informazioni, vedere [Server di Report di Reporting Services](../../../2014/reporting-services/reporting-services-report-server.md).  
  
 **Cambia Database**  
 Consente di avviare una procedura guidata per l'esecuzione semplificata di tutti i passaggi necessari per la creazione o la selezione di un database del server di report.  
  
 **Tipo di credenziale**  
 Consente di specificare le credenziali utilizzate dal server di report per eseguire la connessione al database. È possibile specificare i tipi di credenziale includono l'account del servizio, un utente di dominio di Windows, l'utente locale di Windows, o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] accesso al database. Per altre informazioni sulla selezione delle credenziali, vedere [configurare una connessione di Database Server di Report &#40;Gestione configurazione SSRS&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).  
  
 **Nome utente**  
 Specifica un account utente di dominio se si usa le credenziali di Windows oppure un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso se si usa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] credenziali. Se si usa le credenziali di Windows, specificarle nel formato seguente:  *\<dominio >\\< account\>*.  
  
 **Password**  
 Consente di specificare la password per l'account.  
  
 **Modifica credenziali**  
 Consente di avviare una procedura guidata che semplifica l'esecuzione di tutti i passaggi necessari per la selezione di un account diverso o per l'aggiornamento della password dell'account utilizzato per connettersi al database del server di report.  
  
## <a name="see-also"></a>Vedere anche  
 [Creare un database del server di report in modalità nativa &#40;Gestione configurazione SSRS&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
 [Gli argomenti della Guida F1 di Gestione configurazione di Reporting Services &#40;modalità nativa SSRS&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Database del server di report &#40;modalità nativa SSRS&#41;](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md)   
 [Configurare una connessione di Database Server di Report &#40;Gestione configurazione SSRS&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  
