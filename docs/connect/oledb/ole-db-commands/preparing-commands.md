---
title: Preparazione dei comandi | Documenti Microsoft
description: Preparazione dei comandi utilizzando il Driver OLE DB per SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-commands
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, commands
- prepared statements [OLE DB Driver for SQL Server]
- commands [OLE DB]
- command preparation [OLE DB Driver for SQL Server]
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3e3a0881b3796f1077eee4e8bcc6d8f0d9573a93
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2018
---
# <a name="preparing-commands"></a>Preparazione dei comandi
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Il Driver OLE DB per SQL Server supporta la preparazione del comando per l'esecuzione multipla ottimizzata di un singolo comando; Tuttavia, la preparazione del comando genera un overhead e un consumer non è necessario preparare un comando per eseguirlo più volte. In genere, un comando deve essere preparato se verrà eseguito più di tre volte.  
  
 Per motivi relativi alle prestazioni, la preparazione dei comandi viene rinviata fino all'esecuzione del comando. Questo è il comportamento predefinito. Eventuali errori nel comando da preparare verranno rilevati solo dopo l'esecuzione del comando o dell'operazione di metaproprietà. L'impostazione della proprietà di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SSPROP_DEFERPREPARE su FALSE può determinare la disattivazione del comportamento predefinito.  
  
 In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], quando un comando viene eseguito direttamente (senza preparazione iniziale), viene creato un piano di esecuzione che viene memorizzato nella cache. Se l'istruzione SQL viene eseguita nuovamente, in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] è disponibile un algoritmo efficiente che consente di mettere in corrispondenza la nuova istruzione con il piano di esecuzione esistente nella cache e di riutilizzare il piano di esecuzione per l'istruzione in questione.  
  
 Per i comandi preparati [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fornisce supporto nativo per la preparazione e l'esecuzione delle relative istruzioni. Quando si prepara un'istruzione, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] consente di creare un piano di esecuzione, di memorizzarlo nella cache e di restituire al provider un handle al piano di esecuzione. Il provider quindi utilizza l'handle per eseguire ripetutamente l'istruzione. Non vengono create stored procedure. Poiché l'handle identifica direttamente il piano di esecuzione per un'istruzione SQL, anziché mettere in corrispondenza l'istruzione al piano di esecuzione nella cache (come nel caso dell'esecuzione diretta), è più efficiente preparare un'istruzione piuttosto che eseguirla direttamente, se è noto che l'istruzione verrà eseguita più volte.  
  
 In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] le istruzioni preparate non possono essere utilizzate per creare oggetti temporanei e non possono fare riferimento a stored procedure di sistema che creano oggetti temporanei, ad esempio tabelle temporanee. Tali procedure devono essere eseguite in modo diretto.  
  
 Alcuni comandi non devono essere mai preparati, ad esempio quelli che specificano l'esecuzione di stored procedure o includono testo non valido per la creazione di stored procedure di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Se viene creata una stored procedure temporanea, il Driver OLE DB per SQL Server esegue la stored procedure temporanea, restituzione di risultati come se è stata eseguita l'istruzione stessa.  
  
 Creazione di stored procedure temporanee viene controllata dal Driver OLE DB per SQL Server-proprietà di inizializzazione specifica SSPROP_INIT_USEPROCFORPREP. Se il valore della proprietà è SSPROPVAL_USEPROCFORPREP_ON o SSPROPVAL_USEPROCFORPREP_ON_DROP, il Driver OLE DB per SQL Server tenta di creare una stored procedure quando viene preparato un comando. La creazione della stored procedure riesce se l'utente dell'applicazione dispone di autorizzazioni sufficienti per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Per i consumer che si disconnettono raramente, la creazione di stored procedure temporanee può richiedere notevoli risorse di **tempdb**, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database di sistema in cui vengono creati oggetti temporanei. Quando il valore di SSPROP_INIT_USEPROCFORPREP è sspropval_useprocforprep _ ON, le stored procedure temporanee create dal Driver OLE DB per SQL Server vengono eliminate solo quando la sessione che ha creato il comando perde la connessione all'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Se la connessione in oggetto è quella predefinita, creata al momento dell'inizializzazione dell'origine dati, la stored procedure temporanea viene eliminata solo quando l'origine dati diventa non inizializzata.  
  
 Quando il valore di SSPROP_INIT_USEPROCFORPREP è SSPROPVAL_USEPROCFORPREP_ON_DROP, le procedure Driver OLE DB per SQL Server temporaneo archiviate vengono eliminate quando si verifica una delle operazioni seguenti:  
  
-   Il consumer utilizza **ICommandText:: SetCommandText** per indicare un nuovo comando.  
  
-   Il consumer utilizza **ICommandPrepare::** per indicare che il testo del comando non è più necessario.  
  
-   Il consumer rilascia tutti i riferimenti all'oggetto comando utilizzando la stored procedure temporanea.  
  
 Un oggetto comando dispone al massimo una stored procedure temporanea **tempdb**. Le stored procedure temporanee esistenti rappresentano il testo del comando corrente di un oggetto comando specifico.  
  
## <a name="see-also"></a>Vedere anche  
 [Comandi](../../oledb/ole-db-commands/commands.md)  
  
  
