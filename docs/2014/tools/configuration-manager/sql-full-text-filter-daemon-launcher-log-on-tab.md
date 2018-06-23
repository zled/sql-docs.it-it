---
title: Utilità di avvio del daemon filtri full-text di SQL (scheda Accesso) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- configmgr-client
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 13e260f9-a75f-430b-88a3-959ddcead8fe
caps.latest.revision: 8
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 0e1c4aa4389f72fb81a98e7091ccc5a5d52db1d8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36170922"
---
# <a name="sql-full-text-filter-daemon-launcher-log-on-tab"></a>Utilità di avvio del daemon filtri full-text di SQL (scheda Accesso)
  A partire da [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], il servizio Utilità di avvio del daemon filtri full-text di SQL (FDHOST Launcher) viene utilizzato dalla ricerca full-text in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Se si utilizza la ricerca full-text, questo servizio deve essere in esecuzione. Per informazioni sui processi host del daemon di filtri, vedere "Architettura della ricerca full-text" nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Utilizzare la scheda **Accesso** della finestra di dialogo **Proprietà - Utilità di avvio del daemon filtri full-text di SQL** per specificare l'account utilizzato dal servizio full-text di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per modificare la password di un account e per avviare e arrestare il servizio. La modifica della password di un account diventa effettiva dopo il riavvio del servizio.  
  
> [!NOTE]  
>  Quando si modifica il nome account utilizzato da un servizio in un'istanza cluster, il nuovo account deve essere membro del gruppo di dominio specificato durante l’installazione per il servizio oppure è necessario disporre dell’autorizzazione per aggiungere membri a tale gruppo. Se non si dispone dell’autorizzazione per modificare l'appartenenza al gruppo, contattare l’amministratore di dominio.  
>   
>  Per ulteriori informazioni sulla selezione di un account per l'esecuzione del servizio, vedere "Impostazione di account di servizio Windows" nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="options"></a>Opzioni  
 **Account predefinito**  
 **Sistema locale**  
 Specifica l'account di sistema locale. Per questo account non è necessaria una password. Tuttavia, a seconda dei privilegi concessi, l'account di sistema locale può impedire le interazioni tra il servizio e gli altri server.  
  
 **Servizio locale**  
 Specifica l'account di servizio locale. Per questo account non è necessaria una password. Tuttavia, a seconda dei privilegi concessi, l'account di servizio locale può impedire le interazioni tra il servizio e gli altri server.  
  
 **Servizio di rete**  
 È consigliabile non utilizzare l'account Servizio di rete per i servizi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o i servizi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Per questi servizi sono più adatti gli account utente locale o di dominio.  
  
 **Account seguente**  
 Specificare un account utente locale o di dominio che utilizza l’autenticazione di Windows. È consigliabile utilizzare un account utente di dominio con diritti minimi per i servizi.  
  
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
 Consente di sospendere il servizio. Non disponibile per questo servizio.  
  
 **Riprendi**  
 Consente di riprendere un servizio sospeso.  
  
  