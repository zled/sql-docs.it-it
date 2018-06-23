---
title: Aggiungere un'origine dati (ODBC) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: b4ac6f0e-8e6a-4b1a-9a7e-60e0a69b2180
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 822ac0f5d2e228a982368849ed1c409ef63765ee
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36158437"
---
# <a name="add-a-data-source-odbc"></a>Aggiungere un'origine dei dati (ODBC)
  È possibile aggiungere un'origine dati tramite Amministratore ODBC, a livello di programmazione (tramite [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)), o creando un file.  
  
### <a name="to-add-a-data-source-by-using-odbc-administrator"></a>Per aggiungere un'origine dati tramite Amministratore ODBC.  
  
1.  Dal **Pannello di controllo**, l'accesso **strumenti di amministrazione** e quindi **origine dati (ODBC)**. In alternativa, è possibile richiamare odbcad32.exe.  
  
2.  Fare clic sui **DSN utente**, **DSN di sistema**, o **DSN su File** scheda e quindi fare clic su **Aggiungi**.  
  
3.  Fare clic su **SQL Server**, quindi fare clic su **fine**.  
  
4.  Completare i passaggi della procedura guidata Crea una nuova origine dati per un server SQL.  
  
### <a name="to-add-a-data-source-programmatically"></a>Per aggiungere un'origine dati a livello di programmazione  
  
1.  Chiamare [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md) con il secondo parametro impostato su ODBC_ADD_DSN o ODBC_ADD_SYS_DSN.  
  
### <a name="to-add-a-file-data-source"></a>Per aggiungere un 'origine dati file  
  
1.  Chiamare [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md) con SAVEFILE = nome_file parametro nella stringa di connessione. Se la connessione viene eseguita correttamente, il driver ODBC crea un'origine dati file con i parametri di connessione nel percorso a cui punta il parametro SAVEFILE.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione delle procedure di SQL Server ODBC Driver](../../database-engine/dev-guide/configuring-the-sql-server-odbc-driver-how-to-topics.md)  
  
  