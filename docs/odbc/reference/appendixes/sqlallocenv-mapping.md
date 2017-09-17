---
title: Mapping SQLAllocEnv | Documenti Microsoft
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
- SQLAllocEnv function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLAllocEnv
ms.assetid: 4bb51845-ee91-4b97-9dd4-2fab977f2aec
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 66261c8fd8236a4abc35ac70e29f63b49f646daf
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlallocenv-mapping"></a>Mapping di SQLAllocEnv
Quando un'applicazione chiama **SQLAllocEnv** tramite un'applicazione ODBC 3*x* driver, la chiamata a **SQLAllocEnv**(*phenv*) viene eseguito il mapping a **SQLAllocHandle** come indicato di seguito:  
  
1.  Gestione Driver alloca un handle di ambiente e lo restituisce all'applicazione. Le chiamate di gestione Driver **SQLSetEnvAttr** per impostare l'attributo di ambiente SQL_ATTR_ODBC_VERSION SQL_OV_ODBC2.  
  
2.  Quando l'applicazione consente di stabilire la prima connessione a un driver, Driver Manager chiama  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, OutputHandlePtr)  
    ```  
  
     nel driver con *OutputHandlePtr* impostato su *phenv*.
