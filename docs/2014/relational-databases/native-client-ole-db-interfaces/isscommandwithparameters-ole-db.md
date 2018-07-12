---
title: ISSCommandWithParameters (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ISSCommandWithParameters (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- ISSCommandWithParameters interface
ms.assetid: 3419b7f3-36a3-4863-816e-e641e4e90496
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ceca46260d82cc6f9a179a642821aee55e57d6e3
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37429990"
---
# <a name="isscommandwithparameters-ole-db"></a>ISSCommandWithParameters (OLE DB)
  **ISSCommandWithParameters** espone il supporto per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML e tipi definiti dall'utente (UDT). Si tratta di un'interfaccia facoltativa eredita dall'interfaccia OLE DB principale **ICommandWithParameters**. Oltre ai tre metodi ereditati da **ICommandWithParameters**; **GetParameterInfo**, **MapParameterNames**, e **SetParameterInfo**; **ISSCommandWithParameters** fornisce due nuovi metodi che consentono di gestire i tipi di dati specifici server.  
  
> [!NOTE]  
>  Il **ISSCommandWithParameters** interfaccia può essere utilizzata quando vengono usati i componenti del servizio, ma i componenti del servizio se stessi non utilizzerà questa interfaccia.  
  
|Metodo|Description|  
|------------|-----------------|  
|[Isscommandwithparameters:: Getparameterproperties &#40;OLE DB&#41;](isscommandwithparameters-getparameterproperties-ole-db.md)|Restituisce uno **SSPARAMPROPS** struttura del set di proprietà nella matrice per ogni parametro di tipo definito dall'utente o XML passato al comando, ma restituisce none per gli altri tipi di parametri.|  
|[Isscommandwithparameters:: Setparameterproperties &#40;OLE DB&#41;](isscommandwithparameters-setparameterproperties-ole-db.md)|Imposta le proprietà di parametro per ogni parametro in base al numero ordinale oppure imposta le proprietà dei parametri bulk specificando una matrice di **SSPARAMPROPS** strutture.|  
  
## <a name="see-also"></a>Vedere anche  
 [Le interfacce &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)   
 [Usando tipi di dati XML](../native-client/features/using-xml-data-types.md)   
 [Uso dei tipi definiti dall'utente](../native-client/features/using-user-defined-types.md)  
  
  
