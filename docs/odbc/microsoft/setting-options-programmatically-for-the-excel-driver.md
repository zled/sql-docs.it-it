---
title: Impostazione delle opzioni a livello di codice per il Driver per Excel | Documenti Microsoft
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
- Jet-based ODBC drivers [ODBC], Excel driver
- desktop database drivers [ODBC], Excel driver
- ODBC desktop database drivers [ODBC], Excel driver
- Excel driver [ODBC], setting options programmatically
ms.assetid: b5ee3636-4591-427a-a65a-a2d5926fcc1a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: da1f2ed6bbca3709c8223713f4841ed34288f5a3
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="setting-options-programmatically-for-the-excel-driver"></a>Impostazione delle opzioni a livello di codice per il Driver per Excel
|Opzione|Description|Metodo|  
|------------|-----------------|------------|  
|Nome origine dati|Un nome che identifica l'origine dati, ad esempio: retribuzioni o dipendenti.|Per impostare questa opzione in modo dinamico, usare il **DSN** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Database|Un'origine dati Microsoft Access da impostare senza selezionare o creare un database. Se viene specificato alcun database al momento dell'installazione, l'utente verrà richiesto di scegliere un file di database durante la connessione all'origine dati.|Per impostare questa opzione in modo dinamico, usare il **DBQ** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Description|Una descrizione facoltativa dei dati nell'origine dati; ad esempio, "Hire date, cronologia stipendi e situazione corrente di tutti i dipendenti."|Per impostare questa opzione in modo dinamico, usare il **descrizione** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Directory|Visualizza la directory selezionata.<br /><br /> Per i file di Microsoft Excel versione 3.0 o 4.0, la visualizzazione del percorso con etichetta "Directory", mentre per Microsoft Excel 5.0, 7.0, 97 o file, la visualizzazione del percorso con etichetta "Cartella di lavoro".|Per impostare questa opzione in modo dinamico, usare il **DEFAULTDIR** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Read Only|Indica il database in sola lettura.|Per impostare questa opzione in modo dinamico, usare il **READONLY** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Righe da analizzare|Il numero di righe da esaminare per determinare il tipo di dati di ogni colonna. Il tipo di dati è determinato dal numero massimo di tipi di dati rilevati. Se vengono rilevati dati non corrispondente al tipo di dati previsto per la colonna, il tipo di dati verrà restituito come un valore NULL.<br /><br /> Per il driver Microsoft Excel, è possibile immettere un numero da 1 a 16 per le righe da analizzare. Il valore predefinito è 8; Se è impostato su 0, vengono analizzate tutte le righe. (Un numero di fuori del limite verrà restituito un errore).|Per impostare questa opzione in modo dinamico, usare il **MAXSCANROWS** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Selezionare la Directory|Visualizza una finestra di dialogo in cui è possibile selezionare una directory che contiene i file che si desidera accedere.<br /><br /> Quando si definisce una directory di origine dati (per tutti i driver, ad eccezione di Microsoft Access), specificare la directory in cui si trovano i file utilizzati più di frequente. Il driver ODBC utilizza questa directory come la directory predefinita. Copiare gli altri file in questa directory se vengono usati frequentemente. In alternativa, è possibile qualificare i nomi di file in un'istruzione SELECT con il nome della directory:<br /><br /> SELEZIONARE \* DA C:\MYDIR\EMP<br /><br /> In alternativa, è possibile specificare una nuova directory predefinita utilizzando il **SQLSetConnectOption** funzione con l'opzione SQL_CURRENT_QUALIFIER.<br /><br /> Per Microsoft Excel 3.0 o 4.0 file, la visualizzazione del percorso è denominata "Directory" e il pulsante di selezione del percorso con etichetta "Seleziona Directory". Per i file di Microsoft Excel 97 5.0 o 7.0, la visualizzazione del percorso è denominata "Cartella di lavoro" e il pulsante di selezione del percorso con etichetta "Selezione cartella di lavoro". Quando si definisce una directory di origine dati, specificare la directory in cui i file di Microsoft Excel utilizzati più di frequente si trovano per Microsoft Excel versione 3.0 o 4.0, o la directory in cui il file della cartella di lavoro si trova per Microsoft Excel 97 5.0 o 7.0. **Utilizzare la Directory corrente** è disabilitato per Microsoft Excel 97 5.0 e 7.0.|Per impostare questa opzione in modo dinamico, usare il **DEFAULTDIR** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|

