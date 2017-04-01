---
title: "Definire l&#39;ordinamento di una dimensione | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "OrderBy - proprietà"
  - "dimensioni [Analysis Services], ordinamento"
  - "miglioramenti di Business Intelligence [Analysis Services], ordinamento"
  - "dimensioni [Analysis Services], miglioramenti di Business Intelligence"
  - "ordinamento di dimensioni[Analysis Services]"
  - "OrderByAttributeID - proprietà"
ms.assetid: c42fbd58-244d-4e0a-b715-6f919cbc3ad9
caps.latest.revision: 31
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Definire l&#39;ordinamento di una dimensione
  L'aggiunta della funzionalità avanzata di ordinamento degli attributi a un cubo o una dimensione consente di specificare come verranno ordinati i membri di un attributo. I membri possono essere ordinati in base al nome o alla chiave dell'attributo oppure in base al nome o alla chiave di un altro attributo (tramite una relazione tra attributi). Per impostazione predefinita, i membri vengono ordinati in base al nome. Questa funzionalità avanzata modifica l'impostazione delle proprietà **OrderBy** e **OrderByAttributeID** degli attributi in una dimensione.  
  
 Per aggiungere la funzionalità di ordinamento degli attributi, usare Configurazione guidata funzionalità di Business Intelligence e quindi selezionare l'opzione **Impostazione ordinamento attributi**nella pagina **Scelta funzionalità avanzata**. Questa procedura guidata consente di eseguire in modo semplificato i passaggi relativi alla selezione di una dimensione alla quale si desidera applicare l'ordinamento degli attributi e all'impostazione della modalità di ordinamento degli attributi per la dimensione selezionata.  
  
## Selezione di una dimensione  
 Nella prima pagina **Impostazione ordinamento attributi** della procedura guidata specificare la dimensione alla quale si desidera applicare l'ordinamento degli attributi. L'aggiunta della funzionalità avanzata dell'ordinamento degli attributi alla dimensione selezionata implica modifiche alla dimensione. Tali modifiche verranno ereditate da tutti i cubi che includono la dimensione selezionata.  
  
## Impostazione dell'ordinamento  
 Nella seconda pagina **Impostazione ordinamento attributi** della procedura guidata specificare la modalità di ordinamento di tutti gli attributi nella dimensione.  
  
 Nella colonna **Attributo di ordinamento** è possibile modificare l'attributo usato per l'ordinamento. Se l'attributo che si desidera usare per ordinare i membri non è incluso nell'elenco, scorrere verso il basso e selezionare **\<Nuovo attributo...>** per aprire la finestra di dialogo **Seleziona colonna**, dove è possibile selezionare una colonna in una tabella delle dimensioni. La selezione di una colonna tramite la finestra di dialogo **Seleziona colonna** consente di creare un attributo aggiuntivo in base al quale ordinare i membri di un attributo.  
  
 Nella colonna **Criteri** è quindi possibile selezionare se ordinare i membri dell'attributo in base alla **chiave** oppure al **nome**.  
  
  