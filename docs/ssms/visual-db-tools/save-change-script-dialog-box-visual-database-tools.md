---
title: Finestra di dialogo Salva script modifiche (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.generatechangescript
- vdtsql.chm:65544
ms.assetid: fc9d1639-5efa-44fe-a04f-4d4d0def2833
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 822dbca38dfa6cdf6934bec3353bba531c9e84e7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47804214"
---
# <a name="save-change-script-dialog-box-visual-database-tools"></a>Finestra di dialogo Salva script modifiche (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
In questa finestra di dialogo viene visualizzato lo script [!INCLUDE[tsql](../../includes/tsql-md.md)] relativo alle modifiche apportate a partire dall'ultimo salvataggio della tabella. Questa finestra consente inoltre di salvare lo script in un file di testo nel percorso desiderato.  
  
È possibile accedere a questa finestra di dialogo dopo avere apportato modifiche non salvate a una tabella in Progettazione tabelle. Scegliere **Genera script delle modifiche** dal menu **Progettazione tabelle**.  
  
> [!NOTE]  
> Gli script delle modifiche disponibili in Visual Database Tools non includono la gestione degli errori. Si suppone che gli oggetti di database non abbiano subito modifiche dopo l'apertura dello strumento e che quindi non si verificherà alcun problema relativo a modifiche. Prima di eseguire uno script delle modifiche è consigliabile includere le istruzioni di gestione degli errori appropriate.  
  
## <a name="options"></a>Opzioni  
**Genera automaticamente script delle modifiche a ogni salvataggio**  
Se si seleziona questa opzione, la finestra di dialogo **Salva script modifiche** verrà visualizzata ogni volta che si salvano le modifiche apportate a una tabella.  
  
**Sì**  
Visualizza la finestra di dialogo **Salva** , in cui è possibile selezionare il percorso per il file di testo.  
  
**No**  
Annulla la creazione dello script delle modifiche.  
  
