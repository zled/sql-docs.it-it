---
title: Dimensioni del set di righe del cursore | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], rowset size
- ODBC cursors, rowset size
- rowsets [ODBC]
ms.assetid: 2febe2ae-fdc1-490e-a79f-c516bc8e7c3f
caps.latest.revision: 34
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 7d03701d162e38ba0bd06c82cb3a29a00d87ed0c
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37408690"
---
# <a name="cursor-rowset-size"></a>Dimensione del set di righe del cursore
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  I cursori ODBC non si limitano a recuperare una sola riga alla volta. Possono infatti recuperare più righe in ogni chiamata a **SQLFetch** oppure [SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md). Quando si utilizza un database client/server come Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], è consigliabile recuperare diverse righe contemporaneamente. Il numero di righe restituite durante un'operazione di recupero viene chiamato la dimensione del set di righe e viene specificato utilizzando l'oggetto SQL_ATTR_ROW_ARRAY_SIZE di [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
```  
SQLUINTEGER uwRowsize;  
SQLSetStmtAttr(m_hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)uwRowsetSize, SQL_IS_UINTEGER);  
```  
  
 I cursori con una dimensione del set di righe maggiore di 1 vengono definiti cursori a blocchi.  
  
 Sono disponibili due opzioni per associare le colonne dei set di risultati per i cursori a blocchi:  
  
-   Associazione per colonna  
  
     Ogni colonna viene associata a una matrice di variabili. Ogni matrice include lo stesso numero di elementi come dimensione del set di righe.  
  
-   Associazione per riga  
  
     Una matrice viene compilata utilizzando strutture che contengono i dati e gli indicatori per tutte le colonne di una riga. La matrice include lo stesso numero di strutture come dimensione del set di righe.  
  
 Quando viene utilizzata l'associazione di colonna o riga per riga, ogni chiamata a **SQLFetch** oppure **SQLFetchScroll** riempie le matrici associate con i dati dal set di righe recuperate.  
  
 [SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md) può anche essere utilizzato per recuperare i dati della colonna da un cursore a blocchi. In quanto **SQLGetData** agisce su una riga alla volta **SQLSetPos** deve essere chiamato per impostare una riga specifica nel set di righe come riga corrente prima di chiamare **SQLGetData**.  
  
 Il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] driver ODBC Native Client offre un'ottimizzazione con i set di righe per recuperare un risultato intero impostato rapidamente. Per usare questa ottimizzazione, impostare gli attributi del cursore sui valori predefiniti (dimensioni del set di righe forward-only di sola lettura, = 1) al momento **SQLExecDirect** oppure **SQLExecute** viene chiamato. Il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] driver ODBC Native Client imposta un set di risultati predefinito. Questa soluzione risulta più efficiente dei cursori del server quando si trasferiscono risultati al client senza scorrimento. Al termine dell'esecuzione dell'istruzione, aumentare la dimensione del set di righe e utilizzare l'associazione per colonna o per riga. In questo modo [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilizzare un risultato predefinito impostato per l'invio in modo efficiente le righe di risultati al client, mentre il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] driver ODBC Native Client effettua continuamente il pull righe dai buffer di rete sul client.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà del cursore](../../../relational-databases/native-client-odbc-cursors/properties/cursor-properties.md)  
  
  
