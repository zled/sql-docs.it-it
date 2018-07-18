---
title: Raccolta di errori (ADO) | Documenti Microsoft
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
- Connection15::Errors
- Connection15::get_Errors
- Connection15::GetErrors
helpviewer_keywords:
- Errors collection [ADO]
ms.assetid: 290819e1-7b39-4e1e-a93b-801257138b00
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e7c259dda6c491c1992c19ed0ebe3decdc4a42d3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="errors-collection-ado"></a>Raccolta di errori (ADO)
Contiene tutti i [errore](../../../ado/reference/ado-api/error-object.md) gli oggetti creati in risposta a un singolo errore correlato al provider.  
  
## <a name="remarks"></a>Osservazioni  
 Qualsiasi operazione relativa agli oggetti ADO può generare una o più errori del provider. Quando si verifica ogni errore, uno o più **errore** oggetti possono essere inseriti nel **errori** insieme del [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto. Quando un'altra operazione ADO genera un errore, il **errori** insieme è deselezionata e il nuovo set di **errore** oggetti possono essere inseriti nel **errori** insieme.  
  
 Ogni **errore** oggetto rappresenta un errore del provider specifico, non un errore di ADO. Gli errori ADO vengono esposti al meccanismo di gestione delle eccezioni in fase di esecuzione. Ad esempio, in Microsoft Visual Basic, l'occorrenza di un errore specifico ADO verrà generato un [onError](../../../ado/reference/rds-api/onerror-event-rds.md) eventi e vengono visualizzate nel **Err** oggetto.  
  
 Le operazioni di ADO che non generano un errore non hanno effetto sul **errori** insieme. Utilizzare il [deselezionare](../../../ado/reference/ado-api/clear-method-ado.md) metodo cancellare manualmente le **errori** insieme.  
  
 Il set di **errore** gli oggetti di **errori** raccolta descrive tutti gli errori che si sono verificati in risposta a una singola istruzione. L'enumerazione degli errori specifici di **errori** raccolta consente alle routine di gestione degli errori in più precisamente determinare la causa e l'origine dell'errore e intraprendere le misure necessarie per ripristinare.  
  
 Alcune proprietà e metodi restituiscono avvisi che vengono visualizzati come **errore** gli oggetti di **errori** raccolta ma non arrestano l'esecuzione del programma. Prima di chiamare il [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), o [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) metodi su un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto, il [aprire](../../../ado/reference/ado-api/open-method-ado-connection.md) metodo su un **connessione** dell'oggetto o impostare il [filtro](../../../ado/reference/ado-api/filter-property.md) proprietà in un **Recordset** dell'oggetto, chiamare il **deselezionare**metodo il **errori** insieme. In questo modo è possibile leggere il [conteggio](../../../ado/reference/ado-api/count-property-ado.md) proprietà del **errori** raccolta da testare per avvisi restituiti.  
  
> [!NOTE]
>  Vedere il **errore** argomento di oggetto per una spiegazione più dettagliata del modo in cui una singola operazione ADO può generare più errori.  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Proprietà di raccolta di errori, metodi ed eventi](../../../ado/reference/ado-api/errors-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Error](../../../ado/reference/ado-api/error-object.md)   
 [Appendice A: Provider](../../../ado/guide/appendixes/appendix-a-providers.md)
