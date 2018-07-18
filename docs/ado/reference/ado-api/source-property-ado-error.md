---
title: Proprietà (errore ADO) dell'origine | Documenti Microsoft
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
- Error::get_Source
- Error::Source
- Error::GetSource
helpviewer_keywords:
- Source property [ADO Error]
ms.assetid: 4044ba15-f013-4c4c-9fe1-b4410fe9a778
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1db468ae4575a494b03efc5cf9eb3372b6d5cab2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="source-property-ado-error"></a>Proprietà Source (errore ADO)
Indica il nome dell'oggetto o dell'applicazione che ha generato un errore.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un **stringa** valore che indica il nome di un oggetto o applicazione.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **origine** proprietà in un [errore](../../../ado/reference/ado-api/error-object.md) oggetto per determinare il nome dell'oggetto o dell'applicazione che ha generato un errore. Potrebbe trattarsi dell'oggetto nome di classe o ID a livello di codice. Per gli errori in ADO, il valore della proprietà sarà **ADODB. * * * ObjectName*, dove *ObjectName* è il nome dell'oggetto che ha generato l'errore. Per ADOX e ADO MD, il valore sarà **ADOX. * * * ObjectName* e **ADOMD. * * *, ObjectName* rispettivamente.  
  
 In base alla documentazione di errore dal **origine**, [numero](../../../ado/reference/ado-api/number-property-ado.md), e [descrizione](../../../ado/reference/ado-api/description-property.md) le proprietà di **errore** oggetti, è possibile scrivere codice l'errore che verrà gestito in modo appropriato.  
  
 Il **origine** proprietà è di sola lettura per **errore** oggetti.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Error](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà SQLState (VB), HelpContext, HelpFile, NativeError, numero, origine e descrizione](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Esempio di proprietà SQLState (VC + +), HelpContext, HelpFile, NativeError, numero, origine e descrizione](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Proprietà Description](../../../ado/reference/ado-api/description-property.md)   
 [Proprietà HelpContext, HelpFile](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Proprietà Number (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [Proprietà Source (Record ADO)](../../../ado/reference/ado-api/source-property-ado-record.md)   
 [Proprietà Source (Recordset ADO)](../../../ado/reference/ado-api/source-property-ado-recordset.md)
