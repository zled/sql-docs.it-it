---
title: SQLError (Driver ODBC di Visual FoxPro) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQLError function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 8315ec16-1c22-447a-a577-39bd94f61070
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 03c6fd59fc4b60e1e02f3d13c19bcab0206d571c
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="sqlerror-visual-foxpro-odbc-driver"></a>SQLError (Driver ODBC di Visual FoxPro)
> [!NOTE]  
>  In questo argomento contiene informazioni specifiche del Driver ODBC Visual FoxPro. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Supporto: completo  
  
 Conformità di API ODBC: Il livello di base  
  
 Restituisce le informazioni di stato o di errore sull'ultimo errore. Il driver gestisce un stack o un elenco di errori che possono essere restituite per il *hstmt*, *hdbc*, e *henv* argomenti, a seconda di come la chiamata a **SQLError**  viene eseguita. La coda di errore viene svuotata dopo ogni istruzione.  
  
 Nella tabella seguente vengono descritti il **SQLError** argomenti e valori restituiti usati dal driver.  
  
|Argomento SQLError|Descrizione del valore restituito|  
|-----------------------|------------------------------|  
|*szSQLState*|Il valore per il valore SQLSTATE rappresentato dall'errore.|  
|*pfNativeError*|Un valore diverso da zero indica un [Visual FoxPro ODBC Driver Native messaggio di errore](../../odbc/microsoft/visual-foxpro-odbc-driver-native-error-messages.md). Il valore zero indica che l'errore è stato rilevato dal driver e il mapping appropriati [codice di errore ODBC](../../odbc/microsoft/odbc-error-codes-visual-foxpro-odbc-driver.md).|  
|*szErrorMsg*|Il testo per l'errore nativo o ODBC.|  
|*pcbErrorMsg*|La lunghezza del testo del messaggio e della lunghezza degli identificatori.|  
  
 Per ulteriori informazioni sui messaggi di errore di driver, vedere [Panoramica di messaggi di errore](../../odbc/microsoft/error-messages-visual-foxpro-odbc-driver.md). Per ulteriori informazioni su questa funzione, vedere [SQLError](../../odbc/reference/syntax/sqlerror-function.md) nel *riferimento per programmatori ODBC*.
