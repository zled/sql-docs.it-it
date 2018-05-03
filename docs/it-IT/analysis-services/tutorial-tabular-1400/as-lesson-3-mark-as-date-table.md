---
title: "Lezione dell'esercitazione di Analysis Services 3: contrassegna come tabella data | Documenti Microsoft"
description: Viene descritto come contrassegnare una tabella di data del progetto di Analysis Services tutorial.
ms.prod_service: analysis-services, azure-analysis-services
services: analysis-services
ms.suite: pro-bi
documentationcenter: ''
author: Minewiskan
manager: kfile
editor: ''
tags: ''
ms.assetid: ''
ms.service: analysis-services
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.date: 02/20/2018
ms.author: owend
monikerRange: '>= sql-analysis-services-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 8d15495ef5c1fdfe4150990f5ca24e022b4fe05a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="mark-as-date-table"></a>Contrassegna come tabella data

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

Nella lezione 2: Recuperare i dati, è stato importato una tabella delle dimensioni denominata **DimDate**. Mentre nel modello questa tabella è denominata DimDate, è possibile anche noto come un *tabella data*, in quanto contiene data e ora.  
  
Ogni volta che si utilizzano funzioni di business intelligence DAX, ad esempio quando si creano misure in un secondo momento, è necessario specificare le proprietà che includono un *tabella data* e un identificatore univoco *colonna Data* in tale tabella.
  
In questa lezione si contrassegna il **DimDate** tabella come il *tabella data* e **data** colonna (nella tabella Date) come il *colonna Data* (univoco identificatore).  

Prima di contrassegnare la tabella relativa alla data e la colonna di data, è consigliabile eseguire una piccola manutenzione per rendere più facile comprendere il modello. Si noti che nella tabella DimDate una colonna denominata **FullDateAlternateKey**. Questa colonna contiene una riga per ogni giorno in ogni anno di calendario incluso nella tabella. Utilizzare questa colonna molto nelle formule di misure e nei report. Tuttavia, FullDateAlternateKey non è realmente un identificatore valido per questa colonna. Il nome **data**, rendendo più semplice identificare e includere nelle formule. Quando possibile, è consigliabile rinominare gli oggetti come tabelle e colonne per renderne più semplice identificare in SSDT e applicazioni di reporting client. 
  
Tempo stimato per completare questa lezione: **tre minuti**  
  
## <a name="prerequisites"></a>Prerequisiti  

In questo articolo fa parte di un'esercitazione di modellazione tabulare, che deve essere completata nell'ordine. Prima di eseguire le attività in questa lezione, è necessario avere completato la lezione precedente: [lezione 2: ottenere dati](../tutorial-tabular-1400/as-lesson-2-get-data.md). 

### <a name="to-rename-the-fulldatealternatekey-column"></a>Per rinominare la colonna FullDateAlternateKey

1.  In Progettazione modelli fare clic su di **DimDate** tabella.

2.  Fare doppio clic su intestazione per il **FullDateAlternateKey** colonna e quindi rinominarlo **data**.

  
### <a name="to-set-mark-as-date-table"></a>Per impostare Contrassegna come tabella data  
  
1.  Selezionare la colonna **Data** , quindi nella finestra **Proprietà** verificare che **Data**sia selezionata in  **Tipo di dati** .  
  
2.  Fare clic sul menu **Tabella** , selezionare **Data**, quindi scegliere **Contrassegna come tabella data**.  
  
3.  Nella casella di riepilogo **Data** della finestra di dialogo **Contrassegna come tabella data** selezionare la colonna **Data** come identificatore univoco. In genere viene selezionato per impostazione predefinita. Scegliere **OK**. 

    ![as-lesson3-date-table](../tutorial-tabular-1400/media/as-lesson3-date-table.png)
  

## <a name="whats-next"></a>Quali sono le operazioni successive?

[Lezione 4: Creare relazioni](../tutorial-tabular-1400/as-lesson-4-create-relationships.md).
  
