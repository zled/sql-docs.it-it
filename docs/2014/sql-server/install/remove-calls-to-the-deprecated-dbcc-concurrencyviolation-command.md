---
title: Rimuovere le chiamate al comando DBCC CONCURRENCYVIOLATION deprecato | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 2cc9f6ff-de36-4e94-bd04-59f5c45c4911
caps.latest.revision: 7
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2486546efae7daa63441e12fa350ef878c7daa77
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37261897"
---
# <a name="remove-calls-to-the-deprecated-dbcc-concurrencyviolation-command"></a>Rimuovere le chiamate al comando DBCC CONCURRENCYVIOLATION deprecato
  È stato rilevato il comando DBCC CONCURRENCYVIOLATION. Questo comando non è più disponibile. L'esecuzione di questo comando restituisce l'errore 2526.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Nessuna versione recente dell'edizione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] include un'utilità di Governor del carico di lavoro; pertanto il comando è stato rimosso.  
  
## <a name="corrective-action"></a>Azione correttiva  
 Aggiornare le applicazioni e gli script per rimuovere i riferimenti a questo comando deprecato.  
  
## <a name="external-resources"></a>Risorse esterne  
  
