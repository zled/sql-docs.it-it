---
title: Report attività di valutazione consolidata tramite Power BI (SQL Server Data Migration Assistant) | Documenti Microsoft
ms.custom: ''
ms.date: 09/07/2017
ms.prod: sql
ms.prod_service: dma
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-dma
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: jtoland
manager: craigg
ms.openlocfilehash: 26e3cf21866dced7b9dc8c57e4ffb06e015bf4db
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="report-on-your-consolidated-assessments-by-using-power-bi-data-migration-assistant"></a>Report attività di valutazione consolidata tramite Power BI (dati della migrazione guidata)

In questo articolo viene descritto come creare un report di Power BI per le valutazioni relative alla migrazione consolidati.

Per informazioni su consolidando le valutazioni relative alla migrazione utilizzando l'Assistente per la migrazione dei dati, vedere [consolidare le relazioni di valutazione](../dma/dma-consolidatereports.md).

## <a name="sample-power-bi-reports"></a>Report di esempio di Power BI

È possibile scaricare esempi di report di Power BI per le valutazioni relative alla migrazione consolidati da questo [repository Github](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/data-migration-assistant).

I report seguenti sono inclusi: 

- [Dashboard](#dashboard--details)

  Include statistiche snapshot e un report drill-down.

- [Preparazione dell'aggiornamento in locale](#on-premises-upgrade-readiness--details)

  L'origine dati è la visualizzazione UpgradeSuccessRanking nel database DMAReporting.  Questo report mostra il corretto aggiornamento percentuale per i database di valutazione.

- [Analogie nelle funzionalità in locale](#on-premise-feature-parity--details)

  Mostra le indicazioni di funzionalità per la versione di SQL Server di destinazione.

- [Preparazione dell'aggiornamento di database SQL Azure](#azure-sql-db-upgrade-readiness--details)

  L'origine dati è la visualizzazione UpgradeSuccessRanking nel database DMAReporting.  Questo report mostra la percentuale di aggiornamento completato per i database valutata per la migrazione di database SQL di Azure.

- [Database di SQL Server non supportata di Microsoft Azure](#azure-sql-db-unsupported-features--details)

  Mostra le funzionalità del database esistente che non sono supportate in database SQL di Azure (V12).

È possibile modificare questi report per il funzionamento con l'ambiente, la modifica dell'origine dati in Power BI. 

1. Selezionare la freccia in giù accanto a **modifica query**e selezionare **impostazioni origine dati**.

   ![Le query menu Modifica, impostazioni dell'origine dati](../dma/media/DataSourceSettings.png)

1. Selezionare **modificare l'origine...** e immettere i valori di server e database.

   ![Modificare l'origine, server e database](../dma/media/ChangeSource.png)

1. Selezionare **OK**, quindi selezionare **Chiudi**.

1. Aggiornare i report.

   ![Aggiornare i report di Power BI](../dma/media/RefreshReport.png)

### <a name="dashboard-report"></a>Report del dashboard

![Report del dashboard](../dma/media/DashboardReport.png)

Il dashboard Mostra informazioni dettagliate su tutte le valutazioni. È possibile utilizzare i filtri dei dati sul lato sinistro per filtrare in base al database o istanza. È possibile utilizzare il grafico a barre per il drill-down in categorie specifiche per vedere dove si trovano i problemi.

Per eseguire il drill-, selezionare il cerchio con freccia in giù nell'angolo superiore destro del grafico a barre.

![Categoria di drill-down](../dma/media/CategoryDrillDown.png)

La sequenza di drill-down è impostata come illustrato nell'immagine seguente (in **asse**). Per modificare la sequenza, trascinare le colonne nell'ordine desiderato.

![Visualizzazioni, asse grafico a barre](../dma/media/VisualizationsAxis.png)

Questa vista diventa ancora più potente per filtri prima da un database specifico e quindi eseguire il drill-down i problemi di categoria specifica. Nell'esempio seguente, il database delle risorse Umane è selezionato per l'istanza **SQL01** per visualizzare tutti gli oggetti che impediscono le migrazioni (modifiche di rilievo).

![Modifiche di rilievo per database delle risorse Umane](../dma/media/BreakingChanges.png)

### <a name="on-premises-upgrade-readiness-report"></a>Report di conformità di aggiornamento locale

![Report di conformità di aggiornamento locale](../dma/media/OnPremisesUpgradeReadinessReport.png)

Questo report mostra uno snapshot di database come pronto sono per eseguire la migrazione a una versione successiva di SQL Server. I dati in questo report provengono da dbo. UpgradeSuccessFactor\_OnPrem vista nel database DMAReporting.

Filtraggio in base all'istanza e nome del database e usando le schede di punteggio nella parte superiore, si noterà che il database potrebbe essere migrato troppo versione. Ad esempio, se Filtra per il database AdventureWorks 2012, si noterà che il database è pronto per spostare tutte le versioni di SQL Server elencate nel report. Viene determinato assicurandosi che non sono presenti modifiche di rilievo per tale database e livello di compatibilità.

![Fattore di successo aggiornamento per il database AdventureWorks](../dma/media/UpgradeSuccessFactor.png)

### <a name="on-premises-feature-parity-report"></a>Report di parità di funzionalità locali

![Report di parità di funzionalità locali](../dma/media/OnPremisesFeatureParityReport.png)

Utilizzare questo report per evidenziare nuove funzionalità che può essere utilizzata per il database nella versione di SQL Server di destinazione.

Quando si seleziona una funzionalità nel grafico a imbuto, i dati nella parte inferiore che evidenzia gli oggetti che sono interessati dalla funzionalità. Nell'esempio seguente, il **database di estensione per il risparmio di spazio di archiviazione** funzionalità è selezionata, e una tabella viene elencata che possono trarre vantaggio da questa funzionalità.

![Indicazione di funzionalità per l'estensione Database](../dma/media/FeatureRecommend_StretchDatabase.png)

### <a name="azure-sql-db-upgrade-readiness-report"></a>Report di preparazione aggiornamento database di SQL Azure

![Report di preparazione aggiornamento database di SQL Azure](../dma/media/AzureSQLDBUpgradeReadinessReport.png)

Questo report mostra lo stato di preparazione del database per eseguire la migrazione di Database SQL di Azure V12. I dati del report provengono da dbo. UpgradeSuccessRanking vista nel database DMAReporting.

### <a name="azure-features-parity-report"></a>Report di parità di funzionalità di Azure

![Report di parità di funzionalità di Azure](../dma/media/AzureFeaturesParityReport.png)

Questo report consente di evidenziare il *le funzionalità a livello di istanza* che non sono supportati dal Database SQL di Azure V12.

Quando si seleziona una funzionalità nel grafico a imbuto, i dati nella parte inferiore sono elencate le istanze e funzionalità di database che non sono supportate. Nell'esempio seguente, questa funzionalità è selezionata: **configurazione gruppo di disponibilità AlwaysOn non è supportata in Database SQL di Azure**.  

![Sempre nella funzionalità gruppo di disponibilità](../dma/media/Feature_AlwaysOnAvailability.png)

 
### <a name="azure-sql-db-unsupported-features-report"></a>Report funzionalità non supportata di database SQL di Azure

![Report funzionalità non supportata di database SQL di Azure](../dma/media/AzureSQLDBUnsupportedFeaturesReport.png)

Questo report evidenzia le funzionalità non supportate per un determinato **database** quando la destinazione è il Database SQL di Azure (V12).

Applicando un filtro per il valore di nome e funzionalità di database nel grafico a imbuto, consente di visualizzare i dettagli su funzionalità non supportata. Dettagli includono i requisiti per risolvere il problema e l'oggetto interessato.

Ad esempio, il filtro per il database DTC e **non è possibile aggiornare i database di sola lettura**, è possibile visualizzare un elenco di oggetti che sono interessati.

![Database di sola lettura non possono essere aggiornati problema](../dma/media/ReadOnlyDatabases.png)

## <a name="see-also"></a>Vedere anche

[Panoramica dell'Assistente per la migrazione di dati](../dma/dma-overview.md)

[Download di Assistente per la migrazione dei dati](https://www.microsoft.com/download/details.aspx?id=53595)

[Download di Power BI](https://powerbi.microsoft.com/)
