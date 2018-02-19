---
title: Creare un amministratore di dominio punti di accesso (AP)
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ed52bf78-2b0a-4252-98a7-8c2805e22d3d
caps.latest.revision: 
ms.openlocfilehash: 0ebc616d28fe734b9dac52303641390ce9bc0957
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="create-an-aps-domain-administrator"></a>Creare un amministratore di dominio punti di accesso
Alcune operazioni richiedono privilegi di amministratore di sistema della piattaforma Analitica dominio. Viene descritto come creare gli amministratori di dominio aggiuntivo dello strumento.  
  
## <a name="create-a-domain-administrator"></a>Creare un amministratore di dominio  
Disporre delle autorizzazioni sufficienti per configurare tutti i nodi di punti di accesso, l'utente che esegue il **APS Configuration Manager** (`dwconfig.exe`) deve essere un membro del **Domain Admins** gruppo. Per avviare e arrestare i servizi di punti di accesso, l'utente deve essere un membro del **PdwControlNodeAccess** gruppo.  
  
#### <a name="to-add-a-user-to-the-domain-admins-group"></a>Per aggiungere un utente al gruppo Domain Admins  
  
1.  Accedere al nodo attivo AD **(*appliance_domain*-AD01** o ***appliance_domain*-AD02**) utilizzando un account amministratore di dominio esistente dello strumento.  
  
2.  Nel menu Start fare clic su **Esegui**. Nel **aprire** digitare **dsa.msc**. Scegliere **OK**.  
  
3.  Nel **Active Directory Users and Computers** di programma, fare doppio clic su **utenti**, scegliere **New**e quindi fare clic su **utente**.  
  
4.  Nel **nuovo oggetto-utente** completare la descrizione del nuovo utente nella finestra di dialogo e quindi fare clic su **Avanti**.  
  
    Completare la finestra di dialogo password e quindi fare clic su **Avanti**.  
  
    > [!WARNING]  
    > SQL Server PDW non supporta il carattere di segno di dollaro ($) in cui l'amministratore di dominio o una password di amministratore locale. Una password contenente un segno di dollaro sarà valida e possa essere usato ma può bloccare le attività di aggiornamento e manutenzione  
  
    Confermare la nuova descrizione utente e quindi fare clic su **fine**.  
  
5.  Nell'elenco di utenti, fare doppio clic sul nuovo utente per aprire la finestra di dialogo delle proprietà dell'utente.  
  
6.  Nel **membro di** scheda, fare clic su **Aggiungi**.  
  
    Tipo **Domain Admins; PdwControlNodeAccess** e quindi fare clic su **Controlla nomi**. Scegliere **OK**.  
  
    Aggiunge il nuovo utente per il **Domain Admins** gruppo e **PdwControlNodeAccess** gruppo. Scegliere **OK**.  
  
## <a name="see-also"></a>Vedere anche  
[Avviare Gestione configurazione &#40; Sistema della piattaforma Analitica &#41;](launch-the-configuration-manager.md)  
  
