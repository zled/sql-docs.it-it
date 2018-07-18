---
title: OPENROWSET (DMX) | Documenti Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- OPENROWSET
dev_langs:
- DMX
helpviewer_keywords:
- OPENROWSET statement
ms.assetid: 8c8b61b4-2bf6-46c7-8976-51484004dc22
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: f7ed5b65bf1f8ecf01d6b01939311de562eb85b3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
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
  
## <a name="remarks"></a>Osservazioni  
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
 [Data Mining Extensions & #40; DMX & #41; Riferimento istruzione](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
