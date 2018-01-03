---
title: INSERT - comando SQL | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: INSERT [ODBC]
ms.assetid: 9b648198-349f-46f6-b869-13d129945971
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c78b10cece63014d10d131446d9f43b154e91d7a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="insert---sql-command"></a>INSERT - comando SQL
Accoda un record alla fine di una tabella che contiene i valori di campo specificato.  
  
 Il Driver ODBC di Visual FoxPro supporta la sintassi del linguaggio Visual FoxPro native per questo comando. Per informazioni specifiche del driver, vedere la sezione Osservazioni.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
INSERT INTO dbf_name [(fname1 [, fname2, ...])]  
   VALUES (eExpression1 [, eExpression2, ...])  
```  
  
## <a name="arguments"></a>Argomenti  
 INSERT INTO *dbf_name*  
 Specifica il nome della tabella a cui viene aggiunto il nuovo record. *dbf_name* può includere un percorso e può essere un'espressione di nome.  
  
 Se la tabella specificata non è aperta, viene aperto in modo esclusivo in una nuova area di lavoro e viene aggiunto il nuovo record alla tabella. La nuova area di lavoro non è selezionata; l'area di lavoro corrente rimane selezionato.  
  
 Se la tabella specificata è aperta, l'istruzione INSERT Accoda il nuovo record alla tabella. Se la tabella è aperta in un'area di lavoro oltre l'area di lavoro corrente, non è selezionata dopo che il record viene accodato; l'area di lavoro corrente rimane selezionato.  
  
 [( *fname1*[, *fname2*[,...]])]  
 Specifica i nomi dei campi nel nuovo record in cui vengono inseriti i valori.  
  
 VALORI ( *eExpression1*[, *eExpression2*[,...]])  
 Specifica i valori di campo inseriti un nuovo record. Se si omette i nomi dei campi, è necessario specificare i valori dei campi nell'ordine definito dalla struttura di tabella.  
  
## <a name="remarks"></a>Osservazioni  
 Il nuovo record contiene i dati elencati nella clausola VALUES.  
  
## <a name="driver-remarks"></a>Sezione Osservazioni di driver  
 Quando l'applicazione invia l'istruzione ODBC SQL INSERT per l'origine dati, il Driver ODBC di Visual FoxPro converte il comando al comando FoxProINSERT Visual senza conversione.  
  
## <a name="see-also"></a>Vedere anche  
 [Crea tabella - comando SQL](../../odbc/microsoft/create-table-sql-command.md)   
 [SELECT (comando SQL)](../../odbc/microsoft/select-sql-command.md)
