---
title: Funzione SQLTransact | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLTransact
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLTransact
helpviewer_keywords:
- SQLTransact function [ODBC]
ms.assetid: 496249e0-8eff-4c60-8358-5543bc3ead9c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b76b7a550211522c2b2100776b88f311abb2b932
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47646859"
---
# <a name="sqltransact-function"></a>Funzione SQLTransact
**Conformità**  
 Versione introdotta: Conformità agli standard 1.0 di ODBC: deprecato  
  
 **Riepilogo**  
 In ODBC 3. *x*, l'API ODBC 2 *. x* funzione **SQLTransact** è stato sostituito da **SQLEndTran**. Per altre informazioni, vedere [SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).  
  
> [!NOTE]  
>  L'attributo SQL_ASYNC_DBC_FUNCTION_ENABLE, che è stata introdotta in ODBC 3.8, non è supportato dal **SQLTransact**. Applicazioni con un'operazione asincrona su un handle di connessione devono utilizzare **SQLEndTran**.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)
