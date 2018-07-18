---
title: Gestione degli errori e avvisi (XMLA) | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f2ba225f749364101f800efc4316b941bf18aac5
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="handling-errors-and-warnings-xmla"></a>Gestione di errori e avvisi (XMLA)
  Gestione degli errori è necessaria quando un XML for Analysis (XMLA) [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md) o [Execute](../../analysis-services/xmla/xml-elements-methods-execute.md) chiamata al metodo non viene eseguito, viene eseguito correttamente, ma genera errori o avvisi, o viene eseguito correttamente ma restituisce risultati che contengono errori.  
  
|Errore|Report|  
|-----------|---------------|  
|Chiamata al metodo XMLA non eseguita|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Restituisce un messaggio di errore SOAP che contiene i dettagli dell'errore.<br /><br /> Per ulteriori informazioni, vedere la sezione, [gestione degli errori SOAP](#handling_soap_faults).|  
|Errori o avvisi in una chiamata al metodo eseguita correttamente|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] include un' [errore](../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md) o [avviso](../../analysis-services/xmla/xml-elements-properties/warning-element-xmla.md) elemento per ogni errore o avviso, rispettivamente, nel [messaggi](../../analysis-services/xmla/xml-elements-properties/messages-element-xmla.md) proprietà del [radice](../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) elemento che contiene i risultati della chiamata al metodo.<br /><br /> Per ulteriori informazioni, vedere la sezione, [Handling Errors and Warnings](#handling_errors_and_warnings).|  
|Errori nel risultato di una chiamata al metodo eseguita correttamente|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] include un inline **errore** o **avviso** elemento per l'errore o avviso, rispettivamente, all'interno di appropriata [cella](../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md) o [riga](../../analysis-services/xmla/xml-elements-properties/row-element-xmla.md) elemento dei risultati della chiamata al metodo.<br /><br /> Per ulteriori informazioni, vedere la sezione, [gestione degli errori e avvisi Inline](#handling_inline_errors_and_warnings).|  
  
##  <a name="handling_soap_faults"></a> Gestione di errori SOAP  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] restituisce un errore SOAP quando si verificano le situazioni seguenti:  
  
-   Il messaggio SOAP che contiene il metodo XMLA non è in formato corretto o non è stato convalidato dall'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
-   Si è verificato un errore di comunicazione o di altro tipo relativo al messaggio SOAP che contiene il metodo XMLA.  
  
-   Il metodo XMLA non è stato eseguito nell'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Il codice di errore SOAP per XMLstartA inizia con "XMLForAnalysis", seguito da un punto e dal codice esadecimale restituito HRESULT. Un codice di errore "`0x80000005`" viene formattato come "`XMLForAnalysis.0x80000005`". Per ulteriori informazioni sul formato degli errori SOAP, vedere l'argomento relativo nel documento Simple Object Access Protocol (SOAP) 1.1 del World Wide Web Consortium (W3C).  
  
### <a name="fault-code-information"></a>Informazioni sul codice di errore  
 Nella tabella seguente vengono elencate le informazioni sul codice di errore XMLA contenute nella sezione dei dettagli della risposta SOAP. Le colonne rappresentano gli attributi di un errore nella sezione dei dettagli di un errore SOAP.  
  
|Nome colonna|Tipo|Description|Valore null consentito<sup>1</sup>|  
|-----------------|----------|-----------------|------------------------------|  
|**ErrorCode**|**UnsignedInt**|Codice restituito che indica l'esito positivo o negativo del metodo. Il valore esadecimale deve essere convertito in un **UnsignedInt** valore.|no|  
|**WarningCode**|**UnsignedInt**|Codice restituito che indica una condizione di avviso. Il valore esadecimale deve essere convertito in un **UnsignedInt** valore.|Sì|  
|**Description**|**String**|Testo o descrizione dell'errore o dell'avviso restituiti dal componente che ha generato l'errore.|Sì|  
|**Origine**|**String**|Nome del componente che ha generato l'errore o l'avviso.|Sì|  
|**HelpFile**|**String**|Percorso o URL del file o dell'argomento della Guida in cui è descritto l'errore o l'avviso.|Sì|  
  
 <sup>1</sup> indica se i dati sono obbligatorio e devono essere restituiti, o se i dati sono facoltativi e una stringa null è consentita se la colonna non è applicabile.  
  
 Di seguito viene riportato un esempio di errore SOAP che si è verificato quando una chiamata al metodo non è riuscita:  
  
```  
<?xml version="1.0"?>  
   <SOAP-ENV:Envelope  
   xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"  
   SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">  
      <SOAP-ENV:Fault>  
         <faultcode>XMLAnalysisError.0x80000005</faultcode>  
         <faultstring>The XML for Analysis provider encountered an error.</faultstring>  
         <faultactor>XML for Analysis Provider</faultactor>  
         <detail>  
<Error  
ErrorCode="2147483653"  
Description="An unexpected error has occurred."  
Source="XML for Analysis Provider"  
HelpFile="" />  
         </detail>  
      </SOAP-ENV:Fault>  
</SOAP-ENV:Envelope>  
```  
  
##  <a name="handling_errors_and_warnings"></a> Gestione degli errori e avvisi  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Restituisce il **messaggi** proprietà di **radice** elemento per un comando se si verificano le situazioni seguenti dopo l'esecuzione del comando:  
  
-   Il metodo non ha provocato alcun errore, ma si è verificato un errore nell'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dopo che la chiamata al metodo è stata eseguita correttamente.  
  
-   L'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] restituisce un avviso quando il comando viene eseguito correttamente.  
  
 Il **messaggi** proprietà segue tutte le altre proprietà sono contenuti il **radice** elemento e può contenere uno o più **messaggio** elementi. A sua volta, ogni **messaggio** elemento può contenere un singolo **errore** o **avviso** elemento che descrive rispettivamente, di eventuali errori o avvisi, che si sono verificati per il comando specificato.  
  
 Per ulteriori informazioni sugli errori e avvisi che sono contenuti nel **messaggi** proprietà, vedere [Messages-elemento &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-properties/messages-element-xmla.md).  
  
### <a name="handling-errors-during-serialization"></a>Gestione di errori durante la serializzazione  
 Se si verifica un errore dopo il [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] istanza ha iniziato a serializzare l'output di un comando eseguito correttamente, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] restituisce un [eccezione](../../analysis-services/xmla/xml-elements-properties/exception-element-xmla.md) elemento in un altro spazio dei nomi al momento dell'errore. L'istanza [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] chiude quindi tutti gli elementi aperti in modo che il documento XML inviato al client sia un valido. L'istanza restituisce inoltre un **messaggi** elemento che contiene la descrizione dell'errore.  
  
##  <a name="handling_inline_errors_and_warnings"></a> Gestione degli errori e avvisi Inline  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Restituisce inline **errore** oppure **avviso** per un comando se il metodo XMLA non esito negativo, ma si è verificato un errore specifico a un elemento di dati nei risultati restituiti dal metodo di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] istanza dopo la chiamata al metodo XMLA ha avuto esito positivo.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fornisce inline **errore** e **avviso** elementi se problemi specifici a una cella o altri dati che sono contenuti all'interno di una **radice** elemento utilizzando il [ MDDataSet](../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md) si verificano tipo di dati, ad esempio un errore di sicurezza o di un errore di formattazione per una cella. In questi casi, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] restituisce un **errore** o **avviso** elemento il **cella** o **riga** elemento che contiene l'errore o stato di avviso, rispettivamente.  
  
 L'esempio seguente illustra un set di risultati che contiene un errore nel set di righe restituito da un **Execute** metodo usando il [istruzione](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md) comando.  
  
```  
<return>  
   ...  
   <root>  
      ...  
      <CellData>  
      ...  
         <Cell CellOrdinal="10">  
            <Value>  
               <Error>  
                  <ErrorCode>2148497527</ErrorCode>   
                  <Description>Security Error.</Description>   
               </Error>  
            </Value>  
         </Cell>  
      </CellData>  
      ...  
   </root>  
   ...  
</return>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo con XMLA in Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
