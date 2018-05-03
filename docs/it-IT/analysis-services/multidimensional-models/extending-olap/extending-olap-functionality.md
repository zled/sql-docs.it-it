---
title: Estensione delle funzionalità OLAP | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: olap
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0c162058798051fc57ecb57038e6914969ef39f9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="extending-olap-functionality"></a>Estensione delle funzionalità OLAP
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  I programmatori possono estendere Analysis Services mediante la scrittura di assembly, estensioni personalizzate e stored procedure che forniscono le funzionalità che si desidera utilizzare e ridefinire in più applicazioni di database. Gli assembly vengono utilizzati per estendere le funzionalità dei modelli multidimensionali mediante l'aggiunta di nuove procedure e funzioni al linguaggio MDX o per mezzo del componente aggiuntivo di personalizzazione.  
  
 Consentendo di sviluppare il codice comune una sola volta e di archiviarlo in una singola posizione, le stored procedure possono essere utilizzare per chiamare routine esterne, semplificando le operazioni di sviluppo e di implementazione del database di Analysis Services. Possono essere utilizzate per aggiungere alle applicazioni funzionalità business non presenti in quelle native di MDX.  
  
 Le personalizzazioni sono oggetti personalizzati che si aggiungono a un cubo per fornire un comportamento che varia in base all'utente. Le personalizzazioni non sono oggetti permanenti nel cubo, ma oggetti utilizzati in modo dinamico dall'applicazione client durante la sessione utente. Gli esempi includono la modifica della valuta di un valore valutario a seconda della persona che accede ai dati, la fornitura di indicatori KPI individualizzati o un elenco di suggerimenti di destinazione per clienti regolari che acquistano online.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Estensione di OLAP tramite personalizzazioni](../../../analysis-services/multidimensional-models/extending-olap/extending-olap-through-personalizations.md)  
  
 [Analysis Services Personalization Extensions](../../../analysis-services/multidimensional-models/extending-olap/analysis-services-personalization-extensions.md)  
  
 [Definizione delle Stored procedure](../../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
