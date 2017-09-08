---
title: Impostazioni (oggetti di sistema durante il caricamento) del progetto (DB2ToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 9a545233-1b0a-488a-a1ec-c33aa608dcc1
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ef45d9ecb596daea8701af49dffa37d08d642bd5
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="project-settingsloading-system-objects-db2tosql"></a>Impostazioni (oggetti di sistema durante il caricamento) del progetto (DB2ToSQL)
La pagina di oggetti di sistema durante il caricamento del **impostazioni progetto** la finestra di dialogo consente di specificare quali oggetti di sistema DB2 SSMA converte e li carica in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
Il riquadro oggetti di sistema durante il caricamento è disponibile nel **impostazioni progetto** e **impostazioni di progetto predefinite** finestre di dialogo:  
  
-   Per specificare le impostazioni per tutti i progetti SSMA, il **strumenti** dal menu **impostazioni di progetto predefinite**, selezionare il tipo di progetto di migrazione per i quali impostazioni sono necessarie per essere visualizzati o modificati da **versione di destinazione della migrazione** elenco a discesa fare clic su **generale** nella parte inferiore del riquadro sinistro e quindi fare clic su **durante il caricamento di oggetti di sistema**.  
  
-   Per specificare le impostazioni per il progetto corrente, il **strumenti** dal menu **impostazioni progetto**, fare clic su **generale** nella parte inferiore del riquadro sinistro e quindi fare clic su **durante il caricamento di oggetti di sistema**.  
  
## <a name="default-settings"></a>Impostazioni predefinite  
La conversione di oggetti di sistema utilizza risorse di sistema e richiede tempo. Per migliorare le prestazioni, SSMA seleziona solo gli oggetti di sistema utilizzate più di frequente, come illustrato nel seguente elenco:  
  
-   SYS. DBMS_OUTPUT  
  
-   SYS. DBMS_PIPE  
  
-   SYS. DBMS_UTILITY  
  
-   SYS. STANDARD  
  
-   SYS. UTL_FILE  
  
-   SYS. DBMS_LOB  
  
-   SYS. DBMS_SQL  
  
-   SYS. DBMS_SESSION  
  
Se gli oggetti di DB2 fanno riferimento a oggetti di sistema aggiuntive, è necessario selezionare gli oggetti. Se non si seleziona gli oggetti di sistema che fanno riferimento gli oggetti di database DB2, SSMA verrà segnalati gli errori di conversione. Se si ricevono errori di conversione causati dalla mancanza di oggetti di sistema, selezionare gli oggetti mancanti nella finestra di dialogo. È quindi possibile ripetere la conversione in base alle esigenze.  
  

