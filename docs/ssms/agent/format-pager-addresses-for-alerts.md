---
title: Formattare gli indirizzi di cercapersone per gli avvisi | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pager addresses [SQL Server]
- SQL Server Agent, alerts
- formats [SQL Server], pager addresses
- pager notifications [SQL Server]
- addresses [SQL Server]
- alerts [SQL Server], pager addresses
ms.assetid: a9797d01-1050-442c-9038-ed4bfee1e76a
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d6dd4adbc694dae99c8b16a3dacb60711678d6d7
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="format-pager-addresses-for-alerts"></a>Format Pager Addresses for Alerts
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Questo argomento illustra la procedura di formattazione degli indirizzi dei cercapersone per gli avvisi di [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] o [!INCLUDE[tsql](../../includes/tsql_md.md)].  
  
**Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
    [Security](#Security)  
  
-   **Per formattare gli indirizzi di cercapersone utilizzando:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Prima di iniziare  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
Per impostazione predefinita, i membri del ruolo predefinito del server **sysadmin** possono visualizzare le informazioni su un avviso. Gli altri utenti devono appartenere al ruolo predefinito del database **SQLAgentOperatorRole** nel database **msdb** .  
  
## <a name="SSMSProcedure"></a>Utilizzo di SQL Server Management Studio  
  
#### <a name="to-format-pager-addresses"></a>Per formattare gli indirizzi di cercapersone  
  
1.  In **Esplora oggetti**fare clic sul segno più per espandere il server che contiene l'avviso da inviare a un cercapersone.  
  
2.  Fare clic con il pulsante destro del mouse su **SQL Server Agent** e scegliere **Proprietà**  
  
3.  In **Selezione pagina**selezionare **Sistema avvisi**.  
  
4.  Nelle caselle **Riga A:** e **Riga Cc:** del campo **Formato indirizzo per messaggi di posta elettronica tramite cercapersone** digitare il prefisso o il suffisso dell'indirizzo di cercapersone. L'indirizzo effettivo del cercapersone dell'operatore viene inserito al momento dell'invio di una notifica.  
  
5.  Immettere il prefisso o il suffisso per la riga dell'oggetto nella casella **Oggetto** .  
  
6.  Selezionare **Includi corpo del messaggio nel messaggio di notifica** per includere l'intero messaggio di posta elettronica nel messaggio inviato al cercapersone (invece del solo oggetto).  
  
7.  Al termine, fare clic su **OK**.  
  
