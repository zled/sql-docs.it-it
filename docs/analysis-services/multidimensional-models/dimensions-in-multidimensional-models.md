---
title: Dimensioni nei modelli multidimensionali | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OLAP [Analysis Services], dimensions
- dimensions [Analysis Services], about dimensions
- OLAP objects [Analysis Services], dimensions
ms.assetid: 2b62b05c-00fd-4e60-b77f-f707ba83a19b
caps.latest.revision: 46
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3e98c77a6b243bd5890aac6612db663377bd1bb3
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="dimensions-in-multidimensional-models"></a>Dimensioni nei modelli multidimensionali
  Una dimensione di database è una raccolta di oggetti correlati, denominati attributi, che è possibile utilizzare per offrire informazioni sui dati della tabella dei fatti in uno o più cubi. Gli attributi tipici di una dimensione dei prodotti possono ad esempio essere costituiti da nome del prodotto, categoria di prodotto, linea di prodotti, dimensioni del prodotto e prezzo del prodotto. Tali oggetti sono associati a una o più colonne di una o più tabelle di una vista origine dati Per impostazione predefinita, questi attributi sono visibili come gerarchie di attributo e possono essere utilizzati per acquisire familiarità con le tabelle dei fatti in un cubo. Possono inoltre essere organizzati in gerarchie definite dall'utente che definiscono percorsi di navigazione utili per l'esplorazione dei dati di un cubo.  
  
 I cubi contengono tutte le dimensioni su cui gli utenti basano le analisi dei dati della tabella dei datti. Un'istanza di una dimensione database in un cubo viene denominata dimensione del cubo e fa riferimento a uno o più gruppi di misure nel cubo. Una dimensione del database può essere utilizzata più volte in un cubo. Se una tabella dei fatti include più fatti temporali, ad esempio, è possibile definire una dimensione del cubo separata per facilitare l'analisi di ogni fatto temporale. È tuttavia necessaria una sola dimensione temporale del database e per supportare più dimensioni del cubo basate sul tempo è necessaria una sola tabella del database relazionale di tipo temporale.  
  
> [!NOTE]  
>  Per informazioni sui problemi di prestazioni correlati alla progettazione delle dimensioni, vedere la [Guida alle prestazioni di SQL Server 2008 R2 Analysis Services](http://go.microsoft.com/fwlink/?LinkId=306717).  
  
## <a name="defining-dimensions-attributes-and-hierarchies"></a>Definizione di dimensioni, attributi e gerarchie  
 Il metodo più semplice per definire dimensioni di database e cubi, attributi e gerarchie consiste nell'utilizzare la Creazione guidata cubo per creare dimensioni contemporaneamente alla definizione del cubo. Tramite la Creazione guidata cubo le dimensioni vengono create in base alle tabelle delle dimensioni trovate dalla procedura guidata o specificate dalla vista origine dati utilizzata per il cubo. Nella procedura guidata vengono quindi create le dimensioni del database e vengono aggiunte al nuovo cubo, creando così le dimensioni del cubo.  
  
 Quando si crea un cubo, è inoltre possibile aggiungere al nuovo cubo qualsiasi dimensione già esistente nel database. Tali dimensioni possono essere state definite in precedenza per un altro cubo oppure tramite la Creazione guidata dimensione. Dopo aver definito una dimensione del database, è possibile modificare e configurare la dimensione del database in Progettazione dimensioni. È inoltre possibile personalizzare la dimensione del cubo, entro certi limiti, in Progettazione cubi.  
  
> [!NOTE]  
>  È inoltre possibile progettare e configurare dimensioni, attributi e gerarchie a livello di programmazione utilizzando XMLA o AMO (Analysis Management Objects). Per altre informazioni, vedere [Analysis Services Scripting Language &#40;ASSL for XMLA&#41;](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md) (Linguaggio di script di Analysis Services &#40;ASSL per XMLA&#41;) e [Sviluppo con AMO &#40;Analysis Management Objects&#41;](../../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md).  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 Gli argomenti disponibili in questa sezione sono descritti nella tabella seguente.  
  
 [Definire le dimensioni del database](../../analysis-services/multidimensional-models/define-database-dimensions.md)  
 Descrive come modificare e configurare una dimensione di database tramite Progettazione dimensioni.  
  
 [Riferimento alle proprietà degli attributi delle dimensioni](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
 Descrive come definire, modificare e configurare un attributo di una dimensione di database tramite Progettazione dimensioni.  
  
 [Definire relazioni tra attributi](../../analysis-services/multidimensional-models/attribute-relationships-define.md)  
 Descrive come definire, modificare e configurare una relazione tra attributi tramite Progettazione dimensioni.  
  
 [Creare gerarchie definite dall'utente](../../analysis-services/multidimensional-models/user-defined-hierarchies-create.md)  
 Descrive come definire, modificare e configurare un gerarchia definita dall'utente degli attributi di una dimensione tramite Progettazione dimensioni.  
  
 [Utilizzare la Configurazione guidata funzionalità di Business Intelligence per migliorare le dimensioni](http://msdn.microsoft.com/library/12d995d1-75ca-4890-bf4b-a2656910b8d0)  
 Descrive come ottimizzare una dimensione di database mediante la Configurazione guidata funzionalità di Business Intelligence.  
  
## <a name="see-also"></a>Vedere anche  
 [Cubi nei modelli multidimensionali](../../analysis-services/multidimensional-models/cubes-in-multidimensional-models.md)  
  
  
