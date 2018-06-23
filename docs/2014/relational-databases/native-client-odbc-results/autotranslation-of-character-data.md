---
title: Unite dati di tipo carattere | Documenti Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC], autotranslating character data
- data types [ODBC], autotranslating character data
- ACPs
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- AutoTranslate feature
- ANSI code pages
- character data autotranslation [ODBC]
- autotranslating character data
- SQL Server Native Client ODBC driver, data types
- ODBC data types, autotranslating character data
ms.assetid: 86a8adda-c5ad-477f-870f-cb370c39ee13
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a9a6b9a4faf61d4abe496036a05ca368480967bd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36166374"
---
# <a name="autotranslation-of-character-data"></a>Conversione automatica dei dati di tipo carattere
  Dati di tipo carattere, ad esempio ANSI carattere variabili dichiarate con SQL_C_CHAR o i dati archiviati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzando il **char**, **varchar**, o **testo** tipi di dati, possono rappresentare solo un numero limitato di caratteri. I dati di tipo carattere archiviati utilizzando un byte per carattere possono rappresentare solo 256 caratteri. I valori archiviati nelle variabili SQL_C_CHAR vengono interpretati mediante la tabella codici ANSI (ACP) del computer client. I valori archiviati utilizzando **char**, **varchar**, o **text** tipi di dati nel server vengono valutati utilizzando l'ACP del server.  
  
 Se il server sia il client hanno la stessa tabella codici ANSI, quindi non riscontrano l'interpretazione dei valori archiviati in SQL_C_CHAR **char**, **varchar**, o **text** oggetti. Se il server e il client sia tabelle codici ANSI diverse, quindi i dati SQL_C_CHAR del client possono essere interpretati come un carattere diverso sul server se viene utilizzata in **char**, **varchar**, o **testo** colonne, variabili o parametri. Ad esempio, un byte carattere che contiene il valore 0xA5 viene interpretato come ñ in un computer con tabella codici 437 e viene interpretato come il simbolo dello yen (¥) in un computer con tabella codici 1252.  
  
 I dati Unicode vengono archiviati utilizzando due byte per carattere. Poiché tutti i caratteri estesi sono inclusi nella specifica Unicode, tutti i caratteri Unicode vengono interpretati allo stesso modo da tutti i computer.  
  
 La caratteristica AutoTranslate del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client tenta di ridurre al minimo i problemi relativi allo spostamento di dati di tipo carattere tra un client e un server che dispongono di tabelle codici diverse. Può essere impostate AutoTranslate nella stringa di connessione di [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md), nella stringa di configurazione di [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md), o durante la configurazione di origini dati per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC Native Client driver tramite Amministratore ODBC.  
  
 Quando AutoTranslate è impostata su "no", viene effettuata alcuna conversione sui dati spostati tra le variabili SQL_C_CHAR sul client e **char**, **varchar**, o **text** colonne, variabili i parametri in o un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database. Se i dati contengono caratteri estesi e i due computer dispongono di tabelle codici diverse, gli schemi di bit potrebbero essere interpretati in modo diverso sui computer client e server. I dati verranno interpretati nello stesso modo se entrambi computer dispongono della stessa tabella codici.  
  
 Quando AutoTranslate è impostata su "yes", il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client utilizza Unicode per convertire i dati spostati tra le variabili SQL_C_CHAR sul client e **char**, **varchar**, o **testo** colonne, variabili o parametri in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database:  
  
-   Quando i dati vengono inviati da una variabile SQL_C_CHAR sul client per un **char**, **varchar**, o **testo** colonna, variabile o parametro in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database ODBC driver converte innanzitutto da SQL_C_CHAR a Unicode utilizzando la tabella codici ANSI del client, quindi da Unicode al carattere utilizzando l'ACP del server.  
  
-   Quando i dati vengono inviati da un **char**, **varchar**, o **testo** colonna, variabile o parametro in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database a una variabile SQL_C_CHAR sul client, i [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver converte innanzitutto da carattere a Unicode utilizzando l'ACP del server, quindi da Unicode a SQL_C_CHAR utilizzando l'ACP del client.  
  
 Poiché tutte le conversioni vengono eseguite dal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'esecuzione di driver ODBC di Native Client sul client, l'ACP del server deve essere una delle tabelle codici installate nel computer client.  
  
 L'utilizzo di Unicode consente di eseguire la conversione più appropriata di tutti i caratteri presenti in entrambe le tabelle codici. Se tuttavia un carattere esiste in una tabella codici ma non in un'altra, non può essere rappresentato nella tabella codici di destinazione. Il simbolo del marchio registrato (®), ad esempio, è presente nella tabella codici 1252, ma non nella tabella codici 437.  
  
 L'impostazione di AutoTranslate non ha effetto sulle conversioni seguenti:  
  
-   Lo spostamento dei dati tra variabili del client SQL_C_CHAR carattere e Unicode **nchar**, **nvarchar**, o **ntext** colonne, variabili o parametri in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.  
  
-   Lo spostamento dei dati tra variabili del client SQL_C_WCHAR Unicode e caratteri **char**, **varchar**, o **testo** colonne, variabili o parametri in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.  
  
 I dati devono essere sempre convertiti nel passaggio da carattere a Unicode.  
  
## <a name="see-also"></a>Vedere anche  
 [L'elaborazione dei risultati &#40;ODBC&#41;](processing-results-odbc.md)   
 [Regole di confronto e supporto Unicode](../collations/collation-and-unicode-support.md)  
  
  