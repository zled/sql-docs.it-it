---
title: Trasformazione Esporta colonna | Documenti Microsoft
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
- sql13.dts.designer.exportcolumntrans.f1
helpviewer_keywords:
- exporting data
- append options [Integration Services]
- Export Column transformation [Integration Services]
- columns [Integration Services], exporting
- inserting data
- truncate options [Integration Services]
ms.assetid: 678d2dfc-e40c-4fbb-b2cc-42fffc44478a
caps.latest.revision: 45
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e7e611452f931d049c63c822587dc7610bf1eb25
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="export-column-transformation"></a>Trasformazione Esporta colonna
  La trasformazione Esporta colonna legge dati in un flusso di dati e li inserisce in un file. Se ad esempio il flusso di dati contiene informazioni sui prodotti, ad esempio l'immagine di ogni prodotto, è possibile utilizzare la trasformazione Esporta colonna per salvare tali immagini in uno o più file.  
  
## <a name="append-and-truncate-options"></a>Opzioni Accoda e tronca  
 Nella tabella seguente vengono descritti gli effetti delle impostazioni delle opzioni relative all'accodamento e al troncamento sui risultati.  
  
|Accoda|Troncamento|File esistente|Risultati|  
|------------|--------------|-----------------|-------------|  
|False|False|No|La trasformazione crea un nuovo file e vi scrive i dati.|  
|True|False|No|La trasformazione crea un nuovo file e vi scrive i dati.|  
|False|True|No|La trasformazione crea un nuovo file e vi scrive i dati.|  
|True|True|No|La trasformazione non supera la convalida in fase di progettazione. Non è consentito impostare su **true**entrambe le proprietà.|  
|False|False|Sì|Viene generato un errore di run-time. Il file esiste ma la trasformazione non è in grado di scrivervi.|  
|False|True|Sì|La trasformazione elimina e ricrea il file e vi scrive i dati.|  
|True|False|Sì|La trasformazione apre il file e scrive i dati alla fine.|  
|True|True|Sì|La trasformazione non supera la convalida in fase di progettazione. Non è consentito impostare su **true**entrambe le proprietà.|  
  
## <a name="configuration-of-the-export-column-transformation"></a>Configurazione della trasformazione Esporta colonna  
 Per configurare la trasformazione Esporta colonna, procedere nel modo seguente:  
  
-   Specificare le colonne di dati e le colonne contenenti i percorsi dei file in cui scrivere i dati.  
  
-   Specificare se durante l'operazione di inserimento dei dati in file esistenti i dati vengono troncati o accodati.  
  
-   Specificare se scrivere un indicatore dell'ordine dei byte nel file.  
  
    > [!NOTE]  
    >  L'indicatore dell'ordine dei byte viene scritto solo se i dati non vengono accodati a un file esistente e hanno tipo di dati DT_NTEXT.  
  
 La trasformazione utilizza coppie di colonne di input: una contenente un nome di file e una contenente i dati. Ogni riga nel set di dati può specificare un file diverso. A mano a mano che la trasformazione elabora una riga, i dati vengono inseriti nel file specificato. In fase di esecuzione la trasformazione crea i file, se non esistono ancora, e quindi vi scrive i dati. I dati da scrivere devono avere tipo di dati DT_TEXT, DT_NTEXT o DT_IMAGE. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../../integration-services/data-flow/integration-services-data-types.md).  
  
 Questa trasformazione include un input, un output e un output degli errori.  
  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] o a livello di codice.  
  
 Per altre informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor trasformazione Esportazione colonna**, vedere [Editor trasformazione Esportazione colonna &#40;pagina Colonne&#41;](../../../integration-services/data-flow/transformations/export-column-transformation-editor-columns-page.md).  
  
 Nella finestra di dialogo **Editor avanzato** sono disponibili le proprietà che è possibile impostare a livello di codice. Per ulteriori informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor avanzato** o a livello di codice, fare clic su uno degli argomenti seguenti:  
  
-   [Proprietà comuni](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Proprietà personalizzate delle trasformazioni](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
 Per altre informazioni su come impostare le proprietà, vedere [Impostazione delle proprietà di un componente flusso di dati](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
  
