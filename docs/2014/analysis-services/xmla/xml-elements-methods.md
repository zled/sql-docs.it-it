---
title: Metodi (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
topic_type:
- apiref
- apinav
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#
helpviewer_keywords:
- methods [XML for Analysis]
- XML for Analysis, methods
- XMLA, methods
ms.assetid: c6768dd4-ca06-4a85-93b7-5fd5700886ad
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c1e073eae6637b726a473ea7bf95057ed1548982
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48088591"
---
# <a name="methods-xmla"></a>Metodi (XMLA)
  Il protocollo XML for Analysis (XMLA) utilizza due metodi, `Discover` e `Execute`, per offrire un modo standard per le applicazioni accedere alle informazioni in un'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Poiché questi metodi vengono richiamati utilizzando il protocollo SOAP (Simple Object Access Protocol), accettano input e creano output in formato XML. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] implementa entrambi i metodi, in conformità alla specifica XML for Analysis 1.1.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 Negli argomenti seguenti vengono descritti i metodi XMLA implementati da [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
|Metodo|Description|  
|------------|-----------------|  
|[Metodo Discover &#40;XMLA&#41;](xml-elements-methods-discover.md)|Recupera informazioni, ad esempio l'elenco dei database disponibili o i dettagli su un oggetto specifico, da un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. I dati recuperati con il metodo `Discover` dipendono dai valori dei parametri passati al metodo stesso.|  
|[Eseguire il metodo &#40;XMLA&#41;](xml-elements-methods-execute.md)|Invia comandi XMLA a un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Include richieste che comportano il trasferimento dei dati, ad esempio recuperando o aggiornando dati nel server.|  
  
## <a name="see-also"></a>Vedere anche  
 [Elementi XML &#40;XMLA&#41;](../dev-guide/xml-elements-xmla.md)   
 [Tipi di dati XML &#40;XMLA&#41;](xml-data-types/xml-data-types-xmla.md)   
 [Elementi XML &#40;XMLA&#41;](../dev-guide/xml-elements-xmla.md)  
  
  
