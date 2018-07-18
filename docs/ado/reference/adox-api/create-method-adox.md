---
title: Create (metodo) (ADOX) | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
ms.openlocfilehash: 9ea6f1f4f333b7929758f829585deb1752f7be50
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35285430"
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
  
## <a name="remarks"></a>Remarks  
 Il **crea** metodo crea e apre un nuovo oggetto ADO [connessione](../../../ado/reference/ado-api/connection-object-ado.md) all'origine dati specificata *ConnectString*. Se ha esito positivo, il nuovo **connessione** oggetto è assegnato il [ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md) proprietà.  
  
 Se il provider non supporta la creazione di nuovi cataloghi, si verificherà un errore.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Catalog (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Creare l'esempio di metodo (VB)](../../../ado/reference/adox-api/create-method-example-vb.md)   
 [Proprietà ActiveConnection (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)
