---
title: 'Procedura: Visualizzare le differenze dei dati | Microsoft Docs'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- sql.data.tools.datacompare.f1
ms.assetid: f88d3350-2eaf-44cc-96a8-84008b6cd071
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6c913ffa52c07091e4eec45f6013a3540edfe810
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47614269"
---
# <a name="how-to-view-data-differences"></a>Procedura: Visualizzare le differenze dei dati
Una volta completato il confronto dei dati nei due database, viene visualizzato ogni *oggetto di database* confrontato e ne viene riportato lo stato. È anche possibile visualizzare i risultati per i record in ogni oggetto, raggruppati in base allo stato.  
  
Dopo avere visualizzato le differenze, è possibile aggiornare la *destinazione* in modo corrispondente all'*origine* per alcuni o tutti gli oggetti o record diversi, mancanti o nuovi.  
  
### <a name="to-view-data-differences"></a>Per visualizzare le differenze dei dati  
  
1.  Confrontare i dati in un'origine e una destinazione.  
  
2.  (Facoltativo) Eseguire una o entrambe le operazioni seguenti:  
  
    -   Per impostazione predefinita, sono visualizzati i risultati per tutti gli oggetti, indipendentemente dal loro stato. Per visualizzare solo gli oggetti che presentano uno stato specifico, scegliere un'opzione nell'elenco **Filtro**.  
  
    -   Per visualizzare i risultati per i record in un oggetto specifico, fare clic sull'oggetto nel riquadro principale dei risultati e quindi fare clic su una scheda nel riquadro di visualizzazione dei record. In ogni scheda vengono visualizzati tutti i record nell'oggetto che presenta uno stato particolare: diverso, solo nell'origine, solo nella destinazione e identico. I dati vengono visualizzati per record e per colonna.  
  
## <a name="see-also"></a>Vedere anche  
[Procedura: Usare il confronto schema per confrontare definizioni di database diverse](../ssdt/how-to-use-schema-compare-to-compare-different-database-definitions.md)  
  
