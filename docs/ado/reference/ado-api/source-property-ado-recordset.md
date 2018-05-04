---
title: Proprietà (Recordset ADO) dell'origine | Documenti Microsoft
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
- Recordset15::putref_Source
- Recordset15::Source
- Recordset15::PutSource
- Recordset15::get_Source
- Recordset15::GetSource
- Recordset15::PutRefSource
- Recordset15::put_Source
helpviewer_keywords:
- Source property [ADO Recordset]
ms.assetid: a05ba2c9-2821-4343-8607-4de9b764ec91
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fff874c34b527adc976b608e6b1594427245de24
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="source-property-ado-recordset"></a>Proprietà Source (Recordset ADO)
Indica l'origine dati per un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Imposta un **stringa** valore o [comando](../../../ado/reference/ado-api/command-object-ado.md) riferimento; oggetto restituisce solo un **stringa** valore che indica l'origine il **Recordset**.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **origine** proprietà per specificare un'origine dati per un **Recordset** utilizzando uno dei seguenti: un **comando** oggetto variabile, un'istruzione SQL, una stored procedure, o un nome di tabella.  
  
 Se si imposta la **origine** proprietà per un **comando** oggetto, il [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) proprietà del **Recordset** oggetto erediterà il valore di **ActiveConnection** proprietà per l'oggetto specificato **comando** oggetto. Tuttavia, durante la lettura di **origine** proprietà non restituisce un **comando** oggetto; al contrario, restituisce il [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) proprietà del **comando** dell'oggetto per cui impostare il **origine** proprietà.  
  
 Se il **origine** proprietà è un'istruzione SQL, una stored procedure o un nome di tabella, è possibile ottimizzare le prestazioni passando appropriata *opzioni* argomento con il [aprire](../../../ado/reference/ado-api/open-method-ado-recordset.md)chiamata al metodo.  
  
 Il **origine** proprietà è di lettura/scrittura per chiuso **Recordset** oggetti e di sola lettura per aprire **Recordset** oggetti.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà Source (VB)](../../../ado/reference/ado-api/source-property-example-vb.md)   
 [Proprietà Source (errore ADO)](../../../ado/reference/ado-api/source-property-ado-error.md)   
 [Proprietà Source (Record ADO)](../../../ado/reference/ado-api/source-property-ado-record.md)
