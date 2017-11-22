---
title: Esecuzione di transazioni in ADOMD.NET | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- transactions [ADOMD.NET]
- ADOMD.NET, transactions
- AdomdTransaction object
ms.assetid: 7978c28b-c255-43c0-ad05-f38604d4d8fe
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5c78445de3ed3b17805bc458ce6078e0d9587eed
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="connections-in-adomdnet---performing-transactions"></a>Connessioni in ADOMD.NET - esecuzione di transazioni
  In ADOMD.NET utilizzare l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> per gestire il contesto di transazione per un oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> specifico. Questa funzionalità consente di eseguire numerosi comandi all'interno dello stesso contesto. Ogni comando leggerà gli stessi dati senza modificarli tra ogni esecuzione dei comandi.  
  
> [!NOTE]  
>  Il <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> è un'implementazione della classe di **System.Data.IDbTransaction** interfaccia, parte del [!INCLUDE[msCoName](../../includes/msconame-md.md)] libreria di classi .NET Framework e implementata da tutti i provider di dati .NET Framework che supportano transazioni.  
  
 L'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> supporta solo transazioni di tipo Read Committed in cui i blocchi condivisi vengono mantenuti durante la lettura dei dati per evitare letture dirty.  
  
 La classe <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> viene utilizzata per avviare la transazione. Per utilizzare la transazione, i comandi vengono quindi eseguiti nella connessione che ha avviato la transazione. Quando la transazione è completata, è possibile eseguirne il rollback oppure il commit.  
  
## <a name="starting-a-transaction"></a>Avvio di una transazione  
 Per creare un'istanza di un oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction>, chiamare il metodo <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.BeginTransaction%2A> dell'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>. Nell'esempio seguente viene illustrato come creare un'istanza dell'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction>:  
  
```  
Dim objTransaction As AdomdTransaction = objConnection.BeginTransaction()  
AdomdTransaction objTransaction = objConnection.BeginTransaction();  
```  
  
## <a name="rolling-back-a-transaction"></a>Esecuzione del rollback di una transazione  
 Per eseguire il rollback di una transazione esistente incompleta, chiamare il metodo <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction.Rollback%2A> dell'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction>. Se si chiama questo metodo su una transazione esistente completa, viene generata un'eccezione.  
  
## <a name="committing-a-transaction"></a>Esecuzione del commit di una transazione  
 Dopo avere chiamato il metodo <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.BeginTransaction%2A> per avviare una transazione, è possibile completarla tramite una chiamata al metodo <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction.Commit%2A> dell'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction>. Se si chiama questo metodo su una transazione esistente completa, viene generata un'eccezione.  
  
## <a name="see-also"></a>Vedere anche  
 [Per stabilire le connessioni in ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/connections-in-adomd-net.md)   
 [Programmazione di client ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)  
  
  
