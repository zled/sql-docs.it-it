---
title: Disconnessione da un'origine dei dati | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ODBC data sources, connections
- data sources [SQL Server Native Client]
- disconnecting [ODBC]
- ODBC applications, disconnecting
- SQLDisconnect function
- ODBC applications, data sources
- connections [SQL Server Native Client]
- SQLFreeHandle function
- ODBC data sources, disconnecting
- SQL Server Native Client ODBC driver, data sources
- ODBC functions
- SQL Server Native Client ODBC driver, connections
ms.assetid: 65b0267d-b2ab-4a59-83f2-436d90cfbf79
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 611a9052f9a974608226757d26420948c7bbe420
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37409691"
---
# <a name="disconnecting-from-a-data-source"></a>Disconnessione da un'origine dati
  Quando un'applicazione ha terminato di utilizzare un'origine dati, viene chiamato **SQLDisconnect**. **SQLDisconnect** libera le istruzioni allocate nella connessione e disconnette il driver dell'origine dati. Dopo la disconnessione, l'applicazione può chiamare [SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md) per liberare l'handle di connessione. Prima di uscire, un'applicazione chiama inoltre **SQLFreeHandle** per liberare l'handle di ambiente.  
  
 Dopo la disconnessione, un'applicazione può riutilizzare l'handle di connessione allocato per connettersi a un'origine dati diversa oppure per riconnettersi alla stessa origine dati. La decisione di rimanere connessi anziché disconnettersi e riconnettersi in un secondo momento richiede la valutazione da parte del writer dell'applicazione dei costi relativi di ogni opzione. Connettersi e rimanere connessi a un'origine dati può essere relativamente costoso, a seconda del supporto di connessione utilizzato. Nella valutazione vanno considerati anche la probabilità di dover eseguire operazioni aggiuntive sulla stessa origine dati e il tempo richiesto. È inoltre possibile che un'applicazione debba utilizzare più di una connessione.  
  
## <a name="see-also"></a>Vedere anche  
 [Comunicazione con SQL Server &#40;ODBC&#41;](communicating-with-sql-server-odbc.md)  
  
  
