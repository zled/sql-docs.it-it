---
title: Impostazioni (oggetti di sistema durante il caricamento) del progetto (DB2ToSQL) | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-db2
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 9a545233-1b0a-488a-a1ec-c33aa608dcc1
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 996027fcd919c4689ba3971c618f045b0759c994
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="project-settingsloading-system-objects-db2tosql"></a>Impostazioni (oggetti di sistema durante il caricamento) del progetto (DB2ToSQL)
La pagina di oggetti di sistema durante il caricamento del **impostazioni progetto** la finestra di dialogo consente di specificare quali oggetti di sistema DB2 SSMA converte e li carica in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
Il riquadro oggetti di sistema durante il caricamento è disponibile nel **impostazioni progetto** e **impostazioni di progetto predefinite** finestre di dialogo:  
  
-   Per specificare le impostazioni per tutti i progetti SSMA, il **strumenti** dal menu **impostazioni di progetto predefinite**, selezionare il tipo di progetto di migrazione per i quali impostazioni sono necessarie per essere visualizzati o modificati da **versione di destinazione della migrazione** elenco a discesa fare clic su **generale** nella parte inferiore del riquadro sinistro e quindi fare clic su **durante il caricamento di oggetti di sistema**.  
  
-   Per specificare le impostazioni per il progetto corrente, il **strumenti** dal menu **impostazioni progetto**, fare clic su **generale** nella parte inferiore del riquadro sinistro e quindi fare clic su **durante il caricamento di oggetti di sistema**.  
  
## <a name="default-settings"></a>Impostazioni predefinite  
La conversione di oggetti di sistema utilizza risorse di sistema e richiede tempo. Per migliorare le prestazioni, SSMA seleziona solo gli oggetti di sistema utilizzate più di frequente, come illustrato nel seguente elenco:  
  
-   SYS.DBMS_OUTPUT  
  
-   SYS.DBMS_PIPE  
  
-   SYS. DBMS_UTILITY  
  
-   SYS. STANDARD  
  
-   SYS.UTL_FILE  
  
-   SYS.DBMS_LOB  
  
-   SYS.DBMS_SQL  
  
-   SYS.DBMS_SESSION  
  
Se gli oggetti di DB2 fanno riferimento a oggetti di sistema aggiuntive, è necessario selezionare gli oggetti. Se non si seleziona gli oggetti di sistema che fanno riferimento gli oggetti di database DB2, SSMA verrà segnalati gli errori di conversione. Se si ricevono errori di conversione causati dalla mancanza di oggetti di sistema, selezionare gli oggetti mancanti nella finestra di dialogo. È quindi possibile ripetere la conversione in base alle esigenze.  
  
