---
title: Usare la modalità RAW con FOR XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML RAW mode
- XMLSCHEMA option
- FOR XML clause, RAW mode
- RAW FOR XML mode
- ELEMENTS directive
- RAW mode
- XMLDATA option
ms.assetid: 02c1bc0b-760c-4589-9ab1-6927c6d9c734
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d074ad6fe9dcd3a26a9c9be84a326291df9f5aed
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48084237"
---
# <a name="use-raw-mode-with-for-xml"></a>Utilizzo della modalità RAW con FOR XML
  Nella modalità RAW ogni riga del set di risultati della query viene trasformata in un elemento XML al quale è assegnato l'identificatore generico \<row> o il nome di elemento specificato facoltativamente. Per impostazione predefinita, viene eseguito il mapping di ogni valore di colonna del set di righe diverso da NULL a un attributo dell'elemento \<row>. Se alla clausola FOR XML viene aggiunta la direttiva ELEMENTS, viene eseguito il mapping di ogni valore di colonna a un sottoelemento dell'elemento \<row>. Insieme alla direttiva ELEMENTS è possibile specificare facoltativamente l'opzione XSINIL per eseguire il mapping dei valori di colonna NULL del set di risultati a un elemento con l'attributo xsi:nil=`"`true`"`.  
  
 È possibile richiedere uno schema per il codice XML risultante. Se si specifica l'opzione XMLDATA, verrà restituito uno schema XDR inline. Se si specifica l'opzione XMLSCHEMA, verrà restituito uno schema XDS inline. che viene visualizzato all'inizio dei dati. Nel risultato, il riferimento allo spazio dei nomi dello schema viene ripetuto in ogni elemento di livello principale.  
  
 Per restituire i dati binari nel formato con codifica Base64, è necessario specificare l'opzione BINARY BASE64 nella clausola FOR XML. Se si recuperano dati binari nella modalità RAW senza specificare l'opzione BINARY BASE64, verrà generato un errore.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 In questa sezione sono disponibili gli esempi seguenti:  
  
-   [Esempio: recupero delle informazioni relative al modello del prodotto in formato XML](example-retrieving-product-model-information-as-xml.md)  
  
-   [Esempio: specifica di XSINIL con la direttiva ELEMENTS](example-specifying-xsinil-with-the-elements-directive.md)  
  
-   [Esempio: richiesta di schemi di risultato mediante le opzioni XMLDATA e XMLSCHEMA](example-requesting-schemas-as-results-with-the-xmldata-and-xmlschema-options.md)  
  
-   [Esempio: recupero di dati binari](example-retrieving-binary-data.md)  
  
-   [Esempio: ridenominazione dell'elemento &#60;row&#62;](example-renaming-the-row-element.md)  
  
-   [Esempio: specifica di un elemento radice per codice XML generato da FOR XML](example-specifying-a-root-element-for-the-xml-generated-by-for-xml.md)  
  
-   [Esempio: esecuzione di query sulle colonne di tipo XML](example-querying-xmltype-columns.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiungere spazi dei nomi alle query con WITH XMLNAMESPACES](add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [Utilizzo della modalità AUTO con FOR XML](use-auto-mode-with-for-xml.md)   
 [Utilizzo della modalità EXPLICIT con FOR XML](use-explicit-mode-with-for-xml.md)   
 [Usare la modalità PATH con FOR XML](use-path-mode-with-for-xml.md)   
 [SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql)   
 [FOR XML &#40;SQL Server&#41;](../xml/for-xml-sql-server.md)  
  
  
