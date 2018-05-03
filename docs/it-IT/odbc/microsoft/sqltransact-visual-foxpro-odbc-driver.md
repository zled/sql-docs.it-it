---
title: SQLTransact (Driver ODBC di Visual FoxPro) | Documenti Microsoft
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
- SQLTransact function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 92cf86c0-f7a8-44d7-b59f-a1342677440b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bed779e7c6d0e49674dcf2753ccd64c7f4624347
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqltransact-visual-foxpro-odbc-driver"></a>SQLTransact (Driver ODBC di Visual FoxPro)
> [!NOTE]  
>  In questo argomento contiene informazioni specifiche del Driver ODBC Visual FoxPro. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Supporto: completo  
  
 Conformità di API ODBC: Il livello di base  
  
 Richiede un'operazione di commit o rollback per tutte le operazioni attive in tutti gli handle di istruzione (*hstmt*s) associati a una connessione o per tutte le connessioni associate all'handle di ambiente, *henv*. **SQLTransact** funziona solo per le origini dati che vengono [database](../../odbc/microsoft/visual-foxpro-terminology.md).  
  
 Se un'operazione di commit ha esito negativo quando è in modalità manuale, la transazione rimane attiva. è possibile scegliere di eseguire il rollback della transazione o ripetere l'operazione di commit. Se un'operazione di commit ha esito negativo quando è in modalità automatica delle transazioni, il rollback della transazione. la transazione non può essere inattiva.  
  
 Per ulteriori informazioni, vedere [SQLTransact](../../odbc/reference/syntax/sqltransact-function.md) nel *riferimento per programmatori ODBC*.
