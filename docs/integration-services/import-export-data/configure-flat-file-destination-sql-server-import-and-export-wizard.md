---
title: Configurare destinazione File Flat (SQL Server importazione / esportazione guidata) | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.impexpwizard.configureflatfiledest.f1
ms.assetid: 318e8da0-37d3-46cd-943a-fc5d66aad93a
caps.latest.revision: 53
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 560965a241b24a09f50a23faf63ce74d0049d5a7
ms.openlocfilehash: 93fbd5e9429d06e3f011f6f0aff03d76a3db9000
ms.contentlocale: it-it
ms.lasthandoff: 10/13/2017

---
# <a name="configure-flat-file-destination-sql-server-import-and-export-wizard"></a>Configurazione destinazione file flat (Importazione/Esportazione guidata SQL Server)
  Se è stata selezionata una destinazione file flat, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] importazione / esportazione guidata mostra **configurazione destinazione File Flat** dopo aver specificato che si desidera copiare una tabella o dopo aver fornito di una query. In questa pagina è possibile specificare le opzioni di formattazione per il file flat di destinazione. Facoltativamente, è possibile esaminare il mapping di singole colonne e visualizzare in anteprima i dati di esempio.  
  
## <a name="screen-shot-of-the-configure-flat-file-destination-page"></a>Screenshot della pagina Configurare la destinazione del file flat  
 La schermata seguente mostra un esempio del **configurazione destinazione File Flat** pagina della procedura guidata.
 
 In questo esempio, l'utente ha specificato le opzioni seguenti per creare un tipico CSV (valori delimitati da virgole).
-   **Delimitatore di riga**. Ogni riga di dati nell'output termina con un ritorno a capo / avanzamento riga combinazione.
-   **Delimitatore di colonna**. Colonne di dati all'interno di ogni riga sono separate da una virgola.

 ![Pagina file flat dell'importazione / esportazione guidata di configurazione](../../integration-services/import-export-data/media/flat-file.png)
  
## <a name="pick-a-source-table"></a>Selezionare una tabella di origine
 **Tabella o vista di origine**  
-   Se è stato specificato in una pagina precedente che si desidera copiare una tabella, selezionare la tabella di origine o la vista nell'elenco a discesa.
-   Se si fornisce una query, `"Query"` è selezionata ed è l'unica opzione.  

## <a name="specify-row-and-column-delimiters-for-the-output"></a>Specificare i delimitatori di riga e di colonna per l'output
 **Delimitatore di riga**  
 Selezionare dall'elenco dei delimitatori per separare le righe nell'output. Non è disponibile alcuna opzione per specificare un *personalizzato* delimitatore di riga.  
  
|Valore|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Consente di delimitare le righe con una combinazione di caratteri ritorno a capo/avanzamento riga.|  
|**{CR}**|Consente di delimitare le righe con un ritorno a capo.|  
|**{LF}**|Consente di delimitare le righe con un avanzamento riga.|  
|**Punto e virgola {;}**|Consente di delimitare le righe con un punto e virgola.|  
|**Due punti {:}**|Consente di delimitare le righe con i due punti.|  
|**Virgola {,}**|Delimitare le righe con una virgola.|  
|**Tabulazione {t}**|Consente di delimitare le righe con una tabulazione.|  
|**Barra verticale {&#124;}**|Consente di delimitare le righe con una barra verticale.|  
  
 **Delimitatore di colonna**  
 Selezionare dall'elenco dei delimitatori per separare le colonne nell'output. Non è disponibile alcuna opzione per specificare un *personalizzato* delimitatore di colonna.  
  
|Valore|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Consente di delimitare le colonne con una combinazione di caratteri ritorno a capo/avanzamento riga.|  
|**{CR}**|Consente di delimitare le colonne con un ritorno a capo.|  
|**{LF}**|Consente di delimitare le colonne con un avanzamento riga.|  
|**Punto e virgola {;}**|Consente di delimitare le colonne con un punto e virgola.|  
|**Due punti {:}**|Consente di delimitare le colonne con i due punti.|  
|**Virgola {,}**|Consente di delimitare le colonne con una virgola.|  
|**Tabulazione {t}**|Consente di delimitare le colonne con una tabulazione.|  
|**Barra verticale {&#124;}**|Consente di delimitare le colonne con una barra verticale.|  

## <a name="optionally-review-column-mappings-and-preview-data"></a>Facoltativamente, rivedere i mapping delle colonne e visualizzare l'anteprima dati

**Modifica mapping**   
Facoltativamente, fare clic su **modificare i mapping** per visualizzare il **i mapping delle colonne** la finestra di dialogo per la tabella selezionata. Nella finestra di dialogo **Mapping colonne** eseguire le operazioni seguenti.
-   Esaminare il mapping di singole colonne tra l'origine e la destinazione.
-   Copiare solo un subset di colonne selezionando **ignora** per le colonne da non copiare.

Per altre informazioni, vedere [Mapping colonne](../../integration-services/import-export-data/column-mappings-sql-server-import-and-export-wizard.md).  

**Anteprima**  
Facoltativamente, fare clic su **anteprima** per visualizzare in anteprima fino a 200 righe di dati di esempio nel **Anteprima dati** la finestra di dialogo. Questo permette di verificare che la procedura guidata sta per copiare i dati desiderati. Per altre informazioni, vedere [Anteprima dati](../../integration-services/import-export-data/preview-data-dialog-box-sql-server-import-and-export-wizard.md).  
  
Dopo aver visualizzato i dati in anteprima, potrebbe essere necessario modificare le opzioni selezionate nelle pagine precedenti della procedura guidata. Per apportare queste modifiche, tornare alla pagina **Configurare la destinazione del file flat** e quindi fare clic su **Indietro** per tornare alle pagine precedenti nelle quali modificare le opzioni selezionate.  

## <a name="whats-next"></a>Operazioni successive  
 Dopo aver specificato le opzioni di formattazione per il file flat di destinazione, la pagina successiva è **Salvare ed eseguire il pacchetto**. In questa pagina specificare se eseguire immediatamente l'operazione. A seconda della configurazione, è anche possibile salvare le impostazioni come un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pacchetto per personalizzarlo e riutilizzarla in seguito. Per altre informazioni, vedere [Salvare ed eseguire il pacchetto](../../integration-services/import-export-data/save-and-run-package-sql-server-import-and-export-wizard.md).  


