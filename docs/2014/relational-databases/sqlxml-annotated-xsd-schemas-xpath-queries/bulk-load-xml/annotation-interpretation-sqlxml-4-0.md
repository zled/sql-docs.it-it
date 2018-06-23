---
title: Interpretazione delle annotazioni (SQLXML 4.0) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, XML Bulk Load
- XML Bulk Load [SQLXML], annotation intepretations
- annotations [SQLXML]
- bulk load [SQLXML], annotation interpretations
- annotated XDR schemas, XML Bulk Load
ms.assetid: 1c46bdb6-2812-4a13-b60b-7101c04b299f
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ba4c9e6506b67802a8a9571df80ff4db7d2b3934
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36067990"
---
# <a name="annotation-interpretation-sqlxml-40"></a>Interpretazione delle annotazioni (SQLXML 4.0)
  Negli argomenti riportati in questa sezione viene descritto in che modo il caricamento bulk XML interpreta le annotazioni nello schema XSD. Il comportamento descritto è applicabile anche alle annotazioni nello schema XDR.  
  
> [!NOTE]  
>  Nelle informazioni contenute in questi argomenti vengono descritte solo le annotazioni utilizzate durante l'elaborazione del caricamento bulk XML. Per un elenco completo di annotazioni per lo schema XSD che sono supportate in SQLXML 4.0, vedere [utilizzando le annotazioni negli schemi XSD &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/using-annotations-in-xsd-schemas-sqlxml-4-0.md). Per un elenco di annotazioni supportate per gli schemi XDR, vedere [schemi XDR &#40;deprecato in SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [SQL: Relationship e regola di ordinamento delle chiavi &#40;SQLXML 4.0&#41;](annotation-interpretation-sql-relationship-and-key-ordering-rule.md)  
 Viene descritto in che modo l'annotazione `sql:relationship` viene interpretata nel caricamento bulk XML.  
  
 [SQL: il mapping &#40;SQLXML 4.0&#41;](annotation-interpretation-sql-mapped.md)  
 Viene descritto in che modo l'annotazione `sql:mapped` viene interpretata nel caricamento bulk XML.  
  
 [SQL: limit-field e SQL: limit-valore &#40;SQLXML 4.0&#41;](annotation-interpretation-sql-limit-field-and-sql-limit-value.md)  
 Viene descritto in che modo le annotazioni `sql:limit-field` e `sql:limit-value` vengono interpretate nel caricamento bulk XML.  
  
 [SQL: overflow-campo &#40;SQLXML 4.0&#41;](annotation-interpretation-sql-overflow-field.md)  
 Viene descritto in che modo l'annotazione `sql:overflow` viene interpretata nel caricamento bulk XML.  
  
 [Altre annotazioni &#40;SQLXML 4.0&#41;](annotation-interpretation-other-annotations.md)  
 Viene descritto in che modo le annotazioni seguenti vengono interpretate nel caricamento bulk XML: `sql:id-prefix`, `sql:use-cdata`, `sql:url-encode`, `sql:is-mapping-schema`, `sql:key-fields`.  
  
  