---
title: L'esecuzione preparata | Documenti Microsoft
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
- deferred statement preparation
- prepared execution [ODBC]
- SQLPrepare function
- ODBC applications, statements
- SQLExecute function
- statements [ODBC], prepared execution
ms.assetid: f3a9d32b-6cd7-4f0c-b38d-c8ccc4ee40c3
caps.latest.revision: 34
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 89ccf1c9fe8b3e69b55ec51be53dc6d3b63efdce
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36170349"
---
# <a name="prepared-execution"></a>Esecuzione preparata
  L'API ODBC definisce l'esecuzione preparata per ridurre l'overhead dell'analisi e della compilazione associato all'esecuzione ripetuta di un'istruzione [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Nell'applicazione viene compilata una stringa di caratteri contenente un'istruzione SQL che viene eseguita in due fasi. Viene chiamato [funzione SQLPrepare](http://go.microsoft.com/fwlink/?LinkId=59360) una volta per l'istruzione analizzata e compilata in un piano di esecuzione mediante il [!INCLUDE[ssDE](../../../includes/ssde-md.md)]. Chiama poi **SQLExecute** per ogni esecuzione del piano di esecuzione preparata. con conseguente risparmio dell'overhead correlato all'analisi e alla compilazione in ogni esecuzione. L'esecuzione preparata viene generalmente utilizzata dalle applicazioni per eseguire ripetutamente la stessa istruzione SQL con parametri.  
  
 Per la maggior parte dei database, l'esecuzione preparata è più veloce dell'esecuzione diretta per le istruzioni eseguite più di tre o quattro volte, sopratutto perché l'istruzione viene compilata una sola volta, mentre le istruzioni eseguite direttamente vengono compilate ogni volta che vengono eseguite. L'esecuzione preparata può inoltre offrire una riduzione del traffico di rete perché il driver può inviare all'origine dati un identificatore del piano di esecuzione e i valori dei parametri, anziché un'intera istruzione SQL, ogni volta che viene eseguita l'istruzione.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] riduce la differenza nelle prestazioni tra l'esecuzione diretta e preparata tramite algoritmi migliorati per il rilevamento e il riutilizzo dei piani di esecuzione dal **SQLExecDirect**. offrendo alle istruzioni eseguite direttamente alcuni dei vantaggi di prestazioni associati all'esecuzione preparata. Per altre informazioni, vedere [esecuzione diretta](direct-execution.md).  
  
 In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] è inoltre disponibile il supporto nativo per l'esecuzione preparata. Si basa su un piano di esecuzione **SQLPrepare** ed eseguito in un secondo momento quando **SQLExecute** viene chiamato. Poiché [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] non è necessario compilare stored procedure temporanee **SQLPrepare**, non vi è alcun overhead aggiuntivo nelle tabelle di sistema in **tempdb**.  
  
 Per motivi di prestazioni, la preparazione dell'istruzione viene posticipata fino alla **SQLExecute** viene chiamato o un'operazione di metaproprietà (ad esempio [SQLDescribeCol](../../native-client-odbc-api/sqldescribecol.md) o [SQLDescribeParam](../../native-client-odbc-api/sqldescribeparam.md)in ODBC) viene eseguita. Questo è il comportamento predefinito. Eventuali errori nell'istruzione da preparare saranno noti solo dopo l'esecuzione dell'istruzione o dell'operazione di metaproprietà. È possibile disattivare questo comportamento predefinito impostando l'attributo SQL_SOPT_SS_DEFER_PREPARE dell'istruzione specifica del driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client su SQL_DP_OFF.  
  
 In caso di posticipata preparare, se si chiama **SQLDescribeCol** oppure **SQLDescribeParam** prima di chiamare **SQLExecute** genera un round trip aggiuntivo al server. Nel **SQLDescribeCol**, il driver rimuove la clausola WHERE della query e lo invia al server con SET FMTONLY ON per ottenere la descrizione delle colonne nel primo set di risultati restituiti dalla query. Nel **SQLDescribeParam**, il driver chiama il server per ottenere una descrizione delle espressioni o delle colonne a cui fanno riferimento i marcatori di parametro nella query. Questo metodo presenta inoltre alcune restrizioni, ad esempio non è in grado di risolvere i parametri nelle sottoquery.  
  
 Utilizzo eccessivo di **SQLPrepare** con il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] driver ODBC Native Client comporta una riduzione delle prestazioni, soprattutto quando connesso a versioni precedenti di SQL Server. L'esecuzione preparata non deve essere utilizzata per le istruzioni eseguite una sola volta. L'esecuzione preparata è più lenta dell'esecuzione diretta per una singola esecuzione di un'istruzione perché richiede un round trip in rete aggiuntivo dal client al server. Nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] viene inoltre generata una stored procedure temporanea.  
  
 Le istruzioni preparate non possono essere utilizzate per creare oggetti temporanei in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Alcune applicazioni ODBC precedenti utilizzati **SQLPrepare** qualsiasi momento [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md) è stata utilizzata. **SQLBindParameter** non richiede l'utilizzo di **SQLPrepare**, e può essere utilizzato con **SQLExecDirect**. Ad esempio, utilizzare **SQLExecDirect** con **SQLBindParameter** per recuperare il codice restituito o di output da una stored procedure che viene eseguita una sola volta. Non usare **SQLPrepare** con **SQLBindParameter** , a meno che la stessa istruzione verrà eseguita più volte.  
  
## <a name="see-also"></a>Vedere anche  
 [L'esecuzione di istruzioni &#40;ODBC&#41;](executing-statements-odbc.md)  
  
  