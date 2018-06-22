---
title: Altre annotazioni (SQLXML 4.0) | Documenti Microsoft
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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9f379a046b73dbd073c7e0f01b5c41be7589964d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069139"
---
# <a name="other-annotations-sqlxml-40"></a>Altre annotazioni (SQLXML 4.0)
  Oltre alle annotazioni descritte negli argomenti precedenti di questa sezione, il caricamento bulk XML interpreta queste altre annotazioni, come segue:  
  
 `sql:id-prefix`  
 Se lo schema specifica i prefissi dei dati XML, il caricamento bulk XML rimuove i prefissi prima di inviare i dati a Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 `sql:use-cdata`  
 Il caricamento bulk XML legge il testo archiviato nelle sezioni CDATA e lo invia a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 `sql:url-encode`  
 Il caricamento bulk XML non supporta questa annotazione. Non è possibile ad esempio specificare un URL nei dati XML di input e prevedere che il caricamento bulk XML legga i dati da tale posizione per archiviarli nel database.  
  
 `sql:is-mapping-schema`  
 Il caricamento bulk XML non supporta questa annotazione né supporta `sql:id`.  
  
> [!NOTE]  
>  Il caricamento bulk XML non supporta schemi di mapping inline.  
  
 `sql:key-fields`  
 Il caricamento bulk XML ignora sempre questa annotazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Interpretazione delle annotazioni &#40;SQLXML 4.0&#41;](annotation-interpretation-sqlxml-4-0.md)  
  
  