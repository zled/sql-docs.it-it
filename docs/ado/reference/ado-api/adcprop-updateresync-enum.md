---
title: ADCPROP_UPDATERESYNC_ENUM | Documenti Microsoft
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
f1_keywords: ADCPROP_UPDATERESYNC_ENUM
helpviewer_keywords: ADCPROP_UPDATERESYNC_ENUM [ADO]
ms.assetid: bc9e1a37-e969-47e9-8382-0bbfffa2034f
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d030fa1643cbf836a7380dd3113236ec7961b8d0
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="adcpropupdateresyncenum"></a>ADCPROP_UPDATERESYNC_ENUM
Specifica se il [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) metodo è seguito da implicita [Resync](../../../ado/reference/ado-api/resync-method.md) operazione del metodo e in tal caso, l'ambito dell'operazione.  
  
|Costante|valore|Description|  
|--------------|-----------|-----------------|  
|**adResyncAll**|15|Richiama **Resync** con il valore combinato di tutti gli altri membri ADCPROP_UPDATERESYNC_ENUM.|  
|**adResyncAutoIncrement**|1|Valore predefinito. Tenta di recuperare il nuovo valore identity per le colonne automaticamente incrementato o generati dall'origine dati, ad esempio i campi di Microsoft Jet contatore o le colonne di identità di Microsoft SQL Server.|  
|**adResyncConflicts**|2|Richiama **Resync** per tutte le righe in cui l'operazione di aggiornamento o eliminazione non riuscita a causa di un conflitto di concorrenza.|  
|**adResyncInserts**|8|Richiama **Resync** per tutte le righe inserite correttamente. Tuttavia, i valori di colonna AutoIncrement non vengano sincronizzati. Al contrario, il contenuto di nuove righe inserite viene risincronizzato in base al valore di chiave primaria esistente. Se la chiave primaria è un valore di incremento automatico, **Resync** non recuperare il contenuto della riga desiderata. Per valori di chiave primaria a incremento automatico a incremento automatico, chiamare **UpdateBatch** con il valore combinato **adResyncAutoIncrement** + **adResyncInserts**.|  
|**adResyncNone**|0|Non richiamare **Resync**.|  
|**adResyncUpdates**|4|Richiama **Resync** per tutte le righe aggiornate correttamente.|  
  
## <a name="applies-to"></a>Si applica a  
 [Proprietà dinamica Update Resync (ADO)](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md)
