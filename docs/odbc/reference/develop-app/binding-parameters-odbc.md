---
title: Associazione dei parametri ODBC | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- binding parameters [ODBC]
ms.assetid: 7538a82b-b08b-4c8f-9809-e4ccea16db11
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cc39c8183c996dd4d011d9bcdaba6dfe1f94cc05
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32909295"
---
# <a name="binding-parameters-odbc"></a>Associazione dei parametri ODBC
Ogni parametro in un'istruzione SQL deve essere associato, o *associato,* a una variabile nell'applicazione prima dell'esecuzione dell'istruzione. Quando l'applicazione associa una variabile a un parametro, descrive tale variabile, indirizzo, tipo di dati C e così via, per il driver. Viene inoltre descritto il parametro, i dati SQL tipo, precisione e così via. Il driver, queste informazioni vengono memorizzate nella struttura mantenuta per l'istruzione e utilizza le informazioni per recuperare il valore della variabile quando viene eseguita l'istruzione.  
  
 I parametri associati o riassociati in qualunque momento prima che venga eseguita un'istruzione. Se un parametro è riassociato dopo l'esecuzione di un'istruzione, l'associazione non viene applicato fino a quando non viene eseguita nuovamente l'istruzione. Per associare un parametro a una variabile diversa, un'applicazione riassocia semplicemente il parametro con la nuova variabile. l'associazione precedente viene rilasciata automaticamente.  
  
 Una variabile rimane associata a un parametro fino a quando una variabile diversa è associata al parametro, fino a quando tutti i parametri sono associati chiamando **SQLFreeStmt** con l'opzione SQL_RESET_PARAMS o fino a quando l'istruzione viene rilasciato. Per questo motivo, l'applicazione deve assicurarsi che le variabili non vengono liberate fino a dopo che sono non associati. Per ulteriori informazioni, vedere [allocazione e liberando buffer](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md).  
  
 Poiché le associazioni di parametri sono solo informazioni archiviate nella struttura gestita dal driver per l'istruzione, possono essere impostate in qualsiasi ordine. Sono anche indipendenti dell'istruzione SQL eseguita. Si supponga, ad esempio, un'applicazione associa i tre parametri, quindi viene eseguita l'istruzione SQL seguente:  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Se l'applicazione quindi immediatamente eseguita l'istruzione SQL  
  
```  
SELECT * FROM Orders WHERE OrderID = ?, OpenDate = ?, Status = ?  
```  
  
 sullo stesso handle di istruzione, le associazioni dei parametri per il **inserire** istruzione vengono utilizzati in quanto queste sono le associazioni archiviate nella struttura di istruzione. Nella maggior parte dei casi, questo è un livello di programmazione ridotte e deve essere evitato. Al contrario, l'applicazione deve chiamare **SQLFreeStmt** con l'opzione SQL_RESET_PARAMS per separare tutti i parametri precedenti e quindi associare nuovi.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Associazione di marcatori di parametro](../../../odbc/reference/develop-app/binding-parameter-markers.md)  
  
-   [Associazione di parametri in base al nome (parametri denominati)](../../../odbc/reference/develop-app/binding-parameters-by-name-named-parameters.md)  
  
-   [Offset di associazione di parametri](../../../odbc/reference/develop-app/parameter-binding-offsets.md)  
  
-   [Descrizione di parametri](../../../odbc/reference/develop-app/describing-parameters.md)
