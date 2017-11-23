---
title: Utilizzo SQLConfigDatasource con il Driver ODBC per Oracle | Documenti Microsoft
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
helpviewer_keywords: SQLConfigDataSource function [ODBC], ODBC driver for Oracle
ms.assetid: e535d1ef-aff9-4ae7-a3ed-ef4ca2584289
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 17d7cfdacb91ff3963a1bf77343c171e8f9d3fec
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="using-sqlconfigdatasource-with-the-odbc-driver-for-oracle"></a>Utilizzo SQLConfigDatasource con il Driver ODBC per Oracle
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. In alternativa, utilizzare il driver ODBC fornito da Oracle.  
  
 La tabella seguente elenca valido **SQLConfigDatasource** le impostazioni per il Driver ODBC di Microsoft per Oracle, versione 1.0 (Msorcl10.dll) e il Driver ODBC di Microsoft per Oracle, versione 2.0 (msorcl32. dll).  
  
> [!NOTE]  
>  Il driver Msorcl10.dll (versione 1.0) supporta tutte le opzioni eccetto **Server**. Il driver msorcl32. dll (versione 2.0 e versioni successive) supporta tutte le impostazioni.  
  
 Alcune impostazioni vengono ignorate dal driver, ma vengono accettate da **SQLConfigDatasource**. Tra queste impostazioni nella stringa di connessione ODBC è l'unico modo che sono accettati in fase di esecuzione. Un'impostazione ignorata non verrà archiviata nel Registro di sistema quando **SQLConfigDatasource** crea l'origine dati.  
  
 Nella tabella seguente, *A/N* significa che qualsiasi stringa alfanumerica valida fino alla lunghezza massima consentita. *Max Len* (lunghezza massima) è la lunghezza massima consentita della stringa accettata dall'impostazione, incluso il carattere di terminazione di stringa.  
  
|Impostazione|Lunghezza massima|Valore predefinito|Valori validi|Description|  
|-------------|-------------|-------------------|------------------|-----------------|  
|BufferSize|7|65535|1000|Buffer di recupero minima dimensione fino a 65535 byte|  
|CatalogCap|2|1|0 o 1|Se è 1, gli identificatori nonquoted sarà convertito in lettere maiuscole nel catalogo di funzioni.|  
|ConnectString|128|""|A/N|Stringa di connessione. Metodo richiesto di specificare il nome del server con il driver Msorcl10.dll.|  
|Description|256|""|A/N|Descrizione|  
|DSN|33|""|A/N|Nome dell'origine dati.|  
|GuessTheColDef|4|0|A/N|Restituisce un valore diverso da zero per le colonne senza la scala definita Oracle.|  
|NumberFloat|2|""|0 o 1|Se è 0, le colonne FLOAT sono considerate come SQL_FLOAT. Se è 1, le colonne FLOAT sono considerate come SQL_DOUBLE.|  
|PWD|30|""|A/N|Password.|  
|RDOSupport|2|""|0 o 1|Consente di RDO chiamare le routine di Oracle.|  
|Osservazioni|2|0|0 o 1|Includere la sezione Osservazioni in funzioni di catalogo.|  
|RowLimit|4|""|0 e 99|Numero massimo di righe restituite da un'istruzione SELECT. Una stringa di lunghezza zero indica che viene applicato alcun limite.|  
|Server|128|""|A/N|Nome del server Oracle.|  
|SynonymColumns|2|1|0 o 1|Includere i sinonimi nel SQLColumns.|  
|SystemTable|2|""|0 o 1|Se è 0, non verranno visualizzate tabelle di sistema. Se è 1, verranno visualizzate tabelle di sistema.|  
|TranslationDLL|33|""|A/N|Nome di DLL di conversione.|  
|TranslationName|33|""|A/N|Nome della traduzione.|  
|TranslationOption|33|""|A/N|Opzione di conversione.|  
|TxnCap|2|""|A/N|Transazione in grado di supportare. Se è 0, il driver segnala che non supporta le transazioni. Se è 1, il driver segnala che è in grado di eseguire transazioni.|  
|UID|30|""|A/N|Nome utente.|
