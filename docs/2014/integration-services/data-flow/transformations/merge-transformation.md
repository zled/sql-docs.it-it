---
title: Trasformazione Unione | Microsoft Docs
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
- sql12.dts.designer.mergetrans.f1
helpviewer_keywords:
- merging datasets [Integration Services]
- merging data [Integration Services]
- Merge transformation
- combining datasets
- datasets [Integration Services], merging
ms.assetid: cff8690c-07ac-46a0-aab5-20bd4848c677
caps.latest.revision: 42
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: bde18a7396d10ce15020e92d373239b8c3dd96c3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37215691"
---
# <a name="merge-transformation"></a>Unione - trasformazione
  La trasformazione Unione consente di combinare due set di dati ordinati in un singolo set di dati. Le righe di ogni set di dati vengono inserite nell'output in base ai valori delle relative colonne chiave.  
  
 Includendo la trasformazione Unione in un flusso di dati, è possibile eseguire le attività seguenti:  
  
-   Unire dati da due origini dei dati, ad esempio tabelle e file.  
  
-   Creare set di dati complessi, nidificando più trasformazioni Unione.  
  
-   Unire di nuovo le righe dopo aver corretto gli errori nei dati.  
  
 La trasformazione Unione è simile alle trasformazioni Unione input multipli. Utilizzare la trasformazione Unione input multipli anziché la trasformazione Unione nelle situazioni seguenti:  
  
-   Gli input della trasformazione non sono ordinati.  
  
-   Non è necessario che l'output combinato sia ordinato.  
  
-   La trasformazione include più di due input.  
  
## <a name="input-requirements"></a>Requisiti relativi all'input  
 Per eseguire la trasformazione Unione, è necessario che i relativi dati di input siano ordinati. Per altre informazioni su questo requisito importante, vedere [Ordinamento dei dati per le trasformazioni Unione e Merge Join](sort-data-for-the-merge-and-merge-join-transformations.md).  
  
 La trasformazione Unione richiede inoltre che le colonne da unire nei relativi input abbiano metadati corrispondenti. Non è ad esempio possibile unire una colonna con tipo di dati numeric a una colonna con tipo di dati character. Se i dati sono di tipo string, la lunghezza della colonna nel secondo input dovrà essere minore o uguale a quella della colonna nel primo input, alla quale verrà unita.  
  
 In Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] l'interfaccia utente della trasformazione Unione mappa automaticamente le colonne con gli stessi metadati. È quindi possibile eseguire il mapping manualmente altre colonne con tipi di dati compatibili.  
  
 Questa trasformazione include due input e un output. Non supporta un output degli errori.  
  
## <a name="configuration-of-the-merge-transformation"></a>Configurazione della trasformazione Unione  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] o a livello di codice.  
  
 Per altre informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor trasformazione Unione** , vedere [Editor trasformazione Unione](../../merge-transformation-editor.md).  
  
 Per ulteriori informazioni sulle proprietà che è possibile impostare a livello di codice, fare clic su uno degli argomenti seguenti:  
  
-   [Proprietà comuni](../../common-properties.md)  
  
-   [Proprietà personalizzate delle trasformazioni](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 Per informazioni dettagliate sull'impostazione delle proprietà, vedere i seguenti argomenti:  
  
-   [Impostare le proprietà di un componente del flusso di dati](../set-the-properties-of-a-data-flow-component.md)  
  
-   [Ordinare i dati per le trasformazioni Unione e Merge Join](sort-data-for-the-merge-and-merge-join-transformations.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Trasformazione Merge Join](merge-join-transformation.md)   
 [Unione input multipli-trasformazione](union-all-transformation.md)   
 [Flusso di dati](../data-flow.md)   
 [Trasformazioni di Integration Services](integration-services-transformations.md)  
  
  
