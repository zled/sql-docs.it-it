---
title: Attributi di connessione | Documenti Microsoft
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
- data sources [ODBC], connection attributes
- ODBC drivers [ODBC], connection attributes
- connecting to data source [ODBC], connection attributes
- connection attributes [ODBC]
- connecting to driver [ODBC], connection attributes
ms.assetid: e6d03089-30a3-4627-a642-591ba0980894
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2d2fe93960b2a6cae6cf2916416f7ac6e122ac16
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="connection-attributes"></a>Attributi di connessione
Attributi di connessione sono riportate le caratteristiche della connessione. Poiché ad esempio le transazioni si verificano al livello della connessione, il livello di isolamento delle transazioni è un attributo di connessione. Analogamente, il timeout di accesso o il numero di secondi di attesa durante il tentativo di connessione prima del timeout, è un attributo di connessione.  
  
 Gli attributi di connessione sono impostati con **SQLSetConnectAttr** e le relative impostazioni correnti recuperati con **SQLGetConnectAttr**. Se **SQLSetConnectAttr** viene chiamato prima che il driver viene caricato, gli archivi di gestione Driver gli attributi nella relativa struttura della connessione e li imposta nel driver come parte del processo di connessione. Non è necessario che un'applicazione impostare eventuali attributi di connessione. tutti gli attributi di connessione hanno impostazioni predefinite, alcune delle quali sono specifici del driver.  
  
 Un attributo di connessione può essere impostato prima o dopo la connessione, o entrambi, a seconda dell'attributo e il driver. Il timeout di accesso (SQL_ATTR_LOGIN_TIMEOUT) valido per il processo di connessione ed è efficace solo se è impostato prima della connessione. Gli attributi che specificano se usare la libreria di cursori ODBC (SQL_ATTR_ODBC_CURSORS) e le dimensioni del pacchetto di rete (SQL_ATTR_PACKET_SIZE) devono essere impostati prima della connessione, perché la libreria di cursori ODBC si trova tra gestione Driver e il driver e è pertanto necessario caricare prima il driver.  
  
 Gli attributi per specificare se un'origine dati è di sola lettura o lettura / scrittura (SQL_ATTR_ACCESS_MODE) e il catalogo corrente (SQL_ATTR_CURRENT_CATALOG) può essere impostate prima o dopo la connessione, a seconda del driver. Tuttavia, applicazioni interoperative impostarle prima della connessione poiché alcuni driver non supporta la modifica di questi dopo la connessione.  
  
 Alcuni attributi di connessione è un valore predefinito prima di stabilire la connessione, mentre altri non. Quelli che sono SQL_ATTR_ACCESS_MODE SQL_ATTR_AUTOCOMMIT, SQL_ATTR_LOGIN_TIMEOUT, SQL_ATTR_ODBC_CURSORS, SQL_ATTR_TRACE e SQL_ATTR_TRACEFILE.  
  
 Dopo la connessione, è necessario impostare gli attributi di connessione di conversione (SQL_ATTR_TRANSLATE_DLL e SQL_ATTR_TRANSLATE_OPTION).  
  
 In qualsiasi momento, è possono impostare tutti gli altri attributi di connessione. Per ulteriori informazioni, vedere il [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md) descrizione della funzione. (Gli attributi di connessione non possono essere impostati a livello di ambiente da una chiamata a **SQLSetEnvAttr**.)
