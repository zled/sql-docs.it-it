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
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sprxpredict"></a>sp_rxPredict  
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Genera un valore stimato in base a un modello archiviato.

Fornisce il punteggio in modelli di machine learning in tempo quasi reale. `sp_rxPredict` è una stored procedure fornita come wrapper per il `rxPredict` funzionano in [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler) e [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package). È scritto in C + ed è ottimizzato in modo specifico per le operazioni di assegnazione dei punteggi. Supporta entrambi R o Python di machine learning i modelli.

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

Viene restituita una colonna di punteggio, nonché tutte le colonne pass-through dall'origine dati di input.
Ulteriori colonne, ad esempio l'intervallo di confidenza, può essere restituito se l'algoritmo supporta la generazione di tali valori.

## <a name="remarks"></a>Osservazioni

Per abilitare l'utilizzo della stored procedure, SQLCLR deve essere abilitato nell'istanza.

> [!NOTE]
> Prima di abilitare questa opzione, considerare le implicazioni di sicurezza.

È necessario che l'utente `EXECUTE` autorizzazione per il database.

### <a name="supported-platforms"></a>Piattaforme supportate

Richiede una delle edizioni seguenti:  
- Servizi SQL Server 2017 Machine Learning (include Microsoft R Server 9.1.0)  
- Server di Microsoft Machine Learning  
- SQL Server R Services 2016, con un aggiornamento dell'istanza di R Services da Microsoft R Server 9.1.0 o versione successiva  

### <a name="supported-algorithms"></a>Algoritmi supportati

Per un elenco degli algoritmi supportati, vedere [punteggi in tempo reale](../../advanced-analytics/real-time-scoring.md).

I seguenti tipi di modello sono **non** supportati:  
- Modelli contenenti non supportati, altri tipi di trasformazioni di R  
- Modelli di utilizzo di `rxGlm` o `rxNaiveBayes` algoritmi RevoScaleR  
- Modelli PMML  
- Modelli creati utilizzando altre librerie di R da CRAN o altri repository  
- Modelli che contiene qualsiasi altro tipo di trasformazione R diversi da quelli elencati di seguito  

## <a name="examples"></a>Esempi

```sql
DECLARE @model = SELECT @model 
FROM model_table 
WHERE model_name = 'rxLogit trained';

EXEC sp_rxPredict @model = @model,
@inputData = N'SELECT * FROM data';
```

Oltre a essere una query SQL valida, i dati di input in *@inputData* deve includere colonne compatibili con le colonne del modello archiviato.

`sp_rxPredict` supporta solo i seguenti tipi di colonna .NET: double, float, short, ushort, long, ulong e stringa. Potrebbe essere necessario filtrare i tipi non supportati nei dati di input prima di utilizzarlo per il punteggio in tempo reale. 

  Per informazioni sui tipi SQL corrispondente, vedere [Mapping dei tipi CLR SQL](https://msdn.microsoft.com/library/bb386947.aspx) o [Mapping dei dati di parametro CLR](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).

