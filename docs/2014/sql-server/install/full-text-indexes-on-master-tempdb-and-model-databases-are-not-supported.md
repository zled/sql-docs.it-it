---
title: Non sono supportati gli indici full-text nei database master, tempdb e model | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes
ms.assetid: f7992965-42c1-4eb8-a7fb-afb38b67c740
caps.latest.revision: 21
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8c0982614e41097ea51830212e0548efcc42c6ba
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37200751"
---
# <a name="full-text-indexes-on-master-tempdb-and-model-databases-are-not-supported"></a>Gli indici full-text nei database master, tempdb e model non sono supportati
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non consente indici full-text in un database di sistema.  
  
## <a name="description"></a>Description  
 In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] gli indici full-text sono supportati nei database master, tempdb e model.  
  
 Cataloghi full-text nel master, tempdb e modello di database vengono rimossi durante l'aggiornamento.  
  
## <a name="see-also"></a>Vedere anche  
 [Uso di Preparazione aggiornamento](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
