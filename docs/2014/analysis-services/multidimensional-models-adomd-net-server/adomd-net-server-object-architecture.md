---
title: Architettura degli oggetti Server ADOMD.NET | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ADOMD.NET, object model
- object model [ADOMD.NET]
ms.assetid: bdc81de9-b390-4654-b62a-cd6c0c9ca10d
caps.latest.revision: 16
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f18dd57b9232a9ef9e3405ccc77b5db1bb8a1c82
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37237721"
---
# <a name="adomdnet-server-object-architecture"></a>Architettura degli oggetti server in ADOMD.NET
  Gli oggetti server ADOMD.NET sono oggetti helper che possono essere utilizzati per creare funzioni definite dall'utente (UDF) o stored procedure nel [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
> [!NOTE]  
>  Per utilizzare lo spazio dei nomi `Microsoft.AnalysisServices.AdomdServer` e tali oggetti, è necessario aggiungere un riferimento a msmgdsrv.dll nel progetto di una funzione definita dall'utente o di una stored procedure.  
  
 ![Mostra le relazioni tra oggetti nel Server di ADOMD.NET](../../../2014/analysis-services/dev-guide/media/adomdnetserverobjectmodel.gif "Mostra le relazioni tra oggetti nel Server di ADOMD.NET")  
Modello a oggetti ADOMD.NET  
  
 L'interazione con la gerarchia di oggetti ADOMD.NET viene avviata in genere con uno o più oggetti del livello più alto della gerarchia, come descritto nella tabella seguente.  
  
|Per|Oggetto da utilizzare|  
|--------|---------------------|  
|Espressioni MDX (Multidimensional Expression)|<xref:Microsoft.AnalysisServices.AdomdServer.Expression><br /> L'oggetto <xref:Microsoft.AnalysisServices.AdomdServer.Expression> fornisce una modalità per eseguire un'espressione MDX e valutare tale espressione in base a una tupla specificata.|  
|Supporto per l'esecuzione di funzioni MDX senza creare l'istruzione MDX completa|<xref:Microsoft.AnalysisServices.AdomdServer.MDX><br /> L'oggetto <xref:Microsoft.AnalysisServices.AdomdServer.MDX> è conveniente per la chiamata a funzioni MDX predefinite senza utilizzare l'oggetto <xref:Microsoft.AnalysisServices.AdomdServer.Expression>. Funzioni aggiuntive per l'oggetto <xref:Microsoft.AnalysisServices.AdomdServer.MDX> dovrebbero essere disponibili nelle versioni successive.|  
|Rappresentazione del contesto di esecuzione corrente per la funzione definita dall'utente|<xref:Microsoft.AnalysisServices.AdomdServer.Context><br /> L'oggetto <xref:Microsoft.AnalysisServices.AdomdServer.Context> espone informazioni, ad esempio il cubo corrente o il modello di data mining, e le varie raccolte di metadati. Uno degli utilizzi principali dell'oggetto <xref:Microsoft.AnalysisServices.AdomdServer.Context> è rappresentato dalla proprietà <xref:Microsoft.AnalysisServices.AdomdServer.Hierarchy.CurrentMember%2A> dell'oggetto <xref:Microsoft.AnalysisServices.AdomdServer.Hierarchy>. Tale utilizzo principale consente all'autore della funzione definita dall'utente o della stored procedure di prendere decisioni in base al membro di una dimensione specifica in cui si trova la query.|  
|Creazione di set e di tuple|<xref:Microsoft.AnalysisServices.AdomdServer.SetBuilder>, <xref:Microsoft.AnalysisServices.AdomdServer.TupleBuilder><br /> L'oggetto <xref:Microsoft.AnalysisServices.AdomdServer.SetBuilder> fornisce una modalità per creare set invariabili, mentre l'oggetto <xref:Microsoft.AnalysisServices.AdomdServer.TupleBuilder> fornisce una modalità per creare tuple invariabili.|  
|Supporto della conversione implicita ed esecuzione del cast tra i sei tipi di base del linguaggio MDX|<xref:Microsoft.AnalysisServices.AdomdServer.MDXValue><br /> L'oggetto <xref:Microsoft.AnalysisServices.AdomdServer.MDXValue> fornisce la conversione implicita e il cast tra i tipi seguenti:<br /><br /> -   <xref:Microsoft.AnalysisServices.AdomdServer.Hierarchy><br />-   <xref:Microsoft.AnalysisServices.AdomdServer.Level><br />-   <xref:Microsoft.AnalysisServices.AdomdServer.Member><br />-   <xref:Microsoft.AnalysisServices.AdomdServer.Tuple><br />-   <xref:Microsoft.AnalysisServices.AdomdServer.Set><br />-Scalari, o tipi di valore|  
  
## <a name="see-also"></a>Vedere anche  
 [Programmazione di server ADOMD.NET](../multidimensional-models-adomd-net-server/adomd-net-server-programming.md)  
  
  
