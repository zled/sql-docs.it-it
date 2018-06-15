---
title: ISSCommandWithParameters (OLE DB) | Documenti Microsoft
description: ISSCommandWithParameters (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISSCommandWithParameters (OLE DB)
apitype: COM
helpviewer_keywords:
- ISSCommandWithParameters interface
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 5a33a2af2a89a151ae0aeed96a31956037aa036e
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35305360"
---
# <a name="isscommandwithparameters-ole-db"></a>ISSCommandWithParameters (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **ISSCommandWithParameters** interfaccia espone il supporto per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] XML e tipi definiti dall'utente (UDT). È un'interfaccia facoltativa eredita dall'interfaccia OLE DB principale **ICommandWithParameters**. Oltre ai tre metodi ereditati da **ICommandWithParameters**; **GetParameterInfo**, **MapParameterNames**, e **SetParameterInfo**; **ISSCommandWithParameters** fornisce due nuovi metodi che consentono di gestire i tipi di dati specifici del server.  
  
> [!NOTE]  
>  Il **ISSCommandWithParameters** interfaccia può essere utilizzata quando vengono utilizzati i componenti del servizio, ma i componenti del servizio non utilizzano questa interfaccia.  
  
|Metodo|Description|  
|------------|-----------------|  
|[Isscommandwithparameters:: Getparameterproperties &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/isscommandwithparameters-getparameterproperties-ole-db.md)|Restituisce uno **SSPARAMPROPS** struttura del set di proprietà nella matrice per ogni parametro di tipo definito dall'utente o XML passato al comando, ma viene restituito none per altri tipi di parametri.|  
|[Isscommandwithparameters:: Setparameterproperties &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md)|Imposta le proprietà dei parametri in base al parametro al numero ordinale oppure imposta le proprietà dei parametri bulk specificando una matrice di **SSPARAMPROPS** strutture.|  
  
## <a name="see-also"></a>Vedere anche  
 [Le interfacce &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md)    
 [Utilizzo di tipi di dati XML](../../oledb/features/using-xml-data-types.md)   
 [Uso dei tipi definiti dall'utente](../../oledb/features/using-user-defined-types.md)  
  
  
