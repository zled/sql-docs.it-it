---
title: osql non supporta più i comandi | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ED command
- osql utility [SQL Server]
- '!! command'
ms.assetid: 7cc2852f-94e8-4292-9326-c3f1a1acd281
caps.latest.revision: 13
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cea117423d097fc63441c9bd82a33b4cc3c2e910
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37243998"
---
# <a name="osql-no-longer-supports-the-ed-and--commands"></a>osql non supporta più comandi
  Il **osql** utilità non supporta la **ED** e **!!** .  
  
## <a name="corrective-action"></a>Azione correttiva  
 Rimuovere i riferimenti per il **ED** e **!!** dagli script.  
  
 Se si desidera utilizzare il **ED** e **!!** i comandi, usare il **sqlcmd** utilità anziché **osql**.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Preparazione aggiornamento a SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
