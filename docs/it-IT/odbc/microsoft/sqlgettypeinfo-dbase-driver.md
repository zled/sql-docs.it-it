---
title: SQLGetTypeInfo (dBASE Driver) | Documenti Microsoft
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
- SQLGetTypeInfo function [ODBC], dBASE Driver
- DBase driver [ODBC], SQLGetTypeInfo
ms.assetid: 6e9ce02b-97c7-4c1a-91e0-829df7459c84
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1b1e5c622cf3d3c325972af4057235a41f864d1a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlgettypeinfo-dbase-driver"></a>SQLGetTypeInfo (dBASE Driver)
> [!NOTE]  
>  In questo argomento fornisce informazioni specifiche del Driver dBASE. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Il nome del tipo (TYPE_NAME) restituito nella tabella di prodotti da **SQLGetTypeInfo** sarà il nome più comunemente utilizzato dall'origine dei dati.  
  
 SQL_ALL_EXCEPT_LIKE verrà restituito nella colonna di ricerca per Byte, contatore, Double, tipi di dati singolo, Long e Short. (La funzionalità simile può essere ottenuta dalla conversione del valore in un carattere utilizzando le funzioni di conversione canonica ODBC, quindi eseguire il confronto).
