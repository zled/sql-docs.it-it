---
title: Installare il provider di dati di Analysis Services (AMO, ADOMD.NET, MSOLAP) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: instances
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7aedabc-6af9-4698-a7a4-98f894001476
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: bd6aa812228cce132b4180a8537ba853f3ea92a2
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="install-analysis-services-data-providers-amo-adomdnet-msolap"></a>Installare il provider di dati di Analysis Services (AMO, ADOMD.NET, MSOLAP)
  [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] è un aggiornamento di versione dei provider di dati di Analysis Services, composto da ADOMD.Net, AMO e MSOLAP.  
  
 Per la maggior parte degli scenari di accesso ai dati basati su query è possibile usare le versioni esistenti dei provider di dati già installati nei sistemi client per accedere ai modelli tabulari e multidimensionali in un'istanza di SQL Server 2016 Analysis Services, inclusi i modelli tabulari che usano funzionalità esclusive di SQL Server 2016. Come regola generale, le applicazioni client che generano query, ad esempio Excel, Reporting Services o Tableau, non dovrebbero richiedere i provider di dati più recenti quando accedono a un modello di Analysis Services.  
  
 Gli strumenti di modellazione e amministrazione costituiscono un'eccezione alla regola, almeno in termini di requisiti di versione per i provider di dati. Questi strumenti devono avere i provider di dati creati in modo specifico per il server di destinazione in modo da modificare gli oggetti in tale server. Fortunatamente, gli strumenti forniti con [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] includono automaticamente i provider di dati conformi alla versione corrente del server.  Il programma di installazione di SQL Server Data Tools per Visual Studio 2015 installa i provider di dati per SQL Server 2016 Analysis Services. In modo analogo, SQL Server 2016 Management Studio, che usa AMO e ADOMD.Net, installa entrambi i provider di dati per [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
 Uno scenario che richiede l'installazione manuale di un provider di dati è quello relativo alle applicazioni o agli script personalizzati che usano Analysis Services Management Objects (AMO). Questa versione introduce uno spazio dei nomi a cui è stato eseguito il refactoring che consente di spostare gli oggetti principali, ad esempio server e database, a un nuovo spazio dei nomi (Microsoft.AnalysisServices.Core) che fa parte dell'assembly Microsoft.AnalysisServices.dll. Se si dispone di codice personalizzato o script che usano gli oggetti AMO, è necessario ricompilare il codice e aggiornare manualmente gli oggetti AMO in ogni server e workstation client che esegue una connessione diretta tramite AMO a un'istanza di SQL Server 2016 di Analysis Services.  
  
## <a name="provider-list"></a>Elenco di provider  
 La tabella seguente descrive ciascun parametro.  
  
||||  
|-|-|-|  
|Provider|Filename|Version|  
|Analysis Services Management Objects (AMO)|Microsoft.AnalysisServices.dll|13.0.0.0|  
|Analysis Services Core|Microsoft.AnalysisServices.Core.dll|13.0.0.0|  
|Analysis Services (ADOMD.NET)|Microsoft.AnalysisServices.AdomdClient.dll|13.0.0.0|  
|Provider OLE DB per Analysis Services (MSOLAP)|MSOLAP130.dll|13.0.0.0|  
  
## <a name="download-and-install-data-provider"></a>Scaricare e installare il provider di dati  
  
1.  Andare alla pagina di download per [Feature Pack di SQL Server 2016](http://go.microsoft.com/fwlink/?LinkID=398150)  
  
2.  Fare clic su **Download** per consentire l'installazione dei singoli componenti.  
  
3.  Per i computer a 64 bit, selezionare alcune o tutte le operazioni seguenti. In caso contrario, scegliere l'equivalente di x86:  
  
    -   ENU\x64\SQL_AS_ADOMD.msi  
  
    -   ENU\x64\SQL_AS_AMO.msi  
  
    -   ENU\x64\SQL_AS_OLEDB.msi  
  
4.  Fare clic su **Next** per scaricare i file.  
  
5.  Eseguire ogni programma per installare il provider. Gli assembly ADO.MD e AMO vengono installati in C:\Windows\assembly\GAC_MSIL. Il provider OLE DB per Analysis Services è installato in C:\Programmi\Microsoft Analysis Services\AS OLEDB\130.  
  
## <a name="verify-installation"></a>Verificare l'installazione  
  
1.  In Esplora file passare a C:\Windows\Assembly.  
  
2.  Fare clic con il pulsante destro del mouse su Microsoft.AnalysisServices e scegliere **Proprietà**.  
  
3.  Fare clic su **Versione** per confermare di avere la compilazione più recente.  
  
  

