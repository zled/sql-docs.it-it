---
title: "Proprietà SQL Server Agent (scheda accesso) | Documenti Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 01fc6329-5d6b-4186-9565-395f375477bb
caps.latest.revision: "18"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6c2dd6c43d22f82a0628d7af0f34d4882819e5ff
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="sql-server-agent-properties-log-on-tab"></a>Proprietà - SQL Server Agent (scheda Accesso)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Utilizzare il **accesso** scheda della finestra il **proprietà SQL Server Agent** la finestra di dialogo per specificare l'account utilizzato dal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dell'agente del servizio e avviare e arrestare il servizio. La modifica della password di un account diventa effettiva immediatamente, senza dover riavviare il servizio.  
  
> [!NOTE]  
>  Quando si modifica il nome account utilizzato da un servizio in un'istanza cluster, il nuovo account deve essere membro del gruppo di dominio specificato durante l’installazione per il servizio in corso di modifica oppure è necessario disporre dell’autorizzazione per aggiungere membri a tale gruppo. Se non si dispone dell’autorizzazione per modificare l'appartenenza al gruppo, contattare l’amministratore di dominio.  
  
## <a name="options"></a>Opzioni  
 **Account di sistema locale**  
 Specificare un account di sistema locale che non richiede una password. Tuttavia, a seconda dei privilegi concessi, l'account di sistema locale può impedire le interazioni tra il servizio e gli altri server.  
  
 **Account seguente**  
 Specificare un account utente locale o di dominio che utilizza l’autenticazione di Windows. [!INCLUDE[msCoName](../../includes/msconame-md.md)]consiglia di utilizzare un account utente di dominio con diritti minimi per i servizi. Per ulteriori informazioni sulla selezione di un account, vedere l'argomento "Impostazione di account di Windows per i servizi" nella documentazione online.  
  
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
  
  
