---
title: Editor trasformazione UnPivot | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.unpivottransformation.f1
helpviewer_keywords:
- Unpivot Transformation Editor
ms.assetid: 72a36ef0-4070-4f6c-9c74-0720109617dd
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5b2476969d41acbff7496c14b43e0aa7089eb78e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48119326"
---
# <a name="unpivot-transformation-editor"></a>Editor trasformazione UnPivot
  Utilizzare la finestra di dialogo **Editor trasformazione UnPivot** per selezionare le colonne da trasformare in righe tramite Pivot e specificare la colonna di dati e la nuova colonna di output per il valore pivot.  
  
> [!NOTE]  
>  Per illustrare l'uso delle opzioni, questo argomento si basa sullo scenario UnPivot descritto in [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md) .  
  
 Per ulteriori informazioni sulla trasformazione tramite UnPivot, vedere [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md).  
  
## <a name="options"></a>Opzioni  
 **Colonne di input disponibili**  
 Consente di specificare le colonne da trasformare in righe tramite Pivot utilizzando le caselle di controllo.  
  
 **Nome**  
 Consente di visualizzare il nome della colonna di input disponibile.  
  
 **Pass-through**  
 Indica se includere la colonna nell'output trasformato tramite UnPivot.  
  
 **Colonna di input**  
 Consente di selezionare una colonna di input nell'elenco delle colonne di input disponibili per ogni riga. Le selezioni effettuate vengono riflesse nelle selezioni delle caselle di controllo nella tabella **Colonne di input disponibili** .  
  
 Nello scenario UnPivot descritto in [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md), le colonne di input sono le colonne **Ham**, **Soda**, **Milk**, **Beer**e **Chips** .  
  
 **Colonna di destinazione**  
 Consente di specificare un nome per la colonna di dati.  
  
 Nello scenario UnPivot descritto in [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md), la colonna di destinazione è la colonna delle quantità, ovvero**Qty**.  
  
 **Valore chiave pivot**  
 Consente di specificare un nome per il valore pivot. Per impostazione predefinita viene suggerito il nome della colonna di input. È comunque possibile scegliere qualsiasi nome descrittivo univoco.  
  
 È possibile specificare il valore di questa proprietà tramite un'espressione di proprietà.  
  
 Nello scenario UnPivot descritto in [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md), i valori pivot verranno visualizzati nella nuova colonna Product designata dall'opzione **Nome colonna valore chiave pivot** allo stesso modo dei valori di testo **Ham**, **Soda**, **Milk**, **Beer**e **Chips**.  
  
 **Nome colonna valore chiave pivot**  
 Consente di specificare il nome per la colonna del valore pivot. L'impostazione predefinita è "Valore chiave pivot". È comunque possibile scegliere un nome descrittivo univoco.  
  
 Nello scenario UnPivot descritto in [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md), il Nome colonna valore chiave pivot è **Product** e designa la nuova colonna **Product** come la colonna in cui viene applicata la trasformazione tramite UnPivot alle colonne **Ham**, **Soda**, **Milk**, **Beer**e **Chips** .  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento ai messaggi e agli errori di Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Trasformazione Pivot](data-flow/transformations/pivot-transformation.md)  
  
  
