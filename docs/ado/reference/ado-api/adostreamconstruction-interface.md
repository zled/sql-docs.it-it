---
title: Interfaccia ADOStreamConstruction | Documenti Microsoft
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
- ADOStreamConstruction
helpviewer_keywords:
- ADOStreamConstruction interface [ADO]
ms.assetid: 92f5a939-3e1a-4b14-a9dd-90e6ce2dec74
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 73c5e698ecebee93e6b78d884b0b2978750db63e
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35275690"
---
# <a name="adostreamconstruction-interface"></a>Interfaccia ADOStreamConstruction
Il **ADOStreamConstruction** interfaccia viene utilizzata per costruire un oggetto ADO **flusso** oggetto da OLE DB **IStream** oggetto in un'applicazione C/C++.  
  
## <a name="properties"></a>Proprietà  
  
|||  
|-|-|  
|[Proprietà Stream](../../../ado/reference/ado-api/stream-property.md)|Lettura/scrittura. Ottiene o imposta il valore OLE DB **flusso** oggetto.|  
  
## <a name="methods"></a>Metodi  
 Nessuna.  
  
## <a name="events"></a>Eventi  
 Nessuna.  
  
## <a name="remarks"></a>Remarks  
 Data OLE DB **IStream** oggetto (`pStream`), la costruzione di un oggetto ADO **flusso** oggetto (`adoStr`) gli importi di tre operazioni di base seguenti:  
  
1.  Creare un oggetto ADO **flusso** oggetto:  
  
    ```  
    Stream20Ptr adoStr;  
    adoStr.CreateInstance(__uuidof(Stream));  
    ```  
  
2.  Query di **IADOStreamConstruction** interfaccia il **flusso** oggetto:  
  
    ```  
    adoStreamConstructionPtr adoStrConstruct=NULL;  
    adoStr->QueryInterface(__uuidof(ADOStreamConstruction),  
                         (void**)&adoStrConstruct);  
    ```  
  
 Chiamare il `IADOStreamConstruction::get_Stream` il metodo di proprietà per impostare OLE DB **IStream** sull'oggetto ADO **flusso** oggetto:  
  
```  
IUnknown *pUnk=NULL;  
pRowset->QueryInterface(IID_IUnknown, (void**)&pUnk);  
adoStrConstruct->put_Stream(pUnk);  
```  
  
 I risultanti `adoStr` oggetto rappresenta l'oggetto ADO **flusso** oggetto costruito da OLE DB **IStream** oggetto.  
  
## <a name="requirements"></a>Requisiti  
 **Versione:** ADO 2.0 o versione successiva  
  
 **Libreria:** msado15.dll  
  
 **UUID:** 00000283-0000-0010-8000-00AA006D2EA4  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento API ADO](../../../ado/reference/ado-api/ado-api-reference.md)
