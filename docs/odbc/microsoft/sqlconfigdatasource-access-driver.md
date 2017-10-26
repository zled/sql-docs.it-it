---
title: SQLConfigDataSource (Driver di accesso) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLConfigDataSource function [ODBC], Access Driver
- Access driver [ODBC], SQLConfigDataSource
ms.assetid: 1b152fb7-fa12-46b9-b168-006bb1355e77
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 24154cb8cf4f07699385f773608b929a9a4ed4a3
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlconfigdatasource-access-driver"></a>SQLConfigDataSource (Driver di accesso)
> [!NOTE]  
>  In questo argomento fornisce informazioni di accesso specifici del Driver. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Il **SQLConfigDataSource** funzione che consente di aggiungere, modificare o eliminare un'origine dati utilizzata in modo dinamico le parole chiave seguenti.  
  
|Parola chiave|Description|  
|-------------|-----------------|  
|COLLATINGSEQUENCE|La sequenza in cui i campi vengono ordinati.<br /><br /> Consente di impostare la stessa opzione come **sequenza di ordinamento** nella finestra di dialogo programma di installazione.|  
|COMPACT_DB|Esegue la compattazione dei dati in un file di database. Ha il seguente formato: COMPACT_DB = < nome_percorso >< optionaL_sort_order >\<parola chiave di crittografia facoltativa >.<br /><br /> Quando si utilizza la parola chiave COMPACT_DB nella stessa istruzione con una parola chiave DSN, il driver ignora la parola chiave DSN. Pertanto, la compattazione di un database e specificando un DSN è un processo in due fasi.|  
|CREATE_DB|Crea un file di database. Ha il seguente formato: CREATE_DB = < nome_percorso >\<optional_sort ordine >< optional_ENCRYPT (parola chiave) >, dove il nome del percorso è il percorso completo di un database Microsoft Access. Se il nome di percorso specifica un database esistente, verrà restituito un errore. L'ordinamento sarà come set di backup nella finestra di dialogo Nuovo Database visualizzato quando viene premuto il pulsante Crea nella finestra di dialogo di installazione di Microsoft Access. Se viene specificato alcun ordinamento, viene utilizzato generale.<br /><br /> Quando si utilizza la parola chiave CREATE_DB nella stessa istruzione con una parola chiave DSN, il driver ignora la parola chiave DSN. Pertanto, la creazione di un database e specificando un DSN è un processo in due fasi. Quando si utilizza la parola chiave CREATE_DB, se il percorso del database di Microsoft Access da creare contiene uno o più spazi, quindi l'intero percorso debba essere racchiusi tra virgolette doppie, come illustrato negli esempi seguenti:<br /><br /> "C:\PROGRAM FILES\COMMON Files \ MyAccess.mdb"<br /><br /> "C:\Programmi\Microsoft FILES\Access2.mdb"<br /><br /> CREATE_DB=C:\TEMP\test.mdb (virgolette non necessite)|  
|CREATE_SYSDB|Crea un file di database di sistema. Ha il seguente formato: CREATE_SYSDB =\<percorso-name >\<facoltativo ordinamento >, dove il nome del percorso è il percorso completo di un database Microsoft Access. Se il nome di percorso specifica un database esistente, verrà restituito un errore. L'ordinamento verrà incluso come set di backup di **Nuovo Database** finestra di dialogo visualizzata quando il **crea** pulsante nel **ODBC Microsoft Access Setup** la finestra di dialogo. Se viene specificato alcun ordinamento, viene utilizzato generale.|  
|CREATE_V2DB|Crea un file di database è compatibile con Microsoft Access 2.0. Ha il seguente formato: CREATE_V2DB =\<percorso-name >\<facoltativo ordinamento >, dove il nome del percorso è il percorso completo di un database Microsoft Access. Se il nome di percorso specifica un database esistente, verrà restituito un errore. L'ordinamento sarà come set di backup nella finestra di dialogo Nuovo Database visualizzato quando viene premuto il pulsante Crea nella finestra di dialogo di installazione di Microsoft Access. Se viene specificato alcun ordinamento, viene utilizzato generale.<br /><br /> Quando si utilizza la parola chiave CREATE_V2DB nella stessa istruzione con una parola chiave DSN, il driver ignora la parola chiave DSN. Pertanto, la creazione di un database e specificando un DSN è un processo in due fasi.<br /><br /> Quando si utilizza la parola chiave CREATE_V2DB, se il percorso del database di Microsoft Access da creare contiene uno o più spazi, quindi l'intero percorso debba essere racchiusi tra virgolette doppie, come illustrato negli esempi seguenti:<br /><br /> "C:\PROGRAM FILES\COMMON Files \ MyAccess.mdb"<br /><br /> "C:\Programmi\Microsoft FILES\Access2.mdb"<br /><br /> CREATE_V2DB=C:\TEMP\test.mdb (virgolette non necessite)|  
|DBQ|Il nome del file di database.<br /><br /> Consente di impostare la stessa opzione come **Database** nella finestra di dialogo programma di installazione.|  
|DEFAULTDIR|La specifica del percorso del file di database.|  
|DESCRIPTION|Una descrizione dei dati nell'origine dati.<br /><br /> Consente di impostare la stessa opzione come **descrizione** nella finestra di dialogo programma di installazione.|  
|DRIVER|La specifica del percorso per la DLL del driver.|  
|DRIVERID|Un ID di tipo integer per il driver.  25 (Microsoft Access)|  
|FIL|Tipo di accesso MS per l'accesso a Microsoft di file|  
|IMPLICITCOMMITSYNC|Determina se il driver Microsoft Access eseguirà commit interno o implicito in modo asincrono. Questo valore è inizialmente impostato su "Sì", il che significa che il driver Microsoft Access attenderà per commit in una transazione interna/implicita per il completamento.<br /><br /> Il valore di questa opzione non deve essere modificato senza un'attenta valutazione delle conseguenze. Per ulteriori informazioni sull'opzione, vedere il *manuale del programmatore di Microsoft Jet Database Engine*.<br /><br /> Consente di impostare la stessa opzione come **ImplicitCommitSync** nella finestra di dialogo programma di installazione.|  
|MAXBUFFERSIZE|Le dimensioni del buffer interno, espressa in kilobyte, utilizzata da Microsoft Access per trasferire i dati da e verso il disco. Le dimensioni del buffer predefinita sono 2048 KB (visualizzata come 2048). Qualsiasi valore intero divisibile per 256 può essere utilizzato. Consente di impostare la stessa opzione come **dimensioni del Buffer** nella finestra di dialogo programma di installazione.|  
|MAXSCANROWS|Il numero di righe da analizzare per l'impostazione di un tipo di dati colonna sulla base dei dati esistenti.<br /><br /> Per le righe da analizzare, è possibile specificare un numero compreso tra 1 e 16. Il valore predefinito è 8; Se è impostato su 0, vengono analizzate tutte le righe. (Un numero di fuori del limite verrà restituito un errore).<br /><br /> Consente di impostare la stessa opzione come **righe da analizzare** nella finestra di dialogo programma di installazione.|  
|PAGETIMEOUT|Specifica il periodo di tempo, espresso in millisecondi, che una pagina (se non utilizzato) rimane nel buffer prima di essere rimossa. Il valore predefinito è cinque-decimi di secondo (0,5 secondi). Si noti che questa opzione si applica a tutte le origini dati che utilizzano il driver ODBC.<br /><br /> Consente di impostare la stessa opzione come **Page Timeout** nella finestra di dialogo programma di installazione.|  
|PWD|Password.|  
|READONLY|TRUE per rendere i file di sola lettura. FALSE per rendere i file non di sola lettura.<br /><br /> Consente di impostare la stessa opzione come **in sola lettura** nella finestra di dialogo programma di installazione.|  
|REPAIR_DB|Consente di ripristinare un database danneggiato a causa di un errore che si verifica durante il processo di commit.<br /><br /> Quando si utilizza la parola chiave REPAIR_DB nella stessa istruzione con una parola chiave DSN, il driver ignora la parola chiave DSN. Pertanto, il ripristino di un database e specificando un DSN è un processo in due fasi.|  
|SYSTEMDB|Per il driver Microsoft Access, la specifica del percorso per il file di database di sistema.<br /><br /> Consente di impostare la stessa opzione come **Database di sistema** nella finestra di dialogo programma di installazione.|  
|THREAD|Il numero di thread in background per il motore da utilizzare. Il valore predefinito è 3, ma può essere modificato.<br /><br /> Consente di impostare la stessa opzione come **thread** nella finestra di dialogo programma di installazione.|  
|UID|Per il driver Microsoft Access, il nome dell'ID utente utilizzato per l'account di accesso.|  
|USERCOMMITSYNC|Determina se il driver Microsoft Access eseguirà in modo asincrono le transazioni definite dall'utente. Questo valore è inizialmente impostato su "Sì", il che significa che il driver Microsoft Access attenderà per commit in una transazione definita dall'utente per il completamento.<br /><br /> Il valore di questa opzione non deve essere modificato senza un'attenta valutazione delle conseguenze. Per ulteriori informazioni sull'opzione, vedere il *manuale del programmatore di Microsoft Jet Database Engine*.<br /><br /> Consente di impostare la stessa opzione come **UserCommitSync** nella finestra di dialogo programma di installazione.|

