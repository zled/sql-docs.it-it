---
title: Configurazione destinazione file flat (Importazione/Esportazione guidata SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.impexpwizard.configureflatfiledest.f1
ms.assetid: 318e8da0-37d3-46cd-943a-fc5d66aad93a
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 033b602d712d4ec6e0caf136b1228cd82b552e08
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069639"
---
# <a name="configure-flat-file-destination-sql-server-import-and-export-wizard"></a>Configurazione destinazione file flat (Importazione/Esportazione guidata SQL Server)
  Usare la **configurazione destinazione File Flat** pagina per specificare le opzioni di formattazione per file flat di destinazione e per visualizzare in anteprima i risultati prima di continuare.  
  
 Per ulteriori informazioni su questa procedura guidata, vedere [SQL Server di importazione / esportazione guidata](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Per ulteriori informazioni sulle opzioni per avviare la procedura guidata, nonché le autorizzazioni necessarie per eseguire correttamente la procedura guidata, vedere [eseguire il Server importazione / esportazione guidata SQL](start-the-sql-server-import-and-export-wizard.md).  
  
 Lo scopo di Importazione/Esportazione guidata SQL Server è la copia di dati da un'origine a una destinazione. La procedura guidata può inoltre creare automaticamente un database di destinazione e le tabelle di destinazione. Se tuttavia è necessario copiare più database o tabelle, o altri tipi di oggetti di database, è preferibile utilizzare Copia guidata database. Per altre informazioni, vedere [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Opzioni  
 **File flat di origine**  
 Nome del file di destinazione.  
  
 **Delimitatore di riga**  
 Consente di selezionare un delimitatore di riga nell'elenco.  
  
|valore|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|La riga è delimitata dalla combinazione di caratteri ritorno a capo/avanzamento riga.|  
|**{CR}**|La riga è delimitata da un ritorno a capo.|  
|**{LF}**|La riga è delimitata da un avanzamento riga.|  
|**Punto e virgola {;}**|La riga è delimitata da un punto e virgola.|  
|**Due punti {:}**|La riga è delimitata da due punti.|  
|**Virgola {,}**|La riga è delimitata da una virgola.|  
|**Tabulazione {t}**|La riga è delimitata da una tabulazione.|  
|**Barra verticale {&#124;}**|La riga è delimitata da una barra verticale.|  
  
 **Delimitatore di colonna**  
 Consente di selezionare un delimitatore di colonna nell'elenco.  
  
|valore|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Le colonne sono delimitate dalla combinazione di caratteri ritorno a capo/avanzamento riga.|  
|**{CR}**|Le colonne sono delimitate da un ritorno a capo.|  
|**{LF}**|Le colonne sono delimitate da un avanzamento riga.|  
|**Punto e virgola {;}**|Le colonne sono delimitate da un punto e virgola.|  
|**Due punti {:}**|Le colonne sono delimitate da due punti.|  
|**Virgola {,}**|Le colonne sono delimitate da una virgola.|  
|**Tabulazione {t}**|Le colonne sono delimitate da una tabulazione.|  
|**Barra verticale {&#124;}**|Le colonne sono delimitate da una barra verticale.|  
  
 **Anteprima**  
 Visualizzare il **Anteprima dati** finestra di dialogo i risultati di formattazione selezionate le opzioni per file flat di destinazione.  
  
 **Modifica trasformazione**  
 Eliminare le righe, accodare righe e configurare le colonne nel file di destinazione utilizzando il **mapping delle colonne** finestra di dialogo.  
  
  