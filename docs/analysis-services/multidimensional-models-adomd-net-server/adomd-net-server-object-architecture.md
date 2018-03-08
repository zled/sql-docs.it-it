---
title: Architettura degli oggetti Server ADOMD.NET | Documenti Microsoft
ms.custom: 
ms.date: 02/14/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- ADOMD.NET, object model
- object model [ADOMD.NET]
ms.assetid: bdc81de9-b390-4654-b62a-cd6c0c9ca10d
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8f0cae374f2670228bbced569d81e87b34a350d2
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="adomdnet-server-object-architecture"></a>Architettura degli oggetti server in ADOMD.NET
  Gli oggetti server ADOMD.NET sono oggetti helper che possono essere utilizzati per creare funzioni definite dall'utente (UDF) o stored procedure in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
> [!NOTE]  
>  Utilizzare il **AdomdServer** dello spazio dei nomi e questi oggetti, un riferimento a msmgdsrv.dll nel deve essere aggiunto al progetto definita dall'utente o stored procedure.  
  
 ![Mostra le relazioni tra oggetti server ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-server/media/adomdnetserverobjectmodel.gif "Mostra le relazioni tra oggetti server ADOMD.NET")  
Modello a oggetti ADOMD.NET  
  
 L'interazione con la gerarchia di oggetti ADOMD.NET viene avviata in genere con uno o più oggetti del livello più alto della gerarchia, come descritto nella tabella seguente.  
  
|Per|Oggetto da utilizzare|  
|--------|---------------------|  
|Espressioni MDX (Multidimensional Expression)|<xref:Microsoft.AnalysisServices.AdomdServer.Expression><br /> L'oggetto <xref:Microsoft.AnalysisServices.AdomdServer.Expression> fornisce una modalità per eseguire un'espressione MDX e valutare tale espressione in base a una tupla specificata.|  
|Supporto per l'esecuzione di funzioni MDX senza creare l'istruzione MDX completa|<xref:Microsoft.AnalysisServices.AdomdServer.MDX><br /> L'oggetto <xref:Microsoft.AnalysisServices.AdomdServer.MDX> è conveniente per la chiamata a funzioni MDX predefinite senza utilizzare l'oggetto <xref:Microsoft.AnalysisServices.AdomdServer.Expression>. Funzioni aggiuntive per l'oggetto <xref:Microsoft.AnalysisServices.AdomdServer.MDX> dovrebbero essere disponibili nelle versioni successive.|  
|Rappresentazione del contesto di esecuzione corrente per la funzione definita dall'utente|<xref:Microsoft.AnalysisServices.AdomdServer.Context><br /> L'oggetto <xref:Microsoft.AnalysisServices.AdomdServer.Context> espone informazioni, ad esempio il cubo corrente o il modello di data mining, e le varie raccolte di metadati. Uno degli utilizzi principali dell'oggetto <xref:Microsoft.AnalysisServices.AdomdServer.Context> è rappresentato dalla proprietà <xref:Microsoft.AnalysisServices.AdomdServer.Hierarchy.CurrentMember%2A> dell'oggetto <xref:Microsoft.AnalysisServices.AdomdServer.Hierarchy>. Tale utilizzo principale consente all'autore della funzione definita dall'utente o della stored procedure di prendere decisioni in base al membro di una dimensione specifica in cui si trova la query.|  
|Creazione di set e di tuple|<xref:Microsoft.AnalysisServices.AdomdServer.SetBuilder>, <xref:Microsoft.AnalysisServices.AdomdServer.TupleBuilder><br /> L'oggetto <xref:Microsoft.AnalysisServices.AdomdServer.SetBuilder> fornisce una modalità per creare set invariabili, mentre l'oggetto <xref:Microsoft.AnalysisServices.AdomdServer.TupleBuilder> fornisce una modalità per creare tuple invariabili.|  
|Supporto della conversione implicita ed esecuzione del cast tra i sei tipi di base del linguaggio MDX|<xref:Microsoft.AnalysisServices.AdomdServer.MDXValue><br /> L'oggetto <xref:Microsoft.AnalysisServices.AdomdServer.MDXValue> fornisce la conversione implicita e il cast tra i tipi seguenti:<br /><br /> <xref:Microsoft.AnalysisServices.AdomdServer.Hierarchy><br /><br /> <xref:Microsoft.AnalysisServices.AdomdServer.Level><br /><br /> <xref:Microsoft.AnalysisServices.AdomdServer.Member><br /><br /> <xref:Microsoft.AnalysisServices.AdomdServer.Tuple><br /><br /> <xref:Microsoft.AnalysisServices.AdomdServer.Set><br /><br /> Scalari o tipi di valori|  
  
## <a name="see-also"></a>Vedere anche  
 [Programmazione di server ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-server/adomd-net-server-programming.md)  
  
  
