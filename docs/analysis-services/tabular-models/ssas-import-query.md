---
title: Importare dati utilizzando una query nativa (Analysis Services) | Documenti Microsoft
ms.custom: 
ms.date: 10/26/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 50db699cc1db1af428524c3f9c263569d7a7bbc1
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="import-data-by-using-a-native-query"></a>Importare dati utilizzando una query nativa
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]Per i modelli tabulari 1400, la nuova esperienza di recupera dati nei progetti di Visual Studio Analysis Services fornisce un'enorme flessibilità per la modalità è possibile combinare i dati durante l'importazione. Questo articolo descrive la creazione di una connessione a un'origine dati e quindi la creazione di una query SQL nativa per specificare l'importazione dei dati.

Per completare le attività descritte in questo articolo, assicurarsi che si utilizza la versione più recente di SSDT. Se si utilizza Visual Studio 2017, assicurarsi che è stato scaricato e installato il 2017 settembre o versioni successive Microsoft Analysis Services progetti VSIX.

[Scaricare e installare SSDT](../../ssdt/download-sql-server-data-tools-ssdt.md)

[Scaricare i progetti di Microsoft Analysis Services VSIX](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects)

## <a name="create-a-datasource-connection"></a>Creare una connessione origine dati
Se si dispone già una connessione per l'origine dati, è necessario crearne uno.

1. In Visual Studio > **Esplora modelli tabulari**, fare doppio clic su **origini dati**, quindi fare clic su **nuova origine dati**.
2. In **recupera dati**, selezionare il tipo di origine dati e quindi fare clic su **Connetti**. Seguire eventuali passaggi aggiuntivi necessari per connettere l'origine dati.


## <a name="enter-a-query-as-a-named-expression"></a>Immettere una query come un'espressione denominata
1. In **Esplora modelli tabulari**, fare doppio clic su **espressioni** > **modificare espressioni**.
2. In **Editor di Query**, fare clic su **Query** > **nuova Query** > **Query vuota**
3. Nella barra della formula, digitare
    ```
    = Value.NativeQuery(#"DATA SOURCE NAME", "SELECT * FROM …")
    ```
4. Per creare una tabella, in **query**, la query e quindi scegliere **Crea nuova tabella**. La nuova tabella avrà lo stesso nome della query.


## <a name="example"></a>Esempio
Questa query nativa crea una tabella Employee nel modello che include tutte le colonne dalla tabella Dimension.Employee nell'origine dei dati.

```
= Value.NativeQuery(#"SQL/myserver;WideWorldImportersDW", "SELECT * FROM Dimension.Employee")
```
![Editor di query](media/ssas-import-query-example.png)


Dopo l'importazione, viene creata una tabella denominata Employees nel modello.   

![Editor di query](media/ssas-import-query-example-table.png)


## <a name="see-also"></a>Vedere anche  
 [Value.NativeQuery](https://msdn.microsoft.com/library/mt736917.aspx)   
 [Rappresentazione](../../analysis-services/tabular-models/impersonation-ssas-tabular.md)   

  
