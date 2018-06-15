---
title: SQLGetTypeInfo (Driver di File di testo) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC], Text File Driver
- text file driver [ODBC], SQLGetTypeInfo
ms.assetid: 05a58975-093c-4bd9-bd72-b5f0026a6e36
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6f9709107e8d7369b19608d41e76bcd4dfef7bad
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32902736"
---
# <a name="sqlgettypeinfo-text-file-driver"></a>SQLGetTypeInfo (Driver di File di testo)
> [!NOTE]  
>  In questo argomento fornisce informazioni specifiche del Driver File di testo. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Il nome del tipo (TYPE_NAME) restituito nella tabella di prodotti da **SQLGetTypeInfo** sarà il nome più comunemente utilizzato dall'origine dei dati.  
  
 SQL_ALL_EXCEPT_LIKE verrà restituito nella colonna di ricerca per Byte, contatore, Double, tipi di dati singolo, Long e Short. (La funzionalità simile può essere ottenuta dalla conversione del valore in un carattere utilizzando le funzioni di conversione canonica ODBC, quindi eseguire il confronto).  
  
 Quando viene utilizzato il driver di testo, **SQLGetTypeInfo** restituisce un valore CASE_SENSITIVE false per il testo dei tipi di dati CHAR e LONGCHAR, quando i tipi di dati effettivamente tra maiuscole e minuscole.
