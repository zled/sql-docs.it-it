---
title: Proprietà (errore ADO) dell'origine | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::get_Source
- Error::Source
- Error::GetSource
helpviewer_keywords:
- Source property [ADO Error]
ms.assetid: 4044ba15-f013-4c4c-9fe1-b4410fe9a778
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 50294b936f211b3a841deb57e55b53f0994517a8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47611586"
---
# <a name="source-property-ado-error"></a>Proprietà Source (Error - ADO)
Indica il nome dell'oggetto o applicazione che ha generato un errore.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un **stringa** valore che indica il nome di un oggetto o applicazione.  
  
## <a name="remarks"></a>Note  
 Usare la **origine** proprietà in un [errore](../../../ado/reference/ado-api/error-object.md) oggetto per determinare il nome dell'oggetto o applicazione che ha generato un errore. Potrebbe trattarsi dell'oggetto nome della classe o a livello di codice ID. Per gli errori in ADO, il valore della proprietà sarà **ADODB. * * * ObjectName*, dove *ObjectName* è il nome dell'oggetto che ha generato l'errore. Per ADOX e ADO MD, il valore sarà **ADOX. * * * ObjectName* e **ADOMD. * * * ObjectName,* rispettivamente.  
  
 Sulla base della documentazione di errore dal **origine**, [numero](../../../ado/reference/ado-api/number-property-ado.md), e [descrizione](../../../ado/reference/ado-api/description-property.md) le proprietà di **errore** oggetti, è possibile scrivere codice l'errore che verrà gestito in modo appropriato.  
  
 Il **origine** proprietà è di sola lettura per **errore** oggetti.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Error](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Description, HelpContext, HelpFile, NativeError, numero, origine e SQLState proprietà esempio (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description, HelpContext, HelpFile, NativeError, numero, origine e SQLState esempio di proprietà (VC + +)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Proprietà Description](../../../ado/reference/ado-api/description-property.md)   
 [Proprietà HelpContext, HelpFile](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Proprietà Number (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [Proprietà Source (Record ADO)](../../../ado/reference/ado-api/source-property-ado-record.md)   
 [Proprietà Source (Recordset ADO)](../../../ado/reference/ado-api/source-property-ado-recordset.md)
