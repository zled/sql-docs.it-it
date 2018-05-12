---
title: Algoritmi plug-in | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 571fa03bd9bce4154b7cc9f4714e7bee9dcb5834
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="plugin-algorithms"></a>Algoritmi plug-in
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Oltre agli algoritmi disponibili in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], è possibile usare molti altri algoritmi per il data mining. Di conseguenza, in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] è disponibile un meccanismo per l'inserimento di algoritmi creati da terze parti. Se gli algoritmi rispettano determinati standard, è possibile utilizzarli in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] nello stesso modo in cui si utilizzano gli algoritmi [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Gli algoritmi plug-in offrono tutte le potenzialità degli algoritmi disponibili in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
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
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]Usa le interfacce COM per comunicare con gli algoritmi plug-in. Sebbene gli algoritmi plug-in usati debbano supportare la specifica [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB per il data mining, non è necessario che supportino tutte le opzioni di data mining presenti nella specifica. Per determinare le funzionalità di un algoritmo, è possibile usare il set di righe dello schema [MINING_SERVICES](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-services-rowset.md) . In questo set di righe dello schema sono elencate le opzioni di supporto del data mining per ogni provider di algoritmi plug-in.  
  
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
 [Algoritmi di Data Mining & #40; Analysis Services - Data Mining & #41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Set di righe DMSCHEMA_MINING_SERVICES](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-services-rowset.md)  
  
  
