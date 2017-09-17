---
title: Comando percorso SET | Documenti Microsoft
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
- SET PATH command [ODBC]
ms.assetid: db488d1e-0963-4f45-8c76-a23b9bde9e9d
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 490fefba9286a970b21014c66d681426703978fc
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="set-path-command"></a>Comando percorso SET
Specifica un percorso per la ricerca di file. Per informazioni specifiche del driver, vedere la sezione Osservazioni.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SET PATH TO [Path]  
```  
  
## <a name="arguments"></a>Argomenti  
 PER [ *percorso*]  
 Specifica la directory in cui che si desidera eseguire la ricerca di Visual FoxPro. Usare le virgole o punti e virgola per separare le directory.  
  
## <a name="remarks"></a>Osservazioni  
 SET PATH consente di specificare i percorsi di ricerca per altri programmi Visual FoxPro che possono essere chiamati all'interno di stored procedure. SET PATH non verrà modificato il percorso dell'origine dati specificato per la connessione.  
  
 Eseguire SET percorso senza *percorso* per ripristinare il percorso della cartella o la directory predefinita di.  
  
## <a name="driver-remarks"></a>Sezione Osservazioni di driver  
 Se si esegue percorso impostato in una stored procedure, verrà ignorata per le seguenti funzioni e i comandi:  
  
-   Funzioni di catalogo come [SQLTables](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md) e [SQLColumns](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md) ignorerà il nuovo percorso e continuare a fare riferimento il percorso specificato dall'origine dei dati in [SQLPrepare](../../odbc/microsoft/sqlprepare-visual-foxpro-odbc-driver.md) o [ SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md).  
  
-   I comandi, ad esempio SELECT, INSERT, UPDATE, DELETE e CREATE TABLE ignorerà il nuovo percorso e continuare a fare riferimento il percorso specificato dall'origine dei dati in **SQLPrepare** o **SQLExecDirect**.  
  
 Se si rilascia percorso impostato in una stored procedure e non successivamente impostare il percorso allo stato originale, le altre connessioni al database utilizza il nuovo percorso (poiché SET PATH non è definito per le sessioni di dati).  
  
 Se si desidera creare, selezionare o aggiornare le tabelle in una directory diversa da quella specificata dall'origine dati, specificare il percorso completo del file con il comando.  
  
## <a name="see-also"></a>Vedere anche  
 [La finestra di dialogo programma di installazione di Visual FoxPro ODBC](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)   
 [SQLColumns (Driver ODBC di Visual FoxPro)](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md)   
 [SQLDriverConnect (Driver ODBC di Visual FoxPro)](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)   
 [SQLTables (Driver ODBC di Visual FoxPro)](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md)
