---
title: Convenzioni XML ASSL | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- whitespace [Analysis Services Scripting Language]
- trailing whitespace
- XSD data types [Analysis Services Scripting Language]
- inheritance [Analysis Services Scripting Language]
- cardinality [Analysis Services Scripting Language]
- white space [Analysis Services Scripting Language]
- ASSL, XML conventions
- defaults [Analysis Services Scripting Language]
- leading whitespace
- Analysis Services Scripting Language, XML conventions
- XML [Analysis Services Scripting Language]
- hierarchies [Analysis Services Scripting Language]
- inherited defaults [Analysis Services Scripting Language]
ms.assetid: bce4edad-4420-41ce-9672-8c00c5c0dec6
caps.latest.revision: 24
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a8cd244f64d45ff81ff51cba6b528c81ba743ff1
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="assl-xml-conventions"></a>Convenzioni XML di ASSL
  Nel linguaggio ASSL (Analysis Services Scripting Language) la gerarchia di oggetti viene rappresentata come un set di tipi di elementi, ciascuno dei quali definisce gli elementi figlio che può contenere.  
  
 Per rappresentare la gerarchia di oggetti, in ASSL vengono utilizzate le convenzioni XML seguenti:  
  
-   Tutti gli oggetti e le proprietà vengono rappresentati come elementi, ad eccezione degli attributi XML standard, ad esempio "xml:lang".  
  
-   Sia i nomi degli elementi e i valori di enumerazione seguono la convenzione di denominazione di Microsoft .NET Framework di Pascal maiuscole e minuscole senza caratteri di sottolineatura.  
  
-   La combinazione di lettere maiuscole e minuscole di tutti i valori viene mantenuta. I valori relativi alle enumerazioni rispettano inoltre la distinzione tra maiuscole e minuscole.  
  
 Oltre all'elenco di convenzioni indicato, in Analysis Services vengono seguite inoltre convenzioni specifiche relative alla cardinalità, l'ereditarietà, gli spazi vuoti, i tipi di dati e i valori predefiniti.  
  
## <a name="cardinality"></a>Cardinalità  
 Quando la cardinalità di un elemento è maggiore di 1, è presente una raccolta di elementi XML che incapsula tale elemento. Per il nome della raccolta viene utilizzata la forma plurale degli elementi contenuti nella raccolta stessa. Ad esempio, il frammento XML seguente rappresenta il **dimensioni** insieme all'interno di un **Database** elemento:  
  
 `<Database>`  
  
 `…`  
  
 `<Dimensions>`  
  
 `<Dimension>`  
  
 `...`  
  
 `</Dimension>`  
  
 `<Dimension>`  
  
 `...`  
  
 `</Dimension>`  
  
 `</Dimensions>`  
  
 `</Database>`  
  
 ``  
  
 L'ordine in cui sono visualizzati gli elementi non è importante.  
  
## <a name="inheritance"></a>Ereditarietà  
 L'ereditarietà viene utilizzata quando sono presenti oggetti distinti cui sono associati set di proprietà sovrapposti, ma con differenze significative. Esempi di tali oggetti sovrapposti, ma distinti, sono i cubi virtuali, i cubi collegati e i cubi regolari. Per questo oggetto distinto, Analysis Services utilizza lo standard **tipo** attributo Namespace di istanza di XML per indicare l'ereditarietà. Ad esempio, il codice XML seguente frammento viene illustrato come la **tipo** attributo identifica se un **cubo** elemento eredita da un cubo regolare o da un cubo virtuale:  
  
 `<Cubes>`  
  
 `<Cube xsi:type=”RegularCube”>`  
  
 `<Name>Sales</Name>`  
  
 `...`  
  
 `</Cube>`  
  
 `<Cube xsi:type=”VirtualCube”>`  
  
 `<Name>SalesAndInventory</Name>`  
  
 `...`  
  
 `</Cube>`  
  
 `</Cubes>`  
  
 ``  
  
 In genere l'ereditarietà non viene utilizzata quando a più tipi è associata una proprietà con lo stesso nome. Ad esempio, il **nome** e **ID** proprietà vengono visualizzate in molti elementi, ma queste proprietà non sono state promosse a un tipo astratto.  
  
