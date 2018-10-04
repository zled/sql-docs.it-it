---
title: Installazione di preparazione aggiornamento | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- Setup [Upgrade Advisor]
- Upgrade Advisor [SQL Server], installing
ms.assetid: 1b7d6eca-1df1-47df-bbba-0fc485706a95
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 95bcdfca34b618043515c27030bc74104e4da590
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48078071"
---
# <a name="installing-upgrade-advisor"></a>Installazione di Preparazione aggiornamento
  Il computer in cui installare Preparazione aggiornamento a SQL Server 2014 dipende dai componenti che verranno analizzati. Preparazione aggiornamento supporta l'analisi remota di tutti i componenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ad eccezione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Se non si analizza istanze di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], è possibile installare Preparazione aggiornamento in qualsiasi computer che possono connettersi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], e che soddisfa le [prerequisiti di preparazione aggiornamento](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md). Se si prevede di analizzare le istanze di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], è necessario installare Preparazione aggiornamento nel server di report.  
  
 Eseguire la **sqlua. msi** file per installare Preparazione aggiornamento. È possibile eseguire l'installazione dal prompt dei comandi per installazioni automatiche e automatizzate. Visualizzare [installazione di preparazione aggiornamento dal Prompt dei comandi](../../../2014/sql-server/install/installing-upgrade-advisor-from-the-command-prompt.md) per la sintassi ed esempi.  
  
 Ottenere SQLUA.msi:  
  
-   Nel **redist** cartella della [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporti del prodotto.  
  
-   Durante la [download di SQL 2014 Feature Pack](http://www.microsoft.com/download/details.aspx?id=42295).  
  
## <a name="uninstalling-upgrade-advisor"></a>Disinstallazione di Preparazione aggiornamento  
 È possibile disinstallare Preparazione aggiornamento utilizzando **Aggiungi / Rimuovi programmi**. La sintassi del prompt dei comandi supporta anche la rimozione e/o la disinstallazione.  
  
  
