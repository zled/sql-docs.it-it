---
title: Sottochiave ODBC | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- registry entries for data sources [ODBC], ODBC subkey
- subkeys [ODBC], ODBC subkey
- ODBC subkey [ODBC]
ms.assetid: f9534144-8f42-4946-b0fb-638e9dcde9c8
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c4f7f404eedb8b72f744c882cc69edf2ebc0d515
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="odbc-subkey"></a>Sottochiave ODBC
I valori della sottochiave ODBC specificano le opzioni di traccia ODBC. Queste opzioni vengono impostate tramite la scheda analisi della finestra di dialogo Amministratore origine dati ODBC visualizzato da **SQLManageDataSources**. La sottochiave ODBC stesso è facoltativa. Il formato di questi valori è come illustrato nella tabella seguente.  
  
|Nome|Tipo di dati|data|  
|----------|---------------|----------|  
|Traccia|REG_SZ|**0** &#124; **1**|  
|TraceFile|REG_SZ|*tracefile-path*|  
  
 I valori presentano i significati descritti nella tabella seguente.  
  
|Value|Significato|  
|-----------|-------------|  
|Traccia|Se il valore di traccia è impostato su 1 quando un'applicazione chiama **SQLAllocHandle** con l'opzione impostato su SQL_HANDLE_ENV, la traccia è abilitata per l'applicazione chiamante.<br /><br /> Se la parola chiave di traccia è impostata su 0 quando un'applicazione chiama **SQLAllocHandle** con l'opzione impostato su SQL_HANDLE_ENV, la traccia è disabilitata per l'applicazione chiamante. Si tratta del valore predefinito.<br /><br /> Un'applicazione è possibile abilitare o disabilitare la traccia con l'attributo di connessione SQL_ATTR_TRACE. Tuttavia, tale operazione non modifica i dati per questo valore.|  
|TraceFile|Se è attivata, gestione Driver scrive nel file di traccia specificato dal valore TraceFile.<br /><br /> Se viene specificato alcun file di traccia, gestione Driver scrive il file SQL. log nell'unità corrente. Si tratta del valore predefinito.<br /><br /> L'analisi deve essere utilizzata solo per una singola applicazione oppure ogni applicazione deve specificare un file di traccia diverso. In caso contrario, due o più applicazioni tenterà di aprire il file di traccia stesso allo stesso tempo, causando un errore.<br /><br /> Un'applicazione può specificare un nuovo file di traccia con l'attributo di connessione SQL_ATTR_TRACEFILE. Tuttavia, tale operazione non modifica i dati per questo valore.|  
  
 Ad esempio, si supponga che la traccia è abilitata e il file di traccia C:\Odbc.log. I valori della sottochiave ODBC sarà come segue:  
  
```  
Trace : REG_SZ : 1  
TraceFile : REG_SZ : C:\ODBC.LOG  
  
```
