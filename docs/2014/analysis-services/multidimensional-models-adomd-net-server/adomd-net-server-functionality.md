---
title: Funzionalità Server di ADOMD.NET | Microsoft Docs
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b8463ec4804e1ba7ada8ea4e781a34495f5a0d94
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37269917"
---
# <a name="adomdnet-server-functionality"></a>Funzionalità server di ADOMD.NET
  Tutti gli oggetti server ADOMD.NET forniscono l'accesso in sola lettura ai dati e i metadati presenti nel server. Per recuperare i dati e i metadati, viene utilizzato il modello a oggetti server di ADOMD.NET poiché il modello a oggetti server non supporta i set di righe dello schema.  
  
 Gli oggetti server ADOMD.NET, è possibile creare una funzione definita dall'utente (UDF) o una stored procedure [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Tali metodi in-process vengono chiamati tramite istruzioni di query create in linguaggi diversi, ad esempio MDX (Multidimensional Expressions), DMX (Data Mining Extensions) o SQL. Tali metodi forniscono inoltre funzionalità aggiunte senza le latenze associate alle comunicazioni della rete.  
  
> [!NOTE]  
>  L'oggetto <xref:Microsoft.AnalysisServices.AdomdServer.AdomdCommand> supporta solo DMX.  
  
## <a name="what-is-a-udf"></a>Funzioni definite dall'utente  
 Oggetto *UDF* è un metodo che presenta le caratteristiche seguenti:  
  
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
  
-   Si chiama una stored procedure in un proprio con MDX [CHIAMARE](/sql/mdx/mdx-data-manipulation-call) istruzione.  
  
-   Possibilità di accettare un numero qualsiasi di parametri.  
  
-   Possibilità di restituire un set di dati, un oggetto `IDataReader` oppure un risultato vuoto.  
  
 Nell'esempio seguente viene utilizzata la stored procedure fittizia `FinalSalesNumbers`:  
  
```  
CALL FinalSalesNumbers()  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Programmazione di server ADOMD.NET](adomd-net-server-programming.md)  
  
  
