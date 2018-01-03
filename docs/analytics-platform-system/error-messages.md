---
title: Messaggi di errore (SQL Server PDW)
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/13/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e6223cba-2dec-4b8a-bc10-e2ef6a821fe0
caps.latest.revision: "9"
ms.openlocfilehash: c9c0ebf9b452fdf2ec54ae84bec34288e73e88aa
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="error-messages"></a>messaggi di errore
I messaggi di errore di SQL Server PDW segnalano gli errori e problemi rilevati dai componenti di SQL Server PDW e possono includere anche gli errori di SQL Server con SQL Server PDW. Questi messaggi di errore utilizzano una sintassi coerenza per la presentazione di informazioni. La comprensione di questa sintassi consente di identificare e correggere problemi su SQL Server PDW.  
  
## <a name="Basics"></a>Nozioni fondamentali di messaggio di errore  
I messaggi di errore restituiti seguono la stessa sintassi.  
  
`Error_Indicator [SQL_State_Code] [Driver_Details] [QueryID] Message_String`  
  
Questi sono i possibili valori per ogni campo:  
  
|Campo|Description|Esempio|  
|---------|---------------|-----------|  
|*Error_Indicator*|La parola "Errore" o altro testo dell'avviso all'utente di un problema.|error|  
|*SQL_State_Code*|Codice di stato di SQL, in base alla specifica ODBC. Il driver genera il codice di stato SQL appropriato ogni volta che viene restituito un messaggio a un'applicazione. Il testo "Microsoft" indica l'origine dell'errore.|42000|  
|*Driver_Details*|Dettagli dipendente dal driver, ad esempio il tipo del driver utilizzato.|Driver ODBC SQL Server 2008 R2 Parallel Data Warehouse|  
|*QueryID*|Identificatore univoco per la query. Utilizzare questo valore per trovare informazioni aggiuntive correlate all'elaborazione della query. Ad esempio, i dettagli di esecuzione di query sono reperibile nella Console di amministrazione con l'ID di query. Per ulteriori informazioni, vedere [monitorare il dispositivo tramite la Console di amministrazione](monitor-the-appliance-by-using-the-admin-console.md).<br /><br />Se un QueryID non è applicabile, viene restituito il testo "Interno" per l'utente.|QID2377|  
|*Message_String*|Descrizione leggibile dell'errore o problema. Per la restituzione di errori di SQL Server, questo è il testo del messaggio di SQL Server.|Solo l'assegnazione uguale può essere visualizzati nell'elenco set di un'istruzione UPDATE.|  
  
Questi valori di esempio potrebbero essere presentati all'utente simile al seguente:  
  
`ERROR [42000] [Microsoft][ODBC SQL Server 2008 R2 Parallel Data Warehouse driver][QID2380]Only equal assignment can appear in the set list of an UPDATE statement.`  
  
## <a name="see-also"></a>Vedere anche  
<!-- MISSING LINKS 
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
[Informazioni sugli avvisi di Console di amministrazione](understanding-admin-console-alerts.md)  
  
