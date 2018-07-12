---
title: SQLRowCount | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLRowCount function
ms.assetid: 967ed3d4-3d31-4485-ac92-027076ebc829
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2b1fc405b091f29c4d2660fc554fbbad47a7fdec
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37431860"
---
# <a name="sqlrowcount"></a>SQLRowCount
  Quando vengono associate matrici di valori di parametro per l'esecuzione di istruzione, `SQLRowCount` restituisce SQL_ERROR se qualsiasi riga di valori di parametro genera una condizione di errore nell'esecuzione dell'istruzione. Tramite l'argomento *RowCountPtr* della funzione non viene restituito alcun valore.  
  
 L'applicazione può sfruttare l'attributo di istruzione SQL_ATTR_PARAMS_PROCESSED_PTR per acquisire il numero di parametri elaborati prima del verificarsi dell'errore.  
  
 L'applicazione può inoltre utilizzare una matrice di valori di stato, associata tramite l'attributo di istruzione SQL_ATTR_PARAM_STATUS_PTR, per acquisire gli offset della matrice di righe di parametri con errori. L'applicazione può attraversare la matrice di stati per determinare il numero effettivo di righe elaborate.  
  
 Quando un [!INCLUDE[tsql](../../includes/tsql-md.md)] viene eseguita un'istruzione INSERT, UPDATE, DELETE o MERGE con una clausola OUTPUT, SQLRowCount non restituirà il numero di righe interessate fino a quando non sono state utilizzate tutte le righe nel set di risultati generato dalla clausola OUTPUT. Per utilizzare queste righe, chiamare SQLFetch o SQLFetchScroll. SQLResultCols restituiranno -1 finché tutte le righe di risultati sono state utilizzate. Dopo aver SQLFetch o SQLFetchScroll restituisce SQL_NO_DATA, l'applicazione deve chiamare SQLRowCount per determinare il numero di righe interessate prima di chiamare SQLMoreResults per passare al risultato successivo.  
  
## <a name="see-also"></a>Vedere anche  
 [SQLRowCount-funzione](http://go.microsoft.com/fwlink/?LinkId=59367)   
 [Dettagli di implementazione dell'API ODBC](odbc-api-implementation-details.md)  
  
  
