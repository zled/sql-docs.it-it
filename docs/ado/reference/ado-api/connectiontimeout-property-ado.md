---
title: Proprietà ConnectionTimeout (ADO) | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::ConnectionTimeout
helpviewer_keywords:
- ConnectionTimeout property [ADO]
ms.assetid: 8904a403-1383-4b4b-b53d-5c01d6f5deac
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a1f90890b8f48a4a00fe9469ed978d42d3f6a86a
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35277010"
---
# <a name="connectiontimeout-property-ado"></a>Proprietà ConnectionTimeout (ADO)
Indica il tempo di attesa durante il tentativo di stabilire una connessione prima di terminare il tentativo e generare un errore.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un **lungo** valore che indica, in secondi, il tempo di attesa per la connessione da aprire. Valore predefinito è 15.  
  
## <a name="remarks"></a>Remarks  
 Utilizzare il **ConnectionTimeout** proprietà in un [connessione](../../../ado/reference/ado-api/connection-object-ado.md) se ritardi di rete del traffico o a un elevato utilizzo di server rendono necessario interrompere un tentativo di connessione dell'oggetto. Se l'ora dal **ConnectionTimeout** l'impostazione della proprietà scade prima dell'apertura della connessione, si verifica un errore e ADO Annulla il tentativo. Se si imposta la proprietà su zero, ADO attenderà all'infinito finché non viene aperta la connessione. Verificare che il provider a cui si sta scrivendo codice supporta il **ConnectionTimeout** funzionalità.  
  
 Il **ConnectionTimeout** proprietà è di lettura/scrittura quando la connessione è chiusa e di sola lettura quando è aperto.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio ConnectionString, ConnectionTimeout e la proprietà State (VB)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [Esempio ConnectionString, ConnectionTimeout e la proprietà State (VC + +)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
 [Proprietà CommandTimeout (ADO)](../../../ado/reference/ado-api/commandtimeout-property-ado.md)
