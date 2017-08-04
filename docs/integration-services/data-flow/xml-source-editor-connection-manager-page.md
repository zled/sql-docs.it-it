---
title: Editor origine XML (pagina Gestione connessione) | Documenti Microsoft
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
- sql13.dts.designer.xmlsourceadapter.connectionmanager.f1
helpviewer_keywords:
- XML Source Editor
ms.assetid: e6507403-a3ce-4b6f-91fc-a7de9f7b6283
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c26e589f52d0008c7c1e1b725e0619f343102c40
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="xml-source-editor-connection-manager-page"></a>Editor origine XML (pagina Gestione connessione)
  Utilizzare la pagina **Gestione connessione** di **Editor origine XML** per specificare un file XML e il file XSD che trasforma i dati XML.  
  
 Per ulteriori informazioni sull'origine XML, vedere [XML Source](../../integration-services/data-flow/xml-source.md).  
  
## <a name="static-options"></a>Opzioni statiche  
 **Modalità di accesso ai dati**  
 Consente di specificare il metodo per la selezione dei dati dall'origine.  
  
|Valore|Description|  
|-----------|-----------------|  
|Percorso file XML|Consente di recuperare i dati da un file XML.|  
|File XML da variabile|Consente di specificare il nome del file XML in una variabile.<br /><br /> **Informazioni correlate**: [Utilizzo di variabili nei pacchetti](http://msdn.microsoft.com/library/7742e92d-46c5-4cc4-b9a3-45b688ddb787)|  
|Dati XML da variabile|Consente di recuperare i dati XML da una variabile.|  
  
 **Usa schema inline**  
 Consente di specificare se i dati di origine XML contengono lo schema XSD che ne definisce e ne convalida la struttura e i dati.  
  
 **Percorso XSD**  
 Consente di digitare il percorso e il nome del file dello schema XSD o di individuare il file selezionando **Sfoglia**.  
  
 **Sfoglia**  
 Usare la finestra di dialogo **Apri** per individuare il file di schema XSD.  
  
 **Genera XSD**  
 Usare la finestra di dialogo **Salva con nome** per selezionare un percorso per il file di schema XSD creato automaticamente. L'editor deduce lo schema dalla struttura dei dati XML.  
  
## <a name="data-access-mode-dynamic-options"></a>Opzioni dinamiche relative alla modalità di accesso ai dati  
  
### <a name="data-access-mode--xml-file-location"></a>Modalità di accesso ai dati = Percorso file XML  
 **Percorso XML**  
 Consente di digitare il percorso e il nome del file di dati XML o di individuare il file scegliendo **Sfoglia**.  
  
 **Sfoglia**  
 Usare la finestra di dialogo **Apri** per individuare il file di dati XML.  
  
### <a name="data-access-mode--xml-file-from-variable"></a>Modalità di accesso ai dati = File XML da variabile  
 **Nome variabile**  
 Consente di selezionare la variabile contenente il percorso e il nome del file XML.  
  
### <a name="data-access-mode--xml-data-from-variable"></a>Modalità di accesso ai dati = Dati XML da variabile  
 **Nome variabile**  
 Consente di selezionare la variabile contenente i dati XML.  
  
## <a name="see-also"></a>Vedere anche  
 [Errori di Integration Services e riferimento ai messaggi](../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor origine XML &#40; Pagina colonne &#41;](../../integration-services/data-flow/xml-source-editor-columns-page.md)   
 [Editor origine XML &#40; Pagina Output degli errori &#41;](../../integration-services/data-flow/xml-source-editor-error-output-page.md)   
 [Estrarre i dati tramite l'origine XML](../../integration-services/data-flow/extract-data-by-using-the-xml-source.md)  
  
  
