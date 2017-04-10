---
title: "Configurazione destinazione file flat (Importazione/Esportazione guidata SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.impexpwizard.configureflatfiledest.f1"
ms.assetid: 318e8da0-37d3-46cd-943a-fc5d66aad93a
caps.latest.revision: 53
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 50
---
# Configurazione destinazione file flat (Importazione/Esportazione guidata SQL Server)
  Se è stata selezionata una destinazione file flat, l'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] visualizza **Configurare la destinazione del file flat** dopo aver specificato una tabella da copiare o una query. In questa pagina è possibile specificare le opzioni di formattazione per il file flat di destinazione Facoltativamente, è possibile esaminare il mapping di singole colonne e visualizzare in anteprima i dati di esempio.  
  
## <a name="screen-shot-of-the-configure-flat-file-destination-page"></a>Screenshot della pagina Configurare la destinazione del file flat  
 La cattura di schermata seguente mostra la pagina **Configurare la destinazione del file flat** della procedura guidata.
 
 In questo esempio, l'utente vuole creare un normale file CSV (file con valori delimitati da virgole), ovvero terminare ogni riga di dati nell'output con una combinazione di caratteri ritorno a capo/avanzamento riga e separare le colonne di dati all'interno di ogni riga con una virgola.

 ![Configure flat file page of the Import and Export Wizard](../../integration-services/import-export-data/media/flat-file.png "Configure flat file page of the Import and Export Wizard")  
  
## <a name="pick-a-source-table"></a>Selezionare una tabella di origine. 
 **Tabella o vista di origine**  
 Selezionare la tabella o la vista di origine.  

## <a name="specify-the-row-and-column-delimiters"></a>Specificare i delimitatori di riga e colonna
 **Delimitatore di riga**  
 Consente di selezionare un delimitatore di riga nell'elenco. Non è possibile specificare un delimitatore di riga personalizzato.  
  
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
 Consente di selezionare un delimitatore di colonna nell'elenco. Non è possibile specificare un delimitatore di colonna personalizzato.  
  
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

## <a name="optionally-edit-column-mappings-and-preview-sample-data"></a>Modificare i mapping delle colonne e visualizzare in anteprima i dati di esempio

**Modifica mapping**   
Facoltativamente, fare clic su **Modifica mapping** per visualizzare la finestra di dialogo **Mapping colonne** per la tabella selezionata. Nella finestra di dialogo **Mapping colonne** eseguire le operazioni seguenti.
-   Esaminare il mapping di singole colonne tra l'origine e la destinazione.
-   Copiare solo un subset di colonne selezionando **ignora** per le colonne da non copiare.

Per altre informazioni, vedere [Mapping colonne](../../integration-services/import-export-data/column-mappings-sql-server-import-and-export-wizard.md).  

**Anteprima**  
Facoltativamente, fare clic su **Anteprima** per visualizzare in anteprima fino a 200 righe di dati di esempio nella finestra di dialogo **Anteprima dati**. Questo permette di verificare che la procedura guidata sta per copiare i dati desiderati. Per altre informazioni, vedere [Anteprima dati](../../integration-services/import-export-data/preview-data-dialog-box-sql-server-import-and-export-wizard.md).  
  
Dopo aver visualizzato i dati in anteprima, potrebbe essere necessario modificare le opzioni selezionate nelle pagine precedenti della procedura guidata. Per apportare queste modifiche, tornare alla pagina **Configurare la destinazione del file flat** e quindi fare clic su **Indietro** per tornare alle pagine precedenti nelle quali modificare le opzioni selezionate.  

## <a name="whats-next"></a>Operazioni successive  
 Dopo aver specificato le opzioni di formattazione per il file flat di destinazione, la pagina successiva è **Salvare ed eseguire il pacchetto**. In questa pagina specificare se eseguire immediatamente l'operazione. A seconda della configurazione, è anche possibile salvare il pacchetto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creato dalla procedura guidata per personalizzarlo e usarlo di nuovo in seguito. Per altre informazioni, vedere [Salvare ed eseguire il pacchetto](../../integration-services/import-export-data/save-and-run-package-sql-server-import-and-export-wizard.md).  
