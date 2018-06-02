---
title: XML for Analysis (XMLA) conformità | Documenti Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b618fdd8cca3faed72afb0276f18cd928a3f31f7
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2018
ms.locfileid: "34576883"
---
# <a name="xml-for-analysis-xmla-compliance"></a>XML for Analysis (XMLA) conformità
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]  

  La specifica XML for Analysis 1.1 descrive uno standard aperto che supporta l’accesso a origini dati che risiedono sul World Wide Web. In questo argomento illustra in dettaglio il livello di conformità con la specifica XML for Analysis 1.1 supportata da Azure Analysis Services e SQL Server Analysis Services.  
  
## <a name="compliant-items"></a>Elementi conformi  
Analysis Services è conforme a tutti gli elementi obbligatori elencati nella specifica XML for Analysis 1.1. Inoltre, Analysis Services implementa l'elemento facoltativo seguente descritto nella specifica XML for Analysis 1.1.  
  
|Elemento|Specifica|Implementazione|  
|----------|-------------------|--------------------|  
|Supporto sessione|Gli elementi dell'intestazione SOAP elencati nella sezione "Supporto per Statefulness in XML for Analysis" della specifica XML for Analysis 1.1.|Tutti gli elementi di intestazione SOAP elencati sono supportati da Analysis Services, come descritto all'interno della specifica.|  
  
## <a name="extensions"></a>Estensioni  
 Analysis Services si estende anche la specifica XML for Analysis 1.1 per supportare le funzionalità aggiuntive seguenti.  
  
|Elemento|Specifica|Implementazione|  
|----------|-------------------|--------------------|  
|Negoziazione del protocollo|Nessuna informazione contenuta nella specifica XML for Analysis 1.1|Elemento ProtocolCapabilities dell'intestazione aggiunto da Analysis Services per supportare la negoziazione delle funzionalità del protocollo.|  
|Comandi XML for Analysis (XMLA) supportati dal metodo Discover|I comandi seguenti sono supportati dalla specifica XML for Analysis 1.1:<br /><br /> [Elemento dell'istruzione &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md)|I comandi seguenti sono supportati da Analysis Services:<br /><br /> [Elemento ALTER &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md)<br /><br /> [Elemento di backup &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)<br /><br /> [Elemento batch &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)<br /><br /> [Elemento BeginTransaction &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md)<br /><br /> [Elemento Cancel &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)<br /><br /> [Elemento ClearCache &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/clearcache-element-xmla.md)<br /><br /> [Elemento CommitTransaction &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)<br /><br /> [Creare l'elemento &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)<br /><br /> [Eliminare l'elemento &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/delete-element-xmla.md)<br /><br /> [Elemento DesignAggregations &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/designaggregations-element-xmla.md)<br /><br /> [Elemento DROP &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)<br /><br /> [Inserire l'elemento &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)<br /><br /> [Bloccare l'elemento &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md)<br /><br /> [Elemento MergePartitions &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/mergepartitions-element-xmla.md)<br /><br /> [Elemento NotifyTableChange &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/notifytablechange-element-xmla.md)<br /><br /> [Elaborare l'elemento &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)<br /><br /> [Elemento Restore &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)<br /><br /> [Elemento RollbackTransaction &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)<br /><br /> [Elemento dell'istruzione &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md)<br /><br /> [Elemento Subscribe &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/subscribe-element-xmla.md)<br /><br /> [Elemento Synchronize &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)<br /><br /> [Elemento Unlock &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)<br /><br /> [Aggiornare l'elemento &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)<br /><br /> [Elemento UpdateCells &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)|  
|Errori di colonna nei set di righe di tabella|Non elencato nella specifica XML for Analysis 1.1.|Il [errore](../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md) elemento viene usato da Analysis Services per segnalare gli errori per gli elementi delle colonne contenuti un [riga](../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md) elemento.|  
  
## <a name="see-also"></a>Vedere anche
 [Guida di riferimento a XML for Analysis &#40;XMLA&#41;](../../analysis-services/xmla/xml-for-analysis-xmla-reference.md)  
  
  
