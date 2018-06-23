---
title: Gli indici full-text nei database master, tempdb e model non sono supportati | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- full-text indexes
ms.assetid: f7992965-42c1-4eb8-a7fb-afb38b67c740
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1d334a3626c11050418df3fae483f5b9029adeb4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36056080"
---
# <a name="full-text-indexes-on-master-tempdb-and-model-databases-are-not-supported"></a>Gli indici full-text nei database master, tempdb e model non sono supportati
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non consente indici full-text in un database di sistema.  
  
## <a name="description"></a>Description  
 In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] gli indici full-text sono supportati nei database master, tempdb e model.  
  
 Cataloghi full-text in master, tempdb e modello di database vengono rimosse durante l'aggiornamento.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di preparazione aggiornamento](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  