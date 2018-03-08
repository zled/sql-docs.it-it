---
title: Impostazioni globali (finestre di dialogo) (SybaseToSQL) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-sybase
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: e11452b7-ba94-4367-a745-5ccf1764acec
caps.latest.revision: "3"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5b25e702cec71f04f680d6c24f09f3b9e1e003ae
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="global-settings-dialogs--sybasetosql"></a>Impostazioni globali (finestre di dialogo) (SybaseToSQL)
Utilizzare la pagina di finestre di dialogo del **impostazioni globali** la finestra di dialogo per specificare l'azione predefinita dell'utente e impostazioni di avviso per SSMA.  
  
Per accedere alle impostazioni di finestra di dialogo nel **strumenti** dal menu **impostazioni globali**, fare clic su **GUI** nella parte inferiore del riquadro sinistro, quindi scegliere **finestre di dialogo**.  
  
## <a name="options"></a>Opzioni  
**Avvisa prima di sovrascrivere gli oggetti**  
Quando SSMA converte gli oggetti in SQL Server, alcuni oggetti potrebbero già esistere nei metadati del progetto SQL Server. Questi oggetti possono sono già stati convertiti o gli oggetti siano presenti lo stesso nome all'interno dello schema di destinazione come oggetti di cui che si desidera convertire.  
  
Utilizzare questa opzione per specificare se SSMA venga chiesto di sovrascrivere le definizioni degli oggetti duplicati:  
  
-   Se si seleziona **True**, SSMA verrà visualizzata una finestra di dialogo di avviso quando rileva un oggetto duplicato. In questa finestra di dialogo è possibile specificare per sovrascrivere i singoli oggetti o tutti gli oggetti duplicati o di ignorare i singoli oggetti o tutti gli oggetti duplicati.  
  
-   Se si seleziona **False**, **azione predefinita di sovrascrittura dell'oggetto** opzione viene visualizzata in cui si specifica l'azione predefinita.  
  
**Azione predefinita di sovrascrittura di oggetto**  
Questa opzione viene visualizzata se si seleziona **False** per il **Avvisa prima di sovrascrivere gli oggetti** opzione.  
  
Utilizzare questa opzione per specificare l'oggetto predefinito sovrascrivere il comportamento:  
  
-   Se si seleziona **True**, SSMA sovrascrive automaticamente gli oggetti nei metadati del progetto di SQL Server che hanno lo stesso nome e sono nello stesso schema di destinazione dell'oggetto da convertire.  
  
-   Se si seleziona **False**, SSMA non sovrascrive i metadati degli oggetti durante la conversione.  
  
