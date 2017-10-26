---
title: SQLPrepare (Driver ODBC di Visual FoxPro) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLPrepare function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 0c4cb5a4-9729-4b2e-a0c6-52027b92e8fc
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9ef6287177be3b52b80e0a2439d7d0686da180da
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlprepare-visual-foxpro-odbc-driver"></a>SQLPrepare (Driver ODBC di Visual FoxPro)
> [!NOTE]  
>  In questo argomento contiene informazioni specifiche del Driver ODBC Visual FoxPro. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Supporto: completo  
  
 Conformità di API ODBC: Il livello di base  
  
 Prepara un'istruzione SQL tramite la pianificazione come ottimizzare ed eseguire l'istruzione. L'istruzione SQL viene compilata per l'esecuzione da [SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md).  
  
 La tabella, vista o i nomi dei campi contengono spazi, racchiudere i nomi di backup offerta virgolette ('). Se ad esempio, il database contiene una tabella denominata tabella personale e il campo campo, racchiudere ogni elemento dell'identificatore come indicato di seguito:  
  
```  
SELECT * FROM `My Table`.`My Field`  
```  
  
 Per ulteriori informazioni, vedere [SQLPrepare](../../odbc/reference/syntax/sqlprepare-function.md) nel *riferimento per programmatori ODBC*.

