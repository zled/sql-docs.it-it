---
title: Impostazione di opzioni a livello di codice per il Driver dBASE | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], DBasedriver
- desktop database drivers [ODBC], DBasedriver
- DBase driver [ODBC], setting options programmatically
- ODBC desktop database drivers [ODBC], DBasedriver
ms.assetid: 336d0fd4-5448-4d8c-b7d9-49e857228e36
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fc037c3db2eddaf91338d1ce74aa4894f2a3b7b0
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="setting-options-programmatically-for-the-dbase-driver"></a>Impostazione di opzioni a livello di codice per il Driver dBASE
|Opzione|Description|Metodo|  
|------------|-----------------|------------|  
|Numero approssimativo di righe|Determina se le statistiche sulle dimensioni di tabella sono approssimative. Questa opzione si applica a tutte le origini dati che utilizzano il driver ODBC.|Per impostare questa opzione in modo dinamico, usare il **statistiche** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Sequenza di confronto|La sequenza in cui i campi vengono ordinati.<br /><br /> La sequenza può essere: ASCII (impostazione predefinita) o internazionale.|Per impostare questa opzione in modo dinamico, usare il **COLLATINGSEQUENCE** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Nome origine dati|Un nome che identifica l'origine dati, ad esempio: retribuzioni o dipendenti.|Per impostare questa opzione in modo dinamico, usare il **DSN** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Database|Un'origine dati Microsoft Access da impostare senza selezionare o creare un database. Se viene specificato alcun database al momento dell'installazione, agli utenti verranno richiesto di selezionare un file di database durante la connessione all'origine dati.|Per impostare questa opzione in modo dinamico, usare il **DBQ** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Description|Una descrizione facoltativa dei dati nell'origine dati; ad esempio, "Hire date, cronologia stipendi e situazione corrente di tutti i dipendenti."|Per impostare questa opzione in modo dinamico, usare il **descrizione** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Exclusive|Se il **esclusivo** è selezionata, il database verrà aperto in modalità esclusiva e accessibili da un solo utente alla volta. Prestazioni risulta migliorata quando viene eseguito in modalità esclusiva.|Per impostare questa opzione in modo dinamico, usare il **esclusivo** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Timeout di pagina|Specifica il periodo di tempo, in decimi di secondo, che una pagina (se non utilizzato) rimane nel buffer prima di essere rimosso. Il valore predefinito è 600 decimi di secondo (60 secondi). Questa opzione si applica a tutte le origini dati che utilizzano il driver ODBC.<br /><br /> Il timeout di pagina non può essere 0 a causa di un ritardo inerente. Il timeout di pagina non può essere minore del ritardo intrinseco, anche se è impostata l'opzione di timeout della pagina di sotto di tale valore.|Per impostare questa opzione in modo dinamico, usare il **PAGETIMEOUT** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Read Only|Indica il database in sola lettura.|Per impostare questa opzione in modo dinamico, usare il **READONLY** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Selezionare la Directory|Visualizza una finestra di dialogo in cui è possibile selezionare una directory che contiene i file che si desidera accedere.<br /><br /> Quando si definisce una directory di origine dati, specificare la directory in cui si trovano i file utilizzati più frequentemente. Il driver ODBC utilizza questa directory come la directory predefinita. Copiare gli altri file in questa directory se vengono usati frequentemente. In alternativa, è possibile qualificare i nomi di file in un'istruzione SELECT con il nome della directory:<br /><br /> SELEZIONARE \* DA C:\MYDIR\EMP<br /><br /> In alternativa, è possibile specificare una nuova directory predefinita utilizzando il **SQLSetConnectOption** funzione con l'opzione SQL_CURRENT_QUALIFIER.|Per impostare questa opzione in modo dinamico, usare il **DEFAULTDIR** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Mostra le righe eliminate|Specifica se le righe che sono state contrassegnate come eliminate possono essere recuperate o posizionato in corrispondenza di. Se deselezionata, le righe eliminate non vengono visualizzate. Se selezionata, le righe eliminate vengono considerate come righe non è stato eliminato. Per impostazione predefinita, l'opzione è deselezionata.|Per impostare questa opzione in modo dinamico, usare il **DELETED** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|
