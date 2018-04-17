---
title: Impostazione delle opzioni a livello di codice per il Driver del File di testo | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text file driver [ODBC], setting options programmatically
- ODBC desktop database drivers [ODBC], text file driver
- desktop database drivers [ODBC], text file driver
- Jet-based ODBC drivers [ODBC], text file driver
ms.assetid: cbde2ca1-5d4e-4444-a371-a72f3ac4d92a
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ef5cd363c0365c25536a63b60fbbdbd0dd361592
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="setting-options-programmatically-for-the-text-file-driver"></a>Impostazione delle opzioni a livello di codice per il Driver del File di testo
|Opzione|Description|Metodo|  
|------------|-----------------|------------|  
|Nome origine dati|Un nome che identifica l'origine dati, ad esempio: retribuzioni o dipendenti.|Per impostare questa opzione in modo dinamico, usare il **DSN** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Definire formato|Consente di visualizzare il **Definisci formato testo** la finestra di dialogo e consente di specificare lo schema per le singole tabelle nella directory di origine dati.|Questa opzione non può essere impostata in modo dinamico da una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Description|Una descrizione facoltativa dei dati nell'origine dati; ad esempio, "Hire date, cronologia stipendi e situazione corrente di tutti i dipendenti."|Per impostare questa opzione in modo dinamico, usare il **descrizione** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Directory|Consente di selezionare la directory di destinazione.|Per impostare questa opzione in modo dinamico, usare il **DEFAULTDIR** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Elenco di estensioni|Elenca le estensioni dei file di testo sull'origine dati. Quando viene utilizzato il driver di testo, viene creato un file senza estensione quando viene eseguita l'istruzione CREATE TABLE con un nome che non ha alcuna estensione. Altri driver di creare un file con estensione predefinita quando non viene specificata estensione. Per creare un file con estensione txt, l'estensione deve essere incluso nel nome. Per visualizzare i file senza estensione nel **Definisci formato testo** nella finestra di dialogo "*." deve essere aggiunto all'elenco di estensioni.|Per impostare questa opzione in modo dinamico, usare il **estensioni** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Read Only|Indica il database in sola lettura.|Per impostare questa opzione in modo dinamico, usare il **READONLY** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Righe da analizzare|Il numero di righe da esaminare per determinare il tipo di dati di ogni colonna. Il tipo di dati è determinato dal numero massimo di tipi di dati rilevati. Se vengono rilevati dati non corrispondente al tipo di dati previsto per la colonna, il tipo di dati verrà restituito come un valore NULL.<br /><br /> Per il driver di testo, è possibile immettere un numero compreso tra 1 e 32767 per il numero di righe da analizzare; Tuttavia, il valore verrà sempre aperta a 25. (Un numero di fuori del limite verrà restituito un errore).|Per impostare questa opzione in modo dinamico, usare il **MAXSCANROWS** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Selezionare la Directory|Visualizza una finestra di dialogo in cui è possibile selezionare una directory che contiene i file che si desidera accedere.<br /><br /> Quando la definizione di una directory di origine dati specifica la directory in più file utilizzati di frequente si trovano. Il driver ODBC utilizza questa directory come la directory predefinita. Copiare gli altri file in questa directory se vengono usati frequentemente. In alternativa, è possibile qualificare i nomi di file in un'istruzione SELECT con il nome della directory: `SELECT * FROM C:\MYDIR\EMP`<br /><br /> In alternativa, è possibile specificare una nuova directory predefinita utilizzando il **SQLSetConnectOption** funzione con l'opzione SQL_CURRENT_QUALIFIER.|Per impostare questa opzione in modo dinamico, usare il **DEFAULTDIR** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|
