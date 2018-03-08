---
title: XQuery per la gestione dei dati relazionali | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: xquery
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- relational data [XQuery]
- XQuery, relational data
ms.assetid: 9812b71a-52ec-48a0-92f3-016a93660229
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 420caf1620974293f279e72892f0da2cad6a140b
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="xqueries-handling-relational-data"></a>XQuery per la gestione di dati relazionali
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Si specifica XQuery su un' **xml** colonna di tipo o una variabile utilizzando uno del [metodi con tipo di dati XML](../t-sql/xml/xml-data-type-methods.md). Questi includono **query ()**, **Value ()**, **exist ()**, o **Modify ()**. L'espressione XQuery viene eseguita sull'istanza XML identificata nella query che genera il codice XML.  
  
 Il codice XML generato dall'esecuzione di un'espressione XQuery può includere valori recuperati da altre colonne di set di righe o di variabili Transact-SQL. Per eseguire l'associazione di dati relazionali non XML al codice XML risultante, in SQL Server sono disponibili le pseudofunzioni seguenti come estensioni XQuery:  
  
-   **SQL: Column** (funzione)  
  
-   **SQL: variable** (funzione)  
  
 È possibile utilizzare queste estensioni XQuery quando si specifica un'espressione XQuery nel **query ()** metodo il **xml** tipo di dati. Di conseguenza, il **query ()** metodo può generare codice XML che combina i dati da XML e non-**xml** tipi di dati.  
  
 È inoltre possibile utilizzare queste funzioni quando si utilizza il **xml** metodi con tipo di dati **Modify ()**, **Value ()**, **query ()**, e  **EXIST ()**per esporre un valore relazionale nell'istanza XML.  
  
 Per ulteriori informazioni, vedere [funzione SQL: Column (XQuery)](../xquery/xquery-extension-functions-sql-column.md) e [funzione SQL: variable (XQuery)](../xquery/xquery-extension-functions-sql-variable.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Dati XML &#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)   
 [Riferimento al linguaggio XQuery &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)   
 [Costruzione di strutture XML &#40; XQuery &#41;](../xquery/xml-construction-xquery.md)  
  
  
