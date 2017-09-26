---
title: Catalog.execution_property_override_values | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 83cbdd6f-ddde-47bf-abde-36bd24272621
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ed9ae4ea7a7165efe53a551832d8e4a0eb7a2114
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="catalogexecutionpropertyoverridevalues"></a>catalog.execution_property_override_values
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Visualizza i valori dell'override di proprietà che sono impostati durante l'esecuzione del pacchetto.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|property_id|**bigint**|ID univoco del valore di override di proprietà.|  
|execution_id|**bigint**|ID univoco per l'istanza di esecuzione.|  
|property_path|**nvarchar(4000)**|Percorso alla proprietà nel pacchetto.|  
|property_value|**nvarchar(max)**|Valore di override della proprietà.|  
|sensitive|**bit**|Quando il valore è 1, la proprietà è importante e viene crittografata quando viene archiviata. Quando il valore è 0, la proprietà non è importante e il valore viene archiviato non crittografato.|  
  
## <a name="remarks"></a>Osservazioni  
 Questa vista viene visualizzata una riga per ogni esecuzione proprietà valori sono stati sottoposto a override utilizzando il **esegue l'override di proprietà** sezione il **avanzate** scheda della finestra di **Esegui pacchetto** finestra di dialogo. Il percorso della proprietà è derivato dal **percorso pacchetto** proprietà dell'attività del pacchetto.  
  
## <a name="permissions"></a>Permissions  
 Per questa vista è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazione READ per l'istanza di esecuzione  
  
-   L'appartenenza al **ssis_admin** ruolo del database  
  
-   L'appartenenza al **sysadmin** ruolo del server  
  
> [!NOTE]  
>  Quando si dispone delle autorizzazioni per eseguire un'operazione nel server, si dispone anche delle autorizzazioni per visualizzare le informazioni sull'operazione. È applicata la sicurezza a livello di riga, pertanto vengono visualizzate solo le righe per le quali si dispone delle autorizzazioni per la visualizzazione.  
  
  
