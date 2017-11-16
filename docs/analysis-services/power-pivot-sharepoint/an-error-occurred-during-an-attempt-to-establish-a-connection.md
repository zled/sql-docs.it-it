---
title: "Si è verificato un errore durante il tentativo di stabilire una connessione | Documenti Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: power-pivot-sharepoint
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 1b951da1-f62d-43d2-b40b-270a4a9ab92c
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 226842eb86c8eb7d5981407c805e18495dfb2579
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="an-error-occurred-during-an-attempt-to-establish-a-connection"></a>Si è verificato un errore durante il tentativo di stabilire una connessione
  Questo errore si verifica se si esegue una query sui dati [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] in un server in cui non è installato [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint. Si verifica anche se viene arrestato il servizio SQL Server Analysis Services ([!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]) o se si prova a visualizzare dati [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] di una versione precedente.  
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Applicabile a|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint|  
|Versione prodotto|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Causa|Impossibile stabilire la connessione dati.|  
|Testo del messaggio|Errore durante il tentativo di stabilire una connessione all'origine dati esterna. Impossibile aggiornare le connessioni seguenti: Dati [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]|  
  
## <a name="explanation"></a>Spiegazione  
 Excel Services restituisce questo errore quando si esegue una query sui dati [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] in una cartella di lavoro di Excel pubblicata in SharePoint e l'ambiente SharePoint non include un server [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint o se il servizio SQL Server Analysis Services ([!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]) è stato arrestato.  
  
 L'errore si verifica se si sezionano o filtrano dati [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] quando il motore di query non è disponibile.  
  
## <a name="user-action"></a>Azione dell'utente  
 Installare [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint o spostare la cartella di lavoro di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] in un ambiente SharePoint in cui sia installato [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint. Per altre informazioni, vedere [Power Pivot for SharePoint 2010 Installation (Installazione di PowerPivot per SharePoint 2010)](http://msdn.microsoft.com/en-us/8d47dde7-c941-4280-a934-e2fe3f9a938f).  
  
 Se il software è installato, verificare che l'istanza di SQL Server Analysis Services ([!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]) sia in esecuzione. Selezionare **Gestisci servizi nel server** in Amministrazione centrale. Selezionare inoltre l'applicazione console Servizi in Strumenti di amministrazione.  
  
 Per le cartelle di lavoro di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] create nella versione SQL Server 2008 R2 di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per Excel è necessario installare la versione SQL Server 2008 R2 del provider OLE DB per Analysis Services. Si verificherà questo errore se è stato installato il provider, ma non è stato registrato il file Microsoft.AnalysisServices.ChannelTransport.dll. Per altre informazioni sulla registrazione dei file, vedere [Installazione del provider OLE DB di Analysis Services nei server di SharePoint](http://msdn.microsoft.com/en-us/2c62daf9-1f2d-4508-a497-af62360ee859).  
  
## <a name="see-also"></a>Vedere anche  
 [La connessione dati utilizza l'autenticazione di Windows e non possono essere delegate le credenziali dell'utente. Impossibile aggiornare le connessioni seguenti: dati PowerPivot](../../analysis-services/power-pivot-sharepoint/the-data-connection-user-could-not-be-delegated.md)  
  
  

