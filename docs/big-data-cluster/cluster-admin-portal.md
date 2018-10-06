---
title: Monitoraggio di Cluster tramite il portale di amministrazione di Cluster | Microsoft Docs
description: ''
author: yualan
ms.author: alayu
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 3ae85c9e9078b91589b828d1bee9d3218b5316cc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48796408"
---
# <a name="introduction-to-the-cluster-administration-portal"></a>Introduzione al portale di amministrazione del Cluster
Se si desidera monitorare o risolverne i problemi del cluster di big data di SQL Server, usare il portale di amministrazione cluster. 

Nel portale di amministrazione del cluster consente di:
- Numero di POD in esecuzione e agli eventuali problemi di visualizzare rapidamente
- Monitorare lo stato di distribuzione
- Visualizza endpoint di servizio disponibili
- Controller di visualizzazione e l'istanza master di SQL Server
- Il drill-down informazioni sui POD, incluso l'accesso a Kibana registri e i dashboard di Grafana

## <a name="access-the-cluster-administration-portal"></a>Accedere al portale di amministrazione del cluster
Seguire le [avvio rapido per distribuire il cluster di big data](quickstart-big-data-cluster-deploy.md) finché non viene visualizzata la **portale di amministrazione cluster** sezione. Dopo aver creato il cluster di big data in esecuzione con mssqlctl, seguire queste istruzioni:

Il pod controller è in esecuzione, è possibile utilizzare il portale di amministrazione cluster per monitorare la distribuzione. È possibile accedere al portale con l'esterno indirizzo IP e porta numero per il `service-proxy-lb` (ad esempio: **https://\<ip-address\>: 30777**). Le credenziali per accedere al portale di amministrazione sono i valori delle `CONTROLLER_USERNAME` e `CONTROLLER_PASSWORD` variabili di ambiente fornite sopra.
> [!NOTE]
> Vi si intende usare un avviso di sicurezza all'accesso alla pagina web poiché si sta usando i certificati SSL generati automaticamente. Nelle future versioni, Microsoft fornirà la possibilità di fornire i propri certificati firmati.

## <a name="overview"></a>Panoramica
![cenni preliminari](./media/cluster-admin-portal/portal-overview.png)

Quando si immissione prima il portale, è possibile visualizzare rapidamente il numero di POD in esecuzione in:
- Controller
- Istanza master
- Calcolo del Pool
- Pool di archiviazione
- Pool di dati

Se si verificano problemi, è possibile aprire un collegamento ai problemi noti. È possibile utilizzare il riquadro di spostamento a sinistra per passare al pool specifico se si verifica un problema.

## <a name="deployment"></a>Distribuzione
![distribuzione](./media/cluster-admin-portal/portal-deployment.png)

Per monitorare la distribuzione, fare clic sulla scheda distribuzione a sinistra. È possibile visualizzare una visualizzazione albero della distribuzione, e se sono presenti problemi nella distribuzione.

## <a name="service-endpoints"></a>Endpoint di servizio
![endpoint](./media/cluster-admin-portal/portal-endpoints.png)

È possibile visualizzare gli endpoint di servizio disponibili facendo clic sulla scheda endpoint il riquadro di spostamento a sinistra.

Sono inclusi i collegamenti all'endpoint di Spark, dashboard di Grafana, e registri di Kibana.

## <a name="controller"></a>Controller
![Controller](./media/cluster-admin-portal/portal-controller.png)

Il controller Mostra tutti i POD correlati al controller. Altre informazioni sul controller [qui.](concept-controller.md)

Per altre informazioni aggiuntive su ogni pod, è possibile fare clic su **metriche** colonna per visualizzare i dashboard di Grafana.

Per altre informazioni sui log per i POD con problemi, è possibile fare clic sui **registri** colonna.

## <a name="master-instance"></a>Istanza master
![endpoint](./media/cluster-admin-portal/portal-master.png)

L'istanza Master Mostra tutti i POD correlati all'istanza master di SQL Server. Altre informazioni sull'istanza master di SQL Server [qui.](concept-master-instance.md)

Per altre informazioni aggiuntive su ogni pod, è possibile fare clic su **metriche** colonna per visualizzare i dashboard di Grafana.

Per altre informazioni sui log per i POD con problemi, è possibile fare clic sui **registri** colonna.

## <a name="pool-and-pod-pages"></a>Pagine di Pod e pool
![Pool](./media/cluster-admin-portal/portal-data-pool.png)

In ogni pagina del pool (calcolo, archiviazione e dati), è possibile eseguire il drill down tutte le pagine di pod facendo clic su **predefinito**

![POD](./media/cluster-admin-portal/portal-data-default-pool.png)

Mostra una barra di navigazione nella parte superiore di drill-down percorso.

Per altre informazioni aggiuntive su ogni pod, è possibile fare clic su **metriche** colonna per visualizzare i dashboard di Grafana.

Per altre informazioni sui log per i POD con problemi, è possibile fare clic sui **registri** colonna.

Per altre informazioni su ogni pool:
- [calcolo del pool](concept-compute-pool.md)
- [pool di archiviazione](concept-storage-pool.md)
- [pool di dati](concept-data-pool.md)

## <a name="about-page"></a>Informazioni sulla pagina
![informazioni](./media/cluster-admin-portal/portal-about.png)

Qui è possibile visualizzare le informazioni sul cluster, ad esempio i numeri di versione diverso, contenitori e un collegamento alla documentazione.
