---
title: Impostare le proprietà di una variabile definita dall'utente | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- modifying variables
- variables [Integration Services], properties
ms.assetid: f98ddbec-f668-4dba-a768-44ac3ae0536f
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 1d05e9fc6b6c4f1e5e29a4bff9c163305d977202
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36166877"
---
# <a name="set-the-properties-of-a-user-defined-variable"></a>Impostazione delle proprietà di una variabile definita dall'utente
  Per impostare le proprietà di una variabile definita dall'utente in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] è possibile utilizzare una delle funzionalità seguenti:  
  
-   Finestra Variabili.  
  
-   Finestra Proprietà. La finestra **Proprietà** elenca le proprietà per la configurazione delle variabili non disponibili nella finestra **Variabili** : Description, EvaluateAsExpression, Expression, ReadOnly, ValueType e IncludeInDebugDump.  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] include anche un set di variabili di sistema le cui proprietà non possono essere aggiornate, ad eccezione della proprietà RaiseChangedEvent.  
  
 **Impostazione di espressioni nelle variabili**  
  
 Quando si usa la finestra **Proprietà** per impostare le espressioni in una variabile definita dall'utente:  
  
-   Il valore di una variabile può essere impostato tramite la proprietà Value o Expression. Per impostazione predefinita, la proprietà EvaluateAsExpression è impostata su `False` e il valore della variabile viene impostato dalla proprietà Value. Per utilizzare un'espressione per impostare il valore, è innanzitutto necessario impostare EvaluateAsExpression su `True`e quindi specificare un'espressione nella proprietà espressione. La proprietà Value viene impostata automaticamente sul risultato restituito dall'espressione.  
  
-   La proprietà ValueType contiene il tipo di dati del valore della proprietà Value. Quando la proprietà Value viene impostata tramite un'espressione, la proprietà ValueType viene automaticamente aggiornata a un tipo di dati compatibile con il risultato restituito dall'espressione. Ad esempio, se il valore contiene 0 e proprietà ValueType contiene **Int32** espressione è quindi impostata su GETDATE (), il valore contiene la data e ora correnti e ValueType è impostato su `DateTime`.  
  
-   Tramite la finestra **Proprietà** della variabile è possibile accedere alla finestra di dialogo **Generatore di espressioni** , che consente di compilare, convalidare e valutare le espressioni. Per altre informazioni, vedere [Generatore di espressioni](expressions/expression-builder.md) e [Espressioni di Integration Services &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md).  
  
 Quando si usa la finestra **Variabili** per impostare le espressioni in una variabile definita dall'utente:  
  
-   Per usare un'espressione per impostare il valore della variabile, verificare innanzitutto che il tipo di dati della variabile sia compatibile con il risultato della valutazione dell'espressione e quindi specificare un'espressione nella `Expression` colonna del **variabili** finestra. La proprietà EvaluateAsExpression nel **delle proprietà** finestra viene impostata automaticamente su `True`.  
  
-   Quando si assegna un'espressione a una variabile, accanto a quest'ultima viene visualizzato un marcatore icona speciale. Tale marcatore icona speciale viene visualizzato anche accanto alle gestioni connessioni e alle attività in cui sono impostate espressioni.  
  
-   Tramite la finestra **Variabili** della variabile è possibile accedere alla finestra di dialogo **Generatore di espressioni** , che consente di compilare, convalidare e valutare le espressioni. Per altre informazioni, vedere [Generatore di espressioni](expressions/expression-builder.md) e [Espressioni di Integration Services &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md).  
  
 In entrambi i **variabili** e **delle proprietà** finestra, se si assegna un'espressione alla variabile, e `EvaluateAsExpression` è impostata su `True`, non è possibile modificare il tipo di dati della variabile.  
  
 **Impostazione delle proprietà di nome e Namespace**  
  
 I valori del `Name` e `Namespace` proprietà devono iniziare con una lettera carattere alfabetico, come definito dallo Standard Unicode 2.0, o un carattere di sottolineatura (_). I caratteri successivi possono includere lettere o numeri, come definito dallo standard Unicode 2.0, o il carattere di sottolineatura (\_).  
  
## <a name="using-the-variables-window-to-set-properties"></a>Utilizzo della finestra Variabili per impostare le proprietà  
  
#### <a name="to-set-the-properties-of-a-variable-by-using-the-variables-window"></a>Per impostare le proprietà di una variabile utilizzando la finestra Variabili  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]aprire il progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] che contiene il pacchetto desiderato.  
  
2.  In Esplora soluzioni fare clic con il pulsante destro del mouse sul pacchetto in modo da aprirlo.  
  
3.  Scegliere **Variabili** dal menu **SSIS**.  
  
     Facoltativamente, è possibile visualizzare la finestra **Variabili** eseguendo il mapping del comando View.Variables a una combinazione di tasti scelta dall'utente nella pagina **Tastiera** della finestra di dialogo **Opzioni** .  
  
4.  Facoltativamente, nella finestra **Variabili** fare clic su **Opzioni griglia**, quindi selezionare le colonne che si vuole visualizzare nella finestra **Variabili** e selezionare i filtri da applicare all'elenco di variabili.  
  
5.  Selezionare la variabile nell'elenco e quindi aggiornare i valori di `Name`, **tipo di dati**, `Value`, `Namespace`, **Raise Change Event**, **descrizione,** e `Expression` colonne.  
  
6.  Selezionare la variabile nell'elenco e quindi fare clic su **Sposta variabile** per modificarne l'ambito.  
  
7.  Per salvare il pacchetto aggiornato, dal menu **File** scegliere **Salva elementi selezionati**.  
  
## <a name="using-the-properties-window-to-set-properties"></a>Utilizzo della finestra Proprietà per impostare le proprietà  
  
#### <a name="to-set-the-properties-of-a-variable-by-using-the-properties-window"></a>Per impostare le proprietà di una variabile utilizzando la finestra Proprietà  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]aprire il progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] che contiene il pacchetto desiderato.  
  
2.  In Esplora soluzioni fare clic con il pulsante destro del mouse sul pacchetto in modo da aprirlo.  
  
3.  Scegliere **Finestra Proprietà** dal menu **Visualizza**.  
  
4.  In Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] fare clic sulla scheda **Esplora pacchetti** ed espandere il nodo Pacchetto.  
  
5.  Per modificare le variabili con ambito pacchetto, espandere il nodo Variabili oppure espandere il nodo Gestori eventi o File eseguibili fino a individuare il nodo Variabili contenente la variabile che si desidera modificare.  
  
6.  Fare clic sulla variabile di cui si desidera modificare le proprietà.  
  
7.  Nella finestra **Proprietà** aggiornare le proprietà delle variabili in lettura/scrittura. Alcune proprietà sono di sola lettura per le variabili definite dall'utente.  
  
     Per altre informazioni sulle proprietà, vedere [Variabili di Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md).  
  
8.  Per salvare il pacchetto aggiornato, dal menu **File** scegliere **Salva elementi selezionati**.  
  
## <a name="see-also"></a>Vedere anche  
 [Servizi di integrazione &#40;SSIS&#41; variabili](integration-services-ssis-variables.md)   
 [Utilizzo di variabili nei pacchetti](../../2014/integration-services/use-variables-in-packages.md)   
 [Aggiungere, eliminare o modificare l'ambito della variabile definita dall'utente in un pacchetto](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)  
  
  