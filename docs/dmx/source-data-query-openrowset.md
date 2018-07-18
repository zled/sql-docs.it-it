---
title: OPENROWSET (DMX) | Documenti Microsoft
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 43431be3f68bc7146d9e5a6cc137100ec384c960
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/07/2018
ms.locfileid: "34842114"
---
# <a name="ltsource-data-querygt---openrowset"></a>&lt;query di dati di origine&gt; -OPENROWSET
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Sostituisce la query sui dati dell'origine con una query su un provider esterno. Le istruzioni INSERT, SELECT FROM PREDICTION JOIN e SELECT FROM NATURAL PREDICTION JOIN supportano **OPENROWSET**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
OPENROWSET(provider_name,provider_string,query_syntax)  
```  
  
## <a name="arguments"></a>Argomenti  
 *provider_name*  
 Nome di un provider OLE DB.  
  
 *provider_string*  
 Stringa di connessione OLE DB per il provider specificato.  
  
 *query_syntax*  
 Sintassi di una query che restituisce un set di righe.  
  
## <a name="remarks"></a>Remarks  
 Il provider di data mining stabilisce una connessione all'oggetto di origine dati utilizzando *provider_name* e *provider_string,* e verrà eseguita la query specificata in *query_syntax* per recuperare il set di righe dall'origine dei dati.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente può essere utilizzato in un'istruzione PREDICTION JOIN per recuperare dati dal database [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] tramite un'istruzione [!INCLUDE[tsql](../includes/tsql-md.md)] di tipo SELECT.  
  
```  
OPENROWSET  
(  
'SQLOLEDB.1',  
'Provider=SQLOLEDB.1;Integrated Security=SSPI;Persist Security     Info=False;Initial Catalog=AdventureWorksDW2012;Data Source=localhost',  
'SELECT TOP 1000 * FROM vTargetMail'  
)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [&#60;query di origine dati&#62;](../dmx/source-data-query.md)   
 [Estensioni Data Mining &#40;DMX&#41; istruzioni Data Manipulation](../dmx/dmx-statements-data-manipulation.md)   
 [Guida di riferimento alle istruzioni DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
