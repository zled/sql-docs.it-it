---
title: Elemento Capability (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile"
ms.openlocfilehash: 92e9fa83f19384276abd7401fd809a56187c75b7
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="capability-element-xmla"></a>Elemento Capability (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Indica il supporto per una funzionalità del protocollo nell'elemento padre [ProtocolCapabilities](../../../analysis-services/xmla/xml-elements-headers/protocolcapabilities-element-xmla.md) elemento intestazione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ProtocolCapabilities>  
   ...  
   <Capability>...</Capability>  
   ...  
</ProtocolCapabilities>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[ProtocolCapabilities](../../../analysis-services/xmla/xml-elements-headers/protocolcapabilities-element-xmla.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il **funzionalità** elemento indica che una particolare funzionalità, ad esempio binaria o la compressione, è supportata dall'applicazione che è incluso il **ProtocolCapabilities** elemento intestazione di Intestazione SOAP della richiesta SOAP o dall'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] inclusi il **ProtocolCapabilities** elemento dell'intestazione nell'intestazione SOAP della risposta SOAP. Il valore di **funzionalità** elemento è il nome della funzionalità devono essere supportati.  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] supporta le funzionalità elencate nella tabella seguente.  
  
|Nome della funzionalità|Descrizione|  
|---------------------|-----------------|  
|sx|Supporto di XML binario|  
|xpress|Supporto della compressione|  
  
## <a name="see-also"></a>Vedere anche  
 [La gestione delle connessioni e sessioni & #40; XMLA & #41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Proprietà & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
