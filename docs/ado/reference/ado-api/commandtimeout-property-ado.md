---
title: "Proprietà CommandTimeout (ADO) | Documenti Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
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
- Command15::CommandTimeout
helpviewer_keywords:
- CommandTimeout property [ADO]
ms.assetid: c611f857-d6b0-4dca-8925-f4a02e769eb0
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e88345e295d38872522b1dfc155d90ad139d8e31
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="commandtimeout-property-ado"></a>Proprietà CommandTimeout (ADO)
Indica il tempo di attesa durante l'esecuzione di un comando prima di terminare il tentativo e generare un errore.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un **lungo** valore che indica, in secondi, il tempo di attesa per un comando da eseguire. Valore predefinito è 30.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **CommandTimeout** proprietà in un [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto o [comando](../../../ado/reference/ado-api/command-object-ado.md) oggetto per consentire l'annullamento di un [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) (metodo) chiama, a causa di ritardi di rete del traffico o a un elevato utilizzo di server. Se l'intervallo impostato nel **CommandTimeout** proprietà scade prima del completamento del comando di esecuzione, si verifica un errore e ADO Annulla il comando. Se si imposta la proprietà su zero, ADO attenderà per un periodo illimitato fino al completamento dell'esecuzione. Verificare che il provider e l'origine dati a cui si sta scrivendo il supporto di codice il **CommandTimeout** funzionalità.  
  
 Il **CommandTimeout** l'impostazione su un **connessione** oggetto non ha alcun effetto **CommandTimeout** l'impostazione su un **comando** oggetto di stesso **connessione**, vale a dire il **comando** dell'oggetto **CommandTimeout** non eredita il valore della proprietà di **connessione** dell'oggetto **CommandTimeout** valore.  
  
 In un **connessione** oggetto, il **CommandTimeout** proprietà rimane impostato su lettura/scrittura dopo il **connessione** viene aperto.  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Oggetto Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Oggetto di connessione (ADO.NET)](../../../ado/reference/ado-api/connection-object-ado.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà direzione (VB), CommandText, CommandTimeout, CommandType, dimensioni e ActiveConnection](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [Esempio di proprietà direzione (VC + +), CommandText, CommandTimeout, CommandType, dimensioni e ActiveConnection](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, dimensioni e direzione proprietà esempio (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)   
 [Proprietà ConnectionTimeout (ADO)](../../../ado/reference/ado-api/connectiontimeout-property-ado.md)

