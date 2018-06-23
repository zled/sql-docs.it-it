---
title: Elemento DbStorageLocation | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- DbStorageLocation element
ms.assetid: 1f448249-103a-479f-ae86-b0017acd0436
caps.latest.revision: 15
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 651dc0424c492efefa7828ae327f9bdcf837ed77
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36067662"
---
# <a name="dbstoragelocation-element"></a>Elemento DbStorageLocation
  Specifica la cartella in cui vengono creati e gestiti tutti i file di dati e di metadati dei database di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Database>  
...  
   <ddl100_100:DbStorageLocation>...</ddl100_100:DbStorageLocation>  
...  
</Database>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|""|  
|Cardinalità|0-1: elemento facoltativo che può verificarsi solo una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Database](database-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Il `DbStorageLocation` database deve essere impostata su un percorso di cartella UNC esistente o una stringa vuota. Una stringa vuota è il valore predefinito per la cartella di dati del server. Se la cartella non esiste, quando si esegue un comando `Create`, `Attach` o `Alter` verrà generato un errore.  
  
 Inoltre, il `DbStorageLocation` database non può essere impostata in modo che punti alla cartella di dati del server o una delle relative sottocartelle. Se il percorso punta alla cartella di dati del server o a una delle relative sottocartelle, quando si esegue un comando `Create`, `Attach` o `Alter` verrà generato un errore.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.AnalysisServices.Database.DbStorageLocation%2A>   
 [Collegamento e scollegamento di database di Analysis Services](../../multidimensional-models/attach-and-detach-analysis-services-databases.md)  
  
  