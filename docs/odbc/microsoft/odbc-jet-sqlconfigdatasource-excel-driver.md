---
title: ODBC Jet SQLConfigDataSource (Driver per Excel) | Documenti Microsoft
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
- SQLConfigDataSource function [ODBC], Excel Driver
- Excel driver [ODBC], SqlConfigDataSource
ms.assetid: 885b3bea-f4b6-4902-b994-f78a912b612f
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9a4d5d0b2feb0a09aafeb441c6b33260e4f0738b
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="odbc-jet-sqlconfigdatasource-excel-driver"></a>ODBC Jet SQLConfigDataSource (Driver per Excel)
> [!NOTE]  
>  In questo argomento fornisce informazioni specifiche del Driver Excel. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Il **SQLConfigDataSource** funzione che consente di aggiungere, modificare o eliminare un'origine dati utilizzata in modo dinamico le parole chiave seguenti.  
  
|Parola chiave|Description|  
|-------------|-----------------|  
|DBQ|Per il driver Microsoft Excel quando si accede a Microsoft Excel 5.0 o versioni successive file, il nome del file di cartella di lavoro.<br /><br /> Consente di impostare la stessa opzione come **Database** nella finestra di dialogo programma di installazione.|  
|DEFAULTDIR|La specifica del percorso della directory.<br /><br /> Consente di impostare la stessa opzione come **seleziona Directory** o **Selezione cartella di lavoro** nella finestra di dialogo programma di installazione.|  
|DESCRIPTION|Una descrizione dei dati nell'origine dati.<br /><br /> Consente di impostare la stessa opzione come **descrizione** nella finestra di dialogo programma di installazione.|  
|DRIVER|La specifica del percorso per la DLL del driver.|  
|DRIVERID|Un ID di tipo integer per il driver.<br /><br /> 534 (Microsoft Excel 3.0)<br /><br /> 278 (Microsoft Excel 4.0)<br /><br /> 22 (Microsoft Excel 5.0/7.0)<br /><br /> 790 (Microsoft Excel 97-2003)|  
|FIL|File di tipo, ad esempio, Excel 3.0, Excel 4.0, 5.0 di Excel, Excel 7.0, Excel 97, Excel 2000 o Excel 2003.|  
|FIRSTROWHASNAMES|Indica se le celle della prima riga dell'intervallo contengono i nomi di colonna per la tabella (1) o non (0).|  
|MAXSCANROWS|Il numero di righe da analizzare per l'impostazione di un tipo di dati colonna sulla base dei dati esistenti.<br /><br /> Per le righe da analizzare, è possibile specificare un numero compreso tra 1 e 16. Il valore predefinito è 8; Se è impostato su 0, vengono analizzate tutte le righe. (Un numero di fuori del limite verrà restituito un errore).<br /><br /> Consente di impostare la stessa opzione come **righe da analizzare** nella finestra di dialogo programma di installazione.|  
|READONLY|TRUE per rendere i file di sola lettura. FALSE per rendere i file non di sola lettura.<br /><br /> Consente di impostare la stessa opzione come **in sola lettura** nella finestra di dialogo programma di installazione.|  
|THREAD|Il numero di thread in background per il motore da utilizzare. Per il driver Microsoft Access, questo valore predefinito è 3, ma può essere modificato. Per il file dBASE, MicrosoftExceldriver questo valore è 3 e non può essere modificato.<br /><br /> Consente di impostare la stessa opzione come **thread** nella finestra di dialogo programma di installazione.|

