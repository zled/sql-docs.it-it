---
title: Allocare un Handle di istruzione ODBC | Documenti Microsoft
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
ms.topic: article
helpviewer_keywords:
- SQL statements [ODBC], statement handles
- statement handles [ODBC]
- allocating statement handles [ODBC]
- handles [ODBC], statement
ms.assetid: 4ce3b446-34ab-46dc-96e5-f40ec95c267e
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5c05efc512fefac98743b866b7ab930928f17af0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="allocating-a-statement-handle-odbc"></a>Allocare un Handle di istruzione ODBC
Prima che l'applicazione può eseguire un'istruzione, è necessario allocare un handle di istruzione come indicato di seguito:  
  
1.  L'applicazione dichiara una variabile di tipo HSTMT. Chiama quindi **SQLAllocHandle** e passa l'indirizzo di questa variabile, l'handle della connessione in cui si desidera allocare l'istruzione e l'opzione impostato su SQL_HANDLE_STMT. Esempio:  
  
    ```  
    SQLHSTMT hstmt1;  
  
    SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
    ```  
  
2.  Gestione Driver alloca una struttura in cui archiviare informazioni di istruzione e chiama **SQLAllocHandle** nel driver con l'opzione impostato su SQL_HANDLE_STMT.  
  
3.  Il driver alloca la propria struttura in cui archiviare informazioni sull'istruzione e restituisce l'handle di istruzione di driver per la gestione del Driver.  
  
4.  Gestione Driver restituisce l'handle di istruzione di gestione Driver per l'applicazione nella variabile di applicazione.  
  
 L'handle di istruzione identifica quale istruzione da utilizzare durante la chiamata di funzioni ODBC. Per ulteriori informazioni sugli handle di istruzione, vedere [handle di istruzione](../../../odbc/reference/develop-app/statement-handles.md).
