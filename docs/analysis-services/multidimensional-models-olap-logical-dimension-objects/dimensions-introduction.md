---
title: Introduzione alle dimensioni (Analysis Services - dati multidimensionali) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- dimensions [Analysis Services], about dimensions
- storage [Analysis Services], dimensions
- dimensions [Analysis Services], examples
- storing data [Analysis Services], dimensions
- storage [Analysis Services]
ms.assetid: ab170fdd-4144-42db-9497-690b9189fc25
caps.latest.revision: "41"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 726344198c74d36a0d31368980f305c1426f1607
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="dimensions---introduction"></a>Dimensioni: introduzione
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Tutti i Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] le dimensioni sono gruppi di attributi basati su colonne di tabelle o viste in una vista origine dati. Le dimensioni esistono indipendentemente da un cubo, possono essere utilizzate in più cubi, possono essere utilizzate più volte in un singolo cubo e possono essere collegate tra istanze di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Una dimensione indipendente da un cubo viene denominata dimensione del database e un'istanza di una dimensione del database all'interno di un cubo viene denominata dimensione del cubo.  
  
## <a name="dimension-based-on-a-star-schema-design"></a>Dimensione basata su una progettazione con schema star  
 La struttura di una dimensione è per lo più determinata dalla struttura della tabella della dimensione o delle tabelle delle dimensioni sottostanti. La struttura più semplice è detta schema star, dove ogni dimensione è basata su un'unica tabella delle dimensioni direttamente collegata alla tabella dei fatti tramite una relazione chiave primaria/chiave esterna.  
  
 Nel diagramma seguente viene illustrata una sottosezione del [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)] database di esempio, in cui il **FactResellerSales** tabella dei fatti è correlata a due tabelle delle dimensioni **DimReseller** e **DimPromotion**. Il **ResellerKey** colonna il **FactResellerSales** tabella dei fatti definisce una relazione di chiave esterna per il **ResellerKey** colonna chiave primaria il  **DimReseller** tabella della dimensione. Analogamente, il **PromotionKey** colonna il **FactResellerSales** tabella dei fatti definisce una relazione di chiave esterna per il **PromotionKey** colonna chiave primaria di  **DimPromotion** tabella della dimensione.  
  
 ![Schema logico per la relazione di tipo fatti](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/media/dimfactrelationship.gif "schema logico per la relazione di tipo fatti")  
  
## <a name="dimension-based-on-a-snowflake-schema-design"></a>Dimensione basata su una progettazione con schema snowflake  
 Spesso è necessaria una struttura più complessa in quanto per definire la dimensione sono necessarie informazioni di più tabelle. In questa struttura, denominata schema snowflake, ogni dimensione è basata su attributi di colonne di più tabelle collegate reciprocamente e alla tabella dei fatti tramite relazioni tra chiave primaria e chiave esterna. Ad esempio, il diagramma seguente illustra le tabelle necessarie per descrivere completamente la dimensione Product nel **AdventureWorksDW** progetto di esempio:  
  
 ![Tabelle per la dimensione Product di AdventureWorksAS](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/media/dimproduct.gif "tabelle per la dimensione Product di AdventureWorksAS")  
  
 Per descrivere completamente un prodotto, la categoria e la sottocategoria del prodotto devono essere incluse nella dimensione Product. Tuttavia, tali informazioni non si trovano direttamente nella tabella principale per il **DimProduct** dimensione. Una relazione di chiave esterna da **DimProduct** a **DimProductSubcategory**, che a sua volta ha una relazione di chiave esterna per il **DimProductCategory** tabella, rende è possibile includere le informazioni per le categorie di prodotti e le sottocategorie nella dimensione Product.  
  
## <a name="snowflake-schema-versus-reference-relationship"></a>Confronto tra schema snowflake e relazione di tipo Riferimento  
 È talvolta possibile scegliere tra l'utilizzo di uno schema snowflake per definire gli attributi in una dimensione da più tabelle o l'utilizzo di due dimensioni separate definendo una relazione di tipo Riferimento tra di esse. Nella figura seguente viene illustrato uno scenario di questo tipo.  
  
 ![Schema logico per la dimensione di riferimento di esempio](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/media/dimindirect.gif "schema logico per la dimensione di riferimento di esempio")  
  
 Nel diagramma precedente, il **FactResellerSales** tabella dei fatti non dispone di una relazione di chiave esterna con la **DimGeography** tabella della dimensione. Tuttavia, il **FactResellerSales** tabella dei fatti ha una relazione di chiave esterna con la **DimReseller** tabella della dimensione, che a sua volta ha una relazione di chiave esterna con la  **DimGeography** tabella della dimensione. Per definire una dimensione Reseller contenente informazioni geografiche per ogni rivenditore, è necessario recuperare gli attributi del **DimGeography** e **DimReseller** tabelle delle dimensioni. In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], tuttavia, è possibile ottenere lo stesso risultato creando due dimensioni separate e collegandole in un gruppo di misure definendo una relazione di tipo Riferimento tra le due dimensioni. Per ulteriori informazioni sulle relazioni tra dimensioni di riferimento, vedere [relazioni tra dimensioni](../../analysis-services/multidimensional-models-olap-logical-cube-objects/dimension-relationships.md).  
  
 Un vantaggio dell'utilizzo di relazioni di tipo Riferimento in questo scenario consiste nella possibilità di creare un'unica dimensione Geography e quindi di creare più dimensioni del cubo basate sulla dimensione Geography, senza che sia necessario ulteriore spazio di archiviazione. È ad esempio possibile collegare una delle dimensioni Geography del cubo a una dimensione Reseller e un'altra delle dimensioni Geography del cubo a una dimensione Customer. **Argomenti correlati:**[relazioni tra dimensioni](../../analysis-services/multidimensional-models-olap-logical-cube-objects/dimension-relationships.md), [definire una relazione di tipo riferimento e le proprietà della relazione di riferimento](../../analysis-services/multidimensional-models/define-a-referenced-relationship-and-referenced-relationship-properties.md)  
  
## <a name="processing-a-dimension"></a>Elaborazione di una dimensione  
 Dopo avere creato una dimensione, per poter visualizzare i membri degli attributi e delle gerarchie della dimensione, è necessario elaborare la dimensione stessa. Dopo la modifica della struttura di una dimensione o l'aggiornamento delle informazioni nelle tabelle sottostanti, è necessario elaborare di nuovo la dimensione per poter visualizzare le modifiche. Quando si elabora una dimensione dopo modifiche strutturali, è inoltre necessario elaborare qualsiasi cubo in cui la dimensione è inclusa. In caso contrario, il cubo non sarà visualizzabile.  
  
## <a name="security"></a>Security  
 Tutti gli oggetti subordinati di una dimensione, inclusi membri, livelli e gerarchie, vengono protetti tramite ruoli in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. La sicurezza delle dimensioni può essere applicata a tutti i cubi nel database che utilizzano la dimensione oppure a un solo cubo specifico. Per ulteriori informazioni sulla sicurezza delle dimensioni, vedere [concedere le autorizzazioni per una dimensione &#40; Analysis Services &#41; ](../../analysis-services/multidimensional-models/grant-permissions-on-a-dimension-analysis-services.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Archiviazione della dimensione](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-storage.md)   
 [Traduzioni delle dimensioni](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimension-translations.md)   
 [Dimensioni abilitate per la scrittura](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  
