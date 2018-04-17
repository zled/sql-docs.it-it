---
title: Riepilogo dell'interfaccia del Provider del servizio ODBC | Documenti Microsoft
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
ms.assetid: ace6085b-355b-435b-8734-503fc3c12ec2
caps.latest.revision: 4
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 60cd51075100f77e131e3a9e48dbdf2d10a444b8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="odbc-service-provider-interface-summary"></a>Riepilogo dell'interfaccia del Provider del servizio ODBC
La tabella seguente descrive le funzioni di interfaccia di Provider di servizi di ODBC. Per ulteriori informazioni sulla sintassi e semantica per ogni funzione, vedere [riferimento ODBC Service Provider Interface (SPI)](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md).  
  
|Nome funzione|Scopo|  
|-------------------|-------------|  
|[SQLSetConnectAttrForDbcInfo](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Uguale a [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md), ma l'attributo viene impostato sul token di informazioni di connessione anziché nell'handle di connessione.|  
|[SQLSetDriverConnectInfo](../../../odbc/reference/syntax/sqldrivertodatasource-function.md)|Imposta la stringa di connessione nel token di informazioni di connessione per un'applicazione [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) chiamare.|  
|[SQLSetConnectInfo](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Imposta l'origine dati, l'ID utente e password nel token di informazioni di connessione per un'applicazione [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) chiamare.|  
|[SQLGetPoolID](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Recupera l'ID del pool.|  
|[SQLRateConnection](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Determina se un driver può riutilizzare una connessione esistente nel pool di connessioni.|  
|[SQLPoolConnect](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Creare una nuova connessione se nessuna connessione nel pool può essere riutilizzata.|  
|[SQLCleanupConnectionPoolID](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Indica un driver che è stato verificato il timeout di un ID del pool.|