## <a name="whitespace"></a>Spazi vuoti  
 Gli spazi vuoti all'interno di un valore di elemento vengono mantenuti, mentre gli spazi vuoti iniziali e finali vengono sempre rimossi. Gli elementi seguenti contengono ad esempio lo stesso testo che differisce tuttavia per il numero di spazi vuoti all'interno. Di conseguenza tali elementi vengono considerati come se i relativi valori fossero diversi:  
  
 `<Description>My text<Description>`  
  
 `<Description>My  text<Description>`  
  
 ``  
  
 Gli elementi seguenti differiscono invece solo per gli spazi vuoti iniziali e finali e vengono pertanto considerati come se i relativi valori fossero equivalenti:  
  
 `<Description>My text<Description>`  
  
 `<Description>  My text  <Description>`  
  
 ``  
  
## <a name="data-types"></a>Tipi di dati  
 In Analysis Services vengono utilizzati i seguenti tipi di dati XML Schema Definition Language (XSD) standard:  
  
 **Int**  
 Valore integer compreso nell'intervallo tra -231 e 231 - 1.  
  
 **Long**  
 Valore integer compreso nell'intervallo tra -263 e 263 - 1.  
  
 **String**  
 Valore stringa conforme alle regole globali seguenti:  
  
-   Rimozione dei caratteri di controllo.  
  
-   Eliminazione degli spazi vuoti iniziali e finali.  
  
-   Mantenimento degli spazi vuoti interni.  
  
 **Nome** e **ID** proprietà presentano alcune limitazioni speciali nei caratteri validi negli elementi della stringa. Per ulteriori informazioni su **nome** e **ID** convenzioni, vedere [oggetti ASSL e relative caratteristiche](../../../analysis-services/multidimensional-models/scripting-language-assl/assl-objects-and-object-characteristics.md).  
  
 **DateTime**  
 Oggetto **DateTime** struttura da .NET Framework. Oggetto **DateTime** valore non può essere NULL. La data meno recente supportata dal **DataTime** tipo di dati è il 1 ° gennaio 1601, disponibile per i programmatori come **DateTime. MinValue**. Data meno recente supportata indica che un **DateTime** manca il valore.  
  
 **Boolean**  
 Enumerazione con due soli valori, ovvero {true, false} o {0, 1}.  
  
## <a name="default-values"></a>Valori predefiniti  
 In Analysis Services vengono utilizzati i valori predefiniti elencati nella tabella seguente.  
  
|Tipo di dati XML|Valore predefinito|  
|-------------------|-------------------|  
|**Boolean**|False|  
|**String**|"" (stringa vuota)|  
|**Intero** o **lungo**|0 (zero)|  
|**Timestamp**|12:00:00 AM, 1/1/0001 (corrispondente a una di .NET Framework **System. DateTime** con 0 tick)|  
  
 Un elemento presente, ma vuoto, viene interpretato come se il relativo valore fosse una stringa Null e non quello predefinito.  
  
### <a name="inherited-defaults"></a>Valori predefiniti ereditati  
 Alcune proprietà specificate per un oggetto forniscono i valori predefiniti per la stessa proprietà in oggetti figlio o discendenti. Ad esempio, **Cube.StorageMode** fornisce il valore predefinito per **Partition.StorageMode**. Le regole che Analysis Services applica ai valori predefiniti ereditati sono i seguenti:  
  
-   Quando in XML la proprietà per l'oggetto figlio è Null, per impostazione predefinita viene utilizzato il valore ereditato. Se tuttavia si esegue una query relativa al valore nel server, viene restituito il valore Null dell'elemento XML.  
  
-   Non è possibile determinare a livello di programmazione se la proprietà di un oggetto figlio è stata impostata direttamente su tale oggetto oppure se è stata ereditata.  
  
 Per alcuni elementi sono specificati valori predefiniti che si applicano quando l'elemento è mancante. Ad esempio, il **dimensione** elementi nel seguente frammento XML sono equivalenti anche se un **dimensione** elemento contiene un **Visible** elemento, ma le altre  **Dimensione** non elemento.  
  
 `<Dimension>`  
  
 `<Name>Product</Name>`  
  
 `</Dimension>`  
  
 `<Dimension>`  
  
 `<Name>Product</ Name>`  
  
 `<Visible>true</Visible>`  
  
 `</Dimension>`  
  
 Per ulteriori informazioni sui valori predefiniti ereditati, vedere [oggetti ASSL e relative caratteristiche](../../../analysis-services/multidimensional-models/scripting-language-assl/assl-objects-and-object-characteristics.md).  
  
  

