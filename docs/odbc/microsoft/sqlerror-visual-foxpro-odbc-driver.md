---
title: SQLError (Driver ODBC Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLError function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 8315ec16-1c22-447a-a577-39bd94f61070
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3014c5c2af1a0ef8e5f485c790089e4807834446
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47634049"
---
# <a name="sqlerror-visual-foxpro-odbc-driver"></a>SQLError (driver ODBC Visual FoxPro)
> [!NOTE]  
>  In questo argomento contiene informazioni specifiche del Driver ODBC Visual FoxPro. Per informazioni generali su questa funzione, vedere l'argomento appropriato nel [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Supporto: completo  
  
 Della conformità API ODBC: A livello centrale  
  
 Restituisce le informazioni di stato o di errore sull'ultimo errore. Il driver gestisce un stack o un elenco di errori che possono essere restituite per il *hstmt*, *hdbc*, e *henv* argomenti, a seconda di come la chiamata a **SQLError**  viene eseguita. Nella coda degli errori deve essere scaricata dopo ogni istruzione.  
  
 Nella tabella seguente vengono descritte le **SQLError** argomenti e valori restituiti usati dal driver.  
  
|Argomento di SQLError|Descrizione del valore restituito|  
|-----------------------|------------------------------|  
|*szSQLState*|Il valore per il valore SQLSTATE rappresentato dall'errore.|  
|*pfNativeError*|Un valore diverso da zero indica un [Visual FoxPro ODBC Driver Native messaggio di errore](../../odbc/microsoft/visual-foxpro-odbc-driver-native-error-messages.md). Un valore pari a zero indica l'errore è stato rilevato dal driver e il mapping appropriati [il codice di errore ODBC](../../odbc/microsoft/odbc-error-codes-visual-foxpro-odbc-driver.md).|  
|*szErrorMsg*|Il testo per l'errore nativo o un errore ODBC.|  
|*pcbErrorMsg*|La lunghezza del testo del messaggio più la lunghezza degli identificatori.|  
  
 Per altre informazioni sui messaggi di errore di driver, vedere [Panoramica di messaggi di errore](../../odbc/microsoft/error-messages-visual-foxpro-odbc-driver.md). Per altre informazioni su questa funzione, vedere [SQLError](../../odbc/reference/syntax/sqlerror-function.md) nel *riferimento per programmatori ODBC*.
