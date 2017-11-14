---
title: Metodi (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#
helpviewer_keywords:
- methods [XML for Analysis]
- XML for Analysis, methods
- XMLA, methods
ms.assetid: c6768dd4-ca06-4a85-93b7-5fd5700886ad
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d7e9b7f9ee860b8ff65664d15b17ca9ebe182e15
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="xml-elements---methods"></a>Elementi XML, metodi
  Il protocollo XML for Analysis (XMLA) utilizza due metodi, **Discover** e **Execute**, per offrire un modo standard per le applicazioni accedere alle informazioni in un'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Poiché questi metodi vengono richiamati utilizzando il protocollo SOAP (Simple Object Access Protocol), accettano input e creano output in formato XML. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] implementa entrambi i metodi, in conformità alla specifica XML for Analysis 1.1.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 Negli argomenti seguenti vengono descritti i metodi XMLA implementati da [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
|Metodo|Description|  
|------------|-----------------|  
|[Individuare metodo &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-methods-discover.md)|Recupera informazioni, ad esempio l'elenco dei database disponibili o i dettagli su un oggetto specifico, da un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. I dati recuperati con il metodo **Discover** dipendono dai valori dei parametri passati al metodo stesso.|  
|[Esegui metodo &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-methods-execute.md)|Invia comandi XMLA a un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Include richieste che comportano il trasferimento dei dati, ad esempio recuperando o aggiornando dati nel server.|  
  
## <a name="see-also"></a>Vedere anche  
 [Gli elementi XML &#40; XMLA &#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [Tipi di dati XML &#40; XMLA &#41;](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)   
 [Gli elementi XML &#40; XMLA &#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)  
  
  

