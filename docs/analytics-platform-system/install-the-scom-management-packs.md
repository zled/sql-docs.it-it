---
title: 'Installare pacchetti di gestione SCOM: Analitica Platform System | Documenti Microsoft'
description: Seguire questi passaggi per scaricare e installare i Management Pack di System Center Operations Manager (SCOM) per SQL Server PDW. I Management Pack sono necessari per monitorare SQL Server PDW da SCOM.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 163ab893074e171decb573d876c5f98334437985
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="install-sql-server-operations-manager-scom-management-packs-for-analytics-platform-system"></a>Installare SQL Server Operations Manager (SCOM) management pack per Analitica Platform System
Seguire questi passaggi per scaricare e installare i Management Pack di System Center Operations Manager (SCOM) per SQL Server PDW. I Management Pack sono necessari per monitorare SQL Server PDW da SCOM.  
  
## <a name="BeforeBegin"></a>Prima di iniziare  
**Prerequisiti**  
  
System Center Operations Manager deve essere installato e in esecuzione. SQL Server PDW 2012 richiede System Center Operations Manager 2007 R2, System Center Operations Manager 2012 o System Center Operations Manager 2012 service pack 1.  
  
## <a name="Step1"></a>Passaggio 1: Scaricare i Management Pack  
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
  
    ![Selezione cartella di installazione](./media/install-the-scom-management-packs/SCOM_licnse_agrmt2.png "SCOM_licnse_agrmt2")  
  
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
Dopo aver creato il Management Pack installati, continuare al passaggio successivo: [importare il Management Pack di SCOM per PDW &#40;Analitica Platform System&#41;](import-the-scom-management-pack-for-pdw.md).  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
