---
title: MSSQL_ENG021385 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG021385 error
ms.assetid: a2c0444f-d97b-4760-8905-3574791c2e26
caps.latest.revision: 11
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 08c5cbaa79664ce621746921a404e66e96aee5ee
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36158201"
---
# <a name="mssqleng021385"></a>MSSQL_ENG021385
    
## <a name="message-details"></a>Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|21385|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|Lo snapshot non è in grado di elaborare la pubblicazione '%s', probabilmente perché sono in corso attività di modifica dello schema o di aggiunta di nuovi articoli.|  
  
## <a name="explanation"></a>Spiegazione  
 Questo errore viene generato se l'agente snapshot viene eseguito quando il database di pubblicazione è sottoposto a modifiche, ad esempio l'aggiunta o l'eliminazione di articoli e l'esecuzione di modifiche dello schema negli oggetti pubblicati.  
  
## <a name="user-action"></a>Azione dell'utente  
 Riavviare l'agente snapshot dopo che sono state apportate tutte le modifiche al database di pubblicazione. Per altre informazioni, vedere [Avviare e arrestare un agente di replica &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) e [Concetti di base relativi ai file eseguibili dell'agente di replica](concepts/replication-agent-executables-concepts.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento a errori ed eventi &#40;replica&#41;](errors-and-events-reference-replication.md)  
  
  