---
title: Comando esclusivo SET | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SET EXCLUSIVE command [ODBC]
ms.assetid: d4fe12c5-7e8b-4d20-9ea4-2bcaffb271f2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d0b3fbe2c4902ef58f5060e695a428d2be8879de
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
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
