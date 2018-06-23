---
title: Set di righe | Documenti Microsoft
description: Set di righe nel Driver OLE DB per SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], about rowsets
- OLE DB Driver for SQL Server, rowsets
- OLE DB rowsets
- OLE DB rowsets, about rowsets
- rowsets [OLE DB]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 8ffead535df47ea3f6937e11fa16f5e32318ecf3
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/16/2018
ms.locfileid: "35690174"
---
# <a name="rowsets"></a>Set di righe
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Le righe di un set di righe contengono colonne di dati. I set di righe sono oggetti centrali che consentono a tutti i provider di dati OLE DB di esporre dati di set di risultati in formato tabulare.  
  
 Dopo che un utente crea una sessione utilizzando il **IDBCreateSession:: CreateSession** metodo, il consumer può utilizzare l'il **IOpenRowset** o **IDBCreateCommand** interfaccia nella sessione per creare un set di righe. Il Driver OLE DB per SQL Server supporta entrambe le interfacce. Di seguito sono descritti i due metodi.  
  
-   Creare un set di righe chiamando il **IOpenRowset:: OPENROWSET** metodo.  
  
     Questo metodo equivale a chiamare un set di righe in una singola tabella e consente di aprire e restituire un set di righe che include tutte le righe di una singola tabella di base. Uno degli argomenti per **OpenRowset** è un ID di tabella che identifica la tabella da cui creare il set di righe.  
  
-   Creare un oggetto comando chiamando il **IDBCreateCommand** metodo.  
  
     L'oggetto comando esegue comandi supportati dal provider. Con il Driver OLE DB per SQL Server, il consumer può specificare qualsiasi [!INCLUDE[tsql](../../../includes/tsql-md.md)] istruzione, ad esempio un'istruzione SELECT o una chiamata a una stored procedure. Di seguito sono elencati i passaggi per la creazione di un set di righe tramite un oggetto comando:  
  
    1.  Il consumer chiama il **IDBCreateCommand** metodo nella sessione per ottenere un oggetto comando che richiede il **ICommandText** interfaccia sull'oggetto command. Ciò **ICommandText** interfaccia imposta e recupera il testo del comando effettivo. Il consumer inserisce il comando di testo chiamando il **ICommandText:: SetCommandText** metodo.  
  
    2.  L'utente chiama il **ICommand:: Execute** metodo sul comando. L'oggetto set di righe compilato durante l'esecuzione del comando contiene il set di risultati restituito dal comando.  
  
 Il consumer può utilizzare il **ICommandProperties** interfaccia da ottenere o impostare le proprietà per il set di righe restituito dal comando eseguito dal **ICommand:: Execute** interfacce. Le proprietà generalmente più richieste sono le interfacce che il set di righe deve supportare. Oltre alle interfacce, il consumer può richiedere proprietà che modificano il comportamento del set di righe o dell'interfaccia.  
  
 I consumer rilasciano set di righe con la **IRowset:: Release** metodo. Il rilascio di un set di righe comporta anche il rilascio di tutti gli handle di riga gestiti dal consumer per tale set di righe, ma non comporta il rilascio delle funzioni di accesso. Se dispone di un **IAccessor** interfaccia, questa deve essere rilasciato.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
-   [Creazione di un set di righe con IOpenRowset](../../oledb/ole-db-rowsets/creating-a-rowset-with-iopenrowset.md)  
  
-   [Creazione di set di righe con ICommand::Execute](../../oledb/ole-db-rowsets/creating-rowsets-with-icommand-execute.md)  
  
-   [Proprietà e comportamenti dei set di righe](../../oledb/ole-db-rowsets/rowset-properties-and-behaviors.md)  
  
-   [Set di righe e cursori SQL Server](../../oledb/ole-db-rowsets/rowsets-and-sql-server-cursors.md)  
  
-   [Recupero di righe](../../oledb/ole-db-rowsets/fetching-rows.md)  
  
-   [Recupero di una sola riga con IRow](../../oledb/ole-db-rowsets/fetching-a-single-row-with-irow.md)  
  
-   [Segnalibri](../../oledb/ole-db-rowsets/bookmarks.md)  
  
-   [Aggiornamento dei dati nei set di righe](../../oledb/ole-db-rowsets/updating-data-in-rowsets.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Driver OLE DB per programmazione con SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
