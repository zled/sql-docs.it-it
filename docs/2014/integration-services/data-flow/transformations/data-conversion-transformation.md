---
title: Trasformazione Conversione dati | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.dataconversiontrans.f1
helpviewer_keywords:
- converting data types [Integration Services]
- Data Conversion transformation
- data types [Integration Services], converting
ms.assetid: fd515bbc-6f49-4d0c-ae7f-6ea3c3f24a1c
caps.latest.revision: 52
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 8ba2e554136b01190adfc6fd95cb6b7927553f50
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069432"
---
# <a name="data-conversion-transformation"></a>Conversione dati - trasformazione
  La trasformazione Conversione dati converte i dati in una colonna di input in un tipo di dati diverso e quindi li copia in una nuova colonna di output. Un pacchetto può ad esempio estrarre dati da più origini e quindi utilizzare questa trasformazione per convertire le colonne nel tipo di dati richiesto dall'archivio dati di destinazione. È possibile applicare più conversioni a una singola colonna di input.  
  
 Tramite questa trasformazione un pacchetto può eseguire i tipi di conversioni dei dati seguenti:  
  
-   Modifica del tipo di dati. Per altre informazioni, vedere [Tipi di dati di Integration Services](../integration-services-data-types.md).  
  
    > [!NOTE]  
    >  Se i dati da convertire hanno tipo di dati date o datetime, per la data nella colonna di output verrà utilizzato il formato ISO anche se le impostazioni locali specificano un formato diverso.  
  
-   Impostazione della lunghezza di colonna dei dati stringa, nonché della scala e della precisione dei dati numerici. Per altre informazioni, vedere [Precisione, scala e lunghezza &#40;Transact-SQL&#41;](/sql/t-sql/data-types/precision-scale-and-length-transact-sql).  
  
-   Impostazione di una tabella codici. Per altre informazioni, vedere [Comparing String Data](../comparing-string-data.md).  
  
    > [!NOTE]  
    >  È possibile copiare dati tra colonne con un tipo di dati string solo se le due colonne utilizzano la stessa tabella codici.  
  
 Se la lunghezza di una colonna di output con dati di tipo string è minore di quella della colonna di input corrispondente, i dati di output verranno troncati. Per altre informazioni, vedere [Gestione degli errori nei dati](../error-handling-in-data.md).  
  
 Questa trasformazione include un input, un output e un output degli errori.  
  
## <a name="related-tasks"></a>Related Tasks  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] o a livello di codice. Per informazioni sull'utilizzo della trasformazione Conversione dati in Progettazione SSIS, vedere [Conversione di dati in un tipo di dati diverso utilizzando la trasformazione Conversione dati](data-conversion-transformation.md) e [Editor trasformazione Conversione dati](../../data-conversion-transformation-editor.md). Per informazioni sull'impostazione delle proprietà di questa trasformazione a livello di programmazione, vedere [Proprietà comuni](../../common-properties.md) e [Proprietà personalizzate delle trasformazioni](transformation-custom-properties.md).  
  
## <a name="related-content"></a>Contenuto correlato  
 Intervento nel blog sul [confronto delle prestazioni tra le tecniche di conversione dei tipi di dati in SSIS 2008](http://go.microsoft.com/fwlink/?LinkId=220823)su blogs.msdn.com.  
  
## <a name="see-also"></a>Vedere anche  
 [Analisi veloce](../../fast-parse.md)   
 [Flusso di dati](../data-flow.md)   
 [Trasformazioni di Integration Services](integration-services-transformations.md)  
  
  
