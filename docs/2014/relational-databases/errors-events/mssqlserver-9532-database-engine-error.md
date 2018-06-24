---
title: MSSQLSERVER_9532 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 9532 (Database Engine error)
ms.assetid: ab95cce8-4f97-4aea-a746-a73eea7c9aab
caps.latest.revision: 10
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 75b484e68f58b534391c517b69bd7bced4e79046
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065381"
---
# <a name="mssqlserver9532"></a>MSSQLSERVER_9532
    
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
 Un set di colonne è una rappresentazione XML non tipizzata che combina alcune colonne di una tabella in un output strutturato. Quando i valori di una colonna di tipo sparse vengono inseriti o aggiornati utilizzando il set di colonne XML, i valori inseriti nelle colonne di tipo sparse sottostanti vengono convertiti implicitamente dal tipo di dati `xml`. Non è stato possibile convertire un valore specificato nel tipo di dati della colonna.  
  
## <a name="user-action"></a>Azione dell'utente  
 Poiché il valore specificato non è stato convertito implicitamente, potrebbe costituire una voce non valida. Correggere l'errore e riprovare. Se il valore è corretto, modificare l'istruzione per utilizzare le colonne singole anziché il set di colonne. In questo modo sarà possibile eseguire esplicitamente il cast del valore nel tipo di dati corretto.  
  
  