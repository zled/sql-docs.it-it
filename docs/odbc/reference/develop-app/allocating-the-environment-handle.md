---
title: Allocare l'Handle di ambiente | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC drivers [ODBC], environment handles
- allocating environment handles [ODBC]
- connecting to driver [ODBC], environment handles
- environment handles [ODBC]
- data sources [ODBC], environment handles
- connecting to data source [ODBC], environment handles
- handles [ODBC], environment
ms.assetid: 77b5d1d6-7eb7-428d-bf75-a5c5a325d25c
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c0bbe08b13b45b47fecda5143ca419c31dfe82d5
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="allocating-the-environment-handle"></a>Allocare l'Handle di ambiente
La prima attività per qualsiasi applicazione ODBC consiste nel caricare il Driver Manager; Questa procedura è dipendente dal sistema operativo. Ad esempio, in un computer che esegue Microsoft Windows® 95/98, Windows NT Workstation/Windows 2000 Professional o Microsoft® Windows NT® Server e Windows 2000 Server, l'applicazione sia collegata alla libreria di gestione Driver o chiamate  **LoadLibrary** per caricare la DLL di gestione Driver.  
  
 L'attività successiva, che deve essere eseguita prima di un'applicazione può chiamare qualsiasi altra funzione ODBC, è per inizializzare l'ambiente ODBC e allocare un handle di ambiente, come segue:  
  
1.  L'applicazione dichiara una variabile di tipo SQLHENV. Chiama quindi **SQLAllocHandle** e passa l'indirizzo di questa variabile e l'opzione impostato su SQL_HANDLE_ENV. Esempio:  
  
    ```  
    SQLHENV henv1;  
  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv1);  
    ```  
  
2.  Gestione Driver alloca una struttura in cui archiviare informazioni sull'ambiente e restituisce l'handle di ambiente nella variabile.  
  
 Gestione Driver non chiama **SQLAllocHandle** nel driver questo tempo perché non è a conoscenza driver da chiamare. Un ritardo che termina la chiamata **SQLAllocHandle** nel driver fino a quando l'applicazione chiama una funzione per la connessione a un'origine dati. Per ulteriori informazioni, vedere [di gestione Driver ruolo nel processo di connessione](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md), più avanti in questa sezione.  
  
 Quando l'applicazione ha completato l'utilizzo di ODBC, consente di liberare l'handle di ambiente con **SQLFreeHandle**. Dopo aver liberato l'ambiente, è un'applicazione di un errore di programmazione da utilizzare l'handle dell'ambiente in una chiamata a una funzione ODBC; Questa operazione ha conseguenze irreversibili probabilmente ma non definiti.  
  
 Quando **SQLFreeHandle** viene chiamato, le versioni di driver, la struttura utilizzata per archiviare le informazioni sull'ambiente. Si noti che **SQLFreeHandle** non può essere chiamato per un handle di ambiente fino a dopo essere stati sbloccati tutti gli handle di connessione su tale handle di ambiente.  
  
 Per ulteriori informazioni sull'handle di ambiente, vedere [ambiente gestisce](../../../odbc/reference/develop-app/environment-handles.md).
