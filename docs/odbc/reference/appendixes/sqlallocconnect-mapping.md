---
title: Mapping SQLAllocConnect | Documenti Microsoft
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
- SQLAllocConnect function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLAllocConnect
ms.assetid: ac89dd1f-c565-47cc-8fa3-6fa5f80b5d63
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 09fc3b99f519df49202f8834ca16f585cae903a1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlallocconnect-mapping"></a>Mapping di SQLAllocConnect
Quando un'applicazione chiama **SQLAllocConnect** tramite un'applicazione ODBC 3. *x* driver, la chiamata a **SQLAllocConnect**(*henv*, *phdbc*) viene eseguito il mapping a **SQLAllocHandle** come indicato di seguito:  
  
1.  Gestione Driver alloca una connessione e lo restituisce all'applicazione.  
  
2.  Quando l'applicazione stabilisce una connessione, gestione Driver chiama  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_DBC, InputHandle, OutputHandlePtr)  
    ```  
  
     nel driver con *InputHandle* impostato su *henv*, e *OutputHandlePtr* impostato su *phdbc*.
