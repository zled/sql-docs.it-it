---
title: SQLGetCursorName | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLGetCursorName function
ms.assetid: 3a427a23-28ef-49aa-b9ec-6cab0914bdf3
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 38152648f5ded4098ccceb969828d7be005c90cb
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2018
ms.locfileid: "35702492"
---
# <a name="sqlgetcursorname"></a>SQLGetCursorName
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Se l'applicazione non specifica un nome di cursore, la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client ne genera uno al momento della generazione del cursore. L'applicazione può utilizzare **SQLGetCursorName** per recuperare il nome del cursore definito dal driver per le istruzioni UPDATE e DELETE posizionata. L'applicazione non è necessario chiamare **SQLSetCursorName** per poter sfruttare posizionato le istruzioni di manipolazione dei dati.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione SQLGetCursorName](http://go.microsoft.com/fwlink/?LinkId=59349)   
 [Dettagli di implementazione dell'API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
