---
title: Utilizzo di variabili e parametri (MDX) | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: mdx
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 039668b719a2c6c715139682496117b8239425aa
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="using-variables-and-parameters-mdx"></a>Utilizzo di variabili e parametri (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] è possibile creare istruzioni MDX (Multidimensional Expressions) parametrizzate. Un'istruzione parametrizzata consente di creare istruzioni generiche che possono essere personalizzate in fase di esecuzione.  
  
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
 [Nozioni fondamentali sullo Scripting MDX & #40; Analysis Services & #41;](../../../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)  
  
  
