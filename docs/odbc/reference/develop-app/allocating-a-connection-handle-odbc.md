---
title: Allocare un Handle di connessione ODBC | Documenti Microsoft
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
- allocating connection handles [ODBC]
- data sources [ODBC], connection handles
- connecting to data source [ODBC], connection handles
- ODBC drivers [ODBC], connection handles
- connecting to driver [ODBC], connection handles
- connection handles [ODBC]
- handles [ODBC], connection
ms.assetid: c99a8159-7693-4f97-8dcf-401336550e77
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 33aad1fdd9b707847d7a122d56ba5207e0074f01
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="allocating-a-connection-handle-odbc"></a>Allocare un Handle di connessione ODBC
Prima che l'applicazione può connettersi a un'origine dati o il driver, è necessario allocare un handle di connessione, come indicato di seguito:  
  
1.  L'applicazione dichiara una variabile di tipo SQLHDBC. Chiama quindi **SQLAllocHandle** e passa l'indirizzo di questa variabile, l'handle dell'ambiente in cui si desidera allocare la connessione e l'opzione impostato su SQL_HANDLE_DBC. Esempio:  
  
    ```  
    SQLHDBC hdbc1;  
  
    SQLAllocHandle(SQL_HANDLE_DBC, henv1, &hdbc1);  
    ```  
  
2.  Gestione Driver alloca una struttura in cui archiviare informazioni sull'istruzione e restituisce l'handle di connessione nella variabile.  
  
 Gestione Driver non chiama **SQLAllocHandle** nel driver questo tempo perché non è a conoscenza driver da chiamare. Un ritardo che termina la chiamata **SQLAllocHandle** nel driver fino a quando l'applicazione chiama una funzione per la connessione a un'origine dati. Per ulteriori informazioni, vedere [di gestione Driver ruolo nel processo di connessione](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md), più avanti in questa sezione.  
  
 È importante allocare un handle di connessione non è lo stesso come caricare un driver. Il driver non è caricato finché non viene chiamata una funzione di connessione. Dopo aver allocato un handle di connessione e prima della connessione del driver o l'origine dati, le funzioni sole l'applicazione può chiamare con l'handle di connessione sono pertanto **SQLSetConnectAttr**, **SQLGetConnectAttr**, o **SQLGetInfo** con l'opzione SQL_ODBC_VER. Chiamare altre funzioni con l'handle di connessione, quali **SQLEndTran**, restituisce SQLSTATE 08003 (connessione non aperta). Per informazioni dettagliate, vedere [tabelle di transizione dello stato di appendice b: ODBC](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Per ulteriori informazioni sugli handle di connessione, vedere [handle di connessione](../../../odbc/reference/develop-app/connection-handles.md).
