---
title: Elemento &lt;xsd:redefine&gt; | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: xml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: xsd:redefine element
ms.assetid: 5f3e9b65-f10e-4db2-a62c-b270ac11d04e
caps.latest.revision: "14"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: acb4011d190445476a0fedfc70557cfcb5e36af5
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="the-ltxsdredefinegt-element"></a>Elemento &lt;xsd:redefine&gt;
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)] L'elemento **redefine** dello schema XSD W3C rende disponibile il supporto per la ridefinizione dei componenti di schema. Il supporto per tale direttiva, tuttavia, può influire negativamente sulle prestazioni e richiede che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] esegua nuovamente la convalida di tutte le istanze del tipo di dati **xml** associate allo schema ridefinito. Di conseguenza, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non supporta questo elemento. XML Schema che includono l'elemento **\<xsd:redefine>** verranno rifiutati dal server.  
  
 In alternativa, per aggiornare uno schema o i relativi componenti, è possibile eseguire le operazioni seguenti.  
  
1.  Creare una nuova raccolta XML Schema con i componenti di schema modificati.  
  
2.  Riscrivere tutti i tipi di dati **xml** (XML DT) che usano la raccolta XML Schema da ridefinire per usare in sostituzione la nuova raccolta XML Schema. A questo scopo, utilizzare l'opzione ALTER COLUMN del comando ALTER TABLE per riscrivere colonne o modificare i vincoli della raccolta XML Schema su variabili o parametri.  
  
3.  Eliminare la versione obsoleta della raccolta XML Schema.  
  
## <a name="see-also"></a>Vedere anche  
 [Requisiti e limitazioni per l'utilizzo di raccolte di XML Schema nel server](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
