---
title: Installazione di preparazione aggiornamento | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installing Upgrade Advisor
- Setup [Upgrade Advisor]
- Upgrade Advisor [SQL Server], installing
ms.assetid: 1b7d6eca-1df1-47df-bbba-0fc485706a95
caps.latest.revision: 34
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6cde30d3dd12f6f072d4cb83f869700c7357484f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156139"
---
# <a name="installing-upgrade-advisor"></a>Installazione di Preparazione aggiornamento
  Il computer in cui installare Preparazione aggiornamento a SQL Server 2014 dipende dai componenti che verranno analizzati. Preparazione aggiornamento supporta l'analisi remota di tutti i componenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ad eccezione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Se non si analizza le istanze di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], è possibile installare Preparazione aggiornamento in qualsiasi computer che possono connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], e che soddisfa la [prerequisiti di preparazione aggiornamento](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md). Se si prevede di analizzare le istanze di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], è necessario installare Preparazione aggiornamento nel server di report.  
  
 Eseguire la **sqlua. msi** file per installare Preparazione aggiornamento. È possibile eseguire l'installazione dal prompt dei comandi per installazioni automatiche e automatizzate. Vedere [installazione di preparazione aggiornamento dal Prompt dei comandi](../../../2014/sql-server/install/installing-upgrade-advisor-from-the-command-prompt.md) per sintassi ed esempi.  
  
 Ottenere SQLUA.msi:  
  
-   Nel **redist** cartella del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporto del prodotto.  
  
-   Come parte di [download di SQL 2014 Feature Pack](http://www.microsoft.com/download/details.aspx?id=42295).  
  
## <a name="uninstalling-upgrade-advisor"></a>Disinstallazione di Preparazione aggiornamento  
 È possibile disinstallare Preparazione aggiornamento utilizzando **Aggiungi / Rimuovi programmi**. La sintassi del prompt dei comandi supporta anche la rimozione e/o la disinstallazione.  
  
  