---
title: Mapping di SQLAllocConnect | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLAllocConnect function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLAllocConnect
ms.assetid: ac89dd1f-c565-47cc-8fa3-6fa5f80b5d63
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bdb63e9610d00c0736f640b6f4c4d743f3335c7d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47606239"
---
# <a name="sqlallocconnect-mapping"></a>Mapping di SQLAllocConnect
Quando un'applicazione chiama **SQLAllocConnect** tramite un'applicazione ODBC 3. *x* driver, la chiamata a **SQLAllocConnect**(*henv*, *phdbc*) viene mappato a **SQLAllocHandle** come indicato di seguito:  
  
1.  Gestione Driver alloca una connessione e lo restituisce all'applicazione.  
  
2.  Quando l'applicazione stabilisce una connessione, viene chiamato gestione Driver  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_DBC, InputHandle, OutputHandlePtr)  
    ```  
  
     nel driver con *InputHandle* impostata su *henv*, e *OutputHandlePtr* impostata su *phdbc*.
