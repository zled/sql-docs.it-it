---
title: "Aggiungere funzionalità di Business Intelligence a una dimensione | Documenti Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Business Intelligence enhancements [Analysis Services], dimension intelligence
- dimensions [Analysis Services], Business Intelligence enhancements
- dimension intelligence [Analysis Services]
- Type property
ms.assetid: b64fa386-eac2-4286-a320-0631a1887aac
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 86c5f345dc963667ea5b05177e84517609f7e5a7
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="bi-wizard---add-dimension-intelligence-to-a-dimension"></a>Creazione guidata BI - aggiungere funzionalità di Business Intelligence a una dimensione
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Aggiungere la funzionalità di business intelligence di dimensione a un cubo o una dimensione consente di specificare un tipo aziendale standard per una dimensione. Queste funzionalità avanzate specificano inoltre i tipi corrispondenti per gli attributi dimensione. Queste specifiche del tipo possono essere utilizzate dalle applicazioni client per l'analisi dei dati.  
  
 Per aggiungere funzionalità di Business Intelligence per le dimensioni, usare Configurazione guidata funzionalità di Business Intelligence e quindi selezionare l'opzione **Definizione funzionalità di Business Intelligence per le dimensioni** nella pagina **Scelta funzionalità avanzata** . Questa procedura guidata consente di eseguire in modo semplificato i passaggi relativi alla selezione di una dimensione alla quale si desidera applicare la funzionalità di Business Intelligence per le dimensioni e all'identificazione degli attributi per la dimensione selezionata.  
  
## <a name="selecting-a-dimension"></a>Selezione di una dimensione  
 Nella prima pagina **Funzionalità di Business Intelligence per le dimensioni** della procedura guidata specificare la dimensione alla quale si desidera applicare la funzionalità di Business Intelligence per le dimensioni. L'aggiunta della funzionalità avanzata di Business Intelligence per le dimensioni alla dimensione selezionata implica modifiche alla dimensione. Tali modifiche verranno ereditate da tutti i cubi che includono la dimensione selezionata.  
  
> [!NOTE]  
>  Se come dimensione si seleziona **Conto** , verrà specificata la funzionalità di Business Intelligence per la contabilità per la dimensione. Per altre informazioni, vedere [Aggiungere funzionalità di Business Intelligence per la contabilità a una dimensione](../../analysis-services/multidimensional-models/bi-wizard-add-account-intelligence-to-a-dimension.md).  
  
## <a name="specifying-dimension-attributes"></a>Definizione degli attributi dimensione  
 Nella pagina **Definizione funzionalità di Business Intelligence per le dimensioni** la selezione eseguita nell'elenco **Tipo dimensione** determina l'impostazione della proprietà **Type** della dimensione. L'impostazione della proprietà **Type** fornisce informazioni sul contenuto di una dimensione a server e applicazioni client. Alcune impostazioni forniscono solo indicazioni per le applicazioni client e pertanto queste impostazioni sono facoltative. Altre impostazioni, ad esempio Conti o Ora, determinano funzionalità specifiche e possono essere obbligatorie per l'implementazione di particolari funzionalità avanzate di Business Intelligence. Ad esempio, SQL Server Management Studio utilizza il tipo di dimensione per identificare una dimensione di tipo Valuta e impostare le regole di conversione appropriate per la valuta. L'impostazione predefinita per **Tipo dimensione** è **Regolare**, ovvero non viene usato alcun contenuto specifico della dimensione.  
  
 Dopo aver selezionato il tipo di dimensione, in **Attributi dimensione**nella colonna **Includi** selezionare la casella di controllo accanto a ogni tipo di attributo standard per il quale esiste un attributo corrispondente nella dimensione. Nella colonna **Attributo dimensione** espandere l'elenco a discesa e selezionare l'attributo nella dimensione corrispondente al tipo di attributo selezionato. La selezione dell'attributo dall'elenco comporta l'impostazione della proprietà **Type** degli attributi.  
  
 Si supponga, ad esempio, di voler aggiungere la funzionalità di Business Intelligence per le dimensioni a una dimensione di tipo Conti. In **Tipo dimensione**selezionare **Conti**. Se la dimensione dispone degli attributi **Account Type** e **Account Description** , nella colonna **Includi** selezionare la casella di controllo per i tipi di conto **Account Name** e **Account Type** . Nella colonna **Attributo dimensione** associare questi tipi di conto rispettivamente agli attributi **Account Description** e **Account Type** nella dimensione.  
  
## <a name="see-also"></a>Vedere anche  
 [Definire calcoli delle funzionalità di Business Intelligence per le gerarchie temporali mediante la Configurazione guidata funzionalità di Business Intelligence](../../analysis-services/multidimensional-models/define-time-intelligence-calculations-using-the-business-intelligence-wizard.md)  
  
  
