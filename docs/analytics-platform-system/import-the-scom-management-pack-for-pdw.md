---
title: Importare il Management Pack SCOM per PDW (Analitica piattaforma sistema)
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fa735041-8e58-4886-ae3b-36f3c6298b12
caps.latest.revision: 6
ms.openlocfilehash: d8accd7106cce2274e60793e123779e87b8dfd49
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="import-the-scom-management-pack-for-pdw"></a>Importare il Management Pack SCOM per PDW
Seguire questi passaggi per importare i Management Pack di System Center Operations Manager (SCOM) per SQL Server PDW. I Management Pack sono necessari per monitorare SQL Server PDW da SCOM.  
  
## <a name="BeforeBegin"></a>Prima di iniziare  
**Prerequisiti**  
  
System Center Operations Manager 2007 R2 deve essere installato e in esecuzione.  
  
I management pack deve essere installato. Vedere [installare i Management Pack SCOM &#40;Analitica Platform System&#41;](install-the-scom-management-packs.md).  
  
## <a name="Step1"></a>Passaggio 1: Importare Base Management Pack di SQL Server Appliance  
  
1.  Accedere al computer con un account membro del ruolo di amministratori di Operations Manager per il gruppo di gestione di Operations Manager 2007.  
  
2.  Nella console operatore, fare clic su **amministrazione**.  
  
3.  Fare doppio clic su di **Management Pack** nodo e quindi fare clic su **Importa Management Pack**.  
  
    ![Fare clic su Importa Management Pack](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP.png "SCOM")  
  
4.  Nell'elenco dei management pack, selezionare il management pack che si desidera importare, fare clic su **selezionare**, quindi fare clic su **Aggiungi**.  
  
    ![Elenco dei Management pack](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP2.png "SCOM_IMP2")  
  
5.  Cercare **accessorio** e quindi eseguire il drill down in SQL Server dello strumento Base e quindi fare clic su **Aggiungi** le due opzioni.  
  
    ![Base dello strumento di SQL Server](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP3.png "SCOM_IMP3")  
  
6.  Una volta due Management Pack sono stati nel riquadro inferiore selezionato, quindi fare clic su **OK**.  
  
    ![Selezionare entrambi i management pack](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP4.png "SCOM_IMP4")  
  
7.  Fare clic su **Installa**.  
  
    ![Fare clic su Installa](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP5.png "SCOM_IMP5")  
  
8.  Al termine dell'operazione, fare clic su **Chiudi**.  
  
    ![Al termine dell'operazione, fare clic su Chiudi](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP6.png "SCOM_IMP6")  
  
## <a name="Step2"></a>Importare il Monitoring Pack per Microsoft SQL Server 2008 R2 Parallel Data Warehouse Appliance  
  
1.  Fare doppio clic su di **Management Pack** nodo e quindi fare clic su **Importa Management Pack**.  
  
2.  Scegliere **Aggiungi da disco**...  
  
    ![Fare doppio clic su Management Pack](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW.png "SCOM_PDW")  
  
3.  Passare al percorso in cui sono stati estratti i Management Pack di SQL Server PDW e scegliere i tre management pack che sono descritti nella sezione "Selezionato Management Pack per l'importazione". È possibile farlo scegliendo selezionando il primo, MAIUSC, quella più recente. Una volta siano tutti selezionati, fare clic su **aprire**.  
  
    ![Selezionare i management pack](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW2.png "SCOM_PDW2")  
  
4.  Fare clic su **Installa**.  
  
    ![Click Install](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW3.png "SCOM_PDW3")  
  
5.  Scegliere **Chiudi**.  
  
    ![Fare clic su Chiudi](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW4.png "SCOM_PDW4")  
  
## <a name="next-step"></a>Passaggio successivo  
Ora che sono stati importati i Management Pack, andare al passaggio successivo: [configurare SCOM al sistema di monitoraggio Analitica piattaforma &#40;Analitica Platform System&#41;](configure-scom-to-monitor-analytics-platform-system.md).  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
