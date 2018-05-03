---
title: Determinazione delle funzionalità supportate | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- editing data [ADO], Supports method
- Supports method [ADO]
ms.assetid: 65090cba-6d46-4775-8d61-f6838e7752a6
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 842b700a9359fe513fcdfc0b01009da1c10a084a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="determining-what-is-supported"></a>Determinazione delle funzionalità supportate
Il **supporta** metodo viene utilizzato per determinare se un oggetto **Recordset** oggetto supporta un determinato tipo di funzionalità. Contiene la sintassi seguente:  
  
```  
  
boolean = recordset.Supports(CursorOptions )  
```  
  
## <a name="remarks"></a>Osservazioni  
 Il **supporta** metodo restituisce un valore booleano che indica se il provider supporta tutte le funzionalità identificate dall'argomento CursorOptions. È possibile utilizzare il **supporta** metodo per determinare i tipi di funzionalità un **Recordset** supporta dell'oggetto. Se il **Recordset** oggetto supporta le funzionalità la cui costanti corrispondenti sono *CursorOptions*, **supporta** restituisce **True**. In caso contrario, restituisce **False**.  
  
 Utilizzando il **supporta** (metodo), è possibile cercare la capacità del **Recordset** oggetto per aggiungere nuovi record, utilizzare i segnalibri, utilizzare il **trovare** metodo, utilizzare lo scorrimento, utilizzare il  **Indice** , proprietà ed eseguire gli aggiornamenti in batch. Per un elenco completo delle costanti e i relativi significati, vedere [CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md).  
  
 Sebbene il **supporta** metodo può restituire **True** per una determinata funzionalità non garantisce che il provider può rendere la funzionalità disponibile in tutte le circostanze. Il **supporta** metodo restituisce semplicemente se il provider supporta la funzionalità specificata, presupponendo che vengano soddisfatte determinate condizioni. Ad esempio, il **supporta** metodo può indicare che un **Recordset** oggetto supporta gli aggiornamenti, anche se il cursore è basato su un join tra più tabelle, alcune colonne di cui non sono aggiornabili.
