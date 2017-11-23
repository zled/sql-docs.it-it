---
title: Interfaccia ADOStreamConstruction | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: ADOStreamConstruction
helpviewer_keywords: ADOStreamConstruction interface [ADO]
ms.assetid: 92f5a939-3e1a-4b14-a9dd-90e6ce2dec74
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e22c76c1e484e544e53d9ee313e6e303b7f0b8f2
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="adostreamconstruction-interface"></a>Interfaccia ADOStreamConstruction
Il **ADOStreamConstruction** interfaccia viene utilizzata per costruire un oggetto ADO **flusso** oggetto da OLE DB **IStream** oggetto in un'applicazione C/C++.  
  
## <a name="properties"></a>Proprietà  
  
|||  
|-|-|  
|[Proprietà Stream](../../../ado/reference/ado-api/stream-property.md)|Lettura/scrittura. Ottiene o imposta il valore OLE DB **flusso** oggetto.|  
  
## <a name="methods"></a>Metodi  
 nessuna.  
  
## <a name="events"></a>Eventi  
 nessuna.  
  
## <a name="remarks"></a>Osservazioni  
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
