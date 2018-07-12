---
title: Aggiungere un'origine dati (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: b4ac6f0e-8e6a-4b1a-9a7e-60e0a69b2180
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8e8d3c51595caa5a65f5ac175bdf16a4333511b5
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37432000"
---
# <a name="add-a-data-source-odbc"></a>Aggiungere un'origine dei dati (ODBC)
  È possibile aggiungere un'origine dati tramite Amministratore ODBC, a livello di programmazione (tramite [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)), o creando un file.  
  
### <a name="to-add-a-data-source-by-using-odbc-administrator"></a>Per aggiungere un'origine dati tramite Amministratore ODBC.  
  
1.  Dal **Pannello di controllo**, accesso **strumenti di amministrazione** e quindi **origine dati (ODBC)**. In alternativa, è possibile richiamare odbcad32.exe.  
  
2.  Scegliere il **DSN utente**, **DSN di sistema**, o **DSN su File** scheda e quindi fare clic su **Aggiungi**.  
  
3.  Fare clic su **SQL Server**, quindi fare clic su **fine**.  
  
4.  Completare i passaggi della procedura guidata Crea una nuova origine dati per un server SQL.  
  
### <a name="to-add-a-data-source-programmatically"></a>Per aggiungere un'origine dati a livello di programmazione  
  
1.  Chiamare [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md) con il secondo parametro impostato su ODBC_ADD_DSN o ODBC_ADD_SYS_DSN.  
  
### <a name="to-add-a-file-data-source"></a>Per aggiungere un 'origine dati file  
  
1.  Chiamare [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md) con SAVEFILE = nome_file parametro nella stringa di connessione. Se la connessione viene eseguita correttamente, il driver ODBC crea un'origine dati file con i parametri di connessione nel percorso a cui punta il parametro SAVEFILE.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione delle procedure del driver ODBC di SQL Server](../../database-engine/dev-guide/configuring-the-sql-server-odbc-driver-how-to-topics.md)  
  
  
