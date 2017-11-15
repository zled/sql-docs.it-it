---
title: Errore WMI 0x8007052f | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: 0x8007052f (WMI error)
ms.assetid: a33f12bd-15c4-42a8-b343-de44c3e87729
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 050f4c13d5c7c5f232cca65dd38dbcfcdb27c5bb
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="wmi-provider-error-0x8007052f"></a>Errore del provider WMI 0x8007052f
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|0x8007052f|  
|Origine evento|Errore del provider WMI|  
|Componente|Gestione configurazione SQL Server|  
|Nome simbolico|ND|  
|Testo del messaggio|Errore durante l'accesso: restrizione sull'account utente. Le possibili cause potrebbero essere: campo della password vuoto non consentito, restrizioni sugli orari di accesso o applicazione di restrizioni di criteri.|  
  
## <a name="explanation"></a>Spiegazione  
 Questo errore può verificarsi se si utilizza Gestione configurazione [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] per passare agli account predefiniti (Servizio di rete, Servizio locale o Sistema locale) quando [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] è in esecuzione in un cluster o un controller di dominio di Windows Server. Non eseguire i servizi con account predefiniti in un cluster o un controller di dominio di Windows Server 2003. Per informazioni sugli account di servizio, vedere l'argomento "Impostazione di account di servizio Windows" nella documentazione online di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
## <a name="user-action"></a>Azione dell'utente  
 Configurare [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] affinché utilizzi un account di dominio.  
  
  
