---
title: L'esecuzione di istruzioni (ODBC) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, statements
- statements [ODBC]
- ODBC applications, statements
- statements [ODBC], executing
ms.assetid: 063fc40d-ff81-490d-9c9b-2faefb729f37
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ff5f9dcc3d8087418e3003dedc7f57e56840cba0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36157458"
---
# <a name="executing-statements-odbc"></a>Esecuzione di istruzioni (ODBC)
  Il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] driver ODBC Native Client offre diversi modi per eseguire istruzioni SQL in un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database:  
  
-   Esecuzione diretta  
  
-   Esecuzione preparata  
  
 Esecuzione diretta implica la compilazione di una stringa di caratteri contenente un [!INCLUDE[tsql](../../../includes/tsql-md.md)] istruzione e inviarlo per l'esecuzione mediante il **SQLExecDirect** (funzione). L'esecuzione preparata implica la compilazione di una stringa di caratteri contenente un'istruzione [!INCLUDE[tsql](../../../includes/tsql-md.md)] e la successiva esecuzione di questa in due fasi. La prima fase viene utilizzata la [funzione SQLPrepare](http://go.microsoft.com/fwlink/?LinkId=59360) funzione per analizzare e compilare il piano di esecuzione per l'istruzione nel [!INCLUDE[ssDE](../../../includes/ssde-md.md)]. Nella seconda fase viene utilizzata la **SQLExecute** funzione da eseguire il piano di esecuzione preparata in precedenza. con conseguente risparmio dell'overhead correlato all'analisi e alla compilazione in ogni esecuzione. L'esecuzione preparata viene generalmente utilizzata dalle applicazioni per eseguire ripetutamente la stessa istruzione SQL con parametri.  
  
 Sia nel caso dell'esecuzione diretta che in quello dell'esecuzione preparata è possibile eseguire una singola istruzione [!INCLUDE[tsql](../../../includes/tsql-md.md)] o un batch di istruzioni SQL oppure è possibile chiamare una stored procedure.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
-   [Esecuzione diretta](direct-execution.md)  
  
-   [Esecuzione preparata](prepared-execution.md)  
  
-   [Procedure](procedures.md)  
  
-   [Batch di istruzioni](batches-of-statements.md)  
  
-   [Effetti delle opzioni ISO](effects-of-iso-options.md)  
  
## <a name="see-also"></a>Vedere anche  
 [L'esecuzione di query &#40;ODBC&#41;](../executing-queries-odbc.md)  
  
  