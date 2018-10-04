---
title: Estensioni specifiche SQL Server In-Process per ADO.NET | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- data access [CLR integration]
- ADO.NET [CLR integration]
- common language runtime [SQL Server], ADO.NET
- database objects [CLR integration], in-process extensions
- in-process data access providers [CLR integration]
- extensions [CLR integration]
ms.assetid: 781b812e-eb14-472a-85fa-aa4cdb929bee
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 98781a7258a4fa70f9f8c70c37140445af5bcb76
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48055521"
---
# <a name="sql-server-in-process-specific-extensions-to-adonet"></a>Estensioni specifiche in-process di SQL Server ad ADO.NET
  Sono disponibili quattro estensioni funzionali principali ad ADO.NET specifiche per l'utilizzo in-process. Tali estensioni verranno analizzate dettagliatamente negli argomenti seguenti.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Oggetto SqlContext](sqlcontext-object.md)  
 Questa classe fornisce accesso alle altre estensioni mediante l'astrazione del contesto di un chiamante di una routine di SQL Server che esegue codice gestito in-process.  
  
 [Oggetto SqlPipe](sqlpipe-object.md)  
 Questa classe contiene routine per l'invio di risultati tabulari e messaggi al client.  
  
 [Oggetto SqlTriggerContext](sqltriggercontext-object.md)  
 Questa classe fornisce informazioni sul contesto nel quale viene eseguito un trigger.  
  
 [Oggetto SqlDataRecord](sqldatarecord-object.md)  
 La classe SqlDataRecord rappresenta una sola riga di dati, insieme ai rispettivi metadati correlati, e consente alle stored procedure di restituire set di risultati personalizzati al client.  
  
  
