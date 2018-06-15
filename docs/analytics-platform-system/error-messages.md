---
title: I messaggi di errore - Parallel Data Warehouse | Documenti Microsoft
description: I messaggi di errore Parallel Data Warehouse (PDW) segnalano gli errori e problemi rilevati dai componenti PDW e possono includere anche gli errori di SQL Server rese disponibili tramite PDW. Questi messaggi di errore utilizzano una sintassi coerenza per la presentazione di informazioni. Comprendere questa sintassi verrà consentono di identificare e risolvere i problemi.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 33bdf11388ae52959d264e2df091e9c9669b159b
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
ms.locfileid: "31539071"
---
# <a name="error-messages-in-parallel-data-warehouse"></a>Messaggi di errore in Parallel Data Warehouse

I messaggi di errore Parallel Data Warehouse (PDW) segnalano gli errori e problemi rilevati dai componenti PDW e possono includere anche gli errori di SQL Server rese disponibili tramite PDW. Questi messaggi di errore utilizzano una sintassi coerenza per la presentazione di informazioni. La comprensione di questa sintassi consente di identificare e correggere problemi su SQL Server PDW.  
  
## <a name="Basics"></a>Nozioni fondamentali di messaggio di errore  
I messaggi di errore restituiti seguono la stessa sintassi.  
  
`Error_Indicator [SQL_State_Code] [Driver_Details] [QueryID] Message_String`  
  
Questi sono i possibili valori per ogni campo:  
  
|Campo|Description|Esempio|  
|---------|---------------|-----------|  
|*Error_Indicator*|La parola "Errore" o altro testo dell'avviso all'utente di un problema.|ERROR|  
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
  
