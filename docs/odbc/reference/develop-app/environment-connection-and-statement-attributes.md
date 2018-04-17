---
title: Ambiente di connessione e gli attributi di istruzione | Documenti Microsoft
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
ms.topic: article
helpviewer_keywords:
- environment attributes [ODBC]
- connection attributes [ODBC]
- statement attributes [ODBC]
ms.assetid: 9e15b276-3b7a-428a-b72f-a3ddfe1ba1ce
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a84cd4efc498de20dad68d99aa8ad00e47eb3830
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="environment-connection-and-statement-attributes"></a>Ambiente di connessione e gli attributi di istruzione
ODBC definisce un numero di attributi che sono associati gli ambienti, le connessioni o istruzioni.  
  
 Gli attributi di ambiente interessano l'intero ambiente, ad esempio se il pool di connessioni è abilitato. Gli attributi di ambiente vengono impostati con **SQLSetEnvAttr** e recuperati con **SQLGetEnvAttr**.  
  
 Attributi di connessione su ogni connessione singolarmente, ad esempio come tempo un driver di attesa durante il tentativo di connettersi a un'origine dati prima del timeout. Gli attributi di connessione sono impostati con **SQLSetConnectAttr** e recuperati con **SQLGetConnectAttr**. Per ulteriori informazioni sugli attributi di connessione, vedere [gli attributi di connessione](../../../odbc/reference/develop-app/connection-attributes.md).  
  
 Gli attributi di istruzione interessano singolarmente, ogni istruzione, ad esempio se un'istruzione deve essere eseguita in modo asincrono. Gli attributi di istruzione sono impostati con **SQLSetStmtAttr** e recuperati con **SQLGetStmtAttr**. Alcuni attributi di istruzione sono di sola lettura e non possono essere impostati. Ad esempio, l'attributo di istruzione SQL_ATTR_ROW_NUMBER, viene utilizzato per recuperare il numero della riga corrente del cursore, è di sola lettura. Per ulteriori informazioni sugli attributi di istruzione, vedere [gli attributi di istruzione](../../../odbc/reference/develop-app/statement-attributes.md).  
  
 Oltre agli attributi definiti da ODBC, è possibile definire un driver la propria connessione e gli attributi di istruzione. Attributi definito dal driver devono essere registrati con Open Group per garantire che due fornitori di driver non assegnare lo stesso valore intero per attributi diversi, proprietari. Per ulteriori informazioni, vedere [tipi di dati specifici del Driver, descrittore di tipi, tipi di informazioni, tipi di diagnostica e gli attributi](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md).  
  
 Per un elenco completo degli attributi, vedere [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md), [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md), e [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md). La maggior parte degli attributi sono descritti anche nella descrizione della funzione ODBC che influiscano.
