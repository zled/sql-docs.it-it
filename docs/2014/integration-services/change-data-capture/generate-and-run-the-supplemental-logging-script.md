---
title: Generare ed eseguire lo script di registrazione supplementare | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- supLog
ms.assetid: 6e940d93-12c6-4cda-9333-5489b245f0e4
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 64abc1eed2f37082e07b00daf609a75c09da4beb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36158739"
---
# <a name="generate-and-run-the-supplemental-logging-script"></a>Generare ed eseguire lo script di registrazione supplementare
  Utilizzare la pagina Set up Tables for Capturing Changes per eseguire uno script nel database di origine Oracle per l'impostazione della registrazione supplementare.  
  
 **Per eseguire gli script di registrazione supplementare**  
  
 Fare clic su **Run Script** per eseguire lo script di registrazione supplementare nelle tabelle definite per l'istanza di CDC. Tramite questo script verranno scritte tutte le colonne di interesse nei log delle transazioni durante la registrazione delle operazioni UPDATE nelle tabelle acquisite. Lo script viene in genere esaminato ed eseguito da un amministratore di sistema Oracle.  
  
 È anche possibile eseguire gli script manualmente tramite SQL * Plus.  
  
 **Per eseguire gli script manualmente**  
  
 Scegliere **Copy** per incollare lo script negli Appunti. Aprire SQL* Plus e accedere alla directory contenente il database di origine Oracle. Incollare lo script in SQL\*Plus per eseguirlo.  
  
 Per salvare lo script di registrazione supplementare in un file di testo, scegliere **Save as** e accedere al percorso in cui si desidera salvare il file. Assegnare un nome al file e scegliere **Save** per salvarlo.  
  
 Scegliere **Next** per [Generate Mirror Tables and CDC Capture Instances](generate-mirror-tables-and-cdc-capture-instances.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Come creare l'istanza di Database SQL Server Change](how-to-create-the-sql-server-change-database-instance.md)   
 [Rivedere e generare script di registrazione supplementare](review-and-generate-supplemental-logging-scripts.md)  
  
  