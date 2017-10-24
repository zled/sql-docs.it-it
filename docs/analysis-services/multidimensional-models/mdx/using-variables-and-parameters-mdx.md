---
title: Utilizzo di variabili e parametri (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
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
- parameters [MDX]
- queries [MDX], variables
- queries [MDX], parameters
- variables [MDX]
ms.assetid: a4754d16-d9c4-49f6-9be0-392180b912e4
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 5ac634400b85e49cdaf9f57e683cc13fe781ed2b
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="using-variables-and-parameters-mdx"></a>Utilizzo di variabili e parametri (MDX)
  In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]è possibile creare istruzioni MDX (Multidimensional Expressions) parametrizzate. Un'istruzione parametrizzata consente di creare istruzioni generiche che possono essere personalizzate in fase di esecuzione.  
  
 Durante la creazione di un'istruzione parametrizzata, il nome del parametro viene identificato aggiungendovi come prefisso il simbolo chiocciola (@). Ad esempio, @Year sarebbe un nome di parametro valido  
  
 MDX supporta i parametri solo per valori letterali o scalari. Per creare un parametro che faccia riferimento a un membro, a un set o a una tupla, è possibile usare una funzione quale [StrToMember](../../../mdx/strtomember-mdx.md) o [StrToSet](../../../mdx/strtoset-mdx.md).  
  
 Il codice XML seguente, ad esempio Analysis (XMLA), il @CountryName parametro conterrà il paese per il cliente che vengono recuperati dati:  
  
```  
<Envelope xmlns="http://schemas.xmlsoap.org/soap/envelope/">  
  <Body>  
    <Execute xmlns="urn:schemas-microsoft-com:xml-analysis">  
      <Command>  
        <Statement>  
select [Measures].members on 0,   
       Filter(Customer.[Customer Geography].Country.members,   
              Customer.[Customer Geography].CurrentMember.Name =  
              @CountryName) on 1  
from [Adventure Works]  
</Statement>  
      </Command>  
      <Properties />  
      <Parameters>  
        <Parameter>  
          <Name>CountryName</Name>  
          <Value>'United Kingdom'</Value>  
        </Parameter>  
      </Parameters>  
    </Execute>  
  </Body>  
</Envelope>  
```  
  
 Per usare questa funzionalità con OLE DB, è necessario usare l'interfaccia **ICommandWithParameters** . Per usare questa funzionalità con ADOMD.Net, è necessario usare l'interfaccia **AdomdCommand.Parameters** .  
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni fondamentali sullo scripting MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)  
  
  

