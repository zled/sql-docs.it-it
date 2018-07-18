---
title: Utilizzo di file di dati e i file di formato | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
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
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f56cb9a5bd18ca4080d16b3fa2a4fdbff0398247
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37417990"
---
# <a name="using-data-files-and-format-files"></a>Utilizzo di file di dati e file di formato
  Il programma per la copia bulk più semplice effettua le operazioni seguenti:  
  
1.  Le chiamate [bcp_init](../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) specificare esegue la copia bulk (impostare BCP_OUT) da una tabella o visualizzazione su un file di dati.  
  
2.  Le chiamate [bcp_exec](../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md) per eseguire l'operazione di copia bulk.  
  
 Poiché il file di dati viene creato in modalità nativa, i dati di tutte le colonne nella tabella o nella vista vengono archiviati nel file di dati con lo stesso formato utilizzato nel database. Il file può essere quindi oggetto di copia bulk in un server utilizzando questi stessi passaggi e impostando DB_IN anziché DB_OUT. È possibile procedere in questo modo solo se le tabelle di origine e di destinazione hanno una struttura identica. Il file di dati risultante può essere immesso anche il **bcp** utilità tramite il **/n** switch (modalità nativa).  
  
 Per eseguire la copia bulk dal set di risultati di un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] anziché direttamente da una tabella o una vista:  
  
1.  Chiamare **bcp_init** per specificare la copia bulk, ma specificare NULL per il nome della tabella.  
  
2.  Chiamare [bcp_control](../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) con *eOption* impostato su BCPHINTS e *iValue* impostato su un puntatore a una stringa SQLTCHAR contenente l'istruzione Transact-SQL.  
  
3.  Chiamare **bcp_exec** per eseguire l'operazione di copia bulk.  
  
 L'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] può essere qualsiasi istruzione che genera un set di risultati. Il file di dati creato contiene il primo set di risultati dell'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)]. Nella copia bulk viene ignorato qualsiasi set di risultati successivo al primo se tramite l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] vengono generati più set di risultati.  
  
 Per creare un file di dati nella colonna da cui i dati vengono archiviati in un formato diverso da quello della tabella, chiamare [bcp_columns](../native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md) per specificare quante colonne verranno modificate, quindi chiamare [bcp_colfmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md) per ogni colonna il cui formato si desidera modificare. Questa operazione viene eseguita dopo la chiamata **bcp_init** ma prima di chiamare **bcp_exec**. **bcp_colfmt** specifica il formato in cui i dati della colonna vengano archiviati nel file di dati. e può essere utilizzato quando esegue una copia bulk interna o esterna. È anche possibile usare **bcp_colfmt** per impostare i caratteri di terminazione di riga e colonna. Ad esempio, se i dati non contengono caratteri Nessuna scheda, è possibile creare un file delimitato da tabulazioni usando **bcp_colfmt** per impostare il carattere di tabulazione come carattere di terminazione per ogni colonna.  
  
 Quando si esegue bulk copia e l'utilizzo **bcp_colfmt**, è possibile creare facilmente un file di formato che descriva il file di dati creato chiamando [bcp_writefmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-writefmt.md) dopo l'ultima chiamata a **bcp_colfmt**.  
  
 Quando si esegue la copia bulk da un file di dati descritto da un file di formato, leggere il file di formato chiamando [bcp_readfmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md) dopo **bcp_init** ma prima **bcp_exec**.  
  
 Il **bcp_control** funzione controlla diverse opzioni durante la copia bulk in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da un file di dati. **bcp_control** Imposta opzioni, ad esempio il numero massimo di errori prima della chiusura, la riga nel file in cui iniziare la copia bulk, la riga arrestare in e le dimensioni del batch.  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di operazioni di copia Bulk &#40;ODBC&#41;](performing-bulk-copy-operations-odbc.md)  
  
  
