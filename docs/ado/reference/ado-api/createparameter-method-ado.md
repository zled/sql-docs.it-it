---
title: Metodo CreateParameter (ADO) | Documenti Microsoft
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
- Command15::raw_CreateParameter
- Command15::CreateParameter
helpviewer_keywords:
- CreateParameter method [RDS]
ms.assetid: 9666fdcc-0544-4ed7-a97b-c415f2a56d7e
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a7fc09313bffacefd2d9eff86c9176222c094ebe
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="createparameter-method-ado"></a>Metodo CreateParameter (ADO)
Crea un nuovo [parametro](../../../ado/reference/ado-api/parameter-object.md) oggetto con le proprietà specificate.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Set parameter = command.CreateParameter (Name, Type, Direction, Size, Value)  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un **parametro** oggetto.  
  
#### <a name="parameters"></a>Parametri  
 *Nome*  
 Facoltativa. Oggetto **stringa** valore contenente il nome del **parametro** oggetto.  
  
 *Tipo*  
 Facoltativa. Oggetto [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) valore che specifica il tipo di dati di **parametro** oggetto.  
  
 *Direzione*  
 Facoltativa. Oggetto [ParameterDirectionEnum](../../../ado/reference/ado-api/parameterdirectionenum.md) valore che specifica il tipo di **parametro** oggetto.  
  
 *Dimensione*  
 Facoltativa. Oggetto **lungo** valore che specifica la lunghezza massima per il valore del parametro in caratteri o byte.  
  
 *Valore*  
 Facoltativa. Oggetto **Variant** che specifica il valore per il **parametro** oggetto.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **CreateParameter** metodo per creare un nuovo **parametro** oggetto con un nome, tipo, direzione, dimensioni e valore specificati. Vengono scritti i valori passati negli argomenti corrispondenti **parametro** proprietà.  
  
 Questo metodo non aggiunge automaticamente il **parametro** dell'oggetto per il **parametri** raccolta di un [comando](../../../ado/reference/ado-api/command-object-ado.md) oggetto. Consente di impostare ulteriori proprietà i cui valori ADO verranno convalidati quando si aggiunge il **parametro** oggetto alla raccolta.  
  
 Se si specifica un tipo di dati a lunghezza variabile nel *tipo* argomento, è necessario passare un *dimensioni* argomento o un set di [dimensioni](../../../ado/reference/ado-api/size-property-ado-parameter.md) proprietà del **parametro**  oggetto prima dell'aggiunta per il **parametri** raccolta; in caso contrario, si verifica un errore.  
  
 Se si specifica un tipo di dati numerici (**adNumeric** o **adDecimal**) nei *tipo* argomento, sarà necessario impostare anche la [NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md) e [Precisione](../../../ado/reference/ado-api/precision-property-ado.md) proprietà.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiungere e un esempio di metodi CreateParameter (VB)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vb.md)   
 [Aggiungere e CreateParameter metodi (VC + +)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vc.md)   
 [Append (metodo) (ADO)](../../../ado/reference/ado-api/append-method-ado.md)   
 [Oggetto Parameter](../../../ado/reference/ado-api/parameter-object.md)   
 [Raccolta di parametri (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)

