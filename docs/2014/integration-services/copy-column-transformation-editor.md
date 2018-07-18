---
title: Editor trasformazione Copia colonna | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.copymaptransformation.f1
helpviewer_keywords:
- Copy Column Transformation Editor
ms.assetid: d8e70541-d563-4ce4-bf66-bc888a0d3026
caps.latest.revision: 25
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fd2e21da9766248e2004e2101b4422f8a1942cbc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37250471"
---
# <a name="copy-column-transformation-editor"></a>Editor trasformazione Copia colonna
  La finestra di dialogo **Editor trasformazione Copia colonna** consente di selezionare le colonne da copiare e di assegnare nomi alle nuove colonne di output.  
  
 Per altre informazioni sulla trasformazione Copia colonna, vedere [Trasformazione Copia colonna](data-flow/transformations/copy-column-transformation.md).  
  
> [!NOTE]  
>  Quando si copiano tutti i dati di origine in una destinazione, potrebbe non essere necessario utilizzare la trasformazione Copia colonna. In alcuni casi è possibile connettere un'origine direttamente a una destinazione qualora non sia necessaria alcuna trasformazione dei dati. In simili circostanze è spesso preferibile utilizzare l'Importazione/Esportazione guidata SQL Server per creare automaticamente il pacchetto. Successivamente è possibile perfezionare e riconfigurare il pacchetto in base alle necessità. Per altre informazioni, vedere [SQL Server Import and Export Wizard](import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).  
  
## <a name="options"></a>Opzioni  
 **Colonne di input disponibili**  
 Consente di selezionare le colonne da copiare mediante le caselle di controllo. Le selezioni effettuate determinano l'aggiunta delle colonne di input nella tabella sottostante.  
  
 **Colonna di input**  
 Consente di selezionare le colonne da copiare nell'elenco delle colonne di input disponibili. Le selezioni effettuate vengono riflesse nelle selezioni delle caselle di controllo nella tabella **Colonne di input disponibili** .  
  
 **Alias di output**  
 Consente di digitare un alias per ogni colonna di output. Per impostazione predefinita viene suggerito **Copia di**seguito dal nome della colonna di input. È comunque possibile scegliere qualsiasi nome descrittivo univoco.  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
