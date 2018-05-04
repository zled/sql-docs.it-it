---
title: Creazione di istruzioni SQL interoperabile | Documenti Microsoft
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
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], constructing statements
ms.assetid: dee6f7e2-bcc4-4c74-8c7c-12aeda8a90eb
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 257440b78a466178d09e954e9aed5b9385325b8a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="constructing-interoperable-sql-statements"></a>Creazione di istruzioni SQL interoperabili
Come indicato nelle sezioni precedenti, le applicazioni interoperabili devono utilizzare la grammatica SQL ODBC. Oltre a utilizzare questa grammatica, tuttavia, un numero di ulteriori problemi è riscontrato da applicazioni interoperative. Ad esempio, come un'applicazione vengono se desidera utilizzare una funzionalità, ad esempio gli outer join, che non è supportata da tutte le origini dati?  
  
 A questo punto, il writer dell'applicazione deve prendere alcune decisioni sul quali funzionalità del linguaggio sono necessari e facoltativi. Nella maggior parte dei casi, se un driver specifico non supporta una funzionalità richiesta dall'applicazione, l'applicazione Rifiuta semplicemente per l'esecuzione con tale driver. Tuttavia, se la funzionalità è opzionale, l'applicazione può risolvere la funzionalità. Ad esempio, è possibile disattivare le parti dell'interfaccia che consentono all'utente di utilizzare la funzionalità.  
  
 Per determinare quali funzionalità sono supportate, applicazioni avviate chiamando **SQLGetInfo** con l'opzione SQL_SQL_CONFORMANCE. Il livello di conformità SQL assegna all'applicazione una visione dei quali SQL è supportato. Per perfezionare in questa vista, l'applicazione chiama **SQLGetInfo** con una serie di altre opzioni. Per un elenco completo di queste opzioni, vedere il [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) descrizione della funzione. Infine, **SQLGetTypeInfo** restituisce informazioni sui tipi di dati supportati dall'origine dati. Le sezioni seguenti elencano un numero di fattori che devono controllare le applicazioni durante la costruzione di istruzioni SQL interoperative.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Utilizzo del catalogo e dello schema](../../../odbc/reference/develop-app/catalog-and-schema-usage.md)  
  
-   [Posizione catalogo](../../../odbc/reference/develop-app/catalog-position.md)  
  
-   [Identificatori delimitati](../../../odbc/reference/develop-app/quoted-identifiers.md)  
  
-   [Maiuscole/minuscole identificatore](../../../odbc/reference/develop-app/identifier-case.md)  
  
-   [Sequenza di escape](../../../odbc/reference/develop-app/escape-sequences.md)  
  
-   [Valore letterale prefissi e suffissi](../../../odbc/reference/develop-app/literal-prefixes-and-suffixes.md)  
  
-   [Marcatori di parametro nelle chiamate di procedura](../../../odbc/reference/develop-app/parameter-markers-in-procedure-calls.md)  
  
-   [Istruzioni DDL](../../../odbc/reference/develop-app/ddl-statements.md)
