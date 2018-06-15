---
title: Funzionalità Server di ADOMD.NET | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: adomd
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 003e50efa8ed21720410830a3d02134df15c3c97
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34023778"
---
# <a name="adomdnet-server-functionality"></a>Funzionalità server di ADOMD.NET
  Tutti gli oggetti server ADOMD.NET forniscono l'accesso in sola lettura ai dati e i metadati presenti nel server. Per recuperare i dati e i metadati, viene utilizzato il modello a oggetti server di ADOMD.NET poiché il modello a oggetti server non supporta i set di righe dello schema.  
  
 Gli oggetti server ADOMD.NET, è possibile creare una funzione definita dall'utente (UDF) o una stored procedure per [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Tali metodi in-process vengono chiamati tramite istruzioni di query create in linguaggi diversi, ad esempio MDX (Multidimensional Expressions), DMX (Data Mining Extensions) o SQL. Tali metodi forniscono inoltre funzionalità aggiunte senza le latenze associate alle comunicazioni della rete.  
  
> [!NOTE]  
>  L'oggetto <xref:Microsoft.AnalysisServices.AdomdServer.AdomdCommand> supporta solo DMX.  
  
## <a name="what-is-a-udf"></a>Funzioni definite dall'utente  
 Oggetto *funzione definita dall'utente* è un metodo che presenta le caratteristiche seguenti:  
  
-   Possibilità di essere chiamata nel contesto di una query.  
  
-   Possibilità di accettare un numero qualsiasi di parametri.  
  
-   Possibilità di restituire diversi tipi di dati.  
  
 Nell'esempio seguente viene utilizzata la funzione definita dall'utente fittizia `FinalSalesNumber`:  
  
```  
SELECT SalesPerson.Name ON ROWS,  
       FinalSalesNumber() ON COLUMNS  
FROM SalesModel  
```  
  
## <a name="what-is-a-stored-procedure"></a>Stored procedure  
 Oggetto *stored procedure di* è un metodo che presenta le caratteristiche seguenti:  
  
-   Si chiama una stored procedure nel proprio con MDX [CHIAMARE](../../mdx/mdx-data-manipulation-call.md) istruzione.  
  
-   Possibilità di accettare un numero qualsiasi di parametri.  
  
-   Una stored procedure può restituire un set di dati, un **IDataReader**, o un risultato vuoto.  
  
 Nell'esempio seguente viene utilizzata la stored procedure fittizia `FinalSalesNumbers`:  
  
```  
CALL FinalSalesNumbers()  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Programmazione di server ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-server/adomd-net-server-programming.md)  
  
  
