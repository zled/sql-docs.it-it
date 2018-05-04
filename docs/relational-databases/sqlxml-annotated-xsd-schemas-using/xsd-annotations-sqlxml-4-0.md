---
title: Annotazioni XSD (SQLXML 4.0) | Documenti Microsoft
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, annotations listed
- XSD schemas [SQLXML], annotations
ms.assetid: c62a6785-8d66-40a2-9c5d-80c73d600a3b
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: a7ef117b5abccb1e7e860d0bebafa8f4239e01da
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="xsd-annotations-sqlxml-40"></a>Annotazioni XSD (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Nella tabella seguente sono elencate le annotazioni XSD introdotte in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], che vengono confrontate con le annotazioni XDR introdotte in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].  
  
|Annotazione XSD|Description|Collegamento all'argomento|Annotazione XDR|  
|--------------------|-----------------|----------------|--------------------|  
|**sql:encode**|Quando viene eseguito il mapping a una colonna BLOB di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di un elemento o un attributo XML, è possibile richiedere un URI di riferimento. L'URI può essere utilizzato in seguito per restituire dati BLOB.|[Richiesta di riferimenti URL a dati BLOB utilizzando sql: codificare &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/requesting-url-references-to-blob-data-using-sql-encode-sqlxml-4-0.md)|**url-encode**|  
|**sql:guid**|Consente di specificare se utilizzare un valore GUID generato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o il valore fornito nell'updategram per la colonna.|[Uso delle annotazioni sql:identity e sql:guid](../../relational-databases/sqlxml-annotated-xsd-schemas-using/using-the-sql-identity-and-sql-guid-annotations.md)|Non supportato|  
|**sql:hide**|Nasconde l'elemento o l'attributo specificato nello schema nel documento XML risultante.|[Nascondere gli elementi e gli attributi usando sql:hide](../../relational-databases/sqlxml-annotated-xsd-schemas-using/hiding-elements-and-attributes-by-using-sql-hide.md)|Non supportato|  
|**sql:identity**|Può essere specificato in qualsiasi nodo mappato a una colonna di database di tipo IDENTITY. Il valore specificato per questa annotazione definisce il modo in cui viene aggiornata la colonna di tipo IDENTITY corrispondente nel database.|[Uso delle annotazioni sql:identity e sql:guid](../../relational-databases/sqlxml-annotated-xsd-schemas-using/using-the-sql-identity-and-sql-guid-annotations.md)|Non supportato|  
|**sql:inverse**|Indica all'updategram la logica per invertire l'interpretazione della relazione padre-figlio specificata utilizzando  **\<SQL: Relationship >**.|[Specifica l'attributo SQL: inverse in SQL: Relationship &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)|Non supportato|  
|**sql:is-constant**|Crea un elemento XML che non viene mappato ad alcuna tabella. L'elemento viene visualizzato nell'output della query.|[Creazione di elementi costanti tramite sql: costante è &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/creating-constant-elements-using-sql-is-constant-sqlxml-4-0.md)|Uguale|  
|**sql:key-fields**|Consente la specifica di colonne che identificano in modo univoco le righe di una tabella.|[Identificazione delle colonne chiave mediante SQL: Key-i campi &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)|Uguale|  
|**sql:limit-field**<br /><br /> **sql:limit-value**|Consente di limitare i valori restituiti in base a un valore di limitazione.|[Filtrare valori tramite SQL: limit-field e SQL: limit-valore &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/filtering-values-using-sql-limit-field-and-sql-limit-value-sqlxml-4-0.md)|Uguale|  
|**sql:mapped**|Consente l'esclusione degli elementi dello schema dal risultato.|[Esclusione di elementi dello Schema dal documento XML risultante tramite sql: il mapping &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/excluding-schema-elements-from-the-xml-document-using-sql-mapped.md)|**map-field**|  
|**sql:max-depth**|Consente di specificare la nidificazione nelle relazioni ricorsive indicate nello schema.|[Specifica del livello di nidificazione nelle relazioni ricorsive con sql:max-depth](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-depth-in-recursive-relationships-by-using-sql-max-depth.md)|Non supportato|  
|**sql:overflow-field**|Identifica la colonna di database contenente i dati di overflow.|[Il recupero dei dati non utilizzati tramite SQL: overflow-campo &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/retrieving-unconsumed-data-using-the-sql-overflow-field-sqlxml-4-0.md)|Uguale|  
|**sql:prefix**|Consente di creare attributi ID, IDREF e IDREFS XML validi. Consente di anteporre una stringa ai valori di ID, IDREF e IDREFS.|[Creazione prefix ID valido, IDREF e IDREFS tipo attributi utilizzando &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/creating-valid-id-idref-and-idrefs-type-attributes-using-sql-prefix-sqlxml-4-0.md)|Uguale|  
|**sql:relationship**|Consente di specificare relazioni tra elementi XML. Il **padre**, **figlio**, **chiave padre**, e **chiave figlio** attributi vengono usati per stabilire la relazione.|[Specifica di relazioni tramite SQL: Relationship &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md)|I nomi di attributo sono diversi:<br /><br /> **relazione di chiave**<br /><br /> **la relazione esterna**<br /><br /> **chiave**<br /><br /> **chiave esterna**|  
|**sql:use-cdata**|Consente di specificare sezioni CDATA da utilizzare per determinati elementi nel documento XML.|[Creazione di sezioni CDATA mediante SQL: use-cdata &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/creating-cdata-sections-using-sql-use-cdata-sqlxml-4-0.md)|Uguale|  
  
> [!NOTE]  
>  Nativo XSD **targetNamespace** attributo sostituisce il **spazio dei nomi di destinazione** annotazione che è stata introdotta nel [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] lo schema di mapping XDR.  
  
## <a name="see-also"></a>Vedere anche  
 [La specifica di destinazione Namespace usando l'attributo targetNamespace &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-4-0.md)  
  
  
