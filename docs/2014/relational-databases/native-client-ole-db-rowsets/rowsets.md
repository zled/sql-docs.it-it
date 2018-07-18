---
title: I set di righe | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], about rowsets
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets
- OLE DB rowsets, about rowsets
- rowsets [OLE DB]
ms.assetid: 5e7b3cbe-3670-4e18-8172-2226e0b6b142
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 73f16529f84fd9a7eb0158061ab4f875050a8496
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37411710"
---
# <a name="rowsets"></a>Set di righe
  Le righe di un set di righe contengono colonne di dati. I set di righe sono oggetti centrali che consentono a tutti i provider di dati OLE DB di esporre dati di set di risultati in formato tabulare.  
  
 Dopo che un utente crea una sessione utilizzando il **IDBCreateSession:: CreateSession** metodo, il consumer può utilizzare l'il **IOpenRowset** oppure **IDBCreateCommand** interfaccia nella sessione per creare un set di righe. Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client supporta entrambe le interfacce. Di seguito sono descritti i due metodi.  
  
-   Creare un set di righe chiamando il **IOpenRowset:: OPENROWSET** (metodo).  
  
     Questo metodo equivale a chiamare un set di righe in una singola tabella e consente di aprire e restituire un set di righe che include tutte le righe di una singola tabella di base. Uno degli argomenti per **OpenRowset** è un ID di tabella che identifica la tabella da cui creare il set di righe.  
  
-   Creare un oggetto comando chiamando il **IDBCreateCommand** (metodo).  
  
     L'oggetto comando esegue comandi supportati dal provider. Con il provider OLE DB di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, il consumer può specificare qualsiasi istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)], ad esempio un'istruzione SELECT o una chiamata a una stored procedure. Di seguito sono elencati i passaggi per la creazione di un set di righe tramite un oggetto comando:  
  
    1.  Il consumer chiama il **IDBCreateCommand** metodo nella sessione per ottenere un oggetto comando che richieda il **ICommandText** interfaccia sull'oggetto del comando. Ciò **ICommandText** interfaccia imposta e recupera il testo del comando effettivo. Il consumer inserisce il comando di testo chiamando il **ICommandText:: SetCommandText** (metodo).  
  
    2.  L'utente chiama il **ICommand:: Execute** metodo sul comando. L'oggetto set di righe compilato durante l'esecuzione del comando contiene il set di risultati restituito dal comando.  
  
 Il consumer può utilizzare il **ICommandProperties** interfaccia da ottenere o impostare le proprietà per il set di righe restituito dal comando eseguito dalle **ICommand:: Execute** interfacce. Le proprietà generalmente più richieste sono le interfacce che il set di righe deve supportare. Oltre alle interfacce, il consumer può richiedere proprietà che modificano il comportamento del set di righe o dell'interfaccia.  
  
 I consumer rilasciano set di righe con la **IRowset:: Release** (metodo). Il rilascio di un set di righe comporta anche il rilascio di tutti gli handle di riga gestiti dal consumer per tale set di righe, ma non comporta il rilascio delle funzioni di accesso. Se si dispone di un **IAccessor** interfaccia, anche questa deve essere rilasciato.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
-   [Creazione di un set di righe con IOpenRowset](creating-a-rowset-with-iopenrowset.md)  
  
-   [Creazione di set di righe con ICommand::Execute](creating-rowsets-with-icommand-execute.md)  
  
-   [Proprietà e comportamenti dei set di righe](rowset-properties-and-behaviors.md)  
  
-   [Set di righe e cursori SQL Server](rowsets-and-sql-server-cursors.md)  
  
-   [Recupero di righe](fetching-rows.md)  
  
-   [Recupero di una sola riga con IRow](fetching-a-single-row-with-irow.md)  
  
-   [Segnalibri](bookmarks.md)  
  
-   [Aggiornamento dei dati nei set di righe](updating-data-in-rowsets.md)  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
