---
title: Utilizzo dell'interfaccia IMultipleResults per elaborare più set di risultati | Documenti Microsoft
description: Utilizzo dell'interfaccia IMultipleResults per elaborare i risultati più imposta
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db-commands
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- IMultipleResults interface
- multiple-rowset results
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 162b706391e2128cb715396fd836bf446a625b17
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="using-imultipleresults-to-process-multiple-result-sets"></a>Utilizzo dell'interfaccia IMultipleResults per elaborare più set di risultati
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  I consumer utilizzano le **IMultipleResults** interfaccia per elaborare i risultati restituiti dal Driver OLE DB per l'esecuzione di comandi di SQL Server. Quando il Driver OLE DB per SQL Server invia un comando per l'esecuzione, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] esegue le istruzioni e restituisce i risultati.  
  
 Tutti i risultati ottenuti dall'esecuzione dei comandi devono essere elaborati da un client. Poiché il Driver OLE DB per l'esecuzione di comandi di SQL Server può generare gli oggetti di più set di righe come risultato, usare il **IMultipleResults** interfaccia per essere certi che il recupero dei dati applicazione completino il round trip iniziato dal client.  
  
 Le operazioni seguenti [!INCLUDE[tsql](../../../includes/tsql-md.md)] istruzione genera più set di righe, alcuni dati riga contenente la **OrderDetails** tabella e altri contengono i risultati della clausola COMPUTE BY:  
  
```  
SELECT OrderID, FullPrice = (UnitPrice * Quantity), Discount,  
    Discounted = UnitPrice * (1 - Discount) * Quantity  
FROM OrderDetails  
ORDER BY OrderID  
COMPUTE  
    SUM(UnitPrice * Quantity), SUM(UnitPrice * (1 - Discount) * Quantity)  
    BY OrderID  
```  
  
 Se un consumer esegue un comando contenente questo testo e richiede un set di righe come interfaccia dei risultati restituiti, viene restituito solo il primo set di righe. Il consumer può elaborare tutte le righe del set di righe restituito. Ma, se la proprietà dell'origine dati DBPROP_MULTIPLECONNECTIONS è impostata su VARIANT_FALSE e MARS non è abilitato per la connessione, nessun altro comando può essere eseguito per l'oggetto di sessione (il Driver OLE DB per SQL Server non creerà un'altra connessione) finché il comando viene annullato. Se MARS non è abilitato per la connessione, il Driver OLE DB per SQL Server restituisce un errore DB_E_OBJECTOPEN se DBPROP_MULTIPLECONNECTIONS è VARIANT_FALSE e restituisce E_FAIL se è presente una transazione attiva.  
  
 Il Driver OLE DB per SQL Server restituirà anche DB_E_OBJECTOPEN quando si utilizzano i parametri di output di streaming e l'applicazione non ha utilizzato tutti i valori dei parametri di output restituiti prima di chiamare **IMultipleResults:: GetResults** a ottenere il set di risultati successivo. Se MARS non è abilitato e la connessione è occupata esegue un comando che non produce un set di righe o che produce un set di righe che non è un cursore del server e se proprietà dell'origine dati DBPROP_MULTIPLECONNECTIONS è impostata su VARIANT_TRUE, il Driver OLE DB per SQL Server Crea connessioni aggiuntive per supportare gli oggetti comando simultanei, a meno che una transazione è attiva, nel qual caso restituisce un errore. Le transazioni e il blocco vengono gestiti da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per singola connessione. Se viene generata una seconda connessione, il comando sulle connessioni separate non condivide i blocchi. È necessario assicurarsi che un comando non blocchi un altro comando mantenendo attivi i blocchi sulle righe richieste da quest'ultimo. Se MARS è abilitato, è possibile disporre di più comandi attivi sulle connessioni e se vengono utilizzate transazioni esplicite tutti i comandi condividono una transazione comune.  
  
 Il consumer può annullare il comando utilizzando [issabort:: Abort](../../oledb/ole-db-interfaces/issabort-abort-ole-db.md) oppure rilasciando tutti i riferimenti mantenuti sull'oggetto comando e il set di righe derivato.  
  
 Utilizzando **IMultipleResults** in tutte le istanze consente al consumer di ottenere tutti i set di righe generato dall'esecuzione di comandi e consente ai consumer di determinare in modo appropriato il momento annullare l'esecuzione di comandi e liberare un oggetto di sessione per l'utilizzo da altri comandi.  
  
> [!NOTE]  
>  Quando si utilizzano cursori [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], l'esecuzione di comandi crea il cursore. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] restituisce l'esito positivo o negativo della creazione del cursore. Pertanto, il round trip all'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] viene completato al momento della restituzione da parte dell'esecuzione di comandi. Ogni **GetNextRows** chiamata diventa quindi un round trip. In questo modo, possono esistere più oggetti comando attivi, ognuno dei quali elabora un set di righe che rappresenta il risultato di un recupero dal cursore del server. Per ulteriori informazioni, vedere [set di righe e cursori del Server SQL](../../oledb/ole-db-rowsets/rowsets-and-sql-server-cursors.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Comandi](../../oledb/ole-db-commands/commands.md)  
  
  
