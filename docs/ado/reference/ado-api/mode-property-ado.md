---
title: La proprietà Mode (ADO) | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::Mode
- _Stream::Mode
- _Record::Mode
helpviewer_keywords:
- Mode property [ADO]
ms.assetid: 808661eb-0d7c-4e6d-8e40-9dc3bef3d77a
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e1aa3910a07fd1e24aeab7429234c1d7211eb6f2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="mode-property-ado"></a>Proprietà Mode (ADO)
Indica le autorizzazioni disponibili per la modifica dei dati in un [connessione](../../../ado/reference/ado-api/connection-object-ado.md), [Record](../../../ado/reference/ado-api/record-object-ado.md), o [flusso](../../../ado/reference/ado-api/stream-object-ado.md) oggetto.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un [ConnectModeEnum](../../../ado/reference/ado-api/connectmodeenum.md) valore. Il valore predefinito per un **connessione** è **adModeUnknown**. Il valore predefinito per un **Record** oggetto **adModeRead**. Il valore predefinito per un **flusso** associata a un'origine sottostante (aperto con un URL come origine o come valore predefinito **flusso** di un **Record**) è  **adModeRead**. Il valore predefinito per un **flusso** non associata a un oggetto sottostante è di origine (creazione di un'istanza in memoria) **adModeUnknown**.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **modalità** proprietà per impostare o restituire le autorizzazioni di accesso utilizzato dal provider per la connessione corrente. È possibile impostare il **modalità** proprietà solo quando il **connessione** oggetto viene chiuso.  
  
 Per un **flusso** dell'oggetto, se la modalità di accesso non è specificata, viene ereditata dall'origine utilizzata per aprire la **flusso** oggetto. Ad esempio, se un **flusso** viene aperto da un **Record** oggetto, per impostazione predefinita è aperto nella stessa modalità come il **Record**.  
  
 Questa proprietà è di lettura/scrittura, mentre l'oggetto è chiuso e di sola lettura finché l'oggetto è aperto.  
  
> [!NOTE]
>  **Utilizzo del servizio dati remoti** quando viene utilizzata su un lato client **connessione** oggetto, il **modalità** proprietà può essere impostata solo su **adModeUnknown**.  
  
## <a name="applies-to"></a>Si applica a  
  
||||  
|-|-|-|  
|[Oggetto Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Oggetto Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|[Oggetto Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio IsolationLevel e Mode proprietà (Visual Basic)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vb.md)   
 [Esempio IsolationLevel e Mode proprietà (VC + +)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vc.md)   
