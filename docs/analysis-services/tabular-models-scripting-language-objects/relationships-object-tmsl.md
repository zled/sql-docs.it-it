---
title: Oggetto di relazioni (TMSL) | Documenti Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bec99999e73ef5bdee795324536f05100ec1b9fe
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="relationships-object-tmsl"></a>Oggetto di relazioni (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Definisce una relazione tra una tabella di origine e di destinazione, con la possibilità di specificare la cardinalità e la direzione di filtri di query e sicurezza.  
  
## <a name="object-definition"></a>Definizione dell'oggetto  
 Tutti gli oggetti hanno un set comune di proprietà, inclusi nome, tipo, descrizione, una raccolta di proprietà e le annotazioni. **Relazione** oggetti hanno anche le proprietà seguenti.  
  
 isActive  
 Valore booleano che indica se la relazione è contrassegnata come attivo o inattivo. Una relazione attiva viene usata automaticamente per il filtro tra tabelle. Una relazione inattiva può essere usata in modo esplicito nei calcoli DAX con la funzione USERELATIONSHIP.  
  
 crossFilteringBehavior  
 Indica le influenze delle relazioni sulle operazioni di filtro dei dati. Vedere [bidirezionale tra i filtri per i modelli tabulari in SQL Server 2016 Analysis Services](../../analysis-services/tabular-models/bi-directional-cross-filters-tabular-models-analysis-services.md) per ulteriori informazioni. I valori validi sono i seguenti:  
  
-   OneDirection (1) - righe selezionate in "To" end della relazione filtrano automaticamente l'analisi della tabella l'entità finale "From" della relazione.  
  
-   BothDirections (2) - filtri alle estremità della relazione filtrano automaticamente l'altra tabella.  
  
-   Automatico (3), il motore di analizzare le relazioni e scegliere uno dei comportamenti mediante euristica.  
  
 joinOnDateBehavior  
 Quando si crea un join di due colonne di data e ora, indica se applicare il join sulle parti della data e dell'ora o solo sulla parte della data.  
  
-   DateAndTime (1) - quando si uniscono due colonne, creare un join sulle parti di data e ora.  
  
-   Creare un join (2) - quando si uniscono due colonne, DatePartOnly solo parte della data.  
  
 relyOnReferentialIntegrity  
 Non usato; riservato per usi futuri.  
  
 securityFilteringBehavior  
 Enumerazione che indica influenze delle relazioni sull'applicazione di filtri dei dati durante la valutazione di espressioni di sicurezza a livello di riga. I valori validi sono i seguenti:  
  
-   OneDirection (1) - righe selezionate in "To" end della relazione filtrano automaticamente l'analisi della tabella l'entità finale "From" della relazione.  
  
-   BothDirections (2) - filtri alle estremità della relazione filtrano automaticamente l'altra tabella.  
  
## <a name="usage"></a>Utilizzo  
 Gli oggetti relazione vengono utilizzati [Alter-comando &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/alter-command-tmsl.md), [creare comandi &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/create-command-tmsl.md), [comando CreateOrReplace &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-commands/createorreplace-command-tmsl.md), e [eliminare comandi &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/delete-command-tmsl.md).  
  
 Durante la creazione, la sostituzione o modifica di un oggetto di relazione, specificare tutte le proprietà di sola lettura della definizione dell'oggetto. Omissione di una proprietà di lettura / scrittura è considerata un'operazione di eliminazione.  
  
## <a name="full-syntax"></a>Sintassi completa  
 Di seguito è la rappresentazione dello schema di un oggetto di relazione.  
  
```  
"relationships": {  
          "type": "array",  
          "items": {  
            "anyOf": [  
              {  
                "description": "SingleColumnRelationship object of Tabular Object Model (TOM)",  
                "type": "object",  
                "properties": {  
                  "name": {  
                    "type": "string"  
                  },  
                  "isActive": {  
                    "type": "boolean"  
                  },  
                  "type": {  
                    "enum": [  
                      "singleColumn"  
                    ]  
                  },  
                  "crossFilteringBehavior": {  
                    "enum": [  
                      "oneDirection",  
                      "bothDirections",  
                      "automatic"  
                    ]  
                  },  
                  "joinOnDateBehavior": {  
                    "enum": [  
                      "dateAndTime",  
                      "datePartOnly"  
                    ]  
                  },  
                  "relyOnReferentialIntegrity": {  
                    "type": "boolean"  
                  },  
                  "securityFilteringBehavior": {  
                    "enum": [  
                      "oneDirection",  
                      "bothDirections"  
                    ]  
                  },  
                  "fromCardinality": {  
                    "enum": [  
                      "none",  
                      "one",  
                      "many"  
                    ]  
                  },  
                  "toCardinality": {  
                    "enum": [  
                      "none",  
                      "one",  
                      "many"  
                    ]  
                  },  
                  "fromColumn": {  
                    "type": "string"  
                  },  
                  "fromTable": {  
                    "type": "string"  
                  },  
                  "toColumn": {  
                    "type": "string"  
                  },  
                  "toTable": {  
                    "type": "string"  
                  },  
                  "annotations": {  
                    "type": "array",  
                    "items": {  
                      "description": "Annotation object of Tabular Object Model (TOM)",  
                      "type": "object",  
                      "properties": {  
                        "name": {  
                          "type": "string"  
                        },  
                        "value": {  
                          "anyOf": [  
                            {  
                              "type": "string"  
                            },  
                            {  
                              "type": "array",  
                              "items": {  
                                "type": "string"  
                              }  
                            }  
                          ]  
                        }  
                      },  
                      "additionalProperties": false  
                    }  
                  }  
                },  
                "additionalProperties": false  
              }  
            ]  
          }  
        }  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference (Riferimento a Tabular Model Scripting Language &#40;TMSL&#41;)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Creare relazioni](../../integration-services/data-flow/transformations/create-relationships.md)  
  
  
