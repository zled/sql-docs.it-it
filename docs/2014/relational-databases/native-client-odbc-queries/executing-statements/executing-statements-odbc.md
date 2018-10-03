---
title: L'esecuzione di istruzioni (ODBC) | Documenti di Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, statements
- statements [ODBC]
- ODBC applications, statements
- statements [ODBC], executing
ms.assetid: 063fc40d-ff81-490d-9c9b-2faefb729f37
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4d3d25e94926e3b87dab198c567c1f813732a2f9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48180271"
---
# <a name="executing-statements-odbc"></a>Esecuzione di istruzioni (ODBC)
  Il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] driver ODBC Native Client offre diversi modi per eseguire istruzioni SQL in un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database:  
  
-   Esecuzione diretta  
  
-   Esecuzione preparata  
  
 Esecuzione diretta implica la creazione di una stringa di caratteri contenente un' [!INCLUDE[tsql](../../../includes/tsql-md.md)] istruzione e inviarlo per l'esecuzione mediante il **SQLExecDirect** (funzione). L'esecuzione preparata implica la compilazione di una stringa di caratteri contenente un'istruzione [!INCLUDE[tsql](../../../includes/tsql-md.md)] e la successiva esecuzione di questa in due fasi. La prima fase viene utilizzata la [funzione SQLPrepare](http://go.microsoft.com/fwlink/?LinkId=59360) per analizzare e compilare il piano di esecuzione per l'istruzione nella funzione di [!INCLUDE[ssDE](../../../includes/ssde-md.md)]. La seconda fase viene utilizzata la **SQLExecute** funzione per eseguire il piano di esecuzione precedentemente preparato. con conseguente risparmio dell'overhead correlato all'analisi e alla compilazione in ogni esecuzione. L'esecuzione preparata viene generalmente utilizzata dalle applicazioni per eseguire ripetutamente la stessa istruzione SQL con parametri.  
  
 Sia nel caso dell'esecuzione diretta che in quello dell'esecuzione preparata è possibile eseguire una singola istruzione [!INCLUDE[tsql](../../../includes/tsql-md.md)] o un batch di istruzioni SQL oppure è possibile chiamare una stored procedure.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
-   [Esecuzione diretta](direct-execution.md)  
  
-   [Esecuzione preparata](prepared-execution.md)  
  
-   [Procedure](procedures.md)  
  
-   [Batch di istruzioni](batches-of-statements.md)  
  
-   [Effetti delle opzioni ISO](effects-of-iso-options.md)  
  
## <a name="see-also"></a>Vedere anche  
 [L'esecuzione di query &#40;ODBC&#41;](../executing-queries-odbc.md)  
  
  
