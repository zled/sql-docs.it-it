---
title: La memorizzazione nella cache modelli XSL e schemi (SQLXML 4.0) | Documenti di Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- SQLXML, caching
- cache [SQLXML]
- memory [SQLXML]
ms.assetid: 80b4fa79-243f-442c-9f22-74ad66186501
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: dea5fe9357bdc5431a5a787e1a020832fed35955
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48103041"
---
# <a name="caching-templates-xsl-and-schemas-sqlxml-40"></a>Memorizzazione nella cache di modelli, file XSL e schemi (SQLXML 4.0)
  Per migliorare le prestazioni,  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 supporta la memorizzazione di modelli, file XSL e schemi nella cache.  
  
 Tutti gli schemi, i modelli e i file XSL (ad eccezione dei file provenienti da un percorso http:// o ftp://) vengono memorizzati nella cache. I file memorizzati nella cache restano in memoria mentre il processo è in esecuzione. Al termine del processo, il contenuto della cache va perso. Di conseguenza, se si esegue un processo per query, i vantaggi della memorizzazione nella cache potrebbero essere irrilevanti.  
  
 Negli argomenti di questa sezione vengono fornite ulteriori informazioni sulla memorizzazione nella cache.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [La cache dei modelli &#40;SQLXML 4.0&#41;](template-caching-sqlxml-4-0.md)  
 Viene illustrata e quindi fornita una chiave del Registro di sistema per la memorizzazione nella cache dei modelli.  
  
 [La memorizzazione nella cache di XSL &#40;SQLXML 4.0&#41;](xsl-caching-sqlxml-4-0.md)  
 Viene illustrata e quindi fornita una chiave del Registro di sistema per la memorizzazione nella cache dei file XSL.  
  
 [La cache dello schema &#40;SQLXML 4.0&#41;](schema-caching-sqlxml-4-0.md)  
 Vengono illustrati i problemi dell'installazione affiancata di SQLXML relativi alla memorizzazione nella cache degli schemi e vengono fornite chiavi del Registro di sistema per la memorizzazione nella cache degli schemi.  
  
  
