---
title: Connettersi a un Server SQL del cluster di big data con Azure Data Studio | Microsoft Docs
description: Informazioni su come connettersi a un cluster di big data 2019 di SQL Server con Azure Data Studio.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/05/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 971fc2f8e8a77b00f3d2c5cd6390fec351ffc0f3
ms.sourcegitcommit: c7d3a903eb7f410db3a0230101d24de0af17621a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/05/2018
ms.locfileid: "48827302"
---
# <a name="connect-to-a-sql-server-big-data-cluster-with-azure-data-studio"></a>Connettersi a un cluster di SQL Server i big data con Azure Data Studio

Questo articolo descrive come installare Azure Data Studio, l'estensione di SQL Server 2019 (anteprima) e quindi connettersi a un cluster di big data. La nuova estensione di SQL Server 2019 include il supporto di anteprima per [i cluster dei big data di SQL Server 2019](big-data-cluster-overview.md), un integrata [esperienza notebook](notebooks-guidance.md)e un PolyBase [guidata Create External Table](../relational-databases/polybase/data-virtualization.md?toc=%2fsql%2fbig-data-cluster%2ftoc.json).

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="install-azure-data-studio"></a>Installare Azure Data Studio

Per installare Azure Data Studio, vedere [scaricare e installare la versione più recente di Azure Data Studio](../azure-data-studio/download.md).

## <a name="install-the-sql-server-2019-extension-preview"></a>Installare l'estensione di SQL Server 2019 (anteprima)

Per installare l'estensione, vedere [installare l'estensione di SQL Server 2019 (anteprima)](../azure-data-studio/sql-server-2019-extension.md).

## <a name="connect-to-the-cluster"></a>Connettersi al cluster

Quando ci si connette a un cluster di big data, è possibile connettersi a SQL Server [istanza master](concept-master-instance.md) o al gateway HDFS/Spark. Le sezioni seguenti illustrano come connettersi a ognuna.

## <a name="master-instance"></a>Istanza master

1. In Azure Data Studio, premere **F1** > **nuova connessione**.
1. Nelle **tipo di connessione**, selezionare **Microsoft SQL Server**.
1. Digitare l'indirizzo IP dell'istanza master di SQL Server nella **nome Server** (ad esempio:  **\<indirizzo IP\>, 31433**).
1. Modifica il **sicurissimo** per il **high_value_data** database.

   ![Connettersi all'istanza master](./media/deploy-big-data-tools/connect-to-cluster.png)

1. Premere **Connect**e il **Dashboard di Server** dovrebbe essere visualizzato.

## <a name="hdfsspark-gateway"></a>Gateway HDFS/Spark

1. In Azure Data Studio, premere **F1** > **nuova connessione**.
1. Nelle **tipo di connessione**, selezionare **cluster di big data di SQL Server**.
1. Digitare l'indirizzo IP del cluster di big data nelle **nome Server**.

   ![Connettersi al gateway HDFS/Spark](./media/deploy-big-data-tools/connect-to-cluster-hdfs-spark.png)

1. Premere **Connect**e il **Dashboard di Server** dovrebbe essere visualizzato.

## <a name="next-steps"></a>Passaggi successivi

Per eseguire i notebook in Azure Data Studio, vedere [come usare i notebook in fase di anteprima di SQL Server 2019](notebooks-guidance.md).
