---
title: SQLConfigDataSource (dBASE Driver) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DBase driver [ODBC], SQLConfigDataSource
- SQLConfigDataSource function [ODBC], dBASE Driver
ms.assetid: 19909902-054c-4e19-9c06-a212aace13fe
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8354ed96f68d1471a2deb275506d4d45d4c8f3cf
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sqlconfigdatasource-dbase-driver"></a>SQLConfigDataSource (dBASE Driver)
> [!NOTE]  
>  In questo argomento fornisce informazioni specifiche del Driver dBASE. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Il **SQLConfigDataSource** funzione che consente di aggiungere, modificare o eliminare un'origine dati utilizzata in modo dinamico le parole chiave seguenti.  
  
|Parola chiave|Description|  
|-------------|-----------------|  
|COLLATINGSEQUENCE|La sequenza in cui i campi vengono ordinati.<br /><br /> La sequenza può essere: ASCII (impostazione predefinita) o internazionale.<br /><br /> Consente di impostare la stessa opzione come **sequenza di ordinamento** nella finestra di dialogo programma di installazione.|  
|DEFAULTDIR|La specifica del percorso della directory.|  
|DELETED|Per il driver dBASE, specifica se le righe che sono state contrassegnate come eliminate possono essere recuperate o posizionato in corrispondenza di. Se impostato su 1, le righe eliminate non viene visualizzata. Se impostato su 0, le righe eliminate viene considerate come righe non è stato eliminato.<br /><br /> Consente di impostare la stessa opzione come **Mostra righe eliminate** nella finestra di dialogo programma di installazione.|  
|DESCRIPTION|Una descrizione dei dati nell'origine dati.<br /><br /> Consente di impostare la stessa opzione come **descrizione** nella finestra di dialogo programma di installazione.|  
|DRIVER|La specifica del percorso per la DLL del driver.|  
|DRIVERID|Un ID di tipo integer per il driver.<br /><br /> 21 (dBASE III)<br /><br /> 277 (dBASE IV)<br /><br /> 533 (dBASE 5.0)|  
|FIL|File dBase III, dBase IV o dBase 5 tipo|  
|PAGETIMEOUT|Specifica il periodo di tempo, in decimi di secondo, che una pagina (se non utilizzato) rimane nel buffer prima di essere rimossa. Il valore predefinito è 600 decimi di secondo (60 secondi). Si noti che questa opzione si applica a tutte le origini dati che utilizzano il driver ODBC.<br /><br /> Consente di impostare la stessa opzione come **Page Timeout** nella finestra di dialogo programma di installazione.|  
|READONLY|TRUE per rendere i file di sola lettura. FALSE per rendere i file non di sola lettura.<br /><br /> Consente di impostare la stessa opzione come **in sola lettura** nella finestra di dialogo programma di installazione.|  
|STATISTICS|Per il driver dBASE, determina se le statistiche sulle dimensioni di tabella sono approssimative. Si noti che questa opzione si applica a tutte le origini dati che utilizzano il driver ODBC.<br /><br /> Consente di impostare la stessa opzione come **conteggio approssimativo** nella finestra di dialogo programma di installazione.|  
|THREAD|Il numero di thread in background per il motore da utilizzare. Questo valore è 3 e non può essere modificato.<br /><br /> Consente di impostare la stessa opzione come **thread** nella finestra di dialogo programma di installazione.|
