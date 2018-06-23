---
title: Valore massimo per le dimensioni del pacchetto di rete impostato su 8060 byte | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 86db5da1-afe4-4fbb-8bf8-33cedc7e4361
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4a0502a64ab55ae825d8b8d7f017472f34851e17
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069815"
---
# <a name="network-packet-size-should-not-exceed-8060-bytes"></a>Valore massimo per le dimensioni del pacchetto di rete impostato su 8060 byte
  Se il valore specificato per sp_configure ''network packet size' o se le dimensioni del pacchetto di rete di qualsiasi utente connesso sono maggiori di 8060 byte, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] esegue operazioni di allocazione della memoria diverse. In questo caso, può verificarsi un aumento dello spazio degli indirizzi virtuali dei processi non riservato per il pool di buffer.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 Le dimensioni del pacchetto di rete non devono superare 8060 byte.  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 [Articolo 903002 della Microsoft Knowledge Base](http://go.microsoft.com/fwlink/?linkid=117749)  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare e applicare le procedure consigliate tramite la gestione basata su criteri](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  