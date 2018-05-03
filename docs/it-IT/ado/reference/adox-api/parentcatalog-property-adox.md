---
title: Proprietà ParentCatalog (ADOX) | Documenti Microsoft
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
- _User::get_ParentCatalog
- _Column::ParentCatalog
- _Table::put_ParentCatalog
- _Group::put_ParentCatalog
- _Column::get_ParentCatalog
- _Table::PutParentCatalog
- _Group::putref_ParentCatalog
- _Group::ParentCatalog
- _Column::PutParentCatalog
- _Column::put_ParentCatalog
- _Group::get_ParentCatalog
- _User::put_ParentCatalog
- _User::putref_ParentCatalog
- _Table::get_ParentCatalog
- _Group::PutParentCatalog
- _Table::ParentCatalog
- _Column::GetParentCatalog
- _Table::PutRefParentCatalog
- _User::GetParentCatalog
- _Table::GetParentCatalog
- _Table::putref_ParentCatalog
- _User::PutParentCatalog
- _User::ParentCatalog
- _User::PutRefParentCatalog
- _Group::GetParentCatalog
- _Group::PutRefParentCatalog
helpviewer_keywords:
- ParentCatalog property [ADOX]
ms.assetid: a0bb2ed8-d4cb-4f92-8de7-769bbe0e6273
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 301919cb86891e94d1b2149dda6aaf403c0b05e1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="parentcatalog-property-adox"></a>Proprietà ParentCatalog (ADOX)
Specifica il catalogo padre di un oggetto tabella, un utente o colonna per fornire accesso a proprietà specifiche del provider.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Imposta e restituisce un [catalogo](../../../ado/reference/adox-api/catalog-object-adox.md) oggetto. Impostazione **ParentCatalog** per open **catalogo** consente l'accesso a proprietà specifiche del provider prima di aggiungere una tabella o colonna per un **catalogo** insieme.  
  
## <a name="remarks"></a>Osservazioni  
 Alcuni provider di dati consentono i valori delle proprietà specifiche del provider deve essere scritto solo al momento della creazione: ovvero, quando una tabella o colonna viene aggiunto al relativo **catalogo** insieme. Per accedere a queste proprietà prima di accodare gli oggetti per un **catalogo**, specificare il **catalogo** nel **ParentCatalog** proprietà prima.  
  
 Si verifica un errore quando la tabella o la colonna viene aggiunta a un altro **catalogo** più il **ParentCatalog**.  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Oggetto Column (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)|[Oggetto Table (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|  
|[Oggetto User (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)||  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà ParentCatalog (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)
