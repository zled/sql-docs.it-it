---
title: Funzionalità Server di ADOMD.NET | Documenti Microsoft
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
- functionality [ADOMD.NET]
- ADOMD.NET, functionality
ms.assetid: b74c6957-3f64-4e09-aa09-d06ee93f82fa
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 622a7c51bfd6c2a8a9defba70a412967a48dee50
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065247"
---
# <a name="adomdnet-server-functionality"></a>Funzionalità server di ADOMD.NET
  Tutti gli oggetti server ADOMD.NET forniscono l'accesso in sola lettura ai dati e i metadati presenti nel server. Per recuperare i dati e i metadati, viene utilizzato il modello a oggetti server di ADOMD.NET poiché il modello a oggetti server non supporta i set di righe dello schema.  
  
 Gli oggetti server ADOMD.NET, è possibile creare una funzione definita dall'utente (UDF) o una stored procedure per [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Tali metodi in-process vengono chiamati tramite istruzioni di query create in linguaggi diversi, ad esempio MDX (Multidimensional Expressions), DMX (Data Mining Extensions) o SQL. Tali metodi forniscono inoltre funzionalità aggiunte senza le latenze associate alle comunicazioni della rete.  
  
> [!NOTE]  
>  L'oggetto <xref:Microsoft.AnalysisServices.AdomdServer.AdomdCommand> supporta solo DMX.  
  
## <a name="what-is-a-udf"></a>Funzioni definite dall'utente  
 Un *definita dall'utente* è un metodo che presenta le caratteristiche seguenti:  
  
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
 Un *stored procedure di* è un metodo che presenta le caratteristiche seguenti:  
  
-   Si chiama una stored procedure nel proprio con MDX [CHIAMARE](/sql/mdx/mdx-data-manipulation-call) istruzione.  
  
-   Possibilità di accettare un numero qualsiasi di parametri.  
  
-   Possibilità di restituire un set di dati, un oggetto `IDataReader` oppure un risultato vuoto.  
  
 Nell'esempio seguente viene utilizzata la stored procedure fittizia `FinalSalesNumbers`:  
  
```  
CALL FinalSalesNumbers()  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Programmazione di server ADOMD.NET](adomd-net-server-programming.md)  
  
  
