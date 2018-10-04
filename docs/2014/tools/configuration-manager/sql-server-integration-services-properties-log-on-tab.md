---
title: Proprietà - SQL Server Integration Services (scheda Accesso) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- configmgr-client
ms.topic: conceptual
ms.assetid: c0eb1b87-6bb0-475e-8492-0fd3c3f910ea
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 22c365dfd5a6c6fd38e256821a6dd80ff99345fd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48195161"
---
# <a name="sql-server-integration-services-properties-log-on-tab"></a>Proprietà - SQL Server Integration Services (scheda Accesso)
  Usare la scheda **Accesso** della finestra di dialogo [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] **Proprietà** per specificare l'account usato dal servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] e avviare e arrestare il servizio.  
  
## <a name="options"></a>Opzioni  
 **Account di sistema locale**  
 Specificare un account di sistema locale che non richiede una password. Tuttavia, a seconda dei privilegi concessi, l'account di sistema locale può impedire le interazioni tra il servizio e gli altri server.  
  
 **Account seguente**  
 Specificare un account utente locale o di dominio che utilizza l'autenticazione di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. [!INCLUDE[msCoName](../../includes/msconame-md.md)] consiglia di utilizzare un account utente di dominio con diritti minimi. Per ulteriori informazioni sulla selezione di un account, cercare l'argomento "Impostazione di account di Windows per i servizi" nella documentazione online.  
  
 **Nome account**  
 Specificare il nome dell'account utente locale o di dominio.  
  
 **Password**  
 Digitare la password dell'account.  
  
 **Conferma password**  
 Digitare nuovamente la password dell'account.  
  
 **Start**  
 Avviare il servizio.  
  
 **Arresta**  
 Consente di arrestare il servizio.  
  
 **Sospendi**  
 Consente di sospendere il servizio.  
  
 **Riprendi**  
 Consente di riprendere un servizio sospeso.  
  
  
