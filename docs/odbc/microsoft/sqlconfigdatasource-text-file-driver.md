---
title: SQLConfigDataSource (Driver di File di testo) | Documenti Microsoft
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
- text file driver [ODBC], SQLConfigDataSource
- SQLConfigDataSource function [ODBC], Text File Driver
ms.assetid: c505d36e-1e72-47b2-a9e5-e4926b408468
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f3afa8094eb945306fcc74e555f18409f98cfb63
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sqlconfigdatasource-text-file-driver"></a>SQLConfigDataSource (Driver di File di testo)
> [!NOTE]  
>  In questo argomento fornisce informazioni specifiche del Driver File di testo. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Il **SQLConfigDataSource** funzione che consente di aggiungere, modificare o eliminare un'origine dati utilizzata in modo dinamico le parole chiave seguenti.  
  
|Parola chiave|Description|  
|-------------|-----------------|  
|CHARACTERSET|Per il driver di testo, OEM o ANSI.|  
|COLNAMEHEADER|Per il driver di testo, indica se il primo record di dati è necessario specificare i nomi di colonna. TRUE o FALSE.|  
|DEFAULTDIR|La specifica del percorso della directory.|  
|DESCRIPTION|Una descrizione dei dati nell'origine dati.<br /><br /> Consente di impostare la stessa opzione come **descrizione** nella finestra di dialogo programma di installazione.|  
|DRIVER|La specifica del percorso per la DLL del driver.|  
|DRIVERID|Un ID di tipo integer per il driver. 27 (testo)|  
|ESTENSIONI|Elenca le estensioni dei file di testo sull'origine dati.<br /><br /> Consente di impostare la stessa opzione come **elenco estensioni** nella finestra di dialogo programma di installazione.|  
|FIL|Tipo di file testo|  
|TIPO DI FILE|Tipo di file per il driver di testo (testo).|  
|FORMAT|Per il driver di testo, può essere FIXEDLENGTH, TABDELIMITED, CSVDELIMITED (da una virgola) o DELIMITED() (dal carattere speciale specificato tra parentesi). Il carattere speciale è un carattere di lunghezza e può essere in formato decimale o esadecimale del carattere.|  
|MAXSCANROWS|Il numero di righe da analizzare per l'impostazione di un tipo di dati colonna sulla base dei dati esistenti.<br /><br /> Per il driver di testo, è possibile immettere un numero compreso tra 1 e 32767 per il numero di righe da analizzare; Tuttavia, il valore verrà sempre aperta a 25. (Un numero di fuori del limite verrà restituito un errore).<br /><br /> Consente di impostare la stessa opzione come **righe da analizzare** nella finestra di dialogo programma di installazione.|  
|READONLY|TRUE per rendere i file di sola lettura. FALSE per rendere i file non di sola lettura.<br /><br /> Consente di impostare la stessa opzione come **in sola lettura** nella finestra di dialogo programma di installazione.|
