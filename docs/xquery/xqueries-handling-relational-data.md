---
title: XQuery per la gestione dei dati relazionali | Documenti Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql
ms.component: xquery
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- relational data [XQuery]
- XQuery, relational data
ms.assetid: 9812b71a-52ec-48a0-92f3-016a93660229
caps.latest.revision: 23
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b03a2aa4b8e6f2327a58884defe1e9435bfbc326
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="xqueries-handling-relational-data"></a>XQuery per la gestione di dati relazionali
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Si specifica XQuery su un' **xml** colonna di tipo o una variabile utilizzando uno del [metodi con tipo di dati XML](../t-sql/xml/xml-data-type-methods.md). Questi includono **query ()**, **Value ()**, **exist ()**, o **Modify ()**. L'espressione XQuery viene eseguita sull'istanza XML identificata nella query che genera il codice XML.  
  
 Il codice XML generato dall'esecuzione di un'espressione XQuery può includere valori recuperati da altre colonne di set di righe o di variabili Transact-SQL. Per eseguire l'associazione di dati relazionali non XML al codice XML risultante, in SQL Server sono disponibili le pseudofunzioni seguenti come estensioni XQuery:  
  
-   **SQL: Column** (funzione)  
  
-   **SQL: variable** (funzione)  
  
 È possibile utilizzare queste estensioni XQuery quando si specifica un'espressione XQuery nel **query ()** metodo il **xml** tipo di dati. Di conseguenza, il **query ()** metodo può generare codice XML che combina i dati da XML e non-**xml** tipi di dati.  
  
 È inoltre possibile utilizzare queste funzioni quando si utilizza il **xml** metodi con tipo di dati **Modify ()**, **Value ()**, **query ()**, e  **EXIST ()** per esporre un valore relazionale nell'istanza XML.  
  
 Per ulteriori informazioni, vedere [funzione SQL: Column (XQuery)](../xquery/xquery-extension-functions-sql-column.md) e [funzione SQL: variable (XQuery)](../xquery/xquery-extension-functions-sql-variable.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Dati XML &#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)   
 [Riferimento al linguaggio XQuery &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)   
 [Costruzione di strutture XML &#40;XQuery&#41;](../xquery/xml-construction-xquery.md)  
  
  
