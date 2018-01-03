---
title: Interfaccia ADORecordConstruction | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: ADORecordConstruction
helpviewer_keywords: ADORecordConstruction interface [ADO]
ms.assetid: 52a5429e-5829-455e-be3b-31f05cbecf2d
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1cedc7639b0b5c1559fe137be96c822287a3ff82
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="adorecordconstruction-interface"></a>Interfaccia ADORecordConstruction
Il **ADORecordConstruction**interfaccia viene utilizzata per costruire un oggetto ADO **Record** oggetto da OLE DB **riga** oggetto in un'applicazione C/C++.  
  
 Questa interfaccia supporta le proprietà seguenti:  
  
## <a name="properties"></a>Proprietà  
  
|||  
|-|-|  
|[ParentRow](../../../ado/reference/ado-api/parentrow-property-ado.md)|Sola scrittura.<br />Imposta il contenitore di OLE DB **riga** oggetto questo ADO **Record** oggetto.|  
|[Riga](../../../ado/reference/ado-api/row-property-ado.md)|Lettura/scrittura.<br />Ottiene o imposta il valore OLE DB **riga** oggetto da/su questo ADO **Record** oggetto.|  
  
## <a name="methods"></a>Metodi  
 nessuna.  
  
## <a name="events"></a>Eventi  
 nessuna.  
  
## <a name="remarks"></a>Osservazioni  
 Data OLE DB **riga** oggetto (`pRow`), la costruzione di un oggetto ADO **Record** oggetto (`adoR`), gli importi di tre operazioni di base seguenti:  
  
1.  Creare un oggetto ADO **Record** oggetto:  
  
    ```  
    _RecordPtr adoR;  
    adoRs.CreateInstance(__uuidof(_Record));  
    ```  
  
2.  Query di **IADORecordConstruction** interfaccia il **Record** oggetto:  
  
    ```  
    adoRecordConstructionPtr adoRConstruct=NULL;  
    adoR->QueryInterface(__uuidof(ADORecordConstruction),  
                        (void**)&adoRConstruct);  
    ```  
  
3.  Chiamare il **IADORecordConstruction::** il metodo di proprietà per impostare OLE DB **riga** sull'oggetto ADO **Record** oggetto:  
  
    ```  
    IUnknown *pUnk=NULL;  
    pRow->QueryInterface(IID_IUnknown, (void**)&pUnk);  
    adoRConstruct->put_Row(pUnk);  
    ```  
  
 I risultanti **adoR** oggetto rappresenta l'oggetto ADO **Record** oggetto costruito da OLE DB **riga** oggetto.  
  
 Un oggetto ADO **Record** oggetto può anche essere costruito dal contenitore di OLE DB **riga** oggetto.  
  
## <a name="requirements"></a>Requisiti  
 **Versione:** ADO 2.0 e versioni successiva  
  
 **Libreria:** msado15.dll  
  
 **UUID:** 00000567-0000-0010-8000-00AA006D2EA4
