---
title: Invio in batch chiamate a Stored Procedure | Documenti Microsoft
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
- stored procedures [ODBC], batching
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- batches [ODBC]
- ODBC CALL escape sequence
ms.assetid: b7f53e11-15f0-4602-8134-b166160888f0
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fd3d7fca3dc22d20c9aeadfc3b60fa41fa64f895
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36068024"
---
# <a name="batching-stored-procedure-calls"></a>Invio in batch di chiamate a stored procedure
  Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client invia automaticamente in batch chiamate a stored procedure al server nei casi appropriati. Il driver effettua questa operazione solo quando viene utilizzata la sequenza di escape e non per l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] EXECUTE. L'invio in batch di chiamate a stored procedure può ridurre il numero di round trip al server e migliorare significativamente le prestazioni.  
  
 Il driver invia in batch al server le chiamate alle procedure quando si esegue un batch che contiene più sequenze di escape ODBC CALL. Invia inoltre in batch chiamate alle procedure quando si utilizzano matrici di parametri associati con una sequenza di escape ODBC CALL. Ad esempio, se si utilizza l'associazione di parametri per riga o per associare una matrice con cinque elementi ai parametri di un'istruzione SQL ODBC CALL, quando **SQLExecute** oppure **SQLExecDirect** viene chiamato, il driver invia un singolo batch con cinque chiamate di procedura al server.  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione delle stored procedure](running-stored-procedures.md)  
  
  