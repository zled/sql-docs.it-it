---
title: SQLSetScrollOptions (Driver ODBC di Visual FoxPro) | Documenti Microsoft
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
- SQLSetScrollOptions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 693e6e28-a845-41b1-9622-5058b0d87229
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 22b92ffb804ee7f325367c46a7d78b17c8604d94
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsetscrolloptions-visual-foxpro-odbc-driver"></a>SQLSetScrollOptions (Driver ODBC di Visual FoxPro)
> [!NOTE]  
>  In questo argomento contiene informazioni specifiche del Driver ODBC Visual FoxPro. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Supporto: parziale  
  
 Conformità di API ODBC: Livello 2  
  
 Imposta le opzioni che controllano il comportamento dei cursori associata a un handle di istruzione, *hstmt*.  
  
 Il Driver ODBC di Visual FoxPro supporta solo SQL_CONCUR_READ_ONLY; non supporta il *fConcurrency* valore SQL_CONCUR_ROWVER. Il driver converte SQL_KEYSET_SIZE SQL_CURSOR_DYNAMIC e SQL_CURSOR_KEYSET_DRIVEN SQL_SCROLL_STATIC con avviso ODBC_01S02.  
  
 Per ulteriori informazioni, vedere [SQLSetScrollOptions](../../odbc/reference/syntax/sqlsetscrolloptions-function.md) nel *riferimento per programmatori ODBC*.
