---
title: Monitoraggio con Console di amministrazione - Analitica Platform System | Documenti Microsoft
description: Per il sistema di piattaforma Analitica, la Console di amministrazione è un'applicazione web che espone le informazioni di stato, l'integrità e prestazioni dello strumento. Gli utenti di connettersi alla Console di amministrazione tramite un browser internet.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 5f7c6ef68a8f91121a63def8e2153a5c38873aa3
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
ms.locfileid: "31544983"
---
# <a name="monitor-the-appliance-with-the-admin-console---analytics-platform-system"></a>Monitorare il dispositivo con la Console di amministrazione - Analitica Platform System
La Console di amministrazione è un'applicazione web di SQL Server PDW che espone le informazioni di stato, l'integrità e prestazioni dello strumento. Gli utenti di connettersi alla Console di amministrazione tramite Internet Explorer.  
  
## <a name="About"></a>Sulla Console di amministrazione  
![Appliance Console Home](./media/monitor-the-appliance-by-using-the-admin-console/SQL_Server_PDW_AdminConsol_ApplHome.png "SQL_Server_PDW_AdminConsol_ApplHome")  
  
**Dispositivo**  
Home  
Fornisce un riepilogo rapido dello stato del dispositivo.  
  
Integrità  
Consente di visualizzare la topologia dello strumento con indicatori che mostrano l'integrità di ogni componente monitorato all'interno di ogni nodo. Consente di visualizzare lo stato corrente dei singoli nodi e le proprietà dei componenti di nodo.  
  
Visualizza gli avvisi di hardware e software.  
  
Performance Monitor  
Visualizza i grafici di monitoraggio delle prestazioni.  
  
**Parallel Data Warehouse**  
Home  
Fornisce un riepilogo rapido dello stato di PDW.  
  
Sessioni  
Visualizza sessioni attive di PDW. Ciò consente di specificare per il monitoraggio di contesa delle risorse.  
  
Query  
Visualizza un elenco di query in esecuzione e completati di recente. Visualizza gli errori correlati, se presente. Fornisce inoltre la possibilità di visualizzare i dettagli delle informazioni di esecuzione query piano e di nodo dell'esecuzione.  
  
Carica  
Consente di visualizzare caricare i piani, lo stato corrente di PDW carichi e gli errori correlati, se presente.  
  
Backup e ripristino  
Consente di visualizzare un log di PDW backup e le operazioni di ripristino.  
  
Integrità  
Consente di visualizzare la topologia PDW con indicatori che mostrano l'integrità di ogni componente monitorato all'interno di ogni nodo. Consente di visualizzare lo stato corrente dei singoli nodi e le proprietà dei componenti di nodo.  
  
Visualizza gli avvisi di hardware e software.  
  
Risorse  
Visualizza un elenco di blocchi di risorse PDW e il relativo stato corrente.  
  
Archiviazione  
Riepiloga l'utilizzo di archiviazione PDW.  
  
Performance Monitor  
Visualizza grafici di monitoraggio delle prestazioni di PDW.  
  
**HDInsight**  
Home  
Fornisce un riepilogo rapido dello stato di HDInsight.  
  
HDFS  
Riepiloga l'utilizzo dello spazio di HDInsight e vengono elencati i principali consumer di 10 spazi.  
  
Riduzione/mappe  
Riepiloga lo stato dei processi di MapReduce.  
  
Integrità  
Consente di visualizzare la topologia di HDInsight con indicatori che mostrano l'integrità di ogni componente monitorato all'interno di ogni nodo. Consente di visualizzare lo stato corrente dei singoli nodi e le proprietà dei componenti di nodo.  
  
Visualizza gli avvisi di hardware e software.  
  
Archiviazione  
Riepiloga l'utilizzo di archiviazione di HDInsight.  
  
Performance Monitor  
Visualizza i grafici di monitoraggio delle prestazioni.  
  
> [!NOTE]  
> La console di amministrazione ha una risoluzione dello schermo di 1024 x 768. Consente di visualizzare la console di amministrazione migliore con una risoluzione dello schermo di 1280 X 1024 o superiore.  
  
## <a name="Connect"></a>Connettersi alla Console di amministrazione  
Per connettersi alla Console di amministrazione, è necessario:  
  
-   AT almeno Internet Explorer versione 10.  
  
-   Autorizzazioni per accedere alla Console di amministrazione. <!-- MISSING LINKS See [Grant Permissions to Use the Admin Console &#40;SQL Server PDW&#41;](../sqlpdw/grant-permissions-to-use-the-admin-console-sql-server-pdw.md).  -->  
  
-   L'indirizzo IP del cluster di nodo di controllo.  Ottenere l'oggetto dall'amministratore di SQL Server PDW.  
  
Per connettere la Console di amministrazione, utilizzare https e Internet Explorer per passare all'indirizzo IP del cluster di nodo di controllo. Ad esempio, se l'indirizzo IP del cluster di nodo di controllo è `10.192.63.102`, immettere `https://10.192.63.102` nella barra degli indirizzi del browser. La prima schermata richiederà il **accesso** e **PASSWORD**. Specificare un account di accesso di autenticazione di SQL Server e password, o un account di autenticazione di Windows e password di Windows. Se si utilizza un account di accesso di autenticazione di Windows, la Console di amministrazione utilizzerà la rappresentazione.  
  
## <a name="RelatedTasks"></a>Attività della Console di amministrazione  
La Console di amministrazione consente di monitorare le operazioni seguenti:  
  
|||  
|-|-|  
|**Tipo di informazioni**|**Come l'accesso nella Console di amministrazione**|  
|Stato generale del dispositivo|Fare clic su **stato dello strumento** nel menu in alto o **Home**.|  
|Avvisi|Fare clic su **avvisi**. Per altre informazioni, vedere [informazioni sugli avvisi della Console di amministrazione &#40;Analitica Platform System&#41;](understanding-admin-console-alerts.md).|  
|I componenti dello strumento e il relativo stato|Fare clic su **stato dello strumento** nel menu in alto o **Home**.|  
|Richieste di monitoraggio (incluse le query, caricamenti, backup e ripristini)|Fare clic su **sessioni** per visualizzare le sessioni attualmente attive o recenti.<br /><br />Fare clic su **query** per visualizzare le query attualmente attive o recenti. Le informazioni visualizzate per le query includono carichi, backup e ripristini.<br /><br />Fare clic su **blocchi** per visualizzare i blocchi attivi.|  
|Monitorare le informazioni aggiuntive per i carichi, backup e ripristini.|Fare clic su **carichi** o **backup e ripristino**.|  
|Informazioni sulle prestazioni|Fare clic su **Performance Monitor**.|  
  
## <a name="see-also"></a>Vedere anche  
[Monitoraggio dello strumento &#40;Analitica Platform System&#41;](appliance-monitoring.md)  
  
