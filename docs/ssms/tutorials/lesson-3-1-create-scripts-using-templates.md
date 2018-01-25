---
title: Creare script usando i modelli | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-tutorial
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
ms.assetid: ed48014c-3fc9-48ff-8c0f-8d1822195f14
caps.latest.revision: "28"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: f1972bf4ce414c66a3a4f607af859502680730ea
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="lesson-3-1---create-scripts-using-templates"></a>Lezione 3-1 - Creare script usando i modelli
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] include numerosi modelli di script contenenti istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] per eseguire le attività più comuni. Tali modelli contengono parametri per i valori specificati dall'utente, ad esempio un nome di tabella. L'utilizzo dei parametri consente di digitare il nome una sola volta e quindi copiarlo automaticamente in tutte le posizioni richieste all'interno dello script. È possibile creare modelli personalizzati per supportare gli script che vengono scritti più di frequente. È inoltre possibile riorganizzare l'albero dei modelli spostandoli o creando nuove cartelle dove contenerli. In questa esercitazione verrà utilizzato un modello per creare un database e verranno specificati i parametri del modello.  
  
## <a name="using-templates"></a>Utilizzo dei modelli  
  
#### <a name="to-create-a-script-using-a-template"></a>Per creare uno script utilizzando un modello  
  
1.  In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]scegliere **Esplora modelli** dal menu **Visualizza**.  
  
2.  In Esplora modelli i modelli sono organizzati in gruppi. Espandere **Database**e quindi fare doppio clic su **Crea database**.  
  
3.  Nella finestra di dialogo **Connetti al motore di database** specificare le informazioni di connessione e quindi fare clic su **Connetti**. Viene visualizzata una nuova finestra dell'editor di query che include il contenuto del modello **Crea database** .  
  
4.  Scegliere **Imposta valori per parametri modello** dal menu **Query**.  
  
5.  Nella finestra di dialogo **Specifica valori per parametri modello** la colonna **Valore** contiene un valore consigliato per il parametro **Database_Name** . Nella casella del parametro **Nome database** digitare **Marketing**e quindi fare clic su **OK**. Si noti che il parametro "Marketing" viene inserito in numerosi punti dello script.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Creare modelli personalizzati](../../tools/sql-server-management-studio/lesson-3-2-create-custom-templates.md)  
  
  
  
