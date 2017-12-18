---
title: Connettersi con Server registrati ed Esplora oggetti | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssms-tutorial
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
ms.assetid: d6b3911f-68b4-4483-831b-df89d6400add
caps.latest.revision: "50"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: f280ca05701c1497843a1dd8caf78e166a1b98f5
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="lesson-1-2---connect-with-registered-servers-and-object-explorer"></a>Lezione 1-2 - Connettersi con server registrati ed Esplora oggetti
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Questa esercitazione illustra l'uso di Server registrati ed Esplora oggetti.  
  
In questa esercitazione viene utilizzato il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Per una maggiore sicurezza, i database di esempio non vengono installati per impostazione predefinita. Per ulteriori informazioni, vedere la pagina relativa all' [installazione dei database di esempio e degli esempi di SQL Server](http://sqlserversamples.codeplex.com).  
  
## <a name="connecting-to-servers"></a>Connessione ai server  
Nella barra degli strumenti del componente Server registrati sono inclusi pulsanti per il [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]e [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. È possibile registrare uno o più di questi tipi di server a seconda delle esigenze di gestione. Eseguire le procedure descritte di seguito per registrare il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
#### <a name="to-register-the-database"></a>Per registrare il database  
  
1.  Fare clic su **Motore di database** nella barra degli strumenti Server registrati, se necessario (è possibile che sia già selezionato).  
  
2.  Espandere **Motore di database**.  
  
3.  Fare clic con il pulsante destro del mouse su **Gruppi di server locali**e scegliere **Nuova registrazione server**.  
  
4.  Nella casella di testo **Nome server** della finestra di dialogo **Nuova registrazione server** digitare il nome dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
5.  Nella casella **Nome server registrato** digitare [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
6.  Nell'elenco **Connetti al database** della scheda **Proprietà connessione** selezionare **\<Sfoglia server>**.  
  
7.  Nella finestra di dialogo **Cerca database** fare clic su **Sì**.  
  
8.  Nella finestra di dialogo **Cerca database nel server** selezionare [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], quindi fare clic su **OK**.  
  
9. Per verificare che il server sia stato registrato correttamente, fare clic su **Test**.  
  
10. Nella finestra di dialogo **Nuova registrazione server** fare clic su **Salva**.  
  
## <a name="connecting-with-object-explorer"></a>Connessione con Esplora oggetti  
Analogamente a Server registrati, tramite Esplora oggetti è possibile connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)], ad [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], a [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]e a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
#### <a name="to-connect-with-object-explorer"></a>Per connettersi con Esplora oggetti  
  
1.  Fare clic su **Connetti** nella barra degli strumenti di Esplora oggetti per visualizzare l'elenco dei tipi di connessione disponibili e quindi selezionare **Motore di database**.  
  
2.  Nella casella di testo **Nome server** della finestra di dialogo **Connetti al server** digitare il nome dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
3.  Fare clic su **Opzioni** ed esaminare le impostazioni.  
  
4.  Fare clic su **Connetti**per connettersi al server. Se la connessione è già stata eseguita, si tornerà a Esplora oggetti e il server riceverà lo stato attivo.  
  
    Con Esplora oggetti è possibile amministrare la sicurezza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, Replica e Posta elettronica database. In Esplora oggetti è possibile gestire solo alcune caratteristiche di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]e [!INCLUDE[ssIS](../../includes/ssis-md.md)]. Ognuno di questi componenti contiene strumenti specializzati aggiuntivi.  
  
5.  In Esplora oggetti espandere la cartella **Database** e selezionare [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
    Si noti che [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] include i database di sistema in una cartella distinta.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Modificare il layout ambiente](../../tools/sql-server-management-studio/lesson-1-3-change-the-environment-layout.md)  
  
  
  
