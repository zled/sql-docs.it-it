---
title: Pagina Impostazioni (gestione Report) del sito | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 4d67a01c-eae4-49ba-a6e8-8e983c0248f5
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 3bd40d6b97215329bb2cab060853fc06ef862dbd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48065294"
---
# <a name="site-settings-page-report-manager"></a>Pagina Impostazioni sito (Gestione report)
  La pagina Impostazioni sito consente di modificare il titolo dell'applicazione, di definire le impostazioni predefinite a livello di server per i valori limite per la cronologia dei report e i valori di timeout per l'elaborazione dei report, di gestire le assegnazioni di ruolo a livello di sistema e di gestire le pianificazioni condivise. Per visualizzare questa pagina, è necessario disporre delle autorizzazioni Gestione contenuto e Amministratore sistema.  
  
> [!NOTE]  
>  Le seguenti funzionalità non sono disponibili in ogni edizione di SQL Server: cronologia dei report, esecuzione dei report e pianificazioni condivise. Per un elenco delle funzionalità supportate dalle edizioni di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], vedere [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="navigation"></a>Navigazione  
 Utilizzare la procedura riportata di seguito per navigare fino a questo percorso nell'interfaccia utente.  
  
### <a name="to-open-the-site-settings-page"></a>Per aprire la pagina Impostazioni sito  
  
1.  Aprire Gestione report.  
  
2.  Nella parte superiore della pagina fare clic su **Impostazioni sito**. Viene visualizzata la pagina delle proprietà Generale del sito.  
  
     **Nota:** se non viene visualizzata la **Impostazioni sito** opzione nel menu, non si dispone delle autorizzazioni necessarie, per altre informazioni vedere la sezione "Impostazioni sito" di [configurare un Server di Report in modalità nativa per Amministrazione locale &#40;SSRS&#41;](report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
## <a name="options"></a>Opzioni  
 **Nome**  
 Specificare il titolo da utilizzare per questa istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] gestione Report. Per impostazione predefinita, il titolo è "[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]".  
  
 **Selezionare le impostazioni predefinite per la cronologia dei report**  
 Selezionare un valore predefinito per il numero di copie di cronologia del report da conservare. Il valore predefinito rappresenta un'impostazione iniziale che definisce i limiti per la cronologia dei report. È possibile modificare tali impostazioni a livello dei singoli report. Per altre informazioni, vedere [Pagina delle proprietà Opzioni snapshot &#40;Gestione report&#41;](../../2014/reporting-services/snapshot-options-properties-page-report-manager.md).  
  
 Se si imposta tale limite in un momento successivo e il limite viene superato, la cronologia dei report nel server viene ridotta di conseguenza. Vengono eliminati per primi gli snapshot del report meno recenti. Se la cronologia è vuota o include un numero di snapshot inferiore al limite, vengono aggiunti nuovi snapshot del report. Quando viene raggiunto il limite, all'aggiunta di un nuovo snapshot del report viene eliminato lo snapshot meno recente.  
  
 **Timeout esecuzione report**  
 Consente di specificare se si desidera impostare un timeout per l'elaborazione del report dopo un numero specifico di secondi.  
  
 Tale valore viene applicato all'elaborazione dei report in un server di report. L'impostazione non ha effetto sull'elaborazione dei dati nel server di database che fornisce i dati per il report.  
  
 Il conteggio del timer per l'elaborazione del report inizia al momento della selezione del report e termina all'apertura del report. Quando si imposta questo valore è necessario specificare un tempo sufficiente per completare sia l'elaborazione dei dati che l'elaborazione del report.  
  
 **URL di avvio di Generatore Report personalizzato**  
 Consente di specificare un URL personalizzato se per il server di report non viene utilizzato l'URL predefinito di Generatore report. Questa impostazione è facoltativa. Se non si specifica alcun valore, verrà utilizzato l'URL predefinito, che consente di avviare Generatore report come applicazione ClickOnce. L'URL predefinito corrisponde a uno dei valori seguenti:  
  
 **Server di report in modalità nativa:** In un'installazione in modalità nativa, l'URL predefinito diventerà il formato http://\<*nomecomputer*> / reportserver/ReportBuilder/ReportBuilder_3_0_0_0.application.  
  
 La modalità integrata SharePoint: l'URL predefinito diventerà il formato http://\<*Sito_sharepoint*> / _vti_bin/ReportBuilder/ReportBuilder_3_0_0_0.application. "  
  
 **Applica**  
 Fare clic per salvare le modifiche apportate al server di report.  
  
 **Security**  
 Fare clic su questo collegamento per aprire la pagina Assegnazioni ruolo a livello di sistema, nella quale è possibile assegnare account utente e account di gruppo a ruoli di sistema predefiniti.  
  
 **Pianificazioni**  
 Fare clic su questo collegamento per aprire la pagina Pianificazioni, nella quale è possibile impostare pianificazioni condivise predefinite che gli utenti possono selezionate per i report e le sottoscrizioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione report &#40;modalità nativa SSRS&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Concessione di autorizzazioni in un server di report in modalità nativa](security/granting-permissions-on-a-native-mode-report-server.md)   
 [Ruoli predefiniti](security/role-definitions-predefined-roles.md)   
 [Guida sensibile al contesto di Gestione report](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
