---
title: "Proprietà DefaultDatabase | Documenti Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Connection15::DefaultDatabase
helpviewer_keywords:
- DefaultDatabase property
ms.assetid: 41e8a8dd-e69c-4a09-8736-93502e01961c
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2c4220d8551d7aa9d1bd37f0770474214bc14209
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="defaultdatabase-property"></a>Proprietà DefaultDatabase
Indica il database predefinito per un [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un **stringa** valore che restituisce il nome di un database disponibile dal provider.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **DefaultDatabase** proprietà per impostare o restituire il nome del database predefinito per uno specifico **connessione** oggetto.  
  
 Se è presente un database predefinito, le stringhe SQL possono utilizzare una sintassi non qualificata per accedere agli oggetti in tale database. Per accedere agli oggetti in un database diverso da quello specificato nella **DefaultDatabase** proprietà, è necessario qualificare i nomi degli oggetti con il nome del database desiderato. Al momento della connessione, il provider scriverà le informazioni sul database predefinito per il **DefaultDatabase** proprietà. Alcuni provider consentono un solo database per ogni connessione, nel qual caso non è possibile modificare il **DefaultDatabase** proprietà.  
  
 Alcune origini dati e provider potrebbero non supportare questa funzionalità e può restituire un errore o una stringa vuota.  
  
> [!NOTE]
>  **Utilizzo del servizio dati remoti** questa proprietà non è disponibile sul lato client **connessione** oggetto.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà DefaultDatabase (VB) e di provider](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vb.md)   
 [Esempio di proprietà Provider e DefaultDatabase (VC++)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vc.md)   
