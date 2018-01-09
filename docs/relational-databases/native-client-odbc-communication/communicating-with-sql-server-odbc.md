---
title: La comunicazione con SQL Server (ODBC) | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-communication
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, communicating with SQL Server
- ODBC applications, communicating with SQL Server
- ODBC, communicating with SQL Server
ms.assetid: cca3dcf0-2a7e-465a-84de-7ce055360eb6
caps.latest.revision: "34"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 957ffb336a018128b6cb5de24ba70ac60509de47
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="communicating-with-sql-server-odbc"></a>Comunicazione con SQL Server (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Per un'applicazione ODBC comunicare con un'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è necessario allocare ambiente e connessione gestisce e connettersi all'origine dati. Una volta stabilita una connessione, l'applicazione può inviare query al server ed elaborare qualsiasi set di risultati. Quando l'applicazione ha completato l'utilizzo dell'origine dati, si disconnette dall'origine dati e rilascia l'handle di connessione. Quando l'applicazione ha rilasciato tutti gli handle di connessione, rilascia l'handle di ambiente.  
  
 Un'applicazione può connettersi a qualsiasi numero di origini dati. L'applicazione può utilizzare una combinazione di driver e origini dati, lo stesso driver e una combinazione di origini dati o persino lo stesso driver e più connessioni alla stessa origine dati.  
  
 È possibile scaricare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] esempi ODBC di Native Client dal [SQL Server Downloads](http://go.microsoft.com/fwlink/?LinkId=62796) su MSDN.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
-   [Allocazione di un handle di ambiente](../../relational-databases/native-client-odbc-communication/allocating-an-environment-handle.md)  
  
-   [Allocazione di un handle di connessione](../../relational-databases/native-client-odbc-communication/allocating-a-connection-handle.md)  
  
-   [Origini dati ODBC di SQL Server Native Client](../../relational-databases/native-client-odbc-communication/sql-server-native-client-odbc-data-sources.md)  
  
-   [Connessione a un'origine dati &#40; ODBC &#41;](../../relational-databases/native-client-odbc-communication/connecting-to-a-data-source-odbc.md)  
  
-   [Disconnessione da un'origine dati](../../relational-databases/native-client-odbc-communication/disconnecting-from-a-data-source.md)  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Native Client &#40; ODBC &#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)   
 [SQLSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md)  
  
  
