---
title: 'Lezione 4: Contrassegna come tabella data | Documenti Microsoft'
ms.custom: ''
ms.date: 03/27/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: c32cc336-b7d8-4122-9d62-4936344d2315
caps.latest.revision: 18
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 08a3e1852f58e1f21049d1a5c0551669423845db
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="lesson-3-mark-as-date-table"></a>Lezione 3: Contrassegna come tabella data
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

Nella Lezione 2: Aggiungere dati è stata importata una tabella delle dimensioni denominata DimDate. Mentre nel modello questa tabella è denominata DimDate, è possibile anche noto come un *tabella data*, in quanto contiene data e ora.  
  
Ogni volta che si utilizzano funzioni di business intelligence DAX nei calcoli, come verranno eseguite quando si creano misure leggermente in un secondo momento, è necessario specificare le proprietà di tabella di dati, che includono un *tabella data* e un identificatore univoco *Data colonna* in tale tabella.
  
In questa lezione si sarà contrassegna la tabella DimDate come il *tabella data* e la colonna Data (nella tabella Date) come il *colonna Data* (identificatore univoco).  

Prima si contrassegna la tabella relativa alla data e la colonna di data, è necessario eseguire una piccola manutenzione per rendere più facile comprendere il modello. Si noterà che la tabella DimDate una colonna denominata **FullDateAlternateKey**. Contiene una riga per ogni giorno in ogni anno di calendario incluso nella tabella. Verrà usato molto in questa colonna nelle formule di misure e nei report. Tuttavia, FullDateAlternateKey non sono in effetti un identificatore valido per questa colonna. È il nome **data**, rendendo più semplice identificare e includere nelle formule. Quando possibile, è consigliabile rinominare gli oggetti come tabelle e colonne per renderle più facilmente identificabili nel client di creazione report di applicazioni, quali Power BI ed Excel. 
  
Tempo stimato per il completamento della lezione: **3 minuti**  
  
## <a name="prerequisites"></a>Prerequisiti  
Questo argomento fa parte di un'esercitazione relativa alla modellazione tabulare che deve essere completata nell'ordine specificato. Prima di eseguire le attività in questa lezione, è necessario avere completato la lezione precedente: [lezione 2: aggiungere dati](../analysis-services/lesson-2-add-data.md). 

### <a name="to-rename-the-fulldatealternatekey-column"></a>Per rinominare la colonna FullDateAlternateKey

1.  In Progettazione modelli fare clic su di **DimDate** tabella.

2.  Fare doppio clic sull'intestazione per il **FullDateAlternateKey** colonna e quindi rinominarlo **data**.

  
### <a name="to-set-mark-as-date-table"></a>Per impostare Contrassegna come tabella data  
  
1.  Selezionare la colonna **Data** , quindi nella finestra **Proprietà** verificare che **Data**sia selezionata in  **Tipo di dati** .  
  
2.  Fare clic sul menu **Tabella** , selezionare **Data**, quindi scegliere **Contrassegna come tabella data**.  
  
3.  Nella casella di riepilogo **Data** della finestra di dialogo **Contrassegna come tabella data** selezionare la colonna **Data** come identificatore univoco. Verrà in genere selezionato per impostazione predefinita. Scegliere **OK**. 

    ![come tabulare-lesson3-data-tabella-](../analysis-services/media/as-tabular-lesson3-date-table.png)
  

## <a name="whats-next"></a>Quali sono le operazioni successive?
Passare alla lezione successiva: [lezione 4: creare relazioni](../analysis-services/lesson-4-create-relationships.md).
  
