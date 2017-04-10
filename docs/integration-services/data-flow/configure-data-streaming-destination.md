---
title: "Configurare Destinazione flusso di dati | Microsoft Docs"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SQL11.DTS.DESIGNER.DATASTREAMINGDEST.F1"
ms.assetid: bcdbb833-20c8-47ff-a641-bb517f9a1af3
caps.latest.revision: 7
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 7
---
# Configurare Destinazione flusso di dati
  Per configurare Destinazione del flusso di dati si usa la finestra di dialogo **Editor avanzato per Destinazione flusso di dati** . Per aprire questa finestra di dialogo, fare doppio clic sul componente oppure fare clic con il pulsante destro del mouse sul componente nella finestra di progettazione del flusso di dati e quindi scegliere **Modificare**.  
  
 Questa finestra di dialogo contiene tre schede: **Proprietà componente**, **Colonne di input**e **Proprietà input e output**.  
  
## Scheda Proprietà componente  
 Questa scheda contiene i campi modificabili seguenti:  
  
|Campo|Description|  
|-----------|-----------------|  
|Nome|Nome del componente Destinazione flusso di dati nel pacchetto.|  
|ValidateExternalMetadata|Indica se il componente viene convalidato usando origini dati esterne in fase di progettazione. Se è impostato su false, la convalida rispetto a origini dati esterne viene posticipata fino alla fase di esecuzione.|  
|IDColumnName|La vista generata dalla Pubblicazione guidata di feed di dati contiene questa colonna ID supplementare. La colonna ID funge da EntityKey per i dati di output del flusso di dati quando i dati vengono utilizzati come feed OData da altre applicazioni.<br /><br /> Il nome predefinito di questa colonna è _ID. È possibile specificare un nome diverso per la colonna ID.|  
  
## Scheda Colonne di input  
 Nel riquadro superiore di questa scheda sono mostrate tutte le colonne di input disponibili. Selezionare le colonne da includere nell'output di questo componente. Le colonne selezionate vengono visualizzate in un elenco nel riquadro inferiore. È possibile modificare il nome della colonna di output immettendo il nuovo nome per il campo **Alias di output** nell'elenco.  
  
## Scheda Proprietà input e output  
 Analogamente alla scheda Colonne di input, è possibile modificare i nomi delle colonne di output in questa scheda. Nella visualizzazione albero a sinistra espandere **Input di Destinazione flusso di dati** e quindi espandere **Colonne di input**. Fare clic sul nome della colonna di input e modificare il nome del nome della colonna di output nel riquadro di destra.  
  
## Vedere anche  
 [Destinazione flusso di dati](../../integration-services/data-flow/data-streaming-destination.md)   
 [Procedura dettagliata: Pubblicare un pacchetto SSIS come vista SQL](../../integration-services/data-flow/walkthrough-publish-an-ssis-package-as-a-sql-view.md)  
  
  