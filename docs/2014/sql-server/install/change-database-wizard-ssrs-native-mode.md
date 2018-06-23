---
title: Procedura guidata cambia Database (modalità nativa SSRS) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SQL12.rsconfigtool.changedatabase.F1
helpviewer_keywords:
- Change Database Wizard
- report server database, create
ms.assetid: 1a2e8d18-5997-482f-a9c1-87d99f7407b8
caps.latest.revision: 10
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 256d91789d4bc1413580fde6f5c40ff8151f309a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36068836"
---
# <a name="change-database-wizard-ssrs-native-mode"></a>Procedura guidata Cambia database (modalità nativa SSRS)
  Il [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager fornisce la procedura guidata Database cambia in modo semplificato i passaggi per creare un nuovo database del server di report o selezionare un database di server di report esistente da utilizzare con l'istanza di server di report corrente.  
  
 Se si seleziona un database del server di report di una versione precedente, il database verrà aggiornato in base alla versione dell'istanza del server di report a cui è connesso. All'avvio del servizio, viene verificata la versione del database e il database viene aggiornato automaticamente allo schema corrente.  
  
 Per avviare la procedura guidata, fare clic su **Database delle modifiche** nella pagina Database di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager. Per istruzioni su come avviare il [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager, vedere [Gestione configurazione Reporting Services &#40;modalità nativa&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
## <a name="options"></a>Opzioni  
 **Azione**  
 Consente di selezionare l'attività che si desidera eseguire. È possibile creare un nuovo database in modalità nativa o in modalità integrata SharePoint. In alternativa, è possibile selezionare un database del server di report esistente da utilizzare con l'istanza del server di report corrente.  
  
 **Server di database**  
 Specificare il nome del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] istanza che ospita il database del server di report. È possibile utilizzare un'istanza predefinita o denominata su un computer locale o remoto. Se ci si connette a un'istanza denominata, immettere il nome del server nel formato seguente: \< *server*>\\<*istanza*>.  
  
 Per connettere il [!INCLUDE[ssDE](../../includes/ssde-md.md)] istanza, è necessario utilizzare le credenziali che dispongono dell'autorizzazione per accedere al server e aggiornare le informazioni di database. Il [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager utilizza le credenziali Windows correnti, ma se non si dispone di un account di accesso o database di autorizzazioni, è necessario specificare un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] accesso al database. Non è possibile specificare credenziali di Windows diverse. Se si desidera connettersi come altro utente di Windows, account di accesso come tale utente e quindi avviare il [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.  
  
 Per la connessione a un'istanza remota, è innanzitutto necessario abilitare l'istanza specifica per le connessioni remote. In alcune versioni ed edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le connessioni remote non sono abilitate per impostazione predefinita. Per verificare se sono consentite le connessioni remote, utilizzare il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager e assicurarsi che i protocolli TCP/IP e Named Pipes siano abilitati. Se l'istanza remota è anche un'istanza denominata, verificare che il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser sia abilitato e in esecuzione nel server di destinazione. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser fornisce il numero di porta utilizzato dall'istanza denominata per la [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.  
  
 **Database**  
 Consente di specificare il nome del database del server di report in cui sono archiviati i dati del server. È possibile specificare un database esistente o crearne uno nuovo.  
  
 Le proprietà utilizzate per creare un nuovo database vengono visualizzate nella procedura guidata quando si seleziona **Crea nuovo database** nella pagina Azioni. Il [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager crea due database associati in base al nome: un database contenente i dati statici e un database temporaneo per archiviare i dati di lavoro e della sessione. Per altre informazioni, vedere [Database del Server di Report &#40;modalità nativa SSRS&#41; ](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] documentazione Online.  
  
 È inoltre possibile scegliere un database esistente del server di report. Gestione configurazione [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] non esclude i database non validi. I database validi sono basati sullo schema del database del server di report. Non è possibile selezionare un database in cui manchino le tabelle, le viste o le stored procedure necessarie. Se si sceglie un database creato per una versione precedente di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], il database verrà aggiornato al formato corrente.  
  
 **Lingua**  
 Questo valore è impostato solo quando si crea un nuovo database del server di report  
  
 Questo valore consente di specificare la lingua in cui creare le definizioni di ruolo e le descrizioni. In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] è disponibile un modello di autorizzazione basata sui ruoli che include un set di ruoli predefiniti. Tali ruoli vengono creati una volta nella lingua specificata. I nomi dei ruoli e le descrizioni non vengono mai visualizzati in altre lingue, anche se ci si connette a un server di report tramite un browser con impostazioni della lingua supportate dal server. La lingua specificata determina inoltre la lingua utilizzata per creare i nomi della cartella dei report personali e delle cartelle degli utenti che fanno parte della caratteristica Report personali.  
  
 **Modalità server**  
 Un database del server di report supporta la modalità nativa o la modalità integrata SharePoint. Le due modalità si escludono reciprocamente.  
  
 Se si crea un nuovo database del server di report, è necessario specificare una modalità. La modalità selezionata determina la struttura del database del server di report e imposta il `SharePointIntegrated` proprietà di sistema server di report `true` o `false`.  
  
 Se si seleziona un database del server di report diverso, viene visualizzata la modalità del database corrente per indicare il modo in cui il database viene utilizzato.  
  
 **Credenziali**  
 Viene specificato l'account utilizzato dal server di report per la connessione al database del server di report. I valori validi includono l'account del servizio del servizio Web ReportServer, una [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] accesso al database definito nel [!INCLUDE[ssDE](../../includes/ssde-md.md)] istanza si utilizza per ospitare il server di report o un account di Windows. Se si utilizza un account di Windows, è possibile specificare un account locale (*\<computername >\\< nome utente\>*) se il server di report e il database si trovano nello stesso computer, o un utente di dominio account (*\<dominio >\\< nome utente\>*) se si trovano in computer diversi nello stesso dominio.  
  
 Il server di report creerà un account di accesso al database e assegnerà le autorizzazioni per il database all'account specificato.  
  
 Il server di report non crea l'account stesso. L'account specificato deve essere già presente e valido per la configurazione della distribuzione. In particolare, se il database si trova in un computer remoto e si desidera utilizzare un account di Windows, è necessario specificare un account che disponga di autorizzazioni di accesso nel computer specifico.  
  
 Se il computer è in un dominio diverso o non trusted, è consigliabile utilizzare un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] accesso al database. Per ulteriori informazioni sulla scelta di un account, vedere [configurare una connessione di Database Server di Report &#40;Gestione configurazione SSRS&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).  
  
 **Riepilogo**  
 Verificare le impostazioni prima della configurazione della connessione da parte del programma di installazione.  
  
 **Lo stato di avanzamento e di fine**  
 Consente di monitorare lo stato di ogni attività.  
  
## <a name="see-also"></a>Vedere anche  
 [Database &#40;modalità nativa SSRS&#41;](../../../2014/sql-server/install/database-ssrs-native-mode.md)   
 [Procedura guidata Modifica credenziali &#40;modalità nativa SSRS&#41;](../../../2014/sql-server/install/change-credentials-wizard-ssrs-native-mode.md)   
 [Creare un database del server di report in modalità nativa &#40;Gestione configurazione SSRS&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
 [Argomenti della Guida F1 di Gestione configurazione di Reporting Services &#40;modalità nativa SSRS&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Configurare una connessione di Database Server di Report &#40;Gestione configurazione SSRS&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  