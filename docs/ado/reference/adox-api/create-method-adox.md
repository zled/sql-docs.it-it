---
title: Create (metodo) (ADOX) | Documenti Microsoft
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
- _Catalog::raw_Create
- _Catalog::Create
helpviewer_keywords:
- Create method [ADOX]
ms.assetid: 64f5c21c-b581-42d8-bdc7-c4f1bebaf105
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c1c159f0e53c5c4b39d9c225dd7dfa8cee581445
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="create-method-adox"></a>Create (metodo) (ADOX)
Crea un nuovo catalogo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Catalog.Create ConnectString  
```  
  
#### <a name="parameters"></a>Parametri  
 *ConnectString*  
 Oggetto **stringa** valore utilizzato per connettersi all'origine dati.  
  
## <a name="remarks"></a>Osservazioni  
 Il **crea** metodo crea e apre un nuovo oggetto ADO [connessione](../../../ado/reference/ado-api/connection-object-ado.md) all'origine dati specificata *ConnectString*. Se ha esito positivo, il nuovo **connessione** oggetto è assegnato il [ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md) proprietà.  
  
 Se il provider non supporta la creazione di nuovi cataloghi, si verificherà un errore.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Catalog (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Creare l'esempio di metodo (VB)](../../../ado/reference/adox-api/create-method-example-vb.md)   
 [Proprietà ActiveConnection (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)
