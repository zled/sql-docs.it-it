---
title: "Utilit&#224; di avvio del daemon filtri full-text di SQL (scheda Accesso) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 13e260f9-a75f-430b-88a3-959ddcead8fe
caps.latest.revision: 9
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 9
---
# Utilit&#224; di avvio del daemon filtri full-text di SQL (scheda Accesso)
  A partire da [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], il servizio Utilità di avvio del daemon filtri full-text di SQL (FDHOST Launcher) viene utilizzato dalla ricerca full-text in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se si utilizza la ricerca full-text, questo servizio deve essere in esecuzione. Per informazioni sui processi host del daemon di filtri, vedere "Architettura della ricerca full-text" nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Utilizzare il **accesso** scheda il **proprietà utilità di avvio del Daemon filtri Full-text SQL** la finestra di dialogo per specificare l'account utilizzato dal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] servizio full-text, per modificare la password di un account e per avviare e arrestare il servizio. La modifica della password di un account diventa effettiva dopo il riavvio del servizio.  
  
> [!NOTE]  
>  Quando si modifica il nome account utilizzato da un servizio in un'istanza cluster, il nuovo account deve essere membro del gruppo di dominio specificato durante l’installazione per il servizio oppure è necessario disporre dell’autorizzazione per aggiungere membri a tale gruppo. Se non si dispone dell’autorizzazione per modificare l'appartenenza al gruppo, contattare l’amministratore di dominio.  
>   
>  Per ulteriori informazioni sulla selezione di un account per l'esecuzione del servizio, vedere "Impostazione di account di servizio Windows" nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## Opzioni  
 **Account predefinito**  
 **Sistema locale**  
 Specifica l'account di sistema locale. Per questo account non è necessaria una password. Tuttavia, a seconda dei privilegi concessi, l'account di sistema locale può impedire le interazioni tra il servizio e gli altri server.  
  
 **Servizio locale**  
 Specifica l'account di servizio locale. Per questo account non è necessaria una password. Tuttavia, a seconda dei privilegi concessi, l'account di servizio locale può impedire le interazioni tra il servizio e gli altri server.  
  
 **Servizio di rete**  
 Si consiglia di non utilizzare l'account del servizio di rete per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] servizi o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] servizi dell'agente. Per questi servizi sono più adatti gli account utente locale o di dominio.  
  
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
  
  