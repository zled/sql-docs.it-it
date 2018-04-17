---
title: L'esecuzione di query (ODBC) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-queries
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ODBC applications, executing queries
- SQL Server Native Client ODBC driver, statements
- ODBC applications, statements
- SQL Server Native Client ODBC driver, queries
- queries [ODBC]
ms.assetid: d935bcba-8ce6-4159-8395-6c86431602ad
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: b54ac19883ff608a890528806396c53496fab5f8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="executing-queries-odbc"></a>Esecuzione di query (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Dopo che un'applicazione ODBC inizializza un handle di connessione e si connette a un'origine dati, alloca uno o più handle di istruzione nell'handle di connessione. L'applicazione può quindi eseguire [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istruzioni nell'handle di istruzione. Di seguito viene indicata la sequenza generale degli eventi nell'esecuzione di un'istruzione SQL:  
  
1.  Impostare tutti gli attributi di istruzione necessari.  
  
2.  Creare l'istruzione.  
  
3.  Eseguire l'istruzione.  
  
4.  Recuperare tutti i set di risultati.  
  
 Dopo che un'applicazione recupera tutte le righe in tutti i set di risultati restituiti dall'istruzione SQL, può eseguire un'altra query sullo stesso handle di istruzione. Se un'applicazione determina che non è necessario recuperare tutte le righe in un determinato set di risultati, è possibile annullare il resto del set di risultati tramite una chiamata a [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md) o [SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md).  
  
 Se in un'applicazione ODBC è necessario eseguire la stessa istruzione SQL più volte con dati diversi, utilizzare un marcatore di parametro rappresentato da un punto interrogativo (?) nella creazione di un'istruzione SQL:  
  
```  
INSERT INTO MyTable VALUES (?, ?, ?)  
```  
  
 Ogni marcatore di parametro può quindi essere associato a una variabile di programma chiamando [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md).  
  
 Al termine dell'esecuzione di tutte le istruzioni SQL e dell'elaborazione dei relativi set di risultati, l'applicazione rilascia l'handle di istruzione.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client supporta più handle di istruzione per ogni handle di connessione. Le transazioni vengono gestite a livello di connessione, in modo che tutte le operazioni eseguite su tutti gli handle di gestione in un singolo handle di connessione vengano gestite come parte della stessa transazione.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
-   [Allocazione di un handle di istruzione](../../relational-databases/native-client-odbc-queries/allocating-a-statement-handle.md)  
  
-   [Costruzione di un'istruzione SQL &#40;ODBC&#41;](../../relational-databases/native-client-odbc-queries/constructing-an-sql-statement-odbc.md)  
  
-   [Costruzione di istruzioni SQL per i cursori](../../relational-databases/native-client-odbc-queries/constructing-sql-statements-for-cursors.md)  
  
-   [Uso dei parametri di un'istruzione](../../relational-databases/native-client-odbc-queries/using-statement-parameters.md)  
  
-   [L'esecuzione di istruzioni & #40; ODBC & #41;](../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
-   [Rilascio di un handle di istruzione](../../relational-databases/native-client-odbc-queries/freeing-a-statement-handle.md)  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Native Client & #40; ODBC & #41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
