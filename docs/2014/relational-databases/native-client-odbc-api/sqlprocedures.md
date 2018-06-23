---
title: SQLProcedures | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLProcedures function
ms.assetid: ec41f017-f5e0-40ef-913a-65d206068631
caps.latest.revision: 34
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 26c59b042ba861684402a4b79ce7cb1b5d77e53a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065818"
---
# <a name="sqlprocedures"></a>SQLProcedures
  Tutte le stored procedure di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituiscono un valore. **SQLProcedures** riporta SQL_PT_FUNCTION per il set di risultati PROCEDURE_TYPE colonna.  
  
 **SQLProcedures** restituisce SQL_SUCCESS se esistono o meno valori per *CatalogName, SchemaName* o *ProcName* parametri. **SQLFetch** restituisce SQL_NO_DATA quando in questi parametri vengono utilizzati valori non validi.  
  
 **SQLProcedures** può essere eseguito su un cursore server statico. Un tentativo di eseguire **SQLProcedures** su un cursore aggiornabile (dinamico o keyset) restituirà SQL_SUCCESS_WITH_INFO, che indica che il tipo di cursore è stato modificato.  
  
 **SQLProcedures** restituisce informazioni sulle procedure i cui nomi corrispondono *ProcName* e possono essere eseguite dall'utente corrente o per cui l'utente corrente dispone dell'autorizzazione VIEW DEFINITION.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione SQLProcedures](http://go.microsoft.com/fwlink/?LinkId=59364)   
 [Dettagli di implementazione dell'API ODBC](odbc-api-implementation-details.md)  
  
  