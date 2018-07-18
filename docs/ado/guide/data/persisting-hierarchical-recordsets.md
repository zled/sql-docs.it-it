---
title: Persistenza di recordset gerarchici | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- hierarchical Recordsets [ADO], persisting
- persisting hierarchical Recordsets [ADO]
- data shaping [ADO], hierarchical Recordsets
ms.assetid: 43798bb5-98a6-4ad6-9bf8-78154b3a1827
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 281204b15620eba99f30c4480817973052af0cea
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2018
ms.locfileid: "38980957"
---
# <a name="persisting-hierarchical-recordsets"></a>Persistenza dei recordset gerarchici
È possibile salvare un modello gerarchico **Recordset** in un file in formato ADTG o XML chiamando la [salvare](../../../ado/reference/ado-api/save-method.md) (metodo). Tuttavia, due limitazioni si applicano quando si salva gerarchica **Recordset**s in formato XML: se non è possibile salvare in XML la gerarchica **Recordset** contiene aggiornamenti, in sospeso e non è possibile salvare un con parametri gerarchica **Recordset**.  
  
 Per altre informazioni sul provider di Data Shaping, vedere [Microsoft Data shaping per OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) (ADO) e [Panoramica del servizio Data Shaping dei dati per OLE DB](http://msdn.microsoft.com/9f51e471-8e85-448e-9fb8-b64bbf767bf3).  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di Data Shaping](../../../ado/guide/data/data-shaping-example.md)   
 [Grammatica formale per Shape](../../../ado/guide/data/formal-shape-grammar.md)   
 [Comandi Shape in generale](../../../ado/guide/data/shape-commands-in-general.md)
