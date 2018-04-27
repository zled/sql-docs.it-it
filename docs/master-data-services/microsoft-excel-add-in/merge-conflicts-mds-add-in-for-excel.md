---
title: Conflitti di unione (componente aggiuntivo MDS per Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.service: ''
ms.component: microsoft-excel-add-in
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf95978f-a2c5-4325-8606-dbd4e88741b8
caps.latest.revision: 6
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0764aa9c7ff87d7fbbc0ac85fc39132fdcb6029f
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="merge-conflicts-mds-add-in-for-excel"></a>Conflitti di unione (componente aggiuntivo MDS per Excel)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Se nel componente aggiuntivo [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] per Excel i dati sono stati modificati nel server da un altro utente, la pubblicazione non riesce e viene visualizzato un errore di conflitto. Per risolvere questo errore, è possibile usare la funzionalità Conflitti di unione e ripubblicare le modifiche.  
  
## <a name="prerequisites"></a>Prerequisites  
 Per eseguire questa procedura:  
  
-   È necessario disporre dell'autorizzazione per accedere all'area funzionale **Esplora** .  
  
-   È necessario avere almeno l'autorizzazione Aggiornamento per l'oggetto modello foglia dell'entità da aggiornare.  
  
-   Il foglio di lavoro attivo deve contenere dati gestiti da MDS.  
  
-   Il foglio di lavoro attivo deve contenere un errore di conflitto dopo il tentativo di pubblicazione delle modifiche.  
  
### <a name="to-merge-conflicts"></a>Per gestire i conflitti di unione  
  
1.  Nel foglio di lavoro attivo selezionare la riga o la cella con l'errore di conflitto.  
  
2.  Nel gruppo di menu **Pubblica e convalida** selezionare **Conflitti di unione** per aprire la finestra di dialogo **Conflitti di unione** .  
  
3.  Nella finestra di dialogo **Conflitti di unione** è possibile:  
  
    -   Scegliere **Più recente** e fare clic su **Applica** per annullare le modifiche in sospeso e ricaricare la versione più recente dal server.  
  
    -   Scegliere **Originale** e fare clic su **Applica** per applicare la versione originale nel foglio di lavoro.  
  
    -   Scegliere **Personale** e fare clic su **Applica** per mantenere le modifiche locali esistenti.  
  
4.  Dopo aver fatto clic su **Applica**, è possibile apportare altre modifiche ed eseguire di nuovo la pubblicazione. In alternativa, è possibile fare clic su **Annulla** per annullare l'aggiornamento e ricaricare la versione più recente dal server.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica: Importazione di dati da Excel &#40;componente aggiuntivo MDS per Excel&#41;](../../master-data-services/microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  
