---
title: "Configurare un firewall per l&#39;accesso FILESTREAM | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-blob"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Windows Firewall [Motore di database], FILESTREAM"
  - "FILESTREAM [SQL Server], Windows Firewall"
ms.assetid: fc52007f-c26f-4f8e-b9d8-55a7978f4d56
caps.latest.revision: 15
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 15
---
# Configurare un firewall per l&#39;accesso FILESTREAM
  Per utilizzare FILESTREAM in un ambiente protetto da firewall, il client e il serve devono essere entrambi in grado di risolvere nomi DNS nel server in cui sono presenti i file FILESTREAM. Per FILESTREAM è necessario che le porte 139 e 445 di condivisione file di Windows siano aperte.  
  
### Per aprire le porte di condivisione file di Windows in un computer che esegue Windows 7  
  
1.  Nel Pannello di controllo aprire **Windows Firewall**.  
  
2.  Nel riquadro sinistro scegliere **Impostazioni avanzate**. Se viene richiesta una password di amministratore o una conferma, digitare la password o fornire la conferma.  
  
3.  Nel riquadro sinistro della finestra di dialogo **Windows Firewall con sicurezza avanzata** fare clic su **Regole connessioni in entrata**, quindi scegliere **Nuova regola** nel riquadro destro.  
  
4.  Seguire le istruzioni della Creazione guidata nuova regola connessioni in entrata per aggiungere la porta TCP 139.  
  
5.  Ripetere il passaggio precedente per aggiungere la porta TCP 445.  
  
6.  Chiudere la finestra di dialogo **Windows Firewall con sicurezza avanzata**.  
  
  