---
title: HelpContext e HelpFile | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Error::GetHelpContext
- Error::GetHelpFile
- Error::get_HelpFile
- Error::get_HelpContext
- Error::HelpContext
- Error::HelpFile
helpviewer_keywords:
- HelpContext property [ADO]
- HelpFile property [ADO]
ms.assetid: 2b9ef441-993c-44d4-8f87-fac0979dac1d
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dce4f5513199be2b4c74903741178844c0ecedf6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="helpcontext-helpfile-properties"></a>Proprietà HelpContext, HelpFile
Indica il file e l'argomento associato a un [errore](../../../ado/reference/ado-api/error-object.md) oggetto.  
  
## <a name="return-values"></a>Valori restituiti  
  
-   **ID argomento Guida** restituisce un ID di contesto, come un **lungo** valore, per un argomento in un file della Guida.  
  
-   **HelpFile** restituisce un **stringa** valore che restituisce un percorso completamente risolto a un file della Guida.  
  
## <a name="remarks"></a>Osservazioni  
 Se viene specificato un file della Guida nel **HelpFile** proprietà, il **HelpContext** proprietà viene utilizzata per visualizzare automaticamente l'argomento della Guida vengono identificati. Se non è disponibile, nessun argomento della Guida rilevante di **HelpContext** proprietà restituisce zero e **HelpFile** proprietà restituisce una stringa di lunghezza zero ("").  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Error](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà SQLState (VB), HelpContext, HelpFile, NativeError, numero, origine e descrizione](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Esempio di proprietà SQLState (VC + +), HelpContext, HelpFile, NativeError, numero, origine e descrizione](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Proprietà Description](../../../ado/reference/ado-api/description-property.md)   
 [Proprietà Number (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [Proprietà Source (errore ADO)](../../../ado/reference/ado-api/source-property-ado-error.md)
