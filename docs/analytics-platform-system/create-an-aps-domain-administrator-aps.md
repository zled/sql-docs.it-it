---
title: Creare un amministratore di dominio - Analitica Platform System | Documenti Microsoft
description: Alcune operazioni richiedono privilegi di amministratore di sistema della piattaforma Analitica dominio. Viene descritto come creare gli amministratori di dominio aggiuntivo dello strumento.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 73eff52cb6e583383f13334e78012721a20a3e25
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
ms.locfileid: "31545117"
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
[Avviare Gestione configurazione &#40;Analitica Platform System&#41;](launch-the-configuration-manager.md)  
  
