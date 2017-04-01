---
title: "Editor origine XML (pagina Gestione connessione) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.xmlsourceadapter.connectionmanager.f1"
helpviewer_keywords: 
  - "Editor origine XML"
ms.assetid: e6507403-a3ce-4b6f-91fc-a7de9f7b6283
caps.latest.revision: 20
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 20
---
# Editor origine XML (pagina Gestione connessione)
  Utilizzare la pagina **Gestione connessione** di **Editor origine XML** per specificare un file XML e il file XSD che trasforma i dati XML.  
  
 Per ulteriori informazioni sull'origine XML, vedere [XML Source](../../integration-services/data-flow/xml-source.md).  
  
## Opzioni statiche  
 **Modalità di accesso ai dati**  
 Consente di specificare il metodo per la selezione dei dati dall'origine.  
  
|Valore|Description|  
|-----------|-----------------|  
|Percorso file XML|Consente di recuperare i dati da un file XML.|  
|File XML da variabile|Consente di specificare il nome del file XML in una variabile.<br /><br /> **Informazioni correlate**: [Utilizzo di variabili nei pacchetti](../Topic/Use%20Variables%20in%20Packages.md)|  
|Dati XML da variabile|Consente di recuperare i dati XML da una variabile.|  
  
 **Usa schema inline**  
 Consente di specificare se i dati di origine XML contengono lo schema XSD che ne definisce e ne convalida la struttura e i dati.  
  
 **Percorso XSD**  
 Consente di digitare il percorso e il nome del file dello schema XSD o di individuare il file selezionando **Sfoglia**.  
  
 **Sfoglia**  
 Usare la finestra di dialogo **Apri** per individuare il file di schema XSD.  
  
 **Genera XSD**  
 Usare la finestra di dialogo **Salva con nome** per selezionare un percorso per il file di schema XSD creato automaticamente. L'editor deduce lo schema dalla struttura dei dati XML.  
  
## Opzioni dinamiche relative alla modalità di accesso ai dati  
  
### Modalità di accesso ai dati = Percorso file XML  
 **Percorso XML**  
 Consente di digitare il percorso e il nome del file di dati XML o di individuare il file scegliendo **Sfoglia**.  
  
 **Sfoglia**  
 Usare la finestra di dialogo **Apri** per individuare il file di dati XML.  
  
### Modalità di accesso ai dati = File XML da variabile  
 **Nome variabile**  
 Consente di selezionare la variabile contenente il percorso e il nome del file XML.  
  
### Modalità di accesso ai dati = Dati XML da variabile  
 **Nome variabile**  
 Consente di selezionare la variabile contenente i dati XML.  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor origine XML &#40;pagina Colonne&#41;](../../integration-services/data-flow/xml-source-editor-columns-page.md)   
 [Editor origine XML &#40;pagina Output degli errori&#41;](../../integration-services/data-flow/xml-source-editor-error-output-page.md)   
 [Estrazione dei dati tramite l'origine XML](../../integration-services/data-flow/extract-data-by-using-the-xml-source.md)  
  
  