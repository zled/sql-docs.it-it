---
title: L'esecuzione di istruzioni (ODBC) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
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
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: ed95045df3246098dd98048ad527c086765c7be2
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2018
ms.locfileid: "35703532"
---
# <a name="executing-statements-odbc"></a>Esecuzione di istruzioni (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] driver ODBC Native Client offre diversi modi per eseguire istruzioni SQL in un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database:  
  
-   Esecuzione diretta  
  
-   Esecuzione preparata  
  
 Esecuzione diretta implica la compilazione di una stringa di caratteri contenente un [!INCLUDE[tsql](../../../includes/tsql-md.md)] istruzione e inviarlo per l'esecuzione mediante il **SQLExecDirect** (funzione). L'esecuzione preparata implica la compilazione di una stringa di caratteri contenente un'istruzione [!INCLUDE[tsql](../../../includes/tsql-md.md)] e la successiva esecuzione di questa in due fasi. La prima fase viene utilizzata la [funzione SQLPrepare](http://go.microsoft.com/fwlink/?LinkId=59360) funzione per analizzare e compilare il piano di esecuzione per l'istruzione nel [!INCLUDE[ssDE](../../../includes/ssde-md.md)]. Nella seconda fase viene utilizzata la **SQLExecute** funzione da eseguire il piano di esecuzione preparata in precedenza. con conseguente risparmio dell'overhead correlato all'analisi e alla compilazione in ogni esecuzione. L'esecuzione preparata viene generalmente utilizzata dalle applicazioni per eseguire ripetutamente la stessa istruzione SQL con parametri.  
  
 Sia nel caso dell'esecuzione diretta che in quello dell'esecuzione preparata è possibile eseguire una singola istruzione [!INCLUDE[tsql](../../../includes/tsql-md.md)] o un batch di istruzioni SQL oppure è possibile chiamare una stored procedure.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
-   [Esecuzione diretta](../../../relational-databases/native-client-odbc-queries/executing-statements/direct-execution.md)  
  
-   [Esecuzione preparata](../../../relational-databases/native-client-odbc-queries/executing-statements/prepared-execution.md)  
  
-   [Procedure](../../../relational-databases/native-client-odbc-queries/executing-statements/procedures.md)  
  
-   [Batch di istruzioni](../../../relational-databases/native-client-odbc-queries/executing-statements/batches-of-statements.md)  
  
-   [Effetti delle opzioni ISO](../../../relational-databases/native-client-odbc-queries/executing-statements/effects-of-iso-options.md)  
  
## <a name="see-also"></a>Vedere anche  
 [L'esecuzione di query &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
