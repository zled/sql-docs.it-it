---
title: Comando esclusivo SET | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SET EXCLUSIVE command [ODBC]
ms.assetid: d4fe12c5-7e8b-4d20-9ea4-2bcaffb271f2
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f5aa039c9af4b3dfbabce2647408be7f612c80f3
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="set-exclusive-command"></a>Comando esclusivo SET
Specifica se aprire o meno i file di tabella per l'utilizzo esclusiva o condivisa in rete.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SET EXCLUSIVE ON | OFF  
```  
  
## <a name="arguments"></a>Argomenti  
 ON  
 Limita accesso facilitato di una tabella aperta in una rete per l'utente che è stato aperto. La tabella non è accessibile ad altri utenti nella rete. SET esclusivo ON impedisce inoltre tutti gli altri utenti con accesso in sola lettura.  
  
 OFF  
 (Impostazione predefinita per il driver; i valori predefiniti per Visual FoxPro sono ON per la sessione di dati globali e OFF per una sessione di dati privati). Consente di una tabella aperta in una rete condivisa e modificato da alcun utente sulla rete.  
  
## <a name="remarks"></a>Osservazioni  
 Modificare l'impostazione di SET esclusivo non viene modificato lo stato di tabelle aperte in precedenza. Ad esempio, se una tabella viene aperto con SET esclusivo impostata su ON e SET esclusivo in un secondo momento viene impostato su OFF, la tabella mantiene lo stato di uso esclusivo.  
  
## <a name="see-also"></a>Vedere anche  
 [Finestra di dialogo di configurazione ODBC Visual FoxPro](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)
