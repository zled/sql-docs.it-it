---
title: Gestione delle cache (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- XMLA, cache
- XML for Analysis, cache
- clearing cache
- cache [Analysis Services]
ms.assetid: afad5c39-d4c3-4307-b3b9-a06617da0028
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 69fc72149887598efe1c84c35c88fa24c7cdadbc
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="managing-caches-xmla"></a>Gestione delle cache (XMLA)
  È possibile utilizzare il [ClearCache](../../analysis-services/xmla/xml-elements-commands/clearcache-element-xmla.md) comando XML for Analysis (XMLA) per cancellare la cache di una dimensione specificata o una partizione. Cancellare la cache di forza [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ricompilazione della cache per l'oggetto.  
  
## <a name="specifying-objects"></a>Specifica di oggetti  
 Il [oggetto](../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md) proprietà del **ClearCache** comando può contenere un riferimento all'oggetto solo per uno dei seguenti oggetti. Se un riferimento è relativo a un oggetto diverso da uno di quelli seguenti, si verifica un errore:  
  
 Database  
 Cancella la cache per tutte le dimensioni e le partizioni contenute nel database.  
  
 Dimensione  
 Cancella la cache per la dimensione specificata.  
  
 Cube  
 Cancella la cache per tutte le partizioni contenute nei gruppi di misure per il cubo.  
  
 Gruppo di misure  
 Cancella la cache per tutte le partizioni contenute nel gruppo di misure.  
  
 Partition  
 Cancella la cache per la partizione specificata.  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo con XMLA in Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
