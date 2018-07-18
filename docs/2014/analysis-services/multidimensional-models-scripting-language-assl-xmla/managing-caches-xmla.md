---
title: Gestione delle cache (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- XMLA, cache
- XML for Analysis, cache
- clearing cache
- cache [Analysis Services]
ms.assetid: afad5c39-d4c3-4307-b3b9-a06617da0028
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: da13c86e86a2f51719a9d4f0aedfda33935766ae
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37180811"
---
# <a name="managing-caches-xmla"></a>Gestione delle cache (XMLA)
  È possibile usare la [ClearCache](../xmla/xml-elements-commands/clearcache-element-xmla.md) comando XML for Analysis (XMLA) per cancellare la cache di una dimensione specificata o una partizione. Cancellare le forze della cache [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ricompilazione della cache per l'oggetto.  
  
## <a name="specifying-objects"></a>Specifica di oggetti  
 Il [oggetti](../xmla/xml-elements-properties/object-element-xmla.md) proprietà del `ClearCache` comando può contenere un riferimento all'oggetto solo per uno degli oggetti seguenti. Se un riferimento è relativo a un oggetto diverso da uno di quelli seguenti, si verifica un errore:  
  
 Database  
 Cancella la cache per tutte le dimensioni e le partizioni contenute nel database.  
  
 Dimension  
 Cancella la cache per la dimensione specificata.  
  
 Cube  
 Cancella la cache per tutte le partizioni contenute nei gruppi di misure per il cubo.  
  
 Gruppo di misure  
 Cancella la cache per tutte le partizioni contenute nel gruppo di misure.  
  
 Partition  
 Cancella la cache per la partizione specificata.  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo con XMLA in Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
