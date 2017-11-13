---
title: Impostazione delle opzioni a livello di codice per il Driver Paradox | Documenti Microsoft
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
- ODBC desktop database drivers [ODBC], Paradox driver
- Paradox driver [ODBC], setting options programmatically
- desktop database drivers [ODBC], Paradox driver
- Jet-based ODBC drivers [ODBC], Paradox driver
ms.assetid: 7996d3f8-b5f5-4cac-8a66-fc96a42b603e
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c353ec7cca4744a4189891a4123eaf6263b8fd51
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="setting-options-programmatically-for-the-paradox-driver"></a>Impostazione delle opzioni a livello di codice per il Driver Paradox
|Opzione|Description|Metodo|  
|------------|-----------------|------------|  
|Directory|Imposta la directory di destinazione.|Per impostare questa opzione in modo dinamico, usare il **DEFAULTDIR** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Sequenza di confronto|La sequenza in cui i campi vengono ordinati.<br /><br /> La sequenza può essere ASCII (impostazione predefinita), internazionale, Finnish-Swedish o Norvegese danese.|Per impostare questa opzione in modo dinamico, usare il **COLLATINGSEQUENCE** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Description|Una descrizione facoltativa dei dati nell'origine dati; ad esempio, "Hire date, cronologia stipendi e situazione corrente di tutti i dipendenti."|Per impostare questa opzione in modo dinamico, usare il **descrizione** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Exclusive|Se il **esclusivo** è selezionata, il database verrà aperto in modalità esclusiva e accessibili da un solo utente alla volta. Prestazioni risulta migliorata quando viene eseguito in modalità esclusiva.|Per impostare questa opzione in modo dinamico, usare il **esclusivo** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Tipo di accesso|Il tipo di accesso di rete da utilizzare per l'accesso ai dati Paradox: entrambi "3.*x*" per Paradox 3. *x* o "4. *x*"per Paradox 4. *x* o 5. *x*. Può essere impostato su "3. *x*"o" 4. *x*"se la versione 4 Paradox. *x* o 5. *x*; se la versione 3 Paradox. *x*, lo stile deve essere "3. *x*".|Per impostare questa opzione in modo dinamico, usare il **PARADOXNETSTYLE** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Timeout di pagina|Specifica il periodo di tempo, in decimi di secondo, che una pagina (se non utilizzato) rimane nel buffer prima di essere rimossa. Il valore predefinito è 600 decimi di secondo (60 secondi). Questa opzione si applica a tutte le origini dati che utilizzano il driver ODBC.<br /><br /> Il timeout di pagina non può essere 0 a causa di un ritardo inerente. Il timeout di pagina non può essere minore del ritardo intrinseco, anche se è impostata l'opzione di timeout della pagina di sotto di tale valore.|Per impostare questa opzione in modo dinamico, usare il **PAGETIMEOUT** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Read Only|Indica il database in sola lettura.|Per impostare questa opzione in modo dinamico, usare il **READONLY** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Selezionare la Directory|Visualizza una finestra di dialogo in cui è possibile selezionare una directory che contiene i file che si desidera accedere.<br /><br /> Quando la definizione di una directory di origine dati specifica la directory in più file utilizzati di frequente si trovano. Il driver ODBC utilizza questa directory come la directory predefinita. Copiare gli altri file in questa directory se vengono usati frequentemente. In alternativa, è possibile qualificare i nomi di file in un'istruzione SELECT con il nome della directory:<br /><br /> SELEZIONARE \* DA C:\MYDIR\EMP<br /><br /> In alternativa, è possibile specificare una nuova directory predefinita utilizzando il **SQLSetConnectOption** funzione con l'opzione SQL_CURRENT_QUALIFIER.|Per impostare questa opzione in modo dinamico, usare il **DEFAULTDIR** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Selezionare la Directory di rete|Il percorso completo della directory contenente un database di blocco Paradox, perché contiene il file Pdoxusrs.net (4 Paradox. *x*) o il file Paradox.net (5 Paradox. *x*). Se la directory non contiene uno di questi file, il driver Paradox viene creata una. Per informazioni su questi file, vedere la documentazione di Paradox.<br /><br /> Prima di poter selezionare una directory di rete, è necessario immettere il nome utente Paradox il **nome utente** casella di testo. Fare clic su **seleziona Directory di rete** per selezionare una directory di rete.|Per impostare questa opzione in modo dinamico, usare il **PARADOXNETPATH** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Nome utente|Il nome utente Paradox. Questo è il nome visualizzato agli altri utenti di file Paradox quando viene incontrato un blocco.|Per impostare questa opzione in modo dinamico, usare il **PARADOXUSERNAME** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|

