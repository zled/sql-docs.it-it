---
title: Set di righe | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], about rowsets
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets
- OLE DB rowsets, about rowsets
- rowsets [OLE DB]
ms.assetid: 5e7b3cbe-3670-4e18-8172-2226e0b6b142
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 163ea34c14a35f46e4ee65d21ce2db22a32984e5
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2018
ms.locfileid: "35696452"
---
# <a name="rowsets"></a>Set di righe
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Le righe di un set di righe contengono colonne di dati. I set di righe sono oggetti centrali che consentono a tutti i provider di dati OLE DB di esporre dati di set di risultati in formato tabulare.  
  
 Dopo che un utente crea una sessione utilizzando il **IDBCreateSession:: CreateSession** metodo, il consumer può utilizzare l'il **IOpenRowset** o **IDBCreateCommand** interfaccia nella sessione per creare un set di righe. Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client supporta entrambe le interfacce. Di seguito sono descritti i due metodi.  
  
-   Creare un set di righe chiamando il **IOpenRowset:: OPENROWSET** metodo.  
  
     Questo metodo equivale a chiamare un set di righe in una singola tabella e consente di aprire e restituire un set di righe che include tutte le righe di una singola tabella di base. Uno degli argomenti per **OpenRowset** è un ID di tabella che identifica la tabella da cui creare il set di righe.  
  
-   Creare un oggetto comando chiamando il **IDBCreateCommand** metodo.  
  
     L'oggetto comando esegue comandi supportati dal provider. Con il provider OLE DB di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, il consumer può specificare qualsiasi istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)], ad esempio un'istruzione SELECT o una chiamata a una stored procedure. Di seguito sono elencati i passaggi per la creazione di un set di righe tramite un oggetto comando:  
  
    1.  Il consumer chiama il **IDBCreateCommand** metodo nella sessione per ottenere un oggetto comando che richiede il **ICommandText** interfaccia sull'oggetto command. Ciò **ICommandText** interfaccia imposta e recupera il testo del comando effettivo. Il consumer inserisce il comando di testo chiamando il **ICommandText:: SetCommandText** metodo.  
  
    2.  L'utente chiama il **ICommand:: Execute** metodo sul comando. L'oggetto set di righe compilato durante l'esecuzione del comando contiene il set di risultati restituito dal comando.  
  
 Il consumer può utilizzare il **ICommandProperties** interfaccia da ottenere o impostare le proprietà per il set di righe restituito dal comando eseguito dal **ICommand:: Execute** interfacce. Le proprietà generalmente più richieste sono le interfacce che il set di righe deve supportare. Oltre alle interfacce, il consumer può richiedere proprietà che modificano il comportamento del set di righe o dell'interfaccia.  
  
 I consumer rilasciano set di righe con la **IRowset:: Release** metodo. Il rilascio di un set di righe comporta anche il rilascio di tutti gli handle di riga gestiti dal consumer per tale set di righe, ma non comporta il rilascio delle funzioni di accesso. Se dispone di un **IAccessor** interfaccia, questa deve essere rilasciato.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
-   [Creazione di un set di righe con IOpenRowset](../../relational-databases/native-client-ole-db-rowsets/creating-a-rowset-with-iopenrowset.md)  
  
-   [Creazione di set di righe con ICommand::Execute](../../relational-databases/native-client-ole-db-rowsets/creating-rowsets-with-icommand-execute.md)  
  
-   [Proprietà e comportamenti dei set di righe](../../relational-databases/native-client-ole-db-rowsets/rowset-properties-and-behaviors.md)  
  
-   [Set di righe e cursori SQL Server](../../relational-databases/native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md)  
  
-   [Recupero di righe](../../relational-databases/native-client-ole-db-rowsets/fetching-rows.md)  
  
-   [Recupero di una sola riga con IRow](../../relational-databases/native-client-ole-db-rowsets/fetching-a-single-row-with-irow.md)  
  
-   [Segnalibri](../../relational-databases/native-client-ole-db-rowsets/bookmarks.md)  
  
-   [Aggiornamento dei dati nei set di righe](../../relational-databases/native-client-ole-db-rowsets/updating-data-in-rowsets.md)  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
