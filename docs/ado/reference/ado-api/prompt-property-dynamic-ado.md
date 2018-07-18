---
title: Richiesta proprietà dinamica (ADO) | Documenti Microsoft
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
helpviewer_keywords:
- Prompt property [ADO]
ms.assetid: c4f001b5-8d16-4d39-a42e-c0e2faaaceaf
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a7b5c0637f7befb1419f5cb96bbcd421d59cc7b8
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35280631"
---
# <a name="prompt-property-dynamic-ado"></a>Proprietà dinamica Prompt (ADO)
Specifica se il provider OLE DB deve richiedere all'utente le informazioni di inizializzazione.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Imposta e restituisce un [ConnectPromptEnum](../../../ado/reference/ado-api/connectpromptenum.md) valore.  
  
## <a name="remarks"></a>Remarks  
 **Messaggio di richiesta** è una proprietà dinamica, che può essere aggiunto al [connessione](../../../ado/reference/ado-api/connection-object-ado.md) dell'oggetto [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) raccolta in base al provider OLE DB. Per richiedere le informazioni di inizializzazione, il provider OLE DB in genere visualizzerà una finestra di dialogo per l'utente.  
  
 Proprietà dinamiche di un [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto vengono perse quando il **connessione** viene chiuso. Il **Prompt** proprietà deve essere reimpostata prima di riaprire il **connessione** per utilizzare un valore diverso da quello predefinito.  
  
> [!NOTE]
>  Non si specifica che il provider deve richiedere all'utente in scenari in cui l'utente non sarà in grado di rispondere alla finestra di dialogo. Ad esempio, l'utente non sarà in grado di rispondere se l'applicazione è in esecuzione in un sistema server invece che sul client dell'utente, o se l'applicazione è in esecuzione in un sistema con connesso alcun utente. In questi casi, l'applicazione attenda indefinitamente la risposta e sembra bloccarsi.  
  
## <a name="usage"></a>Utilizzo  
  
```  
Set cn = New Connection  
cn.Provider = "SQLOLEDB"  
cn.Properties("Prompt") = adPromptNever    ' do not prompt the user  
```  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
