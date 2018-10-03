---
title: Esecuzione di transazioni in ADOMD.NET | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- transactions [ADOMD.NET]
- ADOMD.NET, transactions
- AdomdTransaction object
ms.assetid: 7978c28b-c255-43c0-ad05-f38604d4d8fe
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: aa3fd6ad27ced739c6d8ebd5d2fb2ad00bd6f707
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48169751"
---
# <a name="performing-transactions-in-adomdnet"></a>Esecuzione di transazioni in ADOMD.NET
  In ADOMD.NET utilizzare l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> per gestire il contesto di transazione per un oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> specifico. Questa funzionalità consente di eseguire numerosi comandi all'interno dello stesso contesto. Ogni comando leggerà gli stessi dati senza modificarli tra ogni esecuzione dei comandi.  
  
> [!NOTE]  
>  La classe <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> costituisce l'implementazione dell'interfaccia `System.Data.IDbTransaction`, parte della libreria di classi .NET Framework [!INCLUDE[msCoName](../../includes/msconame-md.md)], ed è implementata da tutti i provider di dati .NET Framework che supportano transazioni.  
  
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
 [Per stabilire le connessioni in ADOMD.NET](connections-in-adomd-net.md)   
 [Programmazione di client ADOMD.NET](adomd-net-client-programming.md)  
  
  
