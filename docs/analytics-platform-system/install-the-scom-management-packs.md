---
title: Installare i Management Pack SCOM (Analitica piattaforma sistema)
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
ms.assetid: ab3985d8-0a71-4b28-9d28-9886ae2a110f
caps.latest.revision: "16"
ms.openlocfilehash: 0fce285f730508ec9bf7f384eed4f6b3c9ed3dda
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="install-the-scom-management-packs"></a>Installare i Management Pack SCOM
Seguire questi passaggi per scaricare e installare i Management Pack di System Center Operations Manager (SCOM) per SQL Server PDW. I Management Pack sono necessari per monitorare SQL Server PDW da SCOM.  
  
## <a name="BeforeBegin"></a>Prima di iniziare  
**Prerequisiti**  
  
System Center Operations Manager deve essere installato e in esecuzione. SQL Server PDW 2012 richiede System Center Operations Manager 2007 R2, System Center Operations Manager 2012 o System Center Operations Manager 2012 service pack 1.  
  
## <a name="Step1"></a>Passaggio 1: Scaricare il Management Pack  
Per il carico di lavoro di PDW APS, scaricare il [System Center Management Pack per il sistema di piattaforma Microsoft Analitica](http://go.microsoft.com/fwlink/?LinkId=396857).  
  
Per la gestione dello strumento, scaricare il [Management Pack di SQL Server dello strumento Base](http://www.microsoft.com/en-us/download/details.aspx?displaylang=en&id=11436).  
  
Per le versioni precedenti di PDW senza punti di accesso, scaricare il[System Center Monitoring Pack per Microsoft SQL Server 2012 Parallel Data Warehouse Appliance](http://go.microsoft.com/fwlink/p/?LinkId=282661).  
  
Per il carico di lavoro di HDInsight, scaricare il [Management Pack di System Center per HDInsight](http://go.microsoft.com/fwlink/?LinkId=390208).  
  
## <a name="Step2"></a>Passaggio 2: Installare i Management Pack  
  
### <a name="install-the-sql-server-appliance-base-management-pack"></a>Installare SQL Server dello strumento Base Management Pack  
  
1.  Per eseguire l'installazione, fare doppio clic su download di SQL Server accessorio Base Management Pack.  
  
2.  Accettare il contratto di licenza e fare clic su **Avanti**.  
  
    ![Accettare il contratto di licenza](./media/install-the-scom-management-packs/SCOM_licnse_agrmt.png "SCOM_licnse_agrmt")  
  
3.  Selezionare una cartella di installazione oppure utilizzare il cartella di installazione di Management Pack predefinito.  
  
    ![Selezionare una cartella di installazione](./media/install-the-scom-management-packs/SCOM_licnse_agrmt2.png "SCOM_licnse_agrmt2")  
  
4.  Fare clic su **Installa**.  
  
    ![Confermare l'installazione](./media/install-the-scom-management-packs/SCOM_licnse_agrmt3.png "SCOM_licnse_agrmt3")  
  
5.  Scegliere **Chiudi**.  
  
    ![Fare clic su Chiudi](./media/install-the-scom-management-packs/SCOM_licnse_agrmt4.png "SCOM_licnse_agrmt4")  
  
### <a name="install-the-monitoring-pack-for-sql-server-pdw-appliance"></a>Installare il Monitoring Pack per SQL Server PDW Appliance  
  
1.  Per eseguire l'installazione, fare doppio clic su download di SQL Server PDW Appliance Management Pack.  
  
2.  Accettare il contratto di licenza e fare clic su **Avanti**.  
  
    ![Accettare il contratto di licenza](./media/install-the-scom-management-packs/SCOM_licnse_agmtB.png "SCOM_licnse_agmtB")  
  
3.  Scegliere la cartella che conterrà i file estratti. La cartella di installazione del Management Pack predefinito viene visualizzata per impostazione predefinita. Selezionare il valore predefinito o selezionare una cartella di installazione.  
  
    ![Selezione cartella di installazione](./media/install-the-scom-management-packs/SCOM_licnse_agmtB1.png "SCOM_licnse_agmtB1")  
  
4.  Fare clic su **Installa**.  
  
    ![Confermare l'installazione](./media/install-the-scom-management-packs/SCOM_licnse_agmtB2.png "SCOM_licnse_agmtB2")  
  
5.  Scegliere **Chiudi**.  
  
    ![Installazione completata](./media/install-the-scom-management-packs/SCOM_licnse_agmtB3.png "SCOM_licnse_agmtB3")  
  
## <a name="next-step"></a>Passaggio successivo  
Dopo aver creato il Management Pack installati, continuare al passaggio successivo: [importare il Management Pack di SCOM per PDW &#40; Sistema della piattaforma Analitica &#41; ](import-the-scom-management-pack-for-pdw.md).  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
