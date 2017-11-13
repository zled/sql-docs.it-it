---
title: Mapping SQLSetConnectOption | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLSetConnectOption function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLSetConnectOption
ms.assetid: a1b325cf-0c42-41c1-b141-b5a4fee7e708
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e531888390bbe4f625d308ad983059634e84ba2b
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetconnectoption-mapping"></a>Mapping SQLSetConnectOption
Quando un'applicazione ODBC 2. *x* applicazione chiama **SQLSetConnectOption** tramite un'applicazione ODBC 3*x* driver, la chiamata a  
  
```  
SQLSetConnectOption(hdbc, fOption, vParam)  
```  
  
 restituirà come indicato di seguito:  
  
-   Se *fOption* indica un attributo di connessione definite da ODBC che richiede una stringa, le chiamate di gestione Driver  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, SQL_NTS)  
    ```  
  
-   Se *fOption* indica un attributo di connessione definite da ODBC che restituisce un valore integer a 32 bit, le chiamate di gestione Driver  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, 0)  
    ```  
  
-   Se *fOption* indica un attributo di connessione definito dal driver, le chiamate di gestione Driver  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength)  
    ```  
  
 Nei tre casi precedenti, il *ConnectionHandle* argomento è impostato sul valore *hdbc*, *attributo* argomento è impostato sul valore *fOption* e *ValuePtr* argomento è impostato sullo stesso valore di *vParam*.  
  
 Poiché gestione Driver non è noto se l'attributo di connessione definito dal driver è necessario un valore stringa o integer a 32 bit, deve passare un valore valido per il *BufferLength* argomento di **SQLSetConnectAttr**. Se il driver non è definito per una semantica speciale definito dal driver connettere gli attributi e deve essere chiamato tramite **SQLSetConnectOption**, deve supportare **SQLSetConnectOption**.  
  
 Se un ODBC 2. *x* applicazione chiama **SQLSetConnectOption** per impostare un'opzione di istruzione specifici del driver in un'applicazione ODBC 3*x* driver e l'opzione è stata definita in un ODBC 2. *x* la versione del driver, una nuova costante di manifesto deve essere definita per l'opzione in ODBC 3*x* driver. Se la costante manifesto precedente viene utilizzata nella chiamata a **SQLSetConnectOption**, Driver Manager chiamerà **SQLSetConnectAttr** con il **StringLength** argomento impostato su 0.  
  
 Per un'applicazione ODBC 3*x* driver, gestione Driver non controlla se *fOption* è tra SQL_CONN_OPT_MIN e SQL_CONN_OPT_MAX, oppure è maggiore di SQL_CONNECT_OPT_DRVR_START.  
  
## <a name="setting-statement-options-on-the-connection-level"></a>Impostazione di opzioni di istruzione per il livello di connessione  
 In ODBC 2. *x*, un'applicazione può chiamare **SQLSetConnectOption** per impostare un'opzione di istruzione. Una volta effettuata questa operazione, il driver stabilisce l'opzione dell'istruzione come valore predefinito per tutte le istruzioni in un secondo momento allocate per tale connessione. Si è definito dal driver se il driver imposta l'opzione dell'istruzione per le istruzioni esistente associato alla connessione specificata.  
  
 Questa funzionalità è stata deprecata in ODBC 3*x*. ODBC 3*x* driver necessitano supporta solo l'impostazione di ODBC 2. *x* gli attributi di istruzione a livello di connessione, se si desidera utilizzare con ODBC 2. *x* applicazioni di eseguire tale operazione. ODBC 3*x* applicazioni non devono mai impostata gli attributi di istruzione a livello di connessione. ODBC 3*x* gli attributi di istruzione non possono essere impostati a livello di connessione, fatta eccezione per gli attributi SQL_ATTR_METADATA_ID e SQL_ATTR_ASYNC_ENABLE, sia gli attributi di connessione e gli attributi di istruzione, che può essere impostare il livello di connessione o il livello di istruzione.

