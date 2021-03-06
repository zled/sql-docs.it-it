---
title: SQLBindCol | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLBindCol function
ms.assetid: fbd7ba20-d917-4ca9-b018-018ac6af9f98
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4dafadd6ba64fa08f0329cd73114b4f85a1e376a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48141511"
---
# <a name="sqlbindcol"></a>SQLBindCol
  Come regola generale, considerare le implicazioni dell'utilizzo di **SQLBindCol** per provocare la conversione dei dati. Le conversioni per associazione sono processi client. Se ad esempio viene recuperato un valore a virgola mobile associato a una colonna di tipo character, nel driver viene eseguita in locale la conversione da float a character quando viene recuperata una riga. La funzione [!INCLUDE[tsql](../../includes/tsql-md.md)] CONVERT può essere utilizzata per riportare il costo della conversione dei dati nel server.  
  
 Un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può restituire più set di righe di risultati in una singola esecuzione dell'istruzione. Ogni set di risultati deve essere associato separatamente. Per ulteriori informazioni sull'associazione di più set di risultati, vedere [SQLMoreResults](sqlmoreresults.md).  
  
 Lo sviluppatore può associare le colonne da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-tipi di dati C specifici usando la *TargetType* valore `SQL_C_BINARY`. Le colonne associate a tipi specifici di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non sono portabili. I tipi di dati ODBC C specifici di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] definiti corrispondono alle definizioni del tipo di DB-Library e gli sviluppatori di DB-Library che si occupano della portabilità delle applicazioni potrebbero sfruttare questa caratteristica.  
  
 Il troncamento dei dati di Reporting è un processo impegnativo per la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client. È possibile evitare il troncamento assicurandosi che la larghezza di tutti i buffer di dati associati sia sufficiente per restituire i dati. Per i dati di tipo character, la larghezza deve includere lo spazio per un carattere di terminazione della stringa quando viene utilizzato il comportamento predefinito del driver per la terminazione della stringa. Ad esempio, associa una [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **char(5)** colonna in una matrice dei risultati di cinque caratteri troncamento per ogni valore recuperato. L'associazione della stessa colonna a una matrice di sei caratteri evita il troncamento fornendo un elemento character in cui archiviare il terminatore null. [SQLGetData](sqlgetdata.md) può essere utilizzato per recuperare dati long character e binari senza troncamento.  
  
 Se per i tipi di dati per valori di grandi dimensioni il buffer fornito dall'utente non è sufficientemente grande per contenere l'intero valore della colonna, viene restituito `SQL_SUCCESS_WITH_INFO` e viene generato il messaggio di avviso "Troncamento a destra della stringa di dati". L'argomento `StrLen_or_IndPtr` conterrà il numero di caratteri/byte archiviati nel buffer.  
  
## <a name="sqlbindcol-support-for-enhanced-date-and-time-features"></a>Supporto di SQLBindCol per le caratteristiche avanzate di data e ora  
 I valori di colonna risultato dei tipi data/ora vengono convertiti come descritto in [le conversioni da SQL a C](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md). Si noti che per recuperare le colonne time e datetimeoffset relative strutture corrispondenti (`SQL_SS_TIME2_STRUCT` e **valore SQL_SS_TIMESTAMPOFFSET_STRUCT**), *TargetType* deve essere specificata come `SQL_C_DEFAULT` o `SQL_C_BINARY`.  
  
 Per altre informazioni, vedere [data e miglioramenti per la fase &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlbindcol-support-for-large-clr-udts"></a>Supporto di SQLBindCol per tipi CLR definiti dall'utente di grandi dimensioni  
 **SQLBindCol** supporta grandi CLR a tipi definiti dall'utente (UDT). Per altre informazioni, vedere [Large CLR User-Defined tipi &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione SQLBindCol](http://go.microsoft.com/fwlink/?LinkId=59327)   
 [Dettagli di implementazione dell'API ODBC](odbc-api-implementation-details.md)  
  
  
