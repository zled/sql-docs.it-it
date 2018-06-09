---
title: KPIValue (MDX) | Documenti Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: baa1b95e9eda32bc20e08b61ddd38c130a373050
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740400"
---
# <a name="kpivalue-mdx"></a>KPIValue (MDX)


  Restituisce il membro da cui viene calcolato il valore dell'indicatore di prestazioni chiave (KPI) specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
KPIValue(KPI_Name)  
```  
  
## <a name="arguments"></a>Argomenti  
 *Nome_kpi*  
 Espressione stringa valida che specifica il nome dell'indicatore di prestazioni chiave (KPI).  
  
## <a name="remarks"></a>Remarks  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente vengono restituiti valore, obiettivo, stato e tendenza dell'indicatore di prestazioni chiave (KPI) relativo alla misura del ricavo del canale per i discendenti di tre membri della gerarchia dell'attributo Fiscal Year.  
  
```  
SELECT  
   { KPIValue("Channel Revenue"),   
     KPIGoal("Channel Revenue"),  
     KPIStatus("Channel Revenue"),   
     KPITrend("Channel Revenue")  
   } ON Columns,  
Descendants  
   ( { [Date].[Fiscal].[Fiscal Year].&[2002],  
       [Date].[Fiscal].[Fiscal Year].&[2003],  
       [Date].[Fiscal].[Fiscal Year].&[2004]   
     }, [Date].[Fiscal].[Fiscal Quarter]  
   ) ON Rows  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
