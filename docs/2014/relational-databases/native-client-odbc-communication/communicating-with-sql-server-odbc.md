---
title: La comunicazione con SQL Server (ODBC) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, communicating with SQL Server
- ODBC applications, communicating with SQL Server
- ODBC, communicating with SQL Server
ms.assetid: cca3dcf0-2a7e-465a-84de-7ce055360eb6
caps.latest.revision: 33
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3434d20f7b2eca20db0f94155f0922580e4f2546
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169650"
---
# <a name="communicating-with-sql-server-odbc"></a>Comunicazione con SQL Server (ODBC)
  Per un'applicazione ODBC comunicare con un'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è necessario che allochi ambiente e connessione gestisce e connettersi all'origine dati. Una volta stabilita una connessione, l'applicazione può inviare query al server ed elaborare qualsiasi set di risultati. Quando l'applicazione ha completato l'utilizzo dell'origine dati, si disconnette dall'origine dati e rilascia l'handle di connessione. Quando l'applicazione ha rilasciato tutti gli handle di connessione, rilascia l'handle di ambiente.  
  
 Un'applicazione può connettersi a qualsiasi numero di origini dati. L'applicazione può utilizzare una combinazione di driver e origini dati, lo stesso driver e una combinazione di origini dati o persino lo stesso driver e più connessioni alla stessa origine dati.  
  
 È possibile scaricare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] esempi ODBC di Native Client dal [SQL Server Downloads](http://go.microsoft.com/fwlink/?LinkId=62796) su MSDN.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
-   [Allocazione di un handle di ambiente](allocating-an-environment-handle.md)  
  
-   [Allocazione di un handle di connessione](allocating-a-connection-handle.md)  
  
-   [Origini dati ODBC di SQL Server Native Client](../../integration-services/connection-manager/data-sources.md)  
  
-   [La connessione a un'origine dati &#40;ODBC&#41;](connecting-to-a-data-source-odbc.md)  
  
-   [Disconnessione da un'origine dati](disconnecting-from-a-data-source.md)  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md)   
 [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md)  
  
  