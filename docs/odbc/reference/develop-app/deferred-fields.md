---
title: Posticipata campi | Documenti Microsoft
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
- descriptors [ODBC], deferred fields
- deferred fields [ODBC]
ms.assetid: 5abeb9cc-4070-4f43-a80d-ad6a2004e5f3
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bc2020dc36ce031391194695e40308431c0f06d0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="deferred-fields"></a>Campi posticipati
I valori di *posticipata campi* non vengono utilizzati quando sono impostati, ma il driver vengono salvati gli indirizzi delle variabili per un effetto posticipata. Per un descrittore del parametro dell'applicazione, il driver utilizza il contenuto delle variabili al momento della chiamata a **SQLExecDirect** o **SQLExecute**. Per un descrittore di riga dell'applicazione, il driver utilizza il contenuto delle variabili al momento l'operazione di recupero.  
  
 Di seguito sono campi posticipati:  
  
-   I campi SQL_DESC_DATA_PTR e SQL_DESC_INDICATOR_PTR di un record del descrittore.  
  
-   Il campo SQL_DESC_OCTET_LENGTH_PTR di un record del descrittore dell'applicazione.  
  
-   Nel caso di un'operazione di recupero su più righe, i campi SQL_DESC_ARRAY_STATUS_PTR e SQL_DESC_ROWS_PROCESSED_PTR di un'intestazione del descrittore.  
  
 Quando viene allocato un descrittore, i campi di ogni record del descrittore posticipati inizialmente sono associati un valore null. Il significato del valore null è come segue:  
  
-   Se SQL_DESC_ARRAY_STATUS_PTR ha un valore null, un'operazione di recupero su più righe non restituisce il componente per ogni riga informazioni di diagnostica.  
  
-   Se SQL_DESC_DATA_PTR ha un valore null, il record non è associato.  
  
-   Se il campo SQL_DESC_OCTET_LENGTH_PTR di un ARD ha un valore null, il driver non restituisce informazioni sulla lunghezza della colonna.  
  
-   Se il campo SQL_DESC_OCTET_LENGTH_PTR di un APD ha un valore null e il parametro è una stringa di caratteri, il driver presuppone che si stringa con terminazione null. Per i parametri dinamici di output, un valore null in questo campo impedisce il driver di restituire informazioni sulla lunghezza. (Se il campo SQL_DESC_TYPE non indica un parametro di stringa di caratteri, viene ignorato il campo SQL_DESC_OCTET_LENGTH_PTR.)  
  
 L'applicazione non deve deallocare o eliminare le variabili utilizzate per i campi posticipati tra l'ora che associa i campi e l'ora il driver legge o scrive.
