---
title: Editor origine Excel (pagina Gestione connessione) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.excelsourceadapter.connection.f1
helpviewer_keywords:
- Excel Source Editor
ms.assetid: 428e04e0-ad98-45d0-8345-12ec1b67b2eb
caps.latest.revision: 39
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c1f01be71a5093945a49c43a3a2aec334db7584b
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="excel-source-editor-connection-manager-page"></a>Editor origine Excel (pagina Gestione connessione)
  Usare il nodo **Gestione connessione** della finestra di dialogo **Editor origine Excel** per selezionare la cartella di lavoro di [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] da usare come origine. L'origine Excel legge i dati da un foglio di lavoro o da un intervallo denominato in una cartella di lavoro esistente.  
  
> [!NOTE]  
>  La proprietà **CommandTimeout** dell'origine Excel non è disponibile nell' **Editor origine Excel**, tuttavia può essere impostata usando l' **Editor avanzato**. Per altre informazioni su questa proprietà, vedere la sezione relativa all'origine Excel in [Proprietà personalizzate di Excel](../../integration-services/data-flow/excel-custom-properties.md).  
  
 Per ulteriori informazioni sull'origine Excel, vedere [Excel Source](../../integration-services/data-flow/excel-source.md).  
  
## <a name="static-options"></a>Opzioni statiche  
 **gestione connessione OLE DB**  
 Consente di selezionare una gestione connessione Excel esistente dall'elenco o di creare una nuova connessione facendo clic su **Nuova**.  
  
 **Nuova**  
 Consente di creare una nuova gestione connessione nella finestra di dialogo **Gestione connessione Excel** .  
  
 **Modalità di accesso ai dati**  
 Consente di specificare il metodo per la selezione dei dati dall'origine.  
  
|Valore|Description|  
|-----------|-----------------|  
|Tabella o vista|Consente di recuperare dati da un foglio di lavoro o da un intervallo denominato nel file di Excel.|  
|Variabile nome vista o nome tabella|Consente di specificare il foglio di lavoro o il nome dell'intervallo in una variabile.<br /><br /> **Informazioni correlate:** [Utilizzo di variabili nei pacchetti](http://msdn.microsoft.com/library/7742e92d-46c5-4cc4-b9a3-45b688ddb787)|  
|Comando SQL|Consente di recuperare dati dal file di Excel utilizzando una query SQL. Per informazioni sulla sintassi di query, vedere [Origine Excel](../../integration-services/data-flow/excel-source.md).|  
|Comando SQL da variabile|Consente di specificare il testo della query SQL in una variabile.|  
  
 **Anteprima**  
 Consente di visualizzare in anteprima i risultati nella finestra di dialogo **Vista dati** . L'anteprima supporta la visualizzazione di un massimo di 200 righe.  
  
## <a name="data-access-mode-dynamic-options"></a>Opzioni dinamiche relative alla modalità di accesso ai dati  
  
### <a name="data-access-mode--table-or-view"></a>Modalità di accesso ai dati = Tabella o vista  
 **Nome del foglio di Excel**  
 Consente di selezionare il nome del foglio di lavoro o dell'intervallo denominato in un elenco di fogli di lavoro o intervalli disponibili nella cartella di lavoro di Excel.  
  
### <a name="data-access-mode--table-name-or-view-name-variable"></a>Modalità di accesso ai dati = Variabile nome vista o nome tabella  
 **Nome variabile**  
 Consente di selezionare la variabile contenente il nome del foglio di lavoro o dell'intervallo denominato.  
  
### <a name="data-access-mode--sql-command"></a>Modalità di accesso ai dati = Comando SQL  
 **Testo comando SQL**  
 È possibile digitare il testo di una query SQL, compilare la query facendo clic su **Compila query**o cercare il file contenente il testo della query facendo clic su **Sfoglia**.  
  
 **Parametri**  
 Se è stata immessa una query con parametri utilizzando ? come segnaposto per il parametro nel testo della query, usare la finestra di dialogo **Imposta parametri query** per eseguire il mapping tra i parametri di input della query e le variabili del pacchetto.  
  
 **Build query**  
 Usare la finestra di dialogo **Generatore query** per creare la query SQL con strumenti grafici.  
  
 **Sfoglia**  
 Usare la finestra di dialogo **Apri** per individuare il file contenente il testo della query SQL.  
  
 **Analizza query**  
 Consente di verificare la sintassi del testo della query.  
  
### <a name="data-access-mode--sql-command-from-variable"></a>Modalità di accesso ai dati = Comando SQL da variabile  
 **Nome variabile**  
 Consente di selezionare la variabile contenente il testo della query SQL.  
  
## <a name="see-also"></a>Vedere anche  
 [Errori di Integration Services e riferimento ai messaggi](../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor origine Excel &#40; Pagina colonne &#41;](../../integration-services/data-flow/excel-source-editor-columns-page.md)   
 [Editor origine Excel &#40; Pagina Output degli errori &#41;](../../integration-services/data-flow/excel-source-editor-error-output-page.md)   
 [Gestione connessione Excel](../../integration-services/connection-manager/excel-connection-manager.md)   
 [Ciclo tramite Excel, file e tabelle con un contenitore ciclo Foreach](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
  
