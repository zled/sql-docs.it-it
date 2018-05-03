---
title: Proprietà di fine del flusso | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- EOS
- Stream::EOS
helpviewer_keywords:
- EOS property
ms.assetid: 57e08c5f-f3ed-4ecd-8c66-50b83b1031d1
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d0eb587e81e238e4bedc3bbfabb67e2a1ce92f4f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="eos-property"></a>Proprietà di fine del flusso
Indica se la posizione corrente è alla fine del [flusso](../../../ado/reference/ado-api/stream-object-ado.md).  
  
## <a name="return-values"></a>Valori restituiti  
 Restituisce un **booleano** valore che indica se la posizione corrente è alla fine del flusso. **Fine del flusso** restituisce **True** se esistono più byte nel flusso di; restituisce **False** se sono presenti più byte seguono la posizione corrente.  
  
 Per impostare la fine della posizione di flusso, utilizzare il [SetEOS](../../../ado/reference/ado-api/seteos-method.md) metodo. Per determinare la posizione corrente, utilizzare il [posizione](../../../ado/reference/ado-api/position-property-ado.md) proprietà.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Fine del flusso e proprietà di LineSeparator ed esempio di metodo SkipLine (VB)](../../../ado/reference/ado-api/eos-and-lineseparator-properties-and-skipline-method-example-vb.md)   
 [Oggetto Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
