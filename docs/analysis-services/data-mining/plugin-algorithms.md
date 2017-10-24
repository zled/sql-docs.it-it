---
title: Algoritmi plug-in | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- third-party algorithms [Analysis Services]
- algorithms [data mining], creating
- plugin algorithms [Analysis Services]
ms.assetid: fe364ddc-576e-42fc-9ced-baa399992f92
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 66fad2d8974e832925ab67174f2c635b8f5fbf37
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="plugin-algorithms"></a>Algoritmi plug-in
  Oltre agli algoritmi disponibili in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , è possibile usare molti altri algoritmi per il data mining. Di conseguenza, in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] è disponibile un meccanismo per l'inserimento di algoritmi creati da terze parti. Se gli algoritmi rispettano determinati standard, è possibile utilizzarli in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] nello stesso modo in cui si utilizzano gli algoritmi [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Gli algoritmi plug-in offrono tutte le potenzialità degli algoritmi disponibili in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Per una descrizione completa delle interfacce usate in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] per comunicare con gli algoritmi plug-in, vedere gli esempi relativi alla creazione di un algoritmo personalizzato e di un visualizzatore del modello personalizzato pubblicati sul sito Web [CodePlex](http://go.microsoft.com/fwlink/?LinkID=87843) .  
  
## <a name="algorithm-requirements"></a>Requisiti per gli algoritmi  
 Per inserire un algoritmo in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], è necessario implementare le interfacce COM seguenti:  
  
 **IDMAlgorithm**  
 Implementa un algoritmo che produce modelli e implementa le operazioni di stima dei modelli risultanti.  
  
 **IDMAlgorithmNavigation**  
 Consente ai browser di accedere al contenuto dei modelli.  
  
 **IDMPersist**  
 Consente di salvare e caricare in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]i modelli di cui l'algoritmo esegue il training.  
  
 **IDMAlgorithmMetadata**  
 Descrive le funzionalità e i parametri di input dell'algoritmo.  
  
 **IDMAlgorithmFactory**  
 Crea istanze degli oggetti che implementano l'interfaccia dell'algoritmo e consente ad [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] di accedere all'interfaccia di metadati dell'algoritmo.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Per comunicare con gli algoritmi plug-in vengono usate le interfacce COM. Sebbene gli algoritmi plug-in usati debbano supportare la specifica [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB per il data mining, non è necessario che supportino tutte le opzioni di data mining presenti nella specifica. Per determinare le funzionalità di un algoritmo, è possibile usare il set di righe dello schema [MINING_SERVICES](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-services-rowset.md) . In questo set di righe dello schema sono elencate le opzioni di supporto del data mining per ogni provider di algoritmi plug-in.  
  
 Prima di usare i nuovi algoritmi con [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], è necessario registrarli. Per registrare un algoritmo, includere le informazioni seguenti nel file con estensione ini dell'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in cui si desidera includere gli algoritmi:  
  
-   Nome dell'algoritmo  
  
-   ProgID (facoltativo e incluso solo per gli algoritmi plug-in)  
  
-   Flag che indica se l'algoritmo è attivato o no  
  
 Nell'esempio di codice seguente viene illustrato come registrare un nuovo algoritmo:  
  
 `<ConfigurationSettings>`  
  
 `...`  
  
 `<DataMining>`  
  
 `...`  
  
 `<Algorithms>`  
  
 `...`  
  
 `<Sample_Plugin_Algorithm>`  
  
 `<Enabled>1</Enabled>`  
  
 `<ProgID>Microsoft.DataMining.SamplePlugInAlgorithm.Factory</ProgID>`  
  
 `</Sample_PlugIn_Algorithm>`  
  
 `...`  
  
 `</Algorithms>`  
  
 `...`  
  
 `</DataMining>`  
  
 `...`  
  
 `</ConfigurationSettings>`  
  
## <a name="see-also"></a>Vedere anche  
 [Algoritmi di data mining &#40;Analysis Services - Data mining&#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Set di righe DMSCHEMA_MINING_SERVICES](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-services-rowset.md)  
  
  

