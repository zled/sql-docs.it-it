---
title: Altre annotazioni (SQLXML 4.0) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
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
- url-encode annotation
- sql:key-fields
- use-cdata annotation
- sql:is-mapping-schema
- sql:url-encode
- sql:id-prefix
- sql:use-cdata
- key-fields annotation
- id-prefix annotation [SQLXML]
- is-mapping-schema annotation
ms.assetid: f7b4d37b-d6d3-4ac3-b2fd-a0b534a924e4
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 520e479e4bc3311e8aef17c3ce52e2b26982e2fc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="annotation-interpretation---other-annotations"></a>Interpretazione delle annotazioni - altre annotazioni
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Oltre alle annotazioni descritte negli argomenti precedenti di questa sezione, il caricamento bulk XML interpreta queste altre annotazioni, come segue:  
  
 **sql:id-prefix**  
 Se lo schema specifica i prefissi dei dati XML, il caricamento bulk XML rimuove i prefissi prima di inviare i dati a Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 **sql:use-cdata**  
 Il caricamento bulk XML legge il testo archiviato nelle sezioni CDATA e lo invia a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 **sql:url-encode**  
 Il caricamento bulk XML non supporta questa annotazione. Non è possibile ad esempio specificare un URL nei dati XML di input e prevedere che il caricamento bulk XML legga i dati da tale posizione per archiviarli nel database.  
  
 **sql:is-mapping-schema**  
 Caricamento Bulk XML non supporta questa annotazione né supporta **ID**.  
  
> [!NOTE]  
>  Il caricamento bulk XML non supporta schemi di mapping inline.  
  
 **sql:key-fields**  
 Il caricamento bulk XML ignora sempre questa annotazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Interpretazione delle annotazioni & #40; SQLXML 4.0 & #41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sqlxml-4-0.md)  
  
  
