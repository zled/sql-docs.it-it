---
title: SQLGetTypeInfo (Driver Paradox) | Documenti Microsoft
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
- SQLGetTypeInfo function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLGetTypeInfo
ms.assetid: e65063c7-ba9e-4cf0-ac13-4bb5bd2937db
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 300bc6086246abe0e6faff7801d12b4536520520
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32901406"
---
# <a name="sqlgettypeinfo-paradox-driver"></a>SQLGetTypeInfo (Paradox Driver)
> [!NOTE]  
>  In questo argomento fornisce informazioni specifiche del Driver Paradox. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Il nome del tipo (TYPE_NAME) restituito nella tabella di prodotti da **SQLGetTypeInfo** sarà il nome più comunemente utilizzato dall'origine dei dati.  
  
 SQL_ALL_EXCEPT_LIKE verrà restituito nella colonna di ricerca per Byte, contatore, Double, tipi di dati singolo, Long e Short. (La funzionalità simile può essere ottenuta dalla conversione del valore in un carattere utilizzando le funzioni di conversione canonica ODBC e quindi eseguire il confronto.)
