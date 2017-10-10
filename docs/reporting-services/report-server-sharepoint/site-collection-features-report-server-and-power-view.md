---
title: "Attivare il server di report e le funzionalità di integrazione Power View in SharePoint | Documenti Microsoft"
ms.custom: 
ms.date: 09/25/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: e97378914a59fab938fc3e4c7926847effcffc94
ms.contentlocale: it-it
ms.lasthandoff: 10/06/2017

---
# <a name="activate-the-report-server-and-power-view-integration-features-in-sharepoint"></a>Attivare le funzionalità di integrazione Power View in SharePoint e il server di report

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

  Le funzionalità di raccolta del sito di Reporting Services sono attivate per impostazione predefinita, dopo aver installato il [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] aggiuntivo per prodotti SharePoint. In alcuni casi, è necessario attivare manualmente le funzionalità.  

> [!NOTE]
> Integrazione con SharePoint di Reporting Services non è più disponibile dopo SQL Server 2016.

 Se si installa il componente aggiuntivo di Reporting Services per prodotti SharePoint 2010 dopo l'installazione del prodotto SharePoint, quindi la funzionalità di integrazione del Server di Report e la funzionalità di integrazione Power View saranno attivate solo per le raccolte siti radice. Per altre raccolte siti, è necessario attivare manualmente le funzionalità. Ad esempio, se si dispone di una raccolta siti **http://[my nome del server] /sites/ [nome raccolta siti]** è necessario attivare manualmente le funzionalità di raccolta del sito di Reporting Services.  
  
 Quando è presente alcuna raccolta siti radice, il componente aggiuntivo di Reporting Services registra un messaggio simile al seguente.  
  
 "L'applicazione Web SharePoint 80 non dispone della raccolta siti radice"  
  
 Il messaggio viene trovato nel Registro di installazione di componente aggiuntivo, denominato "Rs_sp _ #. log" dove # è un numero a incremento. Il file di log si trova nella cartella Temp utenti corrente, ad esempio C:\Users\\[nome utente] \AppData\Local\Temp.. Per altre informazioni sulle opzioni di registrazione con il componente aggiuntivo, vedere [Installare o disinstallare il componente aggiuntivo Reporting Services per SharePoint](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).  

## <a name="activate-the-report-server-and-power-view-integration-site-collection-features"></a>Attivare la funzionalità di raccolta siti di integrazione Server di Report e Power View
  
1.  Aprire il browser al sito in cui si desiderano le funzionalità di Reporting Services attivo.  
  
2.  Fare clic su **Azioni sito**.  
  
3.  Fare clic su **Impostazioni sito**.  
  
4.  Fare clic su **Funzionalità raccolta siti** nel gruppo Amministrazione raccolta siti  
  
5.  Individuare **Funzionalità di integrazione Server report** o **Funzionalità di integrazione Power View** nell'elenco.  
  
6.  Fare clic su **Attiva**.  
  
 Per disattivare le funzionalità, è possibile utilizzare la stessa procedura facendo clic su **Disattiva** anziché su **Attiva**.  
  
## <a name="activate-or-deactivate-reporting-services-central-administration-site-collection-feature"></a>Attivare o funzionalità per la raccolta del sito di amministrazione centrale di disattivare Reporting Services
  
1.  Aprire il browser alla pagina Amministrazione centrale SharePoint.  
  
2.  Fare clic su **Azioni sito**.  
  
3.  Fare clic su **Impostazioni sito**.  
  
4.  Fare clic su **Funzionalità raccolta siti** nel gruppo Amministrazione raccolta siti  
  
5.  Individuare **Funzionalità Amministrazione centrale del server di report** nell'elenco.  
  
6.  Fare clic su **Attiva**.  
  
 Per disattivare la funzionalità, è possibile utilizzare la stessa procedura facendo tuttavia clic su **Disattiva** anziché su **Attiva.**  
  
## <a name="next-steps"></a>Passaggi successivi

Dopo aver attivato la funzionalità, è possibile continuare con l'integrazione del server.

Altre domande? [Visitare il forum su Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
