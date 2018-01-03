---
title: Utilizzo di origini dati di File di connessione | Documenti Microsoft
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
- connecting to driver [ODBC], file data sources
- SQLDriverConnect function [ODBC], connecting using file data sources
- connecting to data source [ODBC], SQLDriverConnect
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], file data sources
- file data sources [ODBC]
ms.assetid: 3003f8c2-8be6-41cc-8d9c-612e9bd0f3ae
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: d64a08cc8e748efe984c8aa5acd7deac743c2ed3
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="connecting-using-file-data-sources"></a>Connessione tramite origini dati dei File
Le informazioni di connessione per un'origine dati file viene archiviate in un file DSN. Di conseguenza, la stringa di connessione è possibile utilizzare ripetutamente a un singolo utente o condiviso da più utenti se hanno il driver appropriato installato. Il file contiene un nome di driver (o un altro nome dell'origine dati nel caso di un'origine dati file condivisibile) e, facoltativamente, una stringa di connessione che può essere utilizzata da **SQLDriverConnect**. Gestione Driver compila la stringa di connessione per la chiamata a **SQLDriverConnect** dalle parole chiave nel file DSN.  
  
 Un'origine dati file consente a un'applicazione specificare le opzioni di connessione senza dover compilare una stringa di connessione per l'utilizzo con **SQLDriverConnect**. File dell'origine dati in genere viene creato specificando il **SAVEFILE** (parola chiave), che fa sì che Gestione Driver per salvare la stringa di connessione di output creata da una chiamata a **SQLDriverConnect** per il file DSN. Stringa di connessione può essere utilizzata più volte chiamando **SQLDriverConnect** con il **FILEDSN** (parola chiave). Questo semplifica il processo di connessione e fornisce un'origine persistente della stringa di connessione.  
  
 Origini dati dei file possono anche essere create chiamando **SQLCreateDataSource** nel programma di installazione DLL. Le informazioni possono essere scritti nel file DSN chiamando **SQLWriteFileDSN**e leggere il file DSN chiamando **SQLReadFileDSN**; entrambe queste funzioni sono anche nel programma di installazione DLL. Per informazioni sul programma di installazione DLL, vedere [origini dati di configurazione](../../../odbc/reference/install/configuring-data-sources.md).  
  
 Le parole chiave utilizzate per le informazioni di connessione sono riportate nella sezione [ODBC] di un file DSN. Le informazioni minime che potrebbe avere un file DSN condivisibile nella sezione [ODBC] sono la parola chiave DRIVER:  
  
```  
DRIVER = SQL Server  
```  
  
 Il file DSN condivisibile contiene in genere una stringa di connessione, come indicato di seguito:  
  
```  
DRIVER = SQL Server  
UID = Larry  
DATABASE = MyDB  
```  
  
 Quando l'origine dati di file è condivisibile, il file DSN contiene solo un **DSN** (parola chiave). Quando Gestione Driver viene inviata le informazioni in un'origine dati file condivisibile, si connette necessarie per l'origine dati indicata tramite il **DSN** (parola chiave). Un file DSN condivisibili dovrebbe contenere la parola chiave seguente:  
  
```  
DSN = MyDataSource  
```  
  
 La stringa di connessione utilizzata per un'origine dati di file è l'unione di parole chiave specificate nel file DSN e le parole chiave specificate nella stringa di connessione nella chiamata a **SQLDriverConnect**. Se una delle parole chiave nel file di DSN in conflitto con le parole chiave nella stringa di connessione, gestione Driver decide quale valore della parola chiave deve essere utilizzato. Per ulteriori informazioni, vedere [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
## <a name="see-also"></a>Vedere anche  
 [http://support.microsoft.com/kb/165866](http://support.microsoft.com/kb/165866)
