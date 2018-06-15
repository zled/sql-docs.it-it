---
title: Importare Management Pack di SCOM - Analitica Platform System | Documenti Microsoft
description: Seguire questi passaggi per importare i Management Pack di System Center Operations Manager (SCOM) per Analitica Platform System (AP). I management pack sono necessari per monitorare Parallel Data Warehouse di SCOM.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: e60d87ae58b0804a0a7296f8b489df7441683c5b
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
ms.locfileid: "31538591"
---
# <a name="import-the-scom-management-pack---analytics-platform-system"></a>Importare il Management Pack SCOM - Analitica Platform System
Seguire questi passaggi per importare i Management Pack di System Center Operations Manager (SCOM) per Analitica Platform System (AP). I management pack sono necessari per monitorare Parallel Data Warehouse di SCOM. 
  
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
  
    ![Fare clic su Installa](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW3.png "SCOM_PDW3")  
  
5.  Scegliere **Chiudi**.  
  
    ![Fare clic su Chiudi](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW4.png "SCOM_PDW4")  
  
## <a name="next-step"></a>Passaggio successivo  
Ora che sono stati importati i Management Pack, andare al passaggio successivo: [configurare SCOM al sistema di monitoraggio Analitica piattaforma &#40;Analitica Platform System&#41;](configure-scom-to-monitor-analytics-platform-system.md).  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
