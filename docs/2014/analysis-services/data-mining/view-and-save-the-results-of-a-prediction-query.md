---
title: Visualizzare e salvare i risultati di una Query di stima | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- prediction queries [Analysis Services]
- viewing prediction query results
- displaying prediction query results
- Mining Model Prediction [Analysis Services], viewing results
ms.assetid: abba4d24-3619-44c1-8279-88f27ad627d3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0273919410b5b182b535b805922ec39cdd82d6e6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48195931"
---
# <a name="view-and-save-the-results-of-a-prediction-query"></a>Visualizzare e salvare i risultati di una query di stima
  Dopo aver definito una query in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] mediante il generatore delle query di stima, è possibile eseguire la query e visualizzare i risultati passando alla visualizzazione dei risultati della query.  
  
 È possibile salvare i risultati di una query di stima in una tabella inclusa in qualsiasi origine dati definita in un progetto di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . È possibile creare una nuova tabella oppure salvare i risultati della query in una tabella esistente. Se si salvano i risultati in una tabella esistente, è possibile scegliere di sovrascrivere i dati attualmente archiviati nella tabella. Altrimenti, i risultati della query verranno accodati ai dati esistenti nella tabella.  
  
### <a name="run-a-query-and-view-the-results"></a>Eseguire una query e visualizzare i risultati  
  
1.  Sulla barra degli strumenti della scheda **Stima modello di data mining** di Progettazione modelli di data mining in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]fare clic su **Risultato** .  
  
     Verrà aperta la visualizzazione dei risultati della query, tramite cui verrà eseguita la query. I risultati verranno visualizzati in una griglia nel visualizzatore.  
  
### <a name="save-the-results-of-a-prediction-query-to-a-table"></a>Salvare i risultati di una query di stima in una tabella  
  
1.  Sulla barra degli strumenti della scheda **Stima modello di data mining** di Progettazione modelli di data mining fare clic su **Salva risultati query**.  
  
     Verrà visualizzata la finestra di dialogo **Salva risultati query di data mining** .  
  
2.  Selezionare un'origine dati nell'elenco **Origine dati** oppure fare clic su **Nuova** per creare una nuova origine dati.  
  
3.  Nella casella **Nome tabella** immettere il nome della tabella. Se la tabella esiste già, selezionare **Sovrascrivi se esistente** per sostituire il contenuto della tabella con i risultati della query. Se non si desidera sovrascrivere il contenuto della tabella, non selezionare questa casella di controllo. I nuovi risultati della query verranno accodati ai dati esistenti nella tabella.  
  
4.  Selezionare una vista origine dati in **Aggiungi a vista origine dati** se si desidera aggiungere la tabella a una vista origine dati.  
  
5.  Fare clic su **Salva**.  
  
    > [!WARNING]  
    >  Se la destinazione non supporta set di righe gerarchici, è possibile aggiungere la parola chiave FALTTENED ai risultati per effettuare il salvataggio come tabella flat.  
  
  
