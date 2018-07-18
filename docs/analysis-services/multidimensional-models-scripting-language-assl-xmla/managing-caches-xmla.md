---
title: Gestione delle cache (XMLA) | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a6644b7caff5da31261b115bfc5608823622260a
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34022768"
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
  
  
