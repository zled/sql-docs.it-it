---
title: Eliminare un'origine dati (ODBC) | Documenti Microsoft
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
ms.assetid: 910e3e16-7b91-49d8-80bb-b4243926afaa
caps.latest.revision: 16
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d3b18bfe882147e0c60033dac9efd9dc4e3a6057
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064233"
---
# <a name="delete-a-data-source-odbc"></a>Eliminare un'origine dati (ODBC)
  È possibile eliminare un'origine dati tramite Amministratore ODBC, a livello di programmazione (tramite [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)), o eliminando un file (se un nome origine dati su file).  
  
### <a name="to-delete-a-data-source-by-using-odbc-administrator"></a>Per eliminare un'origine dati tramite Amministratore ODBC.  
  
1.  In **Pannello di controllo**, aprire **strumenti di amministrazione**, quindi fare doppio clic su **origine dati (ODBC)**. In alternativa, è possibile eseguire odbcad32.exe dal prompt dei comandi.  
  
2.  Fare clic sui **DSN utente**, **DSN di sistema**, o **DSN su File** scheda.  
  
3.  Fare clic sull'origine dati da eliminare.  
  
4.  Fare clic su **rimuovere**e quindi confermare l'eliminazione.  
  
## <a name="example"></a>Esempio  
 Per eliminare a livello di programmazione un'origine dati, chiamare [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md) utilizzando ODBC_REMOVE_DSN o ODBC_REMOVE_SYS_DSN come secondo parametro.  
  
 Nell'esempio seguente viene illustrato come è possibile eliminare un'origine dati a livello di programmazione.  
  
```  
// remove_odbc_data_source.cpp  
// compile with: ODBCCP32.lib user32.lib  
#include <iostream>  
#include <windows.h>  
#include <odbcinst.h>  
  
int main() {   
   LPCSTR provider = "SQL Server";   // Windows SQL Server Driver  
   LPCSTR provider = "SQL Server";   // Windows SQL Server driver  
   LPCSTR provider2 = "SQL Server Native Client 11.0";   // SQL Server 2012 Native Client driver  
   LPCSTR dsnname = "DSN=data2";  
   BOOL retval = SQLConfigDataSource(NULL, ODBC_REMOVE_DSN, provider, dsnname);  
   std::cout << retval;   // 1 if successful  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione delle procedure di SQL Server ODBC Driver](../../database-engine/dev-guide/configuring-the-sql-server-odbc-driver-how-to-topics.md)  
  
  