---
title: ISSCommandWithParameters (OLE DB) | Documenti di Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- ISSCommandWithParameters (OLE DB)
apitype: COM
helpviewer_keywords:
- ISSCommandWithParameters interface
ms.assetid: 3419b7f3-36a3-4863-816e-e641e4e90496
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d611c84c78632aa5210bfb36460f1ebb12841ec5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47603069"
---
# <a name="isscommandwithparameters-ole-db"></a>ISSCommandWithParameters (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **ISSCommandWithParameters** espone il supporto per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML e tipi definiti dall'utente (UDT). Si tratta di un'interfaccia facoltativa che eredita dall'interfaccia OLE DB core **ICommandWithParameters**. Oltre ai tre metodi ereditati da **ICommandWithParameters**; **GetParameterInfo**, **MapParameterNames**, e **la funzione SetParameterInfo**; **ISSCommandWithParameters** fornisce due nuovi metodi che vengono utilizzati per gestire server specifici tipi di dati.  
  
> [!NOTE]  
>  Il **ISSCommandWithParameters** interfaccia può essere utilizzata quando vengono utilizzati i componenti del servizio, ma i componenti dei servizi stessi non utilizzerà questa interfaccia.  
  
|Metodo|Description|  
|------------|-----------------|  
|[ISSCommandWithParameters::GetParameterProperties &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-getparameterproperties-ole-db.md)|Restituisce una struttura del set di proprietà **SSPARAMPROPS** della matrice per ogni parametro XML o tipo definito dall'utente passato al comando. Per gli altri tipi di parametro non ne restituisce nessuna.|  
|[ISSCommandWithParameters::SetParameterProperties &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md)|Imposta le proprietà per i singoli parametri in base al numero ordinale oppure imposta proprietà dei parametri bulk specificando una matrice di strutture **SSPARAMPROPS**.|  
  
## <a name="see-also"></a>Vedere anche  
 [Le interfacce &#40;OLE DB&#41;](http://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)   
 [Uso di tipi di dati XML](../../relational-databases/native-client/features/using-xml-data-types.md)   
 [Uso dei tipi definiti dall'utente](../../relational-databases/native-client/features/using-user-defined-types.md)  
  
  
