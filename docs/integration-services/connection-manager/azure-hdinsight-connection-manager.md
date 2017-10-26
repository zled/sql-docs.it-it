---
title: Gestione connessione di Azure HDInsight | Documenti Microsoft
ms.custom: 
ms.date: 02/28/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SQL13.DTS.DESIGNER.AFPHDICM.F1
- SQL14.DTS.DESIGNER.AFPHDICM.F1
ms.assetid: 29d01bd9-8b38-43b1-b937-67f8aea57c0f
caps.latest.revision: 4
author: Lingxi-Li
ms.author: lingxl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 080cd1184d3c29673ac476d6fe6087b697160544
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="azure-hdinsight-connection-manager"></a>Gestione connessione di Azure HDInsight
Il **Connection Manager di Azure HDInsight** consente a un pacchetto SSIS per connettersi a un cluster HDInsight di Azure.

Il **Connection Manager di Azure HDInsight** è un componente del [Feature Pack di SQL Server Integration Services (SSIS) per Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

Per creare e configurare un **Connection Manager di Azure HDInsight**, attenersi alla procedura seguente:

1. Nel **Aggiungi gestione connessione SSIS** nella finestra di dialogo **AzureHDInsight**, fare clic su **Aggiungi**.
2. Nel **Editor gestione connessione HDInsight di Azure** finestra di dialogo, specificare il **nome DNS Cluster** (senza il prefisso del protocollo), **Username**, e **Password** per il cluster HDInsight a cui connettersi.
3. Scegliere **OK** per chiudere la finestra di dialogo.
4. È possibile visualizzare le proprietà del componente Gestione connessione create nella finestra **Proprietà** .

