---
title: SQLNumResultCols | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLNumResultCols function
ms.assetid: f79d8b3c-521e-4e50-a564-21d73ae5767b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 679888376c7ea02570e877ed5eac0e9638af48e3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48220361"
---
# <a name="sqlnumresultcols"></a>SQLNumResultCols
  Per le istruzioni eseguite, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client controlla il server per segnalare il numero di colonne in un set di risultati. In questo caso, `SQLNumResultCols` genera un round trip del server. Ad esempio [SQLDescribeCol](sqldescribecol.md) e [SQLColAttribute](sqlcolattribute.md), la chiamata `SQLNumResultCols` via preparate, ma le istruzioni non eseguite genera un round trip del server.  
  
 Quando un'istruzione o un batch di istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] restituisce più set di righe di risultati, è possibile che il numero di colonne del set di risultati cambi da un set all'altro. `SQLNumResultCols` deve essere chiamato per ogni set. Quando il numero di colonne cambia, l'applicazione deve riassociare i valori dei dati prima di recuperare i risultati delle righe. Per altre informazioni sulla gestione di più risultati set restituiti, vedere [SQLMoreResults](sqlmoreresults.md).  
  
 Miglioramenti apportati al motore di database a partire da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] consentire SQLNumResultCols ottenere descrizioni più accurate dei risultati previsti. Questi risultati più accurati differiscano dai valori restituiti da SQLNumResultCols nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [Metadata Discovery](../native-client/features/metadata-discovery.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione SQLNumResultCols](http://go.microsoft.com/fwlink/?LinkId=59359)   
 [Dettagli di implementazione dell'API ODBC](odbc-api-implementation-details.md)  
  
  
