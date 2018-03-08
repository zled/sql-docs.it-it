---
title: Generare uno schema XDR inline | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: xml
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XDR schemas [SQL Server]
- inline XDR schema generation [SQL Server]
- XMLDATA option
- FOR XML clause, inline XDR schema generation
ms.assetid: 2a40d617-9724-4f7d-80a4-a85c702f14d0
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a907df120142a65c7552da2b66d3b16485e014fa
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/12/2018
---
# <a name="generate-an-inline-xdr-schema"></a>Generazione di uno schema XDR inline
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
La direttiva **XMLDATA** in FOR XML restituisce uno schema XDR inline insieme al risultato della query. Lo schema XDR tuttavia non supporta tutti i nuovi tipi di dati e i miglioramenti introdotti in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive. In alternativa, è possibile richiedere uno schema XSD inline usando [la direttiva XMLSCHEMA](../../relational-databases/xml/generate-an-inline-xsd-schema.md).  
  
> [!IMPORTANT]  
>  La direttiva XMLDATA all'opzione FOR XML è deprecata. Utilizzare la generazione XSD in caso di modalità RAW e AUTO. Non sono disponibili sostituzioni per direttiva XMLDATA in modalità EXPLICIT. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 Per il supporto dello schema XDR inline, notare inoltre quanto segue:  
  
-   Se il risultato della query FOR XML include colonne di tipo **xml** e viene richiesto uno schema XDR inline, sarà generato un errore. Gli schemi XDR inline non supportano infatti questi tipi.  
  
-   Verrà eseguito il mapping dei tipi **(n)varchar(max)** e **(n)varbinary(max)** rispettivamente a **(n)varchar(n)** e **varbinary(n)**.  
  
-   Se la modalità di compatibilità è impostata su 90 o superiore, i valori **timestamp** vengono considerati come dati **varbinary(8)** , trattati come dati binari e restituiti nel risultato nel modo seguente:  
  
    -   Se si specifica **binary base64** , viene usata la codifica Base64.  
  
    -   Se non si specifica **binary base64** , viene usata la codifica URL in modalità AUTO.  
  
  
