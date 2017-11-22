---
title: MSSQLSERVER_9532 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 9532 (Database Engine error)
ms.assetid: ab95cce8-4f97-4aea-a746-a73eea7c9aab
caps.latest.revision: "9"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 514c8efd47a7cb54397db495a268b1c9c415be58
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver9532"></a>MSSQLSERVER_9532
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|9532|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|XMLERR_COLUMNSET_CANNOT_CONVERT_FROM_TO|  
|Testo del messaggio|Conversione non riuscita del tipo di dati '%ls' nel tipo di dati '%ls' per la colonna '%.*ls' durante l'operazione query/DML che interessa il set di colonne '%.\*ls'.|  
  
## <a name="explanation"></a>Spiegazione  
Un set di colonne è una rappresentazione XML non tipizzata che combina alcune colonne di una tabella in un output strutturato. Quando i valori di una colonna di tipo sparse vengono inseriti o aggiornati utilizzando il set di colonne XML, i valori inseriti nelle colonne di tipo sparse sottostanti vengono convertiti implicitamente dal tipo di dati **xml**. Non è stato possibile convertire un valore specificato nel tipo di dati della colonna.  
  
## <a name="user-action"></a>Azione dell'utente  
Poiché il valore specificato non è stato convertito implicitamente, potrebbe costituire una voce non valida. Correggere l'errore e riprovare. Se il valore è corretto, modificare l'istruzione per utilizzare le colonne singole anziché il set di colonne. In questo modo sarà possibile eseguire esplicitamente il cast del valore nel tipo di dati corretto.  
  
