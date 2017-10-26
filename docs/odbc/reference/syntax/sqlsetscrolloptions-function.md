---
title: Funzione SQLSetScrollOptions | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLSetScrollOptions
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetScrollOptions
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC]
ms.assetid: 2a825ba7-7942-4c23-bcdb-c80dc12f8c86
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 432fbea7fb864b0a42a000eb46df6c2642b7c28b
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetscrolloptions-function"></a>SQLSetScrollOptions (funzione)
**Conformità**  
 Introdotta: versione ODBC standard 1.0 conformità: deprecato  
  
 **Riepilogo**  
 In ODBC 3*x*, la funzione ODBC 2.0 **SQLSetScrollOptions** è stato sostituito dalle chiamate a **SQLGetInfo** e **SQLSetStmtAttr**.  
  
> [!NOTE]  
>  Per ulteriori informazioni su cosa the Driver Manager esegue il mapping di questa funzione per quando un ODBC 2*x* applicazione funziona con un'applicazione ODBC 3*x* driver, vedere [Mapping funzioni deprecate](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)nell'appendice g: Driver le linee guida per la compatibilità con le versioni precedenti.  
  
> [!NOTE]  
>  Quando esegue il mapping di gestione Driver **SQLSetScrollOptions** per un'applicazione che utilizza un'applicazione ODBC 3*x* driver che non supporta **SQLSetScrollOptions**, il Driver Manager imposta l'opzione dell'istruzione SQL_ROWSET_SIZE, non l'attributo di istruzione SQL_ATTR_ROW_ARRAY_SIZE sul *RowsetSize* argomento **SQLSetScrollOption**. Di conseguenza, **SQLSetScrollOptions** non può essere utilizzato da un'applicazione durante il recupero di più righe da una chiamata a **SQLFetch** o **SQLFetchScroll**. E può essere utilizzato solo quando più recupero righe da una chiamata a **SQLExtendedFetch**.  
  
## <a name="remarks"></a>Osservazioni  
 Se l'applicazione verrà eseguita in un sistema operativo a 64 bit, vedere [informazioni ODBC a 64 Bit](../../../odbc/reference/odbc-64-bit-information.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)

