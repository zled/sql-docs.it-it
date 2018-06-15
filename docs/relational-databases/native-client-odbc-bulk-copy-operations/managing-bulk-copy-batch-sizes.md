---
title: Gestire le dimensioni di Batch di copia Bulk | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-bulk-copy-operations
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, bulk copy
- ODBC, bulk copy operations
- batches [ODBC]
- bulk copy [ODBC], batch sizes
ms.assetid: 4b24139f-788b-45a6-86dc-ae835435d737
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 816f5ec577e65b84e23ba538008d06542348f02c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32945636"
---
# <a name="managing-bulk-copy-batch-sizes"></a>Gestione delle dimensioni dei batch di copia bulk
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Lo scopo principale di un batch nelle operazioni di copia bulk è definire l'ambito di una transazione. Se non si impostano le dimensioni del batch, le funzioni di copia bulk considerano un'intera copia bulk come una transazione. Se le dimensioni del batch vengono impostate, ogni batch rappresenterà una transazione di cui verrà eseguito il commit alla fine dell'esecuzione.  
  
 Se una copia bulk viene eseguita senza specificare le dimensioni del batch e si verifica un errore, viene eseguito il rollback dell'intera copia bulk. Il recupero di una copia bulk con esecuzione prolungata può richiedere molto tempo. Quando vengono impostate le dimensioni di un batch, la copia bulk considera ogni batch come una singola transazione e ne esegue il commit. Se si verifica un errore, è necessario eseguire il rollback solo dell'ultimo batch in attesa.  
  
 Le dimensioni del batch possono influire anche sull'overhead dei blocchi. Quando si esegue una copia bulk in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], può essere specificato l'hint TABLOCK utilizzando [bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) di acquisire un blocco di tabella anziché blocchi di riga. Il singolo blocco di tabella può essere gestito con un overhead minimo per un'operazione di copia bulk intera. Se TABLOCK non viene specificato, i blocchi vengono gestiti su righe singole e l'overhead della gestione di tutti i blocchi per la durata della copia bulk può rallentare le prestazioni. Poiché i blocchi vengono gestiti solo per la durata di una transazione, la specifica delle dimensioni del batch risolve il problema grazie alla generazione periodica di un commit che libera i blocchi attualmente gestiti.  
  
 Il numero di righe che costituiscono un batch può avere effetti significativi sulle prestazioni quando si esegue la copia bulk di un gran numero di righe. I requisiti per le dimensioni del batch dipendono dal tipo di copia bulk eseguita.  
  
-   Quando si esegue la copia bulk in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], specificare l'hint di copia bulk TABLOCK e impostare le dimensioni del batch su un valore grande.  
  
-   Quando TABLOCK non viene specificato, impostare le dimensioni del batch su un valore che non superi 1.000 righe.  
  
 Quando si esegue la copia bulk da un file di dati, le dimensioni del batch viene specificata chiamando **bcp_control** con l'opzione BCPBATCH prima di chiamare [bcp_exec](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md). Quando esegue la copia bulk dalle variabili di programma utilizzando [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) e [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md), le dimensioni del batch vengono controllate chiamando [bcp_batch](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md) dopo la chiamata [bcp_ sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) *x* volte, dove *x* è il numero di righe in un batch.  
  
 Oltre a specificare le dimensioni di una transazione, i batch influiscono anche sull'invio in rete delle righe al server. Funzioni di copia bulk in genere memorizzano nella cache le righe da **bcp_sendrow** fino a quando non viene compilato un pacchetto di rete e quindi inviare il pacchetto completo al server. Quando un'applicazione chiama **bcp_batch**, tuttavia, il pacchetto corrente viene inviato al server indipendentemente dal fatto che è stato compilato. L'utilizzo di dimensioni del batch molto ridotte può rallentare le prestazioni se determina l'invio al server di più pacchetti riempiti parzialmente. Ad esempio, la chiamata **bcp_batch** dopo ogni **bcp_sendrow** , ogni riga da inviare in un pacchetto separato e, a meno che le righe sono molto grandi, comporta uno spreco di spazio in ogni pacchetto. Le dimensioni predefinite dei pacchetti di rete per SQL Server sono 4 KB, anche se un'applicazione può modificare le dimensioni chiamando [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) specificando l'attributo SQL_ATTR_PACKET_SIZE.  
  
 Un altro effetto collaterale dei batch è che ogni batch viene considerato come un risultato in sospeso finché viene completato con **bcp_batch**. Se sono tentato di eseguire altre operazioni su un handle di connessione mentre un batch è in attesa, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client genera un errore con SQLState = "HY000" e una stringa di messaggio di errore:  
  
```  
"[Microsoft][SQL Server Native Client] Connection is busy with  
results for another hstmt."  
```  
  
## <a name="see-also"></a>Vedere anche  
 [L'esecuzione di operazioni di copia Bulk &#40;ODBC&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)   
 [Informazioni sull'importazione ed esportazione bulk di dati &#40;SQL Server&#41;](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)  
  
  
