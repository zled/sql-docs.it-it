---
title: Prerequisiti per le esercitazioni (Generatore report) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b8346a6-f4f4-4ad3-bc98-8f2be342ef2d
caps.latest.revision: 8
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 5326d5e91521e90f7596e3dd0647cb273078fd82
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169830"
---
# <a name="prerequisites-for-tutorials-report-builder"></a>Prerequisiti per le esercitazioni (Generatore report)
  Nelle esercitazioni di Generatore report si presuppone che l'utente sia in grado di visualizzare e salvare report in un server di report o in un sito di SharePoint integrato in un server di report. Per quanto riguarda i dati, in tutte le esercitazioni vengono utilizzate query letterali che devono essere elaborate da un'istanza di [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
 Se non si dispone dell'accesso a un server di report, a un sito o a un'origine dati, sarà possibile apprendere l'utilizzo di Generatore report attraverso la compilazione di un report offline. Vedere [Esercitazione: Creare un report grafico rapido offline &#40;Generatore report&#41;](report-builder/tutorial-create-a-quick-chart-report-offline-report-builder.md).  
  
## <a name="requirements"></a>Requisiti  
 Per completare le esercitazioni di Generatore report, è necessario soddisfare i requisiti seguenti:  
  
-   Accesso a Generatore report di [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] . È possibile eseguire Generatore report utilizzando la versione autonoma di Generatore report o la versione ClickOnce, disponibile da Gestione report o da un sito di SharePoint. Per le versioni ClickOnce, l'unica differenza riguarda il primo passaggio, ovvero l'apertura di Generatore report.  
  
     Per utilizzare Gestione Report, aprire Gestione Report e fare clic su **Generatore Report**. Per impostazione predefinita, l'URL per gestione Report è http://\<*servername*> / reports.  
  
     Per utilizzare un sito di SharePoint, accedere al sito, fare clic sulla scheda Documenti, fare clic su Nuovo documento, quindi su Report di Generatore report nell'elenco a discesa. Ad esempio, http://\<nomeserver >/siti/mySite/reports. L'amministratore di SharePoint deve abilitare la caratteristica Report di Generatore report per ogni raccolta documenti.  
  
-   L'URL a un [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] server o un sito di SharePoint integrato con un [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] server di report. È necessario disporre dell'autorizzazione per il salvataggio e la visualizzazione di report, origini dati condivise, set di dati condivisi, parti di report e modelli. Per impostazione predefinita, l'URL per un server di report è http://\<nomeserver > / reportserver. Per impostazione predefinita, l'URL per un sito di SharePoint è http://\<nomesito > o http://\<server > / sito.  
  
-   Il nome di un [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] istanza e credenziali sufficienti per l'accesso in lettura a qualsiasi database. Per le query del set di dati delle esercitazioni vengono utilizzati dati letterali, ma per restituire i metadati necessari per un set di dati del report ogni query deve essere elaborata da un'istanza di [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] . Ad esempio, nella stringa di connessione seguente viene specificato solo un server: `data source=<servername>`. È necessario disporre dell'accesso in lettura al database predefinito assegnato all'utente dall'amministratore di sistema che concede l'autorizzazione per l'accesso al server. È inoltre possibile specificare un database, come illustrato nella stringa di connessione seguente: `data source=<servername>;initial catalog=<database>`.  
  
-   Per l'esercitazione in cui è inclusa una mappa, è necessario configurare il server di report affinché supporti le mappe Bing come sfondo. Per altre informazioni, vedere [pianificare per il supporto di Report mappa](plan-for-map-report-support.md) in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] documentazione nella [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [documentazione Online di](http://go.microsoft.com/fwlink/?LinkId=154888) sul sito msdn.microsoft.com.  
  
-   L'esercitazione [esercitazione: creazione di drill-through e report principale &#40;Generatore Report&#41;](tutorial-creating-drillthrough-and-main-reports-report-builder.md), viene utilizzato il set di dati dimostrativo di business intelligence aziendali di Contoso. Questo set di dati è costituito dal data warehouse ContosoDW e dal database dell'elaborazione analitica online (OLAP) di Contoso_Retail. I report che si creeranno in questa esercitazione recuperano i dati di report dal cubo vendite Contoso. Il database OLAP di Contoso_Retail può essere scaricato dall' [Area download Microsoft](http://go.microsoft.com/fwlink/?LinkID=191575). Sarà sufficiente scaricare solo il file ContosoBIdemoABF.exe. Il file contiene il database OLAP.  
  
     L'altro file, ContosoBIdemoBAK.exe, è relativo al data warehouse ContosoDW, che non viene utilizzato in questa esercitazione.  
  
     Il sito Web include istruzioni relative all'estrazione e al ripristino del file di backup ContosoRetail.abf nel database OLAP di Contoso_Retail.  
  
     È necessario avere accesso a un'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sulla quale installare il database OLAP.  
  
 L'amministratore del server di report deve concedere le autorizzazioni necessarie per il server di report, configurare [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] percorsi delle cartelle e configurare le opzioni predefinite di Generatore Report. Per altre informazioni, vedere [di installazione, disinstallazione e supporto di Generatore Report](install-uninstall-and-report-builder-support.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Esercitazioni su &#40;Generatore Report&#41;](report-builder-tutorials.md)  
  
  