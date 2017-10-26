---
title: SQLSpecialColumns (Driver ODBC di Visual FoxPro) | Documenti Microsoft
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
- SQLSpecialColumns function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: b72a978d-6a60-475a-b7d9-c424d77bbe30
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3128dca9f473008b5e5fcae234fd9ba119911e81
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlspecialcolumns-visual-foxpro-odbc-driver"></a>SQLSpecialColumns (Driver ODBC di Visual FoxPro)
> [!NOTE]  
>  In questo argomento contiene informazioni specifiche del Driver ODBC Visual FoxPro. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Supporto: completo  
  
 Conformità di API ODBC: Livello 1  
  
 Recupera il set di colonne ottimale che identifica in modo univoco una riga nella tabella.  
  
 Il Driver ODBC di Visual FoxPro restituisce le colonne che costituiscono la chiave primaria nella tabella FoxPro. (Vedere [SQLPrimaryKeys](../../odbc/microsoft/sqlprimarykeys-visual-foxpro-odbc-driver.md).) Se chiamata con *fColType* impostato su SQL_ROWVER, viene restituita alcuna colonna. **SQLSpecialColumns** funziona solo per le origini dati che sono [database](../../odbc/microsoft/visual-foxpro-terminology.md).  
  
 Per ulteriori informazioni, vedere [SQLSpecialColumns](../../odbc/reference/syntax/sqlspecialcolumns-function.md) nel *riferimento per programmatori ODBC*.

