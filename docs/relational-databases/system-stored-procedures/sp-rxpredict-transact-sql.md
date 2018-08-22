---
title: sp_rxPredict | Microsoft Docs
ms.custom: ''
ms.date: 08/20/2018
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_rxPredict
- sp_rxPredict_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_rxPredict procedure
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 8f46403afef0e2f6cf967561a8fd24ec6409fe93
ms.sourcegitcommit: 9528843359cc43b9c66afac363f542ae343266e9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "40434861"
---
# <a name="sprxpredict"></a>sp_rxPredict  
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Genera un valore stimato per un input specificato in base un modello di machine learning archiviato in un formato binario in un database di SQL Server.

Fornisce l'assegnazione dei punteggi in R e Python modelli di machine learning in tempo quasi reale. `sp_rxPredict` è una stored procedure fornita come wrapper per il `rxPredict` funzione R nel [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler) e [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)e la [rx_predict](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict) funzione Python nella [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) e [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package). È scritto in C + + e ottimizzato in modo specifico per le operazioni di assegnazione dei punteggi.

**Questo articolo si applica a**:  
- SQL Server 2017  
- SQL Server 2016 R Services con [aggiornati i componenti R](https://docs.microsoft.com/sql/advanced-analytics/r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server)

## <a name="syntax"></a>Sintassi

```
sp_rxPredict  ( @model, @input )
```

### <a name="arguments"></a>Argomenti

**model**

Un modello con training preliminare in un formato supportato. 

**input**

Una query SQL valida

### <a name="return-values"></a>Valori restituiti

Viene restituita una colonna di punteggio, e tutte le colonne pass-through dall'origine dati di input.
Ulteriori colonne di tipo, ad esempio l'intervallo di confidenza, può essere restituito se l'algoritmo supporta la generazione di tali valori.

## <a name="remarks"></a>Note

Per abilitare l'utilizzo della stored procedure, SQLCLR deve essere abilitato nell'istanza.

> [!NOTE]
> Prima di abilitare questa opzione, prendere in considerazione le implicazioni di sicurezza.

Le esigenze degli utenti `EXECUTE` autorizzazione per il database.

### <a name="supported-platforms"></a>Piattaforme supportate
 
- SQL Server 2017 Machine Learning Services (che include R Server 9.2)  
- Machine Learning Server (Standalone) di SQL Server 2017 
- SQL Server R Services 2016, con un aggiornamento dell'istanza di R Services a R Server 9.1.0 o versione successiva  

### <a name="supported-algorithms"></a>Algoritmi supportati

Per un elenco degli algoritmi supportati, vedere [punteggio in tempo reale](../../advanced-analytics/real-time-scoring.md).

I seguenti tipi di modello sono **non** supportati:  
- Modelli contenenti non supportati, gli altri tipi di trasformazioni di R  
- I modelli usando la `rxGlm` o `rxNaiveBayes` algoritmi in RevoScaleR  
- Modelli di linguaggio PMML  
- Modelli creati con altre librerie di R da CRAN o ad altri repository  
- Modelli che contiene qualsiasi altro tipo di trasformazione R diversi da quelli elencati di seguito  

## <a name="examples"></a>Esempi

```sql
DECLARE @model = SELECT @model 
FROM model_table 
WHERE model_name = 'rxLogit trained';

EXEC sp_rxPredict @model = @model,
@inputData = N'SELECT * FROM data';
```

Oltre a essere una query SQL valida, dati di input *@inputData* deve includere colonne compatibili con le colonne del modello archiviato.

`sp_rxPredict` supporta solo i seguenti tipi di colonna .NET: double, float, short, ushort, long, ulong e stringa. Potrebbe essere necessario filtrare i tipi non supportati nei dati di input prima di usarlo per assegnare i punteggi in tempo reale. 

  Per informazioni sui tipi SQL corrispondenti, vedere [Mapping dei tipi SQL-CLR](/dotnet/framework/data/adonet/sql/linq/sql-clr-type-mapping) oppure [Mapping dei dati dei parametri CLR](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).

