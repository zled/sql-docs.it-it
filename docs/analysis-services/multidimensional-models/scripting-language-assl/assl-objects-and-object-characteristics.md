---
title: Oggetti ASSL e relative caratteristiche | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
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
helpviewer_keywords:
- reference exceptions [Analysis Services Scripting Language]
- ASSL, objects
- inheritance [Analysis Services Scripting Language]
- localized names [Analysis Services Scripting Language]
- objects [Analysis Services Scripting Language]
- names [Analysis Services Scripting Language]
- Analysis Services Scripting Language, objects
- expansion [Analysis Services Scripting Language]
ms.assetid: 6e5c28b5-c0bc-4ccd-82e5-e174bbb71386
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 54c1e299952f042587389631e3220eb241ea598e
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="assl-objects-and-object-characteristics"></a>Oggetti ASSL e relative caratteristiche
  In ASSL (Analysis Services Scripting Language) gli oggetti seguono linee guida specifiche in relazione ai gruppi di oggetti, all'ereditarietà, alla denominazione, all'espansione e all'elaborazione.  
  
## <a name="object-groups"></a>Gruppi di oggetti  
 Tutti [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] gli oggetti hanno una rappresentazione XML. Gli oggetti sono suddivisi in due gruppi:  
  
 **Oggetti principali**  
 Gli oggetti principali possono essere creati, modificati ed eliminati in modo indipendente. Di seguito vengono riportati gli oggetti principali:  
  
-   Server  
  
-   Database  
  
-   Dimensioni  
  
-   Cubi  
  
-   Gruppi di misure  
  
-   Partizioni  
  
-   Prospettive  
  
-   Modelli di data mining  
  
-   Ruoli  
  
-   Comandi associati a un server o a un database  
  
-   Origini dei dati  
  
 Per tenere traccia della propri cronologia e del proprio stato, gli oggetti principali dispongono delle proprietà seguenti:  
  
-   **CreatedTimestamp**  
  
-   **LastSchemaUpdate**  
  
-   **LastProcessed** (se appropriato)  
  
> [!NOTE]  
>  La classificazione di un oggetto come oggetto principale influisce sul modo in cui un'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] considera l'oggetto e sul modo in cui l'oggetto viene gestito nel linguaggio di definizione dell'oggetto. Tale classificazione non garantisce tuttavia che gli strumenti di gestione e di sviluppo di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] consentiranno la creazione, modifica o l'eliminazione indipendente di questi oggetti.  
  
 **Oggetti secondari**  
 Gli oggetti secondari possono essere creati, modificati o eliminati solo nell'ambito della creazione, la modifica o l'eliminazione dell'oggetto padre principale. Di seguito vengono riportati gli oggetti secondari:  
  
-   Gerarchie e livelli  
  
-   Attributi  
  
-   Misure  
  
-   Colonne del modello di data mining  
  
-   Comandi associati a un cubo  
  
-   Aggregations  
  
## <a name="object-expansion"></a>Espansione di oggetti  
 Il **ObjectExpansion** restrizione può essere utilizzata per controllare il livello di espansione dell'oggetto XML ASSL restituito dal server. Per questa restrizione sono disponibili le opzioni elencate nella tabella seguente.  
  
|Valore di enumerazione|È consentito per \<Alter >|Description|  
|-----------------------|---------------------------|-----------------|  
|*ReferenceOnly*|no|Restituisce solo il nome, l'ID e il timestamp per l'oggetto richiesto e per tutti gli oggetti principali contenuti in modo ricorsivo.|  
|*ObjectProperties*|sì|Espande l'oggetto richiesto e gli oggetti secondari contenuti, ma non restituisce alcun oggetto principale contenuto.|  
|*ExpandObject*|no|Come per *ObjectProperties*, ma restituisce inoltre il nome, l'ID e il timestamp per gli oggetti principali contenuti.|  
|*ExpandFull*|sì|Espande completamente l'oggetto richiesto e tutti gli oggetti contenuti in modo ricorsivo.|  
  
 Questa sezione di riferimento ASSL viene descritta la *ExpandFull* rappresentazione. Tutti gli altri **ObjectExpansion** livelli derivati da questo livello.  
  
## <a name="object-processing"></a>Elaborazione di oggetti  
 ASSL sono disponibili gli elementi di sola lettura o di proprietà (ad esempio, **LastProcessed**) che possono essere lette dal [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza, ma che vengono omessi quando gli script di comando vengono inviati all'istanza. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ignora senza preavviso valori modificati per gli elementi di sola lettura o errore.  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ignora inoltre le proprietà non appropriate o non rilevanti senza generare errori di convalida. L'elemento X deve essere presente ad esempio solo quando all'elemento Y è associato valore specifico. L'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ignora l'elemento X anziché convalidarlo rispetto al valore dell'elemento Y.  
  
  

