---
title: Modifiche del comportamento | Documenti Microsoft
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
- backward compatibility [ODBC], behavioral changes
- behavioral changes [ODBC]
- compatibility [ODBC], behavioral changes
ms.assetid: a17ae701-6ab6-4eaf-9e46-d3b9cd0a3a67
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ed9b06793abef5006e49b2f526d11ead798c7931
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32910916"
---
# <a name="behavioral-changes"></a>Modifiche del comportamento
Modifiche del comportamento sono le modifiche per il quale il *sintassi* dell'interfaccia viene mantenuta, ma la *semantica* sono stati modificati. Per queste modifiche, funzionalità 2 di ODBC utilizzata. *x* presenta un comportamento diverso la stessa funzionalità in ODBC 3. *x*.  
  
 Se un'applicazione presenta ODBC 2. *x* comportamento o ODBC 3. *x* comportamento è determinato dall'attributo SQL_ATTR_ODBC_VERSION ambiente. Questo valore di 32 bit è impostato su SQL_OV_ODBC2 possono presentare ODBC 2. *x* comportamento e SQL_OV_ODBC3 possono presentare ODBC 3. *x* comportamento.  
  
 L'attributo di ambiente SQL_ATTR_ODBC_VERSION è impostato da una chiamata a **SQLSetEnvAttr**. Dopo che un'applicazione chiama **SQLAllocHandle** per allocare un handle di ambiente, è necessario chiamare**SQLSetEnvAttr** immediatamente per impostare il comportamento presenta. (Di conseguenza, vi è un nuovo stato dell'ambiente per descrivere l'handle di ambiente in un allocata, ma versionless, stato). Per ulteriori informazioni, vedere [tabelle di transizione dello stato di appendice b: ODBC](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Un'applicazione segnalare il problema presenta con l'attributo di ambiente SQL_ATTR_ODBC_VERSION, ma l'attributo non ha alcun effetto sulla connessione dell'applicazione con un ODBC 2. *x* o ODBC 3. *x* driver. Un database ODBC 3. *x* applicazione può connettersi a una delle due un ODBC 2. *x* o 3. *x* driver, indipendentemente dall'impostazione dell'attributo di ambiente.  
  
 ODBC 3. *x* applicazioni non devono mai chiamare **SQLAllocEnv**. Di conseguenza, se il Driver Manager riceve una chiamata a **SQLAllocEnv**, riconosce l'applicazione come un ODBC 2. *x* dell'applicazione.  
  
 L'attributo SQL_ATTR_ODBC_VERSION influisce su tre diversi aspetti di un'applicazione ODBC 3. *x* il comportamento del driver:  
  
-   SQLSTATE  
  
-   Tipi di dati per date, time e timestamp  
  
-   Il *CatalogName* argomento nella **SQLTables** accetta i criteri di ricerca in ODBC 3. *x*, ma non in ODBC 2. *x*  
  
 L'impostazione dell'attributo environment SQL_ATTR_ODBC_VERSION non influisce sul **SQLSetParam** o **SQLBindParam**. **SQLColAttribute** non è influenzato da questo bit. Sebbene **SQLColAttribute** restituisce gli attributi che sono interessati dalla versione di ODBC (tipo di dati, precisione, scala e lunghezza), il comportamento previsto è determinato dal valore della *FieldIdentifier*argomento. Quando *FieldIdentifier* è uguale a SQL_DESC_TYPE, **SQLColAttribute** restituisce ODBC 3. *x* codici per date, time e timestamp; quando *FieldIdentifier* è uguale a SQL_COLUMN_TYPE, **SQLColAttribute** restituisce ODBC 2. *x* codici per date, time e timestamp.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Mapping di SQLSTATE](../../../odbc/reference/develop-app/sqlstate-mappings.md)  
  
-   [Modifiche ai tipi di dati datetime](../../../odbc/reference/develop-app/datetime-data-type-changes.md)
