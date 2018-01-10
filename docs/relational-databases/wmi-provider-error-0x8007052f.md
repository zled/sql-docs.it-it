---
title: Errore WMI 0x8007052f | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: relational-databases-misc
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: 0x8007052f (WMI error)
ms.assetid: a33f12bd-15c4-42a8-b343-de44c3e87729
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9dc1a57e937306adca1463b610ad65e0e0ee4240
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="wmi-provider-error-0x8007052f"></a>Errore del provider WMI 0x8007052f
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
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
  
  
