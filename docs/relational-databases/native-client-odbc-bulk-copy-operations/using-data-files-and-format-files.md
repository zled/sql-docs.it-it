---
title: Utilizzo file di dati e formato | Documenti di Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-bulk-copy-operations
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], file formats
- ODBC, functions
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [SQL Server Native Client]
- ODBC, bulk copy operations
- bulk copy [ODBC], data files
ms.assetid: c01b7155-3f0a-473d-90b7-87a97bc56ca5
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: f5c5346335b4f52e986c361f7bc9a51636659d24
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/06/2018
ms.locfileid: "39542561"
---
# <a name="using-data-files-and-format-files"></a>Utilizzo di file di dati e file di formato
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Il programma per la copia bulk più semplice effettua le operazioni seguenti:  
  
1.  Chiamate [bcp_init](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) per specificare la copia di massa out (set BCP_OUT) da una tabella o visualizzazione di un file di dati.  
  
2.  Chiamate [bcp_exec](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md) per eseguire l'operazione di copia di massa.  
  
 Poiché il file di dati viene creato in modalità nativa, i dati di tutte le colonne nella tabella o nella vista vengono archiviati nel file di dati con lo stesso formato utilizzato nel database. Il file può essere quindi oggetto di copia bulk in un server utilizzando questi stessi passaggi e impostando DB_IN anziché DB_OUT. È possibile procedere in questo modo solo se le tabelle di origine e di destinazione hanno una struttura identica. Il file di dati risultante può essere immesso anche per la **bcp** utilità utilizzando il **/n** switch (modalità nativa).  
  
 Per eseguire la copia bulk dal set di risultati di un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] anziché direttamente da una tabella o una vista:  
  
1.  Chiamare **bcp_init** per specificare la copia di massa out, ma specificare NULL per il nome della tabella.  
  
2.  Chiamare [bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) con *eOption* impostato su BCPHINTS e *iValue* impostato su un puntatore a una stringa SQLTCHAR contenente l'istruzione Transact-SQL.  
  
3.  Chiamare **bcp_exec** per eseguire l'operazione di copia di massa.  
  
 L'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] può essere qualsiasi istruzione che genera un set di risultati. Il file di dati creato contiene il primo set di risultati dell'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)]. Nella copia bulk viene ignorato qualsiasi set di risultati successivo al primo se tramite l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] vengono generati più set di risultati.  
  
 Per creare un file di dati in quale colonna vengono memorizzati in un formato diverso da quello della tabella, chiamare [bcp_columns](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md) per specificare quante colonne verranno modificate, quindi chiamare [bcp_colfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md) per ogni colonna il cui formato si desidera modificare. Questa operazione viene eseguita dopo la chiamata a **bcp_init** , ma prima di chiamare **bcp_exec**. **bcp_colfmt** specifica il formato in cui i dati della colonna sono memorizzati nel file di dati. e può essere utilizzato quando esegue una copia bulk interna o esterna. È inoltre possibile utilizzare **bcp_colfmt** per impostare i caratteri di terminazione di riga e colonna. Ad esempio, se i dati non contengono caratteri di tabulazione, è possibile creare un file delimitato da tabulazioni utilizzando **bcp_colfmt** per impostare il carattere di tabulazione come terminatore di ciascuna colonna.  
  
 Quando la massa copiato e **bcp_colfmt**, è possibile creare facilmente un file di formato che descrivono il file di dati creato chiamando [bcp_writefmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-writefmt.md) dopo l'ultima chiamata a **bcp_colfmt**.  
  
 La copia di massa da un file di dati descritto da un file di formato, leggere il file di formato tramite la chiamata [bcp_readfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md) dopo **bcp_init** ma prima che **bcp_exec**.  
  
 Il **bcp_control** funzione controlla diverse opzioni durante la copia di massa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da un file di dati. **sono** Imposta opzioni, ad esempio il numero massimo di errori prima della chiusura, la riga del file in cui iniziare la copia di massa, la riga arrestare su e la dimensione del batch.  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di operazioni di copia Bulk &#40;ODBC&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
  
