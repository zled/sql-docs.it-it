---
title: L'elaborazione dei risultati di Stored Procedure | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- stored procedures [ODBC], results
ms.assetid: 788ef2a4-17de-4526-960b-46bf29aafc9f
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 767eb56845429a19575d1339976a014ec3ea5288
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37411030"
---
# <a name="processing-stored-procedure-results"></a>Risultati dell'elaborazione delle stored procedure
  Per le stored procedure di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono disponibili quattro meccanismi di restituzione dei dati:  
  
-   Ogni istruzione SELECT di una stored procedure genera un set di risultati.  
  
-   La procedura può restituire dati tramite parametri di output.  
  
-   Un parametro di output del cursore può passare nuovamente un cursore del server [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   La procedura può avere un codice restituito di tipo integer.  
  
 Le applicazioni devono essere in grado di gestire tutti questi output dalle stored procedure. L'istruzione CALL o EXECUTE deve includere marcatori di parametro per il codice restituito e i parametri di output. Uso [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) associare le tutti come parametri di output e il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client trasferirà i valori di output alle variabili associate. I parametri di output e i codici restituiti sono gli ultimi elementi restituiti al client da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; non vengono restituiti all'applicazione solo [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) restituisce SQL_NO_DATA.  
  
 ODBC non supporta i parametri di cursore [!INCLUDE[tsql](../../includes/tsql-md.md)] di associazione. Dal momento che tutti i parametri di output devono essere associati prima di eseguire una stored procedure, le stored procedure [!INCLUDE[tsql](../../includes/tsql-md.md)] che contengono un parametro di cursore di output non possono essere chiamate dalle applicazioni ODBC.  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione delle stored procedure](running-stored-procedures.md)  
  
  
