---
title: Impostazione delle opzioni a livello di codice per il Driver Access | Documenti Microsoft
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
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], setting options programmatically
- ODBC desktop database drivers [ODBC], Access driver
- Jet-based ODBC drivers [ODBC], Access driver
- desktop database drivers [ODBC], Access driver
ms.assetid: 1690eb71-0cd3-4c00-9e15-f6a3ac5316dd
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fb5d5f62f5a8bde9a6be1a11eaaa7b9f7f7d8f24
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="setting-options-programmatically-for-the-access-driver"></a>Impostazione delle opzioni a livello di codice per il Driver di accesso
|Opzione|Description|Metodo|  
|------------|-----------------|------------|  
|Dimensione del buffer|Le dimensioni del buffer interno, espressa in kilobyte, utilizzata da Microsoft Access per trasferire i dati da e verso il disco. Le dimensioni del buffer predefinita sono 2048 KB (visualizzata come 2048). Possono essere immessi numeri interi divisibili per 256.|Per impostare questa opzione in modo dinamico, usare la parola chiave MAXBUFFERSIZE in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Nome origine dati|Un nome che identifica l'origine dati, ad esempio: retribuzioni o dipendenti.|Per impostare questa opzione in modo dinamico, usare il **DSN** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Database|Un'origine dati Microsoft Access da impostare senza selezionare o creare un database. Se viene specificato alcun database al momento dell'installazione, l'utente verrà richiesto di scegliere un file di database durante la connessione all'origine dati.|Per impostare questa opzione in modo dinamico, usare il **DBQ** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Description|Una descrizione facoltativa dei dati nell'origine dati; ad esempio, "Hire date, cronologia stipendi e situazione corrente di tutti i dipendenti."|Per impostare questa opzione in modo dinamico, usare il **descrizione** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Exclusive|Se il **esclusivo** è selezionata, il database verrà aperto in modalità esclusiva e accessibili da un solo utente alla volta. Prestazioni risulta migliorata quando viene eseguito in modalità esclusiva.|Per impostare questa opzione in modo dinamico, usare il **esclusivo** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|ImplicitCommitSync|Determina come le modifiche apportate all'esterno di una transazione vengono scritti nel database. Questo valore è inizialmente impostato su "Sì", il che significa che il driver Microsoft Access attenderà per commit in una transazione interna/implicita per il completamento.|Questa opzione è incluso nel **Imposta opzioni avanzate** la finestra di dialogo per il driver Microsoft Access.|  
|Timeout di pagina|Specifica il periodo di tempo, espresso in millisecondi, che una pagina (se non utilizzato) rimane nel buffer prima di essere rimossa. Per il driver Microsoft Access, il valore predefinito è 500 millisecondi (0,5 secondi). Questa opzione si applica a tutte le origini dati che utilizzano il driver ODBC.<br /><br /> Il timeout di pagina non può essere 0 a causa di un ritardo inerente. Il timeout di pagina non può essere minore del ritardo intrinseco, anche se è impostata l'opzione di timeout della pagina di sotto di tale valore.|Per impostare questa opzione in modo dinamico, usare il **PAGETIMEOUT** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Read Only|Indica il database in sola lettura.|Per impostare questa opzione in modo dinamico, usare il **READONLY** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Database di sistema|Il percorso completo del database di sistema di Microsoft Access da utilizzare con il database di Microsoft Access che si desidera accedere.<br /><br /> Fare clic su di **Database di sistema** pulsante per selezionare il database di sistema da utilizzare. Il driver ODBC Microsoft Access richiede all'utente per un nome e una password. Il nome predefinito è l'amministrazione e la password predefinita in Microsoft Access per l'utente amministratore è una stringa vuota.<br /><br /> Per aumentare la sicurezza del database di Microsoft Access, creare un nuovo utente per sostituire l'utente amministratore e l'utente amministratore di eliminare o modificare gli oggetti a cui l'utente amministratore ha accesso.|Per impostare questa opzione in modo dinamico, usare il **SYSTEMDB** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Thread|Il numero di thread in background per il motore da utilizzare. Per il driver Microsoft Access, questo valore predefinito è 3, ma può essere modificato. L'utente desideri aumentare il numero di thread se è presente una grande quantità di attività nel database.<br /><br /> Questa opzione è incluso nel **Imposta opzioni avanzate** la finestra di dialogo per il driver Microsoft Access.|Per impostare questa opzione in modo dinamico, usare il **thread** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|UserCommitSync|Determina se il driver Microsoft Access eseguirà un transazioni esplicite definite dall'utente in modo asincrono. Questo valore è inizialmente impostato su "Sì", il che significa che il driver Microsoft Access attenderà per commit in una transazione definita dall'utente per il completamento.<br /><br /> L'impostazione di questa opzione su False può avere conseguenze imprevedibili in un ambiente multiutente.|Per impostare questa opzione in modo dinamico, usare il **USERCOMMITSYNC** parola chiave in una chiamata a [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|
