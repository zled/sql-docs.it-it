---
title: Persistenza dei recordset gerarchici | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hierarchical Recordsets [ADO], persisting
- persisting hierarchical Recordsets [ADO]
- data shaping [ADO], hierarchical Recordsets
ms.assetid: 43798bb5-98a6-4ad6-9bf8-78154b3a1827
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a1c4a4fc782bfa6c6130a1acbd45ab1aa2ae3fcd
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="persisting-hierarchical-recordsets"></a>Persistenza dei recordset gerarchici
È possibile salvare un gerarchica **Recordset** in un file in formato ADTG o XML chiamando il [salvare](../../../ado/reference/ado-api/save-method.md) metodo. Tuttavia, vengono applicate due limitazioni quando si salva gerarchica **Recordset**s in formato XML: se non è possibile salvare in XML la gerarchica **Recordset** contiene gli aggiornamenti, in sospeso e non è possibile salvare un con parametri gerarchica **Recordset**.  
  
 Per ulteriori informazioni sui provider di Data Shaping, vedere [Microsoft Data shaping per OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) (ADO) e [Panoramica del servizio dati di Data Shaping per OLE DB](http://msdn.microsoft.com/en-us/9f51e471-8e85-448e-9fb8-b64bbf767bf3).  
  
## <a name="see-also"></a>Vedere anche  
 [Data Shaping di esempio](../../../ado/guide/data/data-shaping-example.md)   
 [Grammatica formale forma](../../../ado/guide/data/formal-shape-grammar.md)   
 [Comandi Shape in generale](../../../ado/guide/data/shape-commands-in-general.md)
