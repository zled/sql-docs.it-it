---
title: Provider di dati utilizzati per le connessioni di Analysis Services | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 135ef70178cc3ce231171eafbe429fd21f284535
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="client-libraries-data-providers-used-for-analysis-services-connections"></a>Librerie client (provider di dati) utilizzate per le connessioni di Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

Analysis Services offre tre librerie client, noto anche come **provider di dati**per server e accesso ai dati da strumenti e applicazioni client. Strumenti come SQL Server Management Studio e SSDT e applicazioni, come Power BI Desktop ed Excel connettersi ad Analysis Services utilizzando queste librerie. Sono due delle librerie client, ADOMD.NET e Analysis Services Management Objects (AMO), librerie client gestito. Il provider OLE DB per Analysis Services (MSOLAP DLL) è una libreria client nativa. Le librerie client sono gli stessi per sia SQL Server Analysis Services e Azure Analysis Services.
  
##  <a name="bkmk_downloadsite"></a> Dove trovare le versioni più recenti  
 La versione installata in un computer client deve corrispondere alla versione principale del server che fornisce i dati. Se l'installazione del server è più recente dei provider di dati installati nelle workstation in rete, potrebbe essere necessario installare librerie più recenti.  

Le librerie client incluse in versioni precedenti di SQL Server Feature Pack corrispondono a tale versione SQL. Tuttavia, potrebbe non essere la versione più recente. Connessione ad Azure Analysis Services, potrebbero essere necessarie versioni successive. Tutte le versioni sono compatibili con le versioni precedenti.

Per ottenere la versione più recente, vedere [librerie Client per la connessione ad Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-data-providers). 
  
## <a name="see-also"></a>Vedere anche  
 [Connettersi ad Analysis Services](../../analysis-services/instances/connect-to-analysis-services.md)  
  
  
