---
title: sp_rxPredict | Microsoft Docs
ms.custom: ''
ms.date: 07/14/2017
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
author: jeannt
ms.author: jeannt
manager: craigg
ms.openlocfilehash: ede8232f36f42cc2b9758bdee8f50457ebd58dfe
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38036049"
---
# <a name="sprxpredict"></a>sp_rxPredict  
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Genera un valore stimato in base un modello archiviato.

Fornisce l'assegnazione dei punteggi in modelli di machine learning in tempo quasi reale. `sp_rxPredict` è una stored procedure fornita come wrapper per il `rxPredict` funzionare [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler) e [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package). È scritto in C + + e ottimizzato in modo specifico per le operazioni di assegnazione dei punteggi. Supporta entrambi R o Python modelli di machine learning.

**In questo argomento si applica a**:  
- SQL Server 2017  
- SQL Server 2016 R Services con l'aggiornamento a Microsoft R Server  

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

Richiede una delle edizioni seguenti:  
- SQL Server 2017 Machine Learning Services (che include Microsoft R Server 9.1.0)  
- Microsoft Machine Learning Server  
- SQL Server R Services 2016, con un aggiornamento dell'istanza di R Services per Microsoft R Server 9.1.0 o versione successiva  

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

  Per informazioni sui tipi SQL corrispondenti, vedere [Mapping dei tipi SQL-CLR](https://msdn.microsoft.com/library/bb386947.aspx) oppure [Mapping dei dati dei parametri CLR](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).

