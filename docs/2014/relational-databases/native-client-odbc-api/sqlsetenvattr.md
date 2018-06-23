---
title: SQLSetEnvAttr | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLSetEnvAttr function
ms.assetid: d4114571-feca-4330-b2e4-7bfd1050b812
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 663d274b13a8cc5ac8ac53a2d8f9da4f925c7d55
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36158218"
---
# <a name="sqlsetenvattr"></a>SQLSetEnvAttr
  Il [di riferimento per programmatori ODBC](http://go.microsoft.com/fwlink/?LinkId=45250) definisce il driver ODBC devono interpretare il **SQLSetEnvAttr** attributo specifiche da applicazioni scritte per ODBC 2. *x* o ODBC 3. *x* API. Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client è conforme a tali regole.  
  
 Uno degli attributi controllati da **SQLSetEnvAttr** indica se il pool di connessioni verrà da utilizzare. Se il pool di connessioni viene utilizzato con il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client, il *DriverCompletion* parametro deve essere impostato su SQL_DRIVER_NOPROMPT quando ci si connette tramite [SQLDriverConnect](sqldriverconnect.md) o **SQLConnect**.  
  
## <a name="see-also"></a>Vedere anche  
 [SQLSetEnvAttr-funzione](http://go.microsoft.com/fwlink/?LinkId=59369)   
 [Dettagli di implementazione dell'API ODBC](odbc-api-implementation-details.md)  
  
  