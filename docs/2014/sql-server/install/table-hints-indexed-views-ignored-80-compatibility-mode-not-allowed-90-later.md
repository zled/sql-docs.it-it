---
title: Hint di tabella nella vista definizioni vengono ignorate in modalità di compatibilità 80 e non sono consentite nella modalità 90 o versioni successive indicizzata | Microsoft Docs
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
- query hints [SQL Server]
- indexed views [SQL Server], query hints
ms.assetid: 405dfcff-a3a6-4e6d-a53a-ed77bbacdd13
caps.latest.revision: 22
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 93159a8c32f484fd9c734b4847dfd1e7fca854a8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37317431"
---
# <a name="table-hints-in-indexed-view-definitions-are-ignored-in-80-compatibility-mode-and-are-not-allowed-in-90-mode-or-later"></a>Gli hint di tabella contenuti nelle definizioni delle viste indicizzate vengono ignorati in modalità di compatibilità 80 e non sono consentiti in modalità di compatibilità 90 o successiva
  In modalità di compatibilità 90 o successiva, gli hint di tabella non sono consentiti nelle definizioni delle viste indicizzate. Per ulteriori informazioni, vedere gli argomenti seguenti nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: "Progettazione di viste indicizzate", "Creazione di viste indicizzate" e "Hint per la query ([!INCLUDE[tsql](../../includes/tsql-md.md)])".  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Azione correttiva  
 Gli hint di tabella devono essere rimossi dalle definizioni delle viste indicizzate. Indipendentemente dalla modalità di compatibilità utilizzata, si consiglia di testare l'applicazione per verificare la corretta esecuzione delle operazioni di creazione, aggiornamento e accesso alle viste indicizzate, inclusa l'associazione di query a viste indicizzate.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Preparazione aggiornamento a SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
