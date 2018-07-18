---
title: Personalizzare il comportamento dei word breaker con un dizionario personalizzato | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: search, sql-database
ms.component: search
ms.reviewer: ''
ms.suite: sql
ms.technology: search
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a8e278d1-aeaa-48f1-a0c6-5de232c983e4
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 18a2aba8a554d0c08cf8a09ac0b5c5260d8855c7
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="customize-the-behavior-of-word-breakers-with-a-custom-dictionary"></a>Personalizzare Comportamento di word breaker con un dizionario personalizzato
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  È possibile personalizzare il comportamento del word breaker per una particolare lingua creando un file del dizionario personalizzato specifico della lingua. Ad esempio, è possibile impedire l'attività del word breaker per determinati termini o modelli.  
  
 Per ulteriori informazioni, vedere il seguente articolo SharePoint:  
  
 [Creare un dizionario personalizzato (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkId=215011)  
  
 Per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], posizionare file del dizionario personalizzato nella seguente cartella:  
  
 `C:\Program Files\Microsoft SQL Server\<instance name>\MSSQL\Binn`  
  
 Dopo aver creato o modificato i file del dizionario personalizzato, riavviare l'Utilità di avvio del Daemon Full-text SQL attraverso il seguente comando:  
  
 `exec sp_fulltext_service 'restart_all_fdhosts'`  
  
  
