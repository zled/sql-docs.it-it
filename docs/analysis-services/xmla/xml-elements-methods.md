---
title: Metodi (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 15f930695e13d824e70da748dad20cf574e9bc38
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2018
ms.locfileid: "34579143"
---
# <a name="xml-elements---methods"></a>Elementi XML, metodi
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Il protocollo XML for Analysis (XMLA) utilizza due metodi, **Discover** e **Execute**, per fornire una modalità standard per le applicazioni accedere alle informazioni in un'istanza di Analysis Services. Poiché questi metodi vengono richiamati utilizzando il protocollo SOAP (Simple Object Access Protocol), accettano input e creano output in formato XML. Analysis Services implementa entrambi i metodi, in conformità con la specifica XML for Analysis 1.1.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 Gli argomenti seguenti vengono descritti i metodi XMLA implementati da Analysis Services.  
  
|Metodo|Description|  
|------------|-----------------|  
|[Metodo Discover &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-methods-discover.md)|Recupera informazioni, ad esempio l'elenco dei database disponibili o i dettagli su un oggetto specifico da un'istanza di Analysis Services. I dati recuperati con il metodo **Discover** dipendono dai valori dei parametri passati al metodo stesso.|  
|[Eseguire il metodo &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-methods-execute.md)|Invia comandi XMLA a un'istanza di Analysis Services. Include richieste che comportano il trasferimento dei dati, ad esempio recuperando o aggiornando dati nel server.|  
  
## <a name="see-also"></a>Vedere anche
 [Elementi XML &#40;XMLA&#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [Tipi di dati XML &#40;XMLA&#41;](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)   
 [Elementi XML &#40;XMLA&#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)  
  
  
