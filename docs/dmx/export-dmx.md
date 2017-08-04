---
title: ESPORTAZIONE (DMX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- EXPORT
dev_langs:
- DMX
helpviewer_keywords:
- exporting mining models
- exporting mining structures
- mining structures [DMX], exporting
- EXPORT statement
ms.assetid: 97617071-e560-4080-81af-a80276fc0823
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: bfc3e8344d1c6967185979c0970be6d49b572500
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="export-dmx"></a>EXPORT (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Estrae dal server un oggetto modello o struttura di data mining e lo salva in un file con estensione abf (Analysis Services Backup File).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
EXPORT <object type> <object name>[, <object name>] [<object type> <object name>[, <object name] ] TO <filename> [WITH DEPENDENCIES]  
```  
  
## <a name="arguments"></a>Argomenti  
 *tipo di oggetto*  
 Facoltativo tipo di oggetto da esportare (modello di data mining o struttura di data mining).  
  
 *nome dell'oggetto*  
 Facoltativa. Nome dell'oggetto da esportare.  
  
 *nome file*  
 Nome e percorso del file da esportare, sotto forma di stringa.  
  
## <a name="remarks"></a>Osservazioni  
 Se l'istruzione specifica un modello di data mining, il file risultante conterrà anche la struttura di data mining associata. Se l'istruzione specifica **WITH DEPENDENCIES**, tutti gli oggetti necessari per elaborare l'oggetto (ad esempio, l'origine dati e vista origine dati) sono inclusi nel file con estensione ABF.  
  
 È necessario essere un database o l'amministratore del server per esportare o importare oggetti da un [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.  
  
## <a name="export-mining-structure-example"></a>Esempio di esportazione di una struttura di data mining  
 Nell'esempio seguente vengono esportati in un percorso di file specifico il modello di data mining Association e le strutture Targeted Mailing e Forecasting. Poiché il modello Association fa parte della struttura di data mining Market Basket, nell'esempio viene esportata anche tale struttura. Altri modelli di data mining che potrebbero esistere come parte della struttura di data mining Market Basket non verrà esportati perché il modello Association viene esportato utilizzando **modello di data MINING**, non **struttura di data MINING**.  
  
```  
EXPORT MINING STRUCTURE [Targeted Mailing], [Forecasting] MINING MODEL Association TO 'C:\TM_NEW.abf'  
```  
  
## <a name="export-mining-model-example"></a>Esempio di esportazione di un modello di data mining  
 Nell'esempio seguente il modello di data mining Association viene esportato in un percorso di file specificato. Poiché l'istruzione specifica **WITH DEPENDENCIES**, l'origine dati e oggetti vista origine dati sono incluse anche nel file con estensione ABF.  
  
```  
EXPORT MINING MODEL [Association] TO 'C:\Association_NEW.abf' WITH DEPENDENCIES  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Data Mining Extensions &#40; DMX &#41; Istruzioni di definizione dei dati](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40; DMX &#41; Istruzioni di manipolazione dei dati](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento istruzione](../dmx/data-mining-extensions-dmx-statements.md)   
 [DMX IMPORTAZIONE &#40; &#41;](../dmx/import-dmx.md)   
 [Esportare e importare oggetti di Data Mining](../analysis-services/data-mining/export-and-import-data-mining-objects.md)  
  
  

