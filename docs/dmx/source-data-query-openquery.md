---
title: OPENQUERY (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 895c28f0989debb899c1e01c80a18483d3cda5a1
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/26/2018
ms.locfileid: "50147816"
---
# <a name="ltsource-data-querygt---openquery"></a>&lt;query sull'origine dati&gt; -OPENQUERY
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Sostituisce la query sui dati dell'origine con una query su un'origine dei dati esistente. Le istruzioni INSERT, SELECT FROM PREDICTION JOIN e SELECT FROM NATURAL PREDICTION JOIN supportano **OPENQUERY**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
OPENQUERY(<named datasource>, <query syntax>)  
```  
  
## <a name="arguments"></a>Argomenti  
 *origine dati denominata*  
 Un'origine dati che sia disponibile il [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.  
  
 *sintassi di query*  
 Sintassi di una query che restituisce un set di righe.  
  
## <a name="remarks"></a>Note  
 **La funzione OPENQUERY** fornisce un modo più sicuro per accedere ai dati esterni tramite il supporto delle autorizzazioni dell'origine dati. Poiché la stringa di connessione viene archiviata nell'origine dati, gli amministratori possono utilizzare le proprietà dell'origine dati per gestire l'accesso ai dati. Per altre informazioni sulle origini dati, vedere [origini dati supportate &#40;SSAS - multidimensionale&#41;](../analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional.md).  
  
 È possibile ottenere un elenco delle origini dati che sono disponibili in un server richiedendo la **MDSCHEMA_INPUT_DATASOURCES** set di righe dello schema. Per altre informazioni sull'uso **MDSCHEMA_INPUT_DATASOURCES**, vedere [set di righe MDSCHEMA_INPUT_DATASOURCES](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-input-datasources-rowset).  
  
 È inoltre possibile restituire un elenco di origini dati del database di Analysis Services corrente mediante la seguente query DMX:  
  
 `SELECT * FROM $system.MDSCHEMA_INPUT_DATASOURCES`  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente usa l'origine dati MyDS già definito nel [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database per creare una connessione al [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database ed eseguire una query il **vTargetMail** visualizzazione.  
  
```  
OPENQUERY (MyDS,'SELECT TOP 1000 * FROM vTargetMail')  
```  
  
## <a name="see-also"></a>Vedere anche  
 [&#60;query sull'origine dati&#62;](../dmx/source-data-query.md)   
 [Le estensioni di Data Mining di dati &#40;DMX&#41; istruzioni di manipolazione dei dati](../dmx/dmx-statements-data-manipulation.md)   
 [Guida di riferimento alle istruzioni DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
