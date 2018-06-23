---
title: Sintassi del comando | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, commands
- commands [OLE DB]
- SQL Server Native Client OLE DB provider, stored procedures
- stored procedures [OLE DB], command syntax
ms.assetid: d463d3d7-e5cb-426d-8e92-aa29980356b6
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3186544156fdad861a94017ca6a1ad42aecb64bc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36168498"
---
# <a name="command-syntax"></a>Sintassi dei comandi
  Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client riconosce sintassi dei comandi specificata dalla macro DBGUID_SQL. Per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client, l'identificatore indica che un amalgama di ODBC SQL, ISO, e [!INCLUDE[tsql](../../includes/tsql-md.md)] è una sintassi valida. L'istruzione SQL seguente, ad esempio, utilizza una sequenza di escape ODBC SQL per specificare la funzione per i valori stringa LCASE:  
  
```  
SELECT customerid={fn LCASE(CustomerID)} FROM Customers  
```  
  
 LCASE restituisce una stringa di caratteri, convertendo tutti i caratteri maiuscoli nei rispettivi equivalenti minuscoli. Poiché la funzione per i valori stringa ISO LOWER esegue la stessa operazione, l'istruzione SQL seguente è un equivalente ISO dell'istruzione ODBC presentata nell'esempio precedente:  
  
```  
SELECT customerid=LOWER(CustomerID) FROM Customers  
```  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client elabora qualsiasi forma di istruzione correttamente quando vengono specificate come testo di un comando.  
  
## <a name="stored-procedures"></a>Stored procedure  
 Quando si esegue una [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedura utilizzando un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client di comando, utilizzare la sequenza di escape ODBC CALL nel testo del comando. Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client utilizza quindi il meccanismo di chiamata RPC di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per ottimizzare l'elaborazione del comando. L'istruzione ODBC SQL seguente, ad esempio, rappresenta il testo del comando preferito rispetto alla forma [!INCLUDE[tsql](../../includes/tsql-md.md)]:  
  
-   ODBC SQL  
  
    ```  
    {call SalesByCategory('Produce', '1995')}  
    ```  
  
-   Transact-SQL  
  
    ```  
    EXECUTE SalesByCategory 'Produce', '1995'  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Comandi](commands.md)  
  
  