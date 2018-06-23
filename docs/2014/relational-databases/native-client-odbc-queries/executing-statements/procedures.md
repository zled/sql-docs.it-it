---
title: Procedure | Documenti Microsoft
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
- stored procedures [ODBC]
- stored procedures [ODBC], about ODBC stored procedures
- ODBC applications, statements
- statements [ODBC], stored procedures
- ODBC applications, stored procedures
ms.assetid: c64d5f3a-376b-48ef-84f3-b6148ac8600a
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 260e9a6ab31e2376132c107c19bb30b8aeee8b1c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36167585"
---
# <a name="procedures"></a>Procedure
  Una stored procedure è un oggetto eseguibile precompilato che contiene una o più istruzioni [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Le stored procedure possono includere parametri di input e di output e possono restituire anche codice di tipo integer. Un'applicazione può enumerare le stored procedure disponibili utilizzando funzioni di catalogo.  
  
 Le applicazioni ODBC destinate a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] devono utilizzare solo l'esecuzione diretta per chiamare una stored procedure. Quando si è connessi a versioni precedenti di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] driver ODBC di Native Client implementa [funzione SQLPrepare](http://go.microsoft.com/fwlink/?LinkId=59360) mediante la creazione di una stored procedure temporanea, che viene quindi chiamata in **SQLExecute** . Aggiunge overhead avere **SQLPrepare** creare una stored procedure temporanea che solo le chiamate di stored procedure di destinazione rispetto a direttamente la destinazione di esecuzione di stored procedure. Anche in caso di connessione a un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], la preparazione di una chiamata richiede round trip aggiuntivo in rete e la compilazione di un piano di esecuzione che chiami solo il piano di esecuzione della stored procedure.  
  
 Le applicazioni ODBC devono utilizzare la sintassi ODBC CALL in caso di esecuzione di una stored procedure. Il driver è ottimizzato per l'utilizzo di un meccanismo di chiamata a procedure remote per chiamare la procedura quando si utilizza la sintassi ODBC CALL. Si tratta di un meccanismo molto più efficiente di quello utilizzato per inviare un'istruzione [!INCLUDE[tsql](../../../includes/tsql-md.md)] EXECUTE al server.  
  
 Per altre informazioni, vedere [che eseguono Stored procedure](../../native-client-odbc-stored-procedures/running-stored-procedures.md).  
  
## <a name="see-also"></a>Vedere anche  
 [L'esecuzione di istruzioni &#40;ODBC&#41;](executing-statements-odbc.md)  
  
  