---
title: Utilizzo dell'interfaccia IMultipleResults per elaborare più set di risultati | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-ole-db-commands
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- IMultipleResults interface
- multiple-rowset results
ms.assetid: 754d3f30-7d94-4b67-8dac-baf2699ce9c6
caps.latest.revision: 40
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f3ab7376bcbb6b8237aa2600ac19fb5a13b6304f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="using-imultipleresults-to-process-multiple-result-sets"></a>Utilizzo dell'interfaccia IMultipleResults per elaborare più set di risultati
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  I consumer utilizzano il **IMultipleResults** interfaccia per elaborare i risultati restituiti da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] esecuzione del comando del provider OLE DB Native Client. Quando il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client invia un comando per l'esecuzione, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] esegue le istruzioni e restituisce i risultati.  
  
 Tutti i risultati ottenuti dall'esecuzione dei comandi devono essere elaborati da un client. Poiché il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] esecuzione del comando del provider OLE DB Native Client possono generare oggetti di più set di righe come risultato, usare il **IMultipleResults** interfaccia per essere certi che il recupero dei dati dell'applicazione viene completata la andata iniziata dal client.  
  
 Le operazioni seguenti [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione genera più set di righe, alcuni dati riga contenente la **OrderDetails** tabella e altri contengono i risultati della clausola COMPUTE BY:  
  
```  
SELECT OrderID, FullPrice = (UnitPrice * Quantity), Discount,  
    Discounted = UnitPrice * (1 - Discount) * Quantity  
FROM OrderDetails  
ORDER BY OrderID  
COMPUTE  
    SUM(UnitPrice * Quantity), SUM(UnitPrice * (1 - Discount) * Quantity)  
    BY OrderID  
```  
  
 Se un consumer esegue un comando contenente questo testo e richiede un set di righe come interfaccia dei risultati restituiti, viene restituito solo il primo set di righe. Il consumer può elaborare tutte le righe del set di righe restituito. Ma, se la proprietà dell'origine dati DBPROP_MULTIPLECONNECTIONS è impostata su VARIANT_FALSE e MARS non è abilitato per la connessione, nessun altro comando può essere eseguito sull'oggetto di sessione (la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client non creerà un'altra connessione) fino a quando non viene annullato. Se MARS non è abilitato per la connessione, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client restituisce un errore DB_E_OBJECTOPEN se DBPROP_MULTIPLECONNECTIONS è VARIANT_FALSE e restituisce E_FAIL se è presente una transazione attiva.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client restituirà anche DB_E_OBJECTOPEN quando si utilizzano i parametri di output di streaming e l'applicazione non ha utilizzato tutti i valori di parametro di output restituiti prima di chiamare **IMultipleResults:: GetResults**  per ottenere il set di risultati successivo. Se MARS non è abilitato e la connessione sta eseguendo un comando che non produce un set di righe o che produce un set di righe che non è un cursore del server e se la proprietà dell'origine dati DBPROP_MULTIPLECONNECTIONS è impostata su VARIANT_TRUE, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client Provider OLE DB consente di creare connessioni aggiuntive per supportare gli oggetti comando simultanei, a meno che una transazione è attiva, nel qual caso restituisce un errore. Le transazioni e il blocco vengono gestiti da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per singola connessione. Se viene generata una seconda connessione, il comando sulle connessioni separate non condivide i blocchi. È necessario assicurarsi che un comando non blocchi un altro comando mantenendo attivi i blocchi sulle righe richieste da quest'ultimo. Se MARS è abilitato, è possibile disporre di più comandi attivi sulle connessioni e se vengono utilizzate transazioni esplicite tutti i comandi condividono una transazione comune.  
  
 Il consumer può annullare il comando utilizzando [issabort:: Abort](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md) oppure rilasciando tutti i riferimenti mantenuti sull'oggetto comando e il set di righe derivato.  
  
 Utilizzando **IMultipleResults** in tutte le istanze consente al consumer di ottenere tutti i set di righe generato dall'esecuzione di comandi e consente ai consumer di determinare in modo appropriato il momento annullare l'esecuzione di comandi e liberare un oggetto di sessione per l'utilizzo da altri comandi.  
  
> [!NOTE]  
>  Quando si utilizzano cursori [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l'esecuzione di comandi crea il cursore. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce l'esito positivo o negativo della creazione del cursore. Pertanto, il round trip all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene completato al momento della restituzione da parte dell'esecuzione di comandi. Ogni **GetNextRows** chiamata diventa quindi un round trip. In questo modo, possono esistere più oggetti comando attivi, ognuno dei quali elabora un set di righe che rappresenta il risultato di un recupero dal cursore del server. Per ulteriori informazioni, vedere [set di righe e cursori del Server SQL](../../relational-databases/native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Comandi](../../relational-databases/native-client-ole-db-commands/commands.md)  
  
  
