---
title: "Funzionalità Server di ADOMD.NET | Documenti Microsoft"
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
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- functionality [ADOMD.NET]
- ADOMD.NET, functionality
ms.assetid: b74c6957-3f64-4e09-aa09-d06ee93f82fa
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 40d68e739a9628113b7adfeab5db2a6b1445981f
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

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
 [Programmazione di Server ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-server/adomd-net-server-programming.md)  
  
  

