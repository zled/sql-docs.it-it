---
title: SQLPrepare (Driver ODBC di Visual FoxPro) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQLPrepare function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 0c4cb5a4-9729-4b2e-a0c6-52027b92e8fc
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b810cd3adff4e5903a3ce515eb501b4a8f202c14
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
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
