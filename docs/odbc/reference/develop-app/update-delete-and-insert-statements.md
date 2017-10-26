---
title: Le istruzioni INSERT, DELETE e UPDATE | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- updating data [ODBC], about updating data
- DELETE [ODBC]
- UPDATE [ODBC]
- INSERT [ODBC]
- data updates [ODBC], about data updates
ms.assetid: 5004ea72-4c49-4064-9752-f7032ba7f133
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b150288c113b1aebf92abedbd6f7eabd0b4b7d24
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="update-delete-and-insert-statements"></a>Le istruzioni INSERT, DELETE e UPDATE
Applicazioni basate su SQL apportano modifiche alle tabelle mediante l'esecuzione di **aggiornamento**, **eliminare**, e **inserire** istruzioni. Queste istruzioni fanno parte del livello di conformità di grammatica SQL minima e devono essere supportate da tutti i driver e origini dati.  
  
 La sintassi di queste istruzioni è:  
  
 **AGGIORNAMENTO***-nome della tabella  *  
  
 **IMPOSTARE** *colonna identificatore* ** = ** {*espressione* &#124; **NULL**}  
  
 [**,** *colonna identificatore* ** = ** {*espressione* &#124; **NULL**}]...  
  
 [**In** *condizione di ricerca*]  
  
 **DELETE FROM** *-nome della tabella*[**in** *condizione di ricerca*]  
  
 **INSERT INTO** *-nome della tabella*[**(***colonna identificatore* [**,** *-identificatoredellacolonna*] ... **)**]  
  
 {*specifica di query* &#124; **Valori (***Inserisci valore* [**,** *Inserisci valore*]... **)**}  
  
 Si noti che il *specifica di query* elemento è valido solo nelle grammatiche Core e SQL estesa e che il *espressione* e *condizione di ricerca* diventano più elementi complessi nelle grammatiche Core e SQL estesa.  
  
 Come le altre istruzioni SQL, **aggiornamento**, **eliminare**, e **inserire** istruzioni sono spesso più efficiente quando usano i parametri. Ad esempio, è possibile preparato ed eseguita ripetutamente per inserire più righe nella tabella Orders l'istruzione seguente:  
  
```  
INSERT INTO Orders (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Questa efficienza può essere aumentata mediante il passaggio di matrici di valori di parametro. Per ulteriori informazioni sui parametri dell'istruzione e le matrici di valori dei parametri, vedere [parametri dell'istruzione](../../../odbc/reference/develop-app/statement-parameters.md).

