---
title: Generare ed eseguire lo script di registrazione supplementare | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: change-data-capture
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- supLog
ms.assetid: 6e940d93-12c6-4cda-9333-5489b245f0e4
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ee20cd83df04d4ec3929f9ee39068969c0d18950
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/13/2018
---
# <a name="generate-and-run-the-supplemental-logging-script"></a>Generare ed eseguire lo script di registrazione supplementare
  Utilizzare la pagina Set up Tables for Capturing Changes per eseguire uno script nel database di origine Oracle per l'impostazione della registrazione supplementare.  
  
 **Per eseguire gli script di registrazione supplementare**  
  
 Fare clic su **Run Script** per eseguire lo script di registrazione supplementare nelle tabelle definite per l'istanza di CDC. Tramite questo script verranno scritte tutte le colonne di interesse nei log delle transazioni durante la registrazione delle operazioni UPDATE nelle tabelle acquisite. Lo script viene in genere esaminato ed eseguito da un amministratore di sistema Oracle.  
  
 È anche possibile eseguire gli script manualmente tramite SQL * Plus.  
  
 **Per eseguire gli script manualmente**  
  
 Scegliere **Copy** per incollare lo script negli Appunti. Aprire SQL* Plus e accedere alla directory contenente il database di origine Oracle. Incollare lo script in SQL\*Plus per eseguirlo.  
  
 Per salvare lo script di registrazione supplementare in un file di testo, scegliere **Save as** e accedere al percorso in cui si desidera salvare il file. Assegnare un nome al file e scegliere **Save** per salvarlo.  
  
 Scegliere **Next** per [Generate Mirror Tables and CDC Capture Instances](../../integration-services/change-data-capture/generate-mirror-tables-and-cdc-capture-instances.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura di creazione dell'istanza del database delle modifiche di SQL Server](../../integration-services/change-data-capture/how-to-create-the-sql-server-change-database-instance.md)   
 [Rivedere e generare script di registrazione supplementare](../../integration-services/change-data-capture/review-and-generate-supplemental-logging-scripts.md)  
  
  
