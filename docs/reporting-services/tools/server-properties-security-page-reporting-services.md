---
title: "Proprietà server (pagina sicurezza) - Reporting Services | Microsoft Docs"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.reportserver.serverproperties.security.f1
ms.assetid: f49aedc6-f145-4df1-8f69-d5d910f492c6
caps.latest.revision: 11
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8da36c90d2eb22600ad6560a37367e68de933971
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="server-properties-security-page---reporting-services"></a>Proprietà server (pagina sicurezza) - Reporting Services
  Usare questa pagina di [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] in [!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)] per disattivare le caratteristiche che possono compromettere un server di report. La disattivazione di queste caratteristiche comporta l'impostazione di determinati limiti, ma consente di migliorare la sicurezza globale del server di report riducendo i rischi di minacce specifiche.  
  
 Per aprire la pagina:
 1) Avviare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].
 2) Connettersi a un'istanza del server di report.
 3) Fare clic con il pulsante destro del mouse sul nodo del server di report, quindi scegliere **Proprietà**. 
 4) Fare clic su **sicurezza** per aprire la pagina.  
  
## <a name="options"></a>Opzioni  
 **Attiva la sicurezza integrata di Windows per le origini dati dei report**  
 Consente di specificare se è possibile stabilire una connessione all'origine dati di un report utilizzando il token di sicurezza di Windows dell'utente che ha richiesto il report.  
  
 Se si disattiva questa caratteristica, la sicurezza integrata di Windows non sarà disponibile nelle pagine delle proprietà dell'origine dati del report. Se le origini dati del report sono configurate per la sicurezza integrata di Windows e successivamente si disattiva questa caratteristica, nel server di report vengono immediatamente aggiornate tutte le proprietà di connessione all'origine dati in modo che vengano richieste le credenziali.  
  
 **Consenti reporting ad hoc**  
 Consente di specificare se gli utenti possono eseguire query ad hoc da un report di Generatore report, nel caso in cui i nuovi report vengano generati automaticamente quando un utente fa clic su dati di interesse.  
  
 L'impostazione di questa opzione determina se il valore della proprietà **EnableLoadReportDefinition** nel server di report è impostato su **True** o su **False**. Se si deseleziona questa opzione, la proprietà viene impostata su **False** e nel server di report non verranno generati report click-through creati durante l'esplorazione dei dati. Tutte le chiamate al metodo **LoadReportDefinition** verranno bloccate.  
  
 La disattivazione di questa opzione consente di attenuare i rischi di attacchi Denial of Service condotti da utenti malintenzionati tramite overload del server di report con richieste **LoadReportDefinition** .  
  
## <a name="see-also"></a>Vedere anche  
 [Impostare le proprietà di un server di report &#40;Management Studio&#41;](../../reporting-services/tools/set-report-server-properties-management-studio.md)   
 [Eseguire la connessione a un server di report in Management Studio](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)   
 [Specificare le credenziali e le informazioni sulla connessione per le origini dati del report](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Guida sensibile al contesto del server di report in Management Studio](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)  
  
  

