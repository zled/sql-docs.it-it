---
title: Proprietà DefaultDatabase | Documenti Microsoft
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
apitype: COM
f1_keywords:
- Connection15::DefaultDatabase
helpviewer_keywords:
- DefaultDatabase property
ms.assetid: 41e8a8dd-e69c-4a09-8736-93502e01961c
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f90b450fa2421d47a16946b20fdc707cc266b3e6
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
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
>  **Utilizzo del servizio dati remoti** questa proprietà non è disponibile in un client-side **connessione** oggetto.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà DefaultDatabase (VB) e di provider](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vb.md)   
 [Esempio di proprietà Provider e DefaultDatabase (VC++)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vc.md)   
