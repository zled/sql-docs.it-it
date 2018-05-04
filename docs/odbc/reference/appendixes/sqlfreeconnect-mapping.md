---
title: Mapping SQLFreeConnect | Documenti Microsoft
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
- mapping deprecated functions [ODBC], SQLFreeConnect
- SQLFreeConnect function [ODBC], mapping
ms.assetid: 8a844538-93c0-4709-bab6-35c45e771d80
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 62ece3d41b67b6978d7a99603434c74aec1b9a0a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlfreeconnect-mapping"></a>Mapping di SQLFreeConnect
Quando un'applicazione chiama **SQLFreeConnect** tramite un'applicazione ODBC 3*x* driver, la chiamata a  
  
```  
SQLFreeConnect(hdbc)   
```  
  
 è stato eseguito il mapping a  
  
```  
SQLFreeHandle(SQL_HANDLE_DBC,Handle)  
```  
  
 con il *gestire* argomento impostato sul valore *hdbc*.
