---
title: Destinazione File flat | Documenti Microsoft
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
- sql13.dts.designer.flatfiledest.f1
helpviewer_keywords:
- flat files
- Flat File destination
- text file writing [Integration Services]
- destinations [Integration Services], Flat File
ms.assetid: e0d6e356-8db4-48aa-ba66-029397f98f61
caps.latest.revision: 49
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 78a0ec526f83dcab8d7358ef5a51f1f6ccfd0a04
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="flat-file-destination"></a>file flat - destinazione
  La destinazione file flat scrive dati in un file di testo che può essere in formato delimitato, a larghezza fissa, a larghezza fissa con delimitatore di riga o non allineato a destra.  
  
 Per configurare la destinazione file flat, procedere nel modo seguente:  
  
-   Specificare un blocco di testo inserito nel file prima di iniziare a scrivere i dati. Il testo può ad esempio contenere le intestazioni delle colonne.  
  
-   Specificare se sovrascrivere i dati eventualmente presenti in un file di destinazione con lo stesso nome.  
  
 Per accedere al file di testo, questa destinazione utilizza una gestione connessione file flat. Impostando le proprietà della gestione connessione file flat utilizzata dalla destinazione file flat è possibile specificare la modalità con cui la destinazione file flat deve formattare e scrivere il file di testo. Durante la configurazione della gestione connessione file flat si specificano informazioni sul file e sulle singole colonne nel file. È ad esempio possibile specificare i caratteri che delimitano le righe e le colonne del file, oltre al tipo di dati e alla lunghezza di ogni colonna. Per ulteriori informazioni, vedere [Flat File Connection Manager](../../integration-services/connection-manager/flat-file-connection-manager.md).  
  
 La destinazione file flat include la proprietà personalizzata Header, che può essere aggiornata da un'espressione di proprietà al caricamento del pacchetto. Per altre informazioni, vedere [Espressioni di Integration Services &#40;SSIS&#41;](../../integration-services/expressions/integration-services-ssis-expressions.md), [Utilizzo delle espressioni di proprietà nei pacchetti](../../integration-services/expressions/use-property-expressions-in-packages.md) e [Proprietà personalizzate del file flat](../../integration-services/data-flow/flat-file-custom-properties.md).  
  
 Questa destinazione include un solo output. Non supporta un output degli errori.  
  
## <a name="configuration-of-the-flat-file-destination"></a>Configurazione della destinazione file flat  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Per altre informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor origine file flat** , fare clic su uno degli argomenti seguenti:  
  
-   [Editor destinazione file flat &#40;pagina Gestione connessione&#41;](../../integration-services/data-flow/flat-file-destination-editor-connection-manager-page.md)  
  
-   [Editor destinazione file flat &#40;pagina Mapping&#41;](../../integration-services/data-flow/flat-file-destination-editor-mappings-page.md)  
  
 Nella finestra di dialogo **Editor avanzato** sono disponibili le proprietà che è possibile impostare a livello di codice. Per ulteriori informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor avanzato** o a livello di codice, fare clic su uno degli argomenti seguenti:  
  
-   [Proprietà comuni](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Proprietà personalizzate del file flat](../../integration-services/data-flow/flat-file-custom-properties.md)  
  
## <a name="related-tasks"></a>Attività correlate  
 Per informazioni su come impostare le proprietà di un componente del flusso di dati, vedere [Impostazione delle proprietà di un componente del flusso di dati](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Origine file flat](../../integration-services/data-flow/flat-file-source.md)   
 [Flusso di dati](../../integration-services/data-flow/data-flow.md)  
  
  
