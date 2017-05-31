---
title: Personalizzare il comportamento dei word breaker con un dizionario personalizzato | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-search
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8e278d1-aeaa-48f1-a0c6-5de232c983e4
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 9325fc9817b8c0f57ebeb9c6a0e9ae8f29b899cc
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="customize-the-behavior-of-word-breakers-with-a-custom-dictionary"></a>Personalizzare Comportamento di word breaker con un dizionario personalizzato
  È possibile personalizzare il comportamento del word breaker per una particolare lingua creando un file del dizionario personalizzato specifico della lingua. Ad esempio, è possibile impedire l'attività del word breaker per determinati termini o modelli.  
  
 Per ulteriori informazioni, vedere il seguente articolo SharePoint:  
  
 [Creare un dizionario personalizzato (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkId=215011)  
  
 Per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], posizionare file del dizionario personalizzato nella seguente cartella:  
  
 `C:\Program Files\Microsoft SQL Server\<instance name>\MSSQL\Binn`  
  
 Dopo aver creato o modificato i file del dizionario personalizzato, riavviare l'Utilità di avvio del Daemon Full-text SQL attraverso il seguente comando:  
  
 `exec sp_fulltext_service 'restart_all_fdhosts'`  
  
  
