---
title: Sintassi del comando | Documenti Microsoft
description: Sintassi di comando e Stored procedure
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-commands
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, commands
- commands [OLE DB]
- OLE DB Driver for SQL Server, stored procedures
- stored procedures [OLE DB], command syntax
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: a3ea215d3596842503517a9485187ba2b1368059
ms.sourcegitcommit: e1bc8c486680e6d6929c0f5885d97d013a537149
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/15/2018
ms.locfileid: "35665751"
---
# <a name="command-syntax"></a>Sintassi dei comandi
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Il Driver OLE DB per SQL Server riconosce sintassi dei comandi specificata dalla macro DBGUID_SQL. Per il Driver OLE DB per SQL Server, l'identificatore indica che un amalgama di ODBC SQL, ISO, e [!INCLUDE[tsql](../../../includes/tsql-md.md)] è una sintassi valida. L'istruzione SQL seguente, ad esempio, utilizza una sequenza di escape ODBC SQL per specificare la funzione per i valori stringa LCASE:  
  
```  
SELECT customerid={fn LCASE(CustomerID)} FROM Customers  
```  
  
 LCASE restituisce una stringa di caratteri, convertendo tutti i caratteri maiuscoli nei rispettivi equivalenti minuscoli. Poiché la funzione per i valori stringa ISO LOWER esegue la stessa operazione, l'istruzione SQL seguente è un equivalente ISO dell'istruzione ODBC presentata nell'esempio precedente:  
  
```  
SELECT customerid=LOWER(CustomerID) FROM Customers  
```  
  
 Il Driver OLE DB per SQL Server elabora qualsiasi forma di istruzione correttamente quando vengono specificate come testo di un comando.  
  
## <a name="stored-procedures"></a>Stored procedure  
 Quando si esegue un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stored procedure tramite un Driver OLE DB per il comando di SQL Server, utilizzare la sequenza di escape ODBC CALL nel testo del comando. Il Driver OLE DB per SQL Server utilizza quindi il meccanismo di chiamata RPC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per ottimizzare l'elaborazione del comando. L'istruzione ODBC SQL seguente, ad esempio, rappresenta il testo del comando preferito rispetto alla forma [!INCLUDE[tsql](../../../includes/tsql-md.md)]:  
  
-   ODBC SQL  
  
    ```  
    {call SalesByCategory('Produce', '1995')}  
    ```  
  
-   Transact-SQL  
  
    ```  
    EXECUTE SalesByCategory 'Produce', '1995'  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Comandi](../../oledb/ole-db-commands/commands.md)  
  
  
