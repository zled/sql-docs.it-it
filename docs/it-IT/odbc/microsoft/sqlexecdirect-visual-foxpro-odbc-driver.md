---
title: SQLExecDirect (Driver ODBC di Visual FoxPro) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLExecDirect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5004060f-8510-4018-87a4-d41789e69d3e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b2089fb2289110ba175e4446f372c8a968b82a2e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlexecdirect-visual-foxpro-odbc-driver"></a>SQLExecDirect (Driver ODBC di Visual FoxPro)
> [!NOTE]  
>  In questo argomento contiene informazioni specifiche del Driver ODBC Visual FoxPro. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Supporto: completo  
  
 Conformità di API ODBC: Il livello di base  
  
 Esegue un nuovo [istruzione SQL preparabile](../../odbc/microsoft/visual-foxpro-terminology.md). Il Driver ODBC di Visual FoxPro utilizza i valori correnti delle variabili di marcatore di parametro, se sono presenti parametri nell'istruzione.  
  
 Per creare un comando batch per inviare più di un'istruzione SQL in un momento, utilizzare un punto e virgola (;) per separare ogni istruzione SQL del batch.  
  
 La tabella, vista o i nomi dei campi contengono spazi, racchiudere i nomi di backup offerta contrassegni. Se ad esempio, il database contiene una tabella denominata tabella personale e il campo campo, racchiudere ogni elemento dell'identificatore come indicato di seguito:  
  
```  
SELECT `My Table`.`Field1`, `My Table`.`Field2` FROM `My Table`  
```  
  
 Per ulteriori informazioni, vedere [SQLExecDirect](../../odbc/reference/syntax/sqlexecdirect-function.md) nel *riferimento per programmatori ODBC*.
