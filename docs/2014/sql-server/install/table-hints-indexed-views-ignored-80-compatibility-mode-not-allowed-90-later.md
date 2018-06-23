---
title: Hint di tabella nella vista definizioni vengono ignorate in modalità di compatibilità 80 e non sono consentite nella modalità 90 o versioni successive indicizzata | Documenti Microsoft
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
- query hints [SQL Server]
- indexed views [SQL Server], query hints
ms.assetid: 405dfcff-a3a6-4e6d-a53a-ed77bbacdd13
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b56e965ecfcfc802457bfa3b5a78118afae5c531
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36070197"
---
# <a name="table-hints-in-indexed-view-definitions-are-ignored-in-80-compatibility-mode-and-are-not-allowed-in-90-mode-or-later"></a>Gli hint di tabella contenuti nelle definizioni delle viste indicizzate vengono ignorati in modalità di compatibilità 80 e non sono consentiti in modalità di compatibilità 90 o successiva
  In modalità di compatibilità 90 o successiva, gli hint di tabella non sono consentiti nelle definizioni delle viste indicizzate. Per ulteriori informazioni, vedere gli argomenti seguenti nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: "Progettazione di viste indicizzate", "Creazione di viste indicizzate" e "Hint per la query ([!INCLUDE[tsql](../../includes/tsql-md.md)])".  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Azione correttiva  
 Gli hint di tabella devono essere rimossi dalle definizioni delle viste indicizzate. Indipendentemente dalla modalità di compatibilità utilizzata, si consiglia di testare l'applicazione per verificare la corretta esecuzione delle operazioni di creazione, aggiornamento e accesso alle viste indicizzate, inclusa l'associazione di query a viste indicizzate.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;nuovo&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
