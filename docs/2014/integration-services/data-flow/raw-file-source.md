---
title: Origine file non elaborato | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rawfilesource.f1
helpviewer_keywords:
- sources [Integration Services], Raw File
- raw data [Integration Services]
- Raw File source
ms.assetid: 5b4daea5-7f76-4674-aa77-0a79f9f97f7d
caps.latest.revision: 42
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d5cf3454a024a6d600fa6af2bd0dcb98fd545fb9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37267107"
---
# <a name="raw-file-source"></a>origine file non elaborato
  L'origine file non elaborato legge i dati non elaborati da un file. Poiché la rappresentazione dei dati è nativa per l'origine, non è necessaria alcuna conversione e quasi nessuna analisi dei dati. Ciò significa che l'origine file non elaborato è in grado di leggere i dati più rapidamente rispetto ad altre origini, ad esempio l'origine file flat e l'origine OLE DB.  
  
 L'origine file non elaborato consente di recuperare dati non elaborati scritti in precedenza dalla destinazione file non elaborato. È anche possibile puntare l'origine file non elaborato a un file non elaborato vuoto in cui sono contenute solo le colonne (file di soli metadati). Si utilizza la destinazione file non elaborato per generare il file di soli metadati senza dover eseguire il pacchetto. Per altre informazioni, vedere [Destinazione file non elaborato](raw-file-destination.md).  
  
 Nel formato di file non elaborato sono contenute informazioni di ordinamento. Con la destinazione file non elaborato è possibile salvare tutte le informazioni di ordinamento in cui sono inclusi i flag di confronto per le colonne stringa. Con l'origine file non elaborato è possibile leggere e riconoscere le informazioni di ordinamento. È possibile configurare l'origine file non elaborato in modo da ignorare i flag di ordinamento nel file utilizzando l'editor avanzato. Per altre informazioni sui flag di confronto, vedere [Confronto di dati stringa](comparing-string-data.md).  
  
 Per configurare il file non elaborato è necessario specificare il nome del file che deve essere letto dall'origine file non elaborato.  
  
> [!NOTE]  
>  Questa origine non utilizza alcuna gestione connessione.  
  
 Questa origine include un solo output. Non supporta un output degli errori.  
  
## <a name="configuration-of-the-raw-file-source"></a>Configurazione dell'origine file non elaborato  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Nella finestra di dialogo **Editor avanzato** sono disponibili le proprietà che è possibile impostare a livello di codice. Per ulteriori informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor avanzato** o a livello di codice, fare clic su uno degli argomenti seguenti:  
  
-   [Proprietà comuni](../common-properties.md)  
  
-   [Proprietà personalizzate del file non elaborato](raw-file-custom-properties.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 Per informazioni su come impostare le proprietà del componente, vedere [Impostare le proprietà di un componente del flusso di dati](set-the-properties-of-a-data-flow-component.md).  
  
## <a name="related-content"></a>Contenuto correlato  
  
-   Post di blog sugli [aspetti positivi dei file non elaborati](http://www.sqlservercentral.com/blogs/stratesql/archive/2011/1/1/31-days-of-ssis-_1320_-raw-files-are-awesome-_2800_1_2F00_31_2900_.aspx)nel sito Web sqlservercentral.com.  
  
## <a name="see-also"></a>Vedere anche  
 [Destinazione File non elaborato](raw-file-destination.md)   
 [Flusso di dati](data-flow.md)  
  
  
