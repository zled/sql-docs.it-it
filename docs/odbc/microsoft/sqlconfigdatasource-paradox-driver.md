---
title: SQLConfigDataSource (Driver Paradox) | Documenti Microsoft
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
- SQLConfigDataSource function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLConfigDataSource
ms.assetid: 59e84c4e-debe-49d7-b97b-84c736b0c793
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b9acd359d2d99531e3fe4092b3bd20f00e94622a
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlconfigdatasource-paradox-driver"></a>SQLConfigDataSource (Paradox Driver)
> [!NOTE]  
>  In questo argomento fornisce informazioni specifiche del Driver Paradox. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Il **SQLConfigDataSource** funzione che consente di aggiungere, modificare o eliminare un'origine dati utilizzata in modo dinamico le parole chiave seguenti.  
  
|Parola chiave|Description|  
|-------------|-----------------|  
|COLLATINGSEQUENCE|La sequenza in cui i campi vengono ordinati.<br /><br /> Quando viene utilizzato il driver Paradox, la sequenza può essere ASCII (impostazione predefinita), internazionale, Finnish-Swedish o Norvegese danese.<br /><br /> Consente di impostare la stessa opzione come **sequenza di ordinamento** nella finestra di dialogo programma di installazione.|  
|DBQ|Il nome del file di database.<br /><br /> Consente di impostare la stessa opzione come **Database** nella finestra di dialogo programma di installazione.|  
|DEFAULTDIR|La specifica del percorso della directory.|  
|DESCRIPTION|Una descrizione dei dati nell'origine dati.<br /><br /> Consente di impostare la stessa opzione come **descrizione** nella finestra di dialogo programma di installazione.|  
|DRIVER|La specifica del percorso per la DLL del driver.|  
|DRIVERID|Un ID di tipo integer per il driver.<br /><br /> 26 (paradox 3. x)<br /><br /> 282 (paradox 4. x)<br /><br /> 538 (paradox 5. x)|  
|ESCLUSIVO|Determina se il database verrà aperto in modalità esclusiva (accessibili da un solo utente alla volta) o condiviso modalità (accessibili da più di un utente alla volta). Può essere true (modalità esclusiva) o false (modalità condivisa).<br /><br /> Consente di impostare la stessa opzione come **esclusivo** nella finestra di dialogo programma di installazione.|  
|FIL|File di tipo Paradox 3. x, Paradox 4. x o Paradox 5. x|  
|TIPO DI FILE|Tipo di file per il driver di testo (testo).|  
|PAGETIMEOUT|Specifica il periodo di tempo, in decimi di secondo, che una pagina (se non utilizzato) rimane nel buffer prima di essere rimossa. Il valore predefinito è 600 decimi di secondo (60 secondi). Si noti che questa opzione si applica a tutte le origini dati che utilizzano il driver ODBC.<br /><br /> Consente di impostare la stessa opzione come **Page Timeout** nella finestra di dialogo programma di installazione.|  
|PARADOXNETPATH|Il percorso completo della directory contenente un database di blocco Paradox, perché contiene il file PDOXUSRS.net (4 Paradox.* x*) o il file PARADOX.net (5 Paradox.* x*). Se la directory non contiene uno di questi file, il driver Paradox viene creata una. Per informazioni su questi file, vedere la documentazione di Paradox.<br /><br /> Prima di una directory di rete può essere selezionata, è necessario specificare un nome utente Paradox.<br /><br /> Consente di impostare la stessa opzione come **Directory di rete selezionare** nella finestra di dialogo programma di installazione.|  
|PARADOXNETSTYLE|Per il driver Paradox, la rete accedere stile da utilizzare per l'accesso ai dati Paradox: entrambi "3. x" per Paradox 3. *x* o "4. x" per Paradox 4.* x* o 5.* x*. Impostare "3" o "4" se la versione 4 Paradox. *x* o 5.* x*; se la versione 3 Paradox.* x*, lo stile deve essere "3".<br /><br /> Consente di impostare la stessa opzione come **stile Net** nella finestra di dialogo programma di installazione.|  
|PARADOXUSERNAME|Per il driver Paradox, il nome utente Paradox.<br /><br /> Consente di impostare la stessa opzione come **nome utente** nella finestra di dialogo programma di installazione.|  
|PWD|Password.<br /><br /> Questa parola chiave facoltativa e mai essere scritta nel file dal driver. Viene utilizzato in una chiamata a **SQLDriverConnect** sui file di Paradox protetto da password. Apertura di una tabella, la password utilizzata sarà più valida. Se nessuna password viene passata nella stringa di connessione, non viene stabilita alcuna password per la tabella. Se le tabelle avere password differenti, più di uno non è aperto nella stessa sessione, né possono essere unite le tabelle.|  
|READONLY|TRUE per rendere i file di sola lettura. FALSE per rendere i file non di sola lettura.<br /><br /> Consente di impostare la stessa opzione come **in sola lettura** nella finestra di dialogo programma di installazione.|  
|THREAD|Il numero di thread in background per il motore da utilizzare. Questo valore è 3 e non può essere modificato.<br /><br /> Consente di impostare la stessa opzione come **thread** nella finestra di dialogo programma di installazione.|
