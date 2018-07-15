---
title: Directory virtuale (Upgrade Advisor) metodo di autenticazione non supportato | Microsoft Docs
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
- virtual directories [Reporting Services]
ms.assetid: 216eca6f-9a66-42e1-aa54-dcf99cec9f7d
caps.latest.revision: 13
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: b707af2c203875553d614244c5bf6bbc87aaa4bd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37297751"
---
# <a name="virtual-directory-has-unsupported-authentication-method-upgrade-advisor"></a>Metodo di autenticazione non supportato nella directory virtuale (Upgrade Advisor)
  È stato rilevato un metodo di autenticazione non supportato nella directory virtuale del server di report o di Gestione report. I metodi di autenticazione non supportati dall'aggiornamento sono anonimo, digest e .NET Passport.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 Non è possibile aggiornare un'installazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] che utilizza uno dei metodi di autenticazione seguenti.  
  
-   Anonima  
  
-   Digest  
  
-   .NET Passport  
  
 Per continuare, è possibile modificare il metodo di autenticazione specificato per le directory virtuali di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in Internet Information Services (IIS) o eseguire la migrazione dell'installazione. Per ulteriori informazioni sulla migrazione dell'installazione, vedere la documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="corrective-action"></a>Azione correttiva  
 Per continuare con aggiornamento, modificare il metodo di autenticazione in IIS per le directory virtuali ReportServer e Report. Per ulteriori informazioni sulla modifica dei metodi di autenticazione in IIS, vedere la documentazione di IIS. Dopo avere modificato il metodo di autenticazione per le directory virtuali di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], eseguire nuovamente Preparazione aggiornamento per confermare che sono presenti altri problemi di aggiornamento.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento di Reporting Services &#40;Preparazione aggiornamento&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
