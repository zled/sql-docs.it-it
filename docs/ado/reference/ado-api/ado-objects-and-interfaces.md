---
title: Interfacce e gli oggetti ADO | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ADO, objects and interfaces
- objects [ADO]
ms.assetid: d0b7e254-c89f-4406-b846-a060ef038c30
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d4d0b2c896be1059d999418d1f88053225c5d44a
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="ado-objects-and-interfaces"></a>Le interfacce e gli oggetti ADO
Le relazioni tra questi oggetti sono rappresentate nel [modello a oggetti ADO](../../../ado/reference/ado-api/ado-object-model.md).  
  
 Ogni oggetto può essere contenuto nell'insieme corrispondente. Ad esempio, un [errore](../../../ado/reference/ado-api/error-object.md) oggetto può essere contenuto un [errori](../../../ado/reference/ado-api/errors-collection-ado.md) insieme. Per ulteriori informazioni, vedere [insiemi ADO](../../../ado/reference/ado-api/ado-collections.md) o un argomento di raccolta specifica.  
  
|||  
|-|-|  
|[IADOCommandConstruction](https://msdn.microsoft.com/library/windows/desktop/aa965677.aspx)|Consente di recuperare il comando OLE DB sottostante da un oggetto ADOCommand.|  
|[ADORecordConstruction](../../../ado/reference/ado-api/adorecordconstruction-interface.md)|Costruisce un oggetto ADO **Record** oggetto da OLE DB **riga** oggetto in un'applicazione C/C++.|  
|[ADORecordsetConstruction](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)|Costruisce un oggetto ADO **Recordset** oggetto da OLE DB **set di righe** oggetto in un'applicazione C/C++.|  
|[Interfaccia ADOStreamConstruction](../../../ado/reference/ado-api/adostreamconstruction-interface.md)|Costruisce un oggetto ADO **flusso** oggetto da OLE DB **IStream** oggetto in un'applicazione C/C++.|  
|[Command](../../../ado/reference/ado-api/command-object-ado.md)|Definisce un comando specifico che si desidera eseguire in un'origine dati.<br /><br /> Il **comando** oggetto non è sicuro per lo scripting.|  
|[Connessione](../../../ado/reference/ado-api/connection-object-ado.md)|Rappresenta una connessione aperta a un'origine dati.<br /><br /> Il **connessione** oggetto è sicuro per lo script.|  
|[Interfaccia IDSOShapeExtensions](../../../ado/reference/ado-api/idsoshapeextensions-interface.md)|Ottiene l'oggetto origine dati OLE DB sottostante per il provider SHAPE.|  
|[Errore](../../../ado/reference/ado-api/error-object.md)|Contiene informazioni sugli errori di accesso ai dati relativi a una singola operazione che include il provider.<br /><br /> Il **errore** oggetto non è sicuro per lo scripting.|  
|[Campo](../../../ado/reference/ado-api/field-object.md)|Rappresenta una colonna di dati con un tipo di dati.|  
|[Parametro](../../../ado/reference/ado-api/parameter-object.md)|Rappresenta un parametro o un argomento associato a un **comando** oggetto basato su una query con parametri o stored procedure.<br /><br /> Il **parametro** oggetto non è sicuro per lo scripting.|  
|[Proprietà](../../../ado/reference/ado-api/property-object-ado.md)|Rappresenta una caratteristica dinamica di un oggetto ADO definito dal provider.|  
|[Record](../../../ado/reference/ado-api/record-object-ado.md)|Rappresenta una riga di un **Recordset**, o una directory o file in un file system. Il **Record** oggetto è sicuro per lo script.|  
|[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)|Rappresenta il set di record da una tabella di base o i risultati di un comando eseguito. In qualsiasi momento, il **Recordset** oggetto fa riferimento a un solo record all'interno del set di record corrente.<br /><br /> Il **Recordset** oggetto è sicuro per lo script.|  
|[Flusso](../../../ado/reference/ado-api/stream-object-ado.md)|Rappresenta un flusso di dati binario.<br /><br /> Il **flusso** oggetto è sicuro per lo script.|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ADO](../../../ado/reference/ado-api/ado-api-reference.md)   
 [Raccolte di ADO](../../../ado/reference/ado-api/ado-collections.md)   
 [Proprietà dinamiche ADO](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [Costanti enumerate ADO](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [Appendice b: errori ADO](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [Eventi ADO](../../../ado/reference/ado-api/ado-events.md)   
 [Metodi ADO](../../../ado/reference/ado-api/ado-methods.md)   
 [Modello a oggetti ADO](../../../ado/reference/ado-api/ado-object-model.md)   
 [Proprietà ADO](../../../ado/reference/ado-api/ado-properties.md)

