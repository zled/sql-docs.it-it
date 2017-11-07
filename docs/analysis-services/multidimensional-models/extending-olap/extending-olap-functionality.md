---
title: "Estensione delle funzionalità OLAP | Documenti Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 49a17ff3-94e9-4969-84fc-37d49e63933b
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 20749b47397d4cd1826fbdca65be78e7f1905025
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="extending-olap-functionality"></a>Estensione delle funzionalità OLAP
  I programmatori possono estendere Analysis Services mediante la scrittura di assembly, estensioni personalizzate e stored procedure che forniscono le funzionalità che si desidera utilizzare e ridefinire in più applicazioni di database. Gli assembly vengono utilizzati per estendere le funzionalità dei modelli multidimensionali mediante l'aggiunta di nuove procedure e funzioni al linguaggio MDX o per mezzo del componente aggiuntivo di personalizzazione.  
  
 Consentendo di sviluppare il codice comune una sola volta e di archiviarlo in una singola posizione, le stored procedure possono essere utilizzare per chiamare routine esterne, semplificando le operazioni di sviluppo e di implementazione del database di Analysis Services. Possono essere utilizzate per aggiungere alle applicazioni funzionalità business non presenti in quelle native di MDX.  
  
 Le personalizzazioni sono oggetti personalizzati che si aggiungono a un cubo per fornire un comportamento che varia in base all'utente. Le personalizzazioni non sono oggetti permanenti nel cubo, ma oggetti utilizzati in modo dinamico dall'applicazione client durante la sessione utente. Gli esempi includono la modifica della valuta di un valore valutario a seconda della persona che accede ai dati, la fornitura di indicatori KPI individualizzati o un elenco di suggerimenti di destinazione per clienti regolari che acquistano online.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Estensione di OLAP tramite personalizzazioni](../../../analysis-services/multidimensional-models/extending-olap/extending-olap-through-personalizations.md)  
  
 [Analysis Services Personalization Extensions](../../../analysis-services/multidimensional-models/extending-olap/analysis-services-personalization-extensions.md)  
  
 [Definizione delle Stored procedure](../../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  

