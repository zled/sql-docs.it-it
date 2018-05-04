---
title: Oggetto tabelle (TMSL) | Documenti Microsoft
ms.custom: ''
ms.date: 05/30/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 98da08fc-8744-4d0f-bc62-e63f1e9e6b08
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: befd3f17f034151924cc962eb5355bd7543ffddb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="tables-object-tmsl"></a>Oggetto tabelle (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Definisce le tabelle contenute in un modello. Tabelle in un modello utente sono associate a tabelle in un database esterno da cui i dati vengono importati o eseguire una query o una tabella calcolata costruita da un'espressione DAX. All'interno di una tabella, una o più **partizione** oggetti descrivono l'origine dei dati.  Tra le tabelle, una **relazione** oggetto specifica la cardinalità, direzione filtro e altre proprietà della relazione.  
  
## <a name="object-definition"></a>Definizione di oggetto  
 Tutti gli oggetti hanno un set comune di proprietà, inclusi nome, tipo, descrizione, una raccolta di proprietà e le annotazioni. **Tabella** oggetti hanno anche le proprietà seguenti.  
  
 dataCategory  
 Specifica il tipo di tabella, in genere a sinistra non specificato. I valori validi sono 0 - sconosciuto, 1 - ora, 2 - misura, - 3, 5 - quantitativa, 6-account, 7 - clienti, prodotti-8, 9 - SCENARIO 10: utilità, valuta - 11, 12 - velocità, 4 - innalzamento di livello, 15 - 16 organizzazione - 13 - canale distinta base, 17: GEOGRAPHY.  
  
 isHidden  
 Valore booleano che indica se la tabella viene considerata come nascosti dagli strumenti di visualizzazione di client.  
True se l'oggetto Table viene considerato come nascosto; in caso contrario, false.  
  
 colonne  
 Rappresenta una colonna in una tabella. È un elemento figlio di un oggetto Table. Ogni colonna ha un numero di proprietà in cui è definito che determinano come applicazioni client di visualizzare i dati nella colonna.  
  
 misure  
 Rappresenta un valore calcolato in base a un'espressione. È un elemento figlio di un oggetto Table.  
  
 gerarchie  
 Rappresenta una raccolta di livelli che forniscono un percorso di drill-down gerarchico logico per le applicazioni client. È un elemento figlio di un oggetto Table.  
  
## <a name="usage"></a>Utilizzo  
 Tabella oggetti vengono utilizzati negli [Alter-comando &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/alter-command-tmsl.md), [creare comandi &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/create-command-tmsl.md), [comando CreateOrReplace &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-commands/createorreplace-command-tmsl.md), [Eliminare comandi &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/delete-command-tmsl.md), [comando Refresh &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/refresh-command-tmsl.md), e [comando MergePartitions &#40;&#41;](../../analysis-services/tabular-models-scripting-language-commands/mergepartitions-command-tmsl.md).  
  
 Durante la creazione, la sostituzione o modifica di un oggetto tabella, specificare tutte le proprietà di sola lettura della definizione dell'oggetto. Omissione di una proprietà di lettura / scrittura è considerata un'operazione di eliminazione.  
  
## <a name="condensed-syntax"></a>Sintassi abbreviata  
 Le definizioni degli oggetti di tabella sono complessi. Questa sintassi consente di comprimere le proprietà interne e oggetti per fornire una panoramica sulle parti principali.  
  
```  
"tables": {  
          "type": "array",  
          "items": {  
            "description": "Table object of Tabular Object Model (TOM)",  
            "type": "object",  
            "properties": {    
              "dataCategory": {  },  
              "description": {  },  
              "isHidden": {  },  
              "partitions": {  },  
              "annotations": {  },  
              "columns": {  },  
              "measures": {   },  
              "hierarchies": {  },  
```  
  
## <a name="full-syntax"></a>Sintassi completa  
 Di seguito è la rappresentazione dello schema di un oggetto di tabelle di un modello. Per ridurre le dimensioni di questa definizione, gli oggetti di partizione sono descritti in un' posizione. Vedere [oggetto partizioni &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/partitions-object-tmsl.md).  
  
```  
"tables": {  
          "type": "array",  
          "items": {  
            "description": "Table object of Tabular Object Model (TOM)",  
            "type": "object",  
            "properties": {  
              "name": {  
                "type": "string"  
              },  
              "dataCategory": {  
                "type": "string"  
              },  
              "description": {  
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
              },  
              "isHidden": {  
                "type": "boolean"  
              },  
              "partitions":  {   
                 },  
              "columns": {  
                "type": "array",  
                "items": {  
                  "anyOf": [  
                    {  
                      "description": "DataColumn object of Tabular Object Model (TOM)",  
                      "type": "object",  
                      "properties": {  
                        "name": {  
                          "type": "string"  
                        },  
                        "dataType": {  
                          "enum": [  
                            "automatic",  
                            "string",  
                            "int64",  
                            "double",  
                            "dateTime",  
                            "decimal",  
                            "boolean",  
                            "binary",  
                            "unknown",  
                            "variant"  
                          ]  
                        },  
                        "dataCategory": {  
                          "type": "string"  
                        },  
                        "description": {  
                          "type": "string"  
                        },  
                        "isHidden": {  
                          "type": "boolean"  
                        },  
                        "isUnique": {  
                          "type": "boolean"  
                        },  
                        "isKey": {  
                          "type": "boolean"  
                        },  
                        "isNullable": {  
                          "type": "boolean"  
                        },  
                        "alignment": {  
                          "enum": [  
                            "default",  
                            "left",  
                            "right",  
                            "center"  
                          ]  
                        },  
                        "tableDetailPosition": {  
                          "type": "integer"  
                        },  
                        "isDefaultLabel": {  
                          "type": "boolean"  
                        },  
                        "isDefaultImage": {  
                          "type": "boolean"  
                        },  
                        "summarizeBy": {  
                          "enum": [  
                            "default",  
                            "none",  
                            "sum",  
                            "min",  
                            "max",  
                            "count",  
                            "average",  
                            "distinctCount"  
                          ]  
                        },  
                        "type": {  
                          "enum": [  
                            "data",  
                            "calculated",  
                            "rowNumber",  
                            "calculatedTableColumn"  
                          ]  
                        },  
                        "formatString": {  
                          "type": "string"  
                        },  
                        "isAvailableInMdx": {  
                          "type": "boolean"  
                        },  
                        "keepUniqueRows": {  
                          "type": "boolean"  
                        },  
                        "displayOrdinal": {  
                          "type": "integer"  
                        },  
                        "sourceProviderType": {  
                          "type": "string"  
                        },  
                        "displayFolder": {  
                          "type": "string"  
                        },  
                        "sourceColumn": {  
                          "type": "string"  
                        },  
                        "sortByColumn": {  
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
                    },  
                    {  
                      "description": "CalculatedTableColumn object of Tabular Object Model (TOM)",  
                      "type": "object",  
                      "properties": {  
                        "name": {  
                          "type": "string"  
                        },  
                        "dataType": {  
                          "enum": [  
                            "automatic",  
                            "string",  
                            "int64",  
                            "double",  
                            "dateTime",  
                            "decimal",  
                            "boolean",  
                            "binary",  
                            "unknown",  
                            "variant"  
                          ]  
                        },  
                        "dataCategory": {  
                          "type": "string"  
                        },  
                        "description": {  
                          "type": "string"  
                        },  
                        "isHidden": {  
                          "type": "boolean"  
                        },  
                        "isUnique": {  
                          "type": "boolean"  
                        },  
                        "isKey": {  
                          "type": "boolean"  
                        },  
                        "isNullable": {  
                          "type": "boolean"  
                        },  
                        "alignment": {  
                          "enum": [  
                            "default",  
                            "left",  
                            "right",  
                            "center"  
                          ]  
                        },  
                        "tableDetailPosition": {  
                          "type": "integer"  
                        },  
                        "isDefaultLabel": {  
                          "type": "boolean"  
                        },  
                        "isDefaultImage": {  
                          "type": "boolean"  
                        },  
                        "summarizeBy": {  
                          "enum": [  
                            "default",  
                            "none",  
                            "sum",  
                            "min",  
                            "max",  
                            "count",  
                            "average",  
                            "distinctCount"  
                          ]  
                        },  
                        "type": {  
                          "enum": [  
                            "data",  
                            "calculated",  
                            "rowNumber",  
                            "calculatedTableColumn"  
                          ]  
                        },  
                        "formatString": {  
                          "type": "string"  
                        },  
                        "isAvailableInMdx": {  
                          "type": "boolean"  
                        },  
                        "keepUniqueRows": {  
                          "type": "boolean"  
                        },  
                        "displayOrdinal": {  
                          "type": "integer"  
                        },  
                        "sourceProviderType": {  
                          "type": "string"  
                        },  
                        "displayFolder": {  
                          "type": "string"  
                        },  
                        "isNameInferred": {  
                          "type": "boolean"  
                        },  
                        "isDataTypeInferred": {  
                          "type": "boolean"  
                        },  
                        "sourceColumn": {  
                          "type": "string"  
                        },  
                        "sortByColumn": {  
                          "type": "string"  
                        },  
                        "columnOriginTable": {  
                          "type": "string"  
                        },  
                        "columnOriginColumn": {  
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
                    },  
                    {  
                      "description": "CalculatedColumn object of Tabular Object Model (TOM)",  
                      "type": "object",  
                      "properties": {  
                        "name": {  
                          "type": "string"  
                        },  
                        "dataType": {  
                          "enum": [  
                            "automatic",  
                            "string",  
                            "int64",  
                            "double",  
                            "dateTime",  
                            "decimal",  
                            "boolean",  
                            "binary",  
                            "unknown",  
                            "variant"  
                          ]  
                        },  
                        "dataCategory": {  
                          "type": "string"  
                        },  
                        "description": {  
                          "type": "string"  
                        },  
                        "isHidden": {  
                          "type": "boolean"  
                        },  
                        "isUnique": {  
                          "type": "boolean"  
                        },  
                        "isKey": {  
                          "type": "boolean"  
                        },  
                        "isNullable": {  
                          "type": "boolean"  
                        },  
                        "alignment": {  
                          "enum": [  
                            "default",  
                            "left",  
                            "right",  
                            "center"  
                          ]  
                        },  
                        "tableDetailPosition": {  
                          "type": "integer"  
                        },  
                        "isDefaultLabel": {  
                          "type": "boolean"  
                        },  
                        "isDefaultImage": {  
                          "type": "boolean"  
                        },  
                        "summarizeBy": {  
                          "enum": [  
                            "default",  
                            "none",  
                            "sum",  
                            "min",  
                            "max",  
                            "count",  
                            "average",  
                            "distinctCount"  
                          ]  
                        },  
                        "type": {  
                          "enum": [  
                            "data",  
                            "calculated",  
                            "rowNumber",  
                            "calculatedTableColumn"  
                          ]  
                        },  
                        "formatString": {  
                          "type": "string"  
                        },  
                        "isAvailableInMdx": {  
                          "type": "boolean"  
                        },  
                        "keepUniqueRows": {  
                          "type": "boolean"  
                        },  
                        "displayOrdinal": {  
                          "type": "integer"  
                        },  
                        "sourceProviderType": {  
                          "type": "string"  
                        },  
                        "displayFolder": {  
                          "type": "string"  
                        },  
                        "isDataTypeInferred": {  
                          "type": "boolean"  
                        },  
                        "expression": {  
                          "type": "string"  
                        },  
                        "sortByColumn": {  
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
              },  
              "measures": {  
                "type": "array",  
                "items": {  
                  "description": "Measure object of Tabular Object Model (TOM)",  
                  "type": "object",  
                  "properties": {  
                    "name": {  
                      "type": "string"  
                    },  
                    "description": {  
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
                    },  
                    "expression": {  
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
                    },  
                    "formatString": {  
                      "type": "string"  
                    },  
                    "isHidden": {  
                      "type": "boolean"  
                    },  
                    "isSimpleMeasure": {  
                      "type": "boolean"  
                    },  
                    "displayFolder": {  
                      "type": "string"  
                    },  
                    "kpi": {  
                      "description": "KPI object of Tabular Object Model (TOM)",  
                      "type": "object",  
                      "properties": {  
                        "description": {  
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
                        },  
                        "targetDescription": {  
                          "type": "string"  
                        },  
                        "targetExpression": {  
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
                        },  
                        "targetFormatString": {  
                          "type": "string"  
                        },  
                        "statusGraphic": {  
                          "type": "string"  
                        },  
                        "statusDescription": {  
                          "type": "string"  
                        },  
                        "statusExpression": {  
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
                        },  
                        "trendGraphic": {  
                          "type": "string"  
                        },  
                        "trendDescription": {  
                          "type": "string"  
                        },  
                        "trendExpression": {  
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
              },  
              "hierarchies": {  
                "type": "array",  
                "items": {  
                  "description": "Hierarchy object of Tabular Object Model (TOM)",  
                  "type": "object",  
                  "properties": {  
                    "name": {  
                      "type": "string"  
                    },  
                    "description": {  
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
                    },  
                    "isHidden": {  
                      "type": "boolean"  
                    },  
                    "displayFolder": {  
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
                    },  
                    "levels": {  
                      "type": "array",  
                      "items": {  
                        "description": "Level object of Tabular Object Model (TOM)",  
                        "type": "object",  
                        "properties": {  
                          "ordinal": {  
                            "type": "integer"  
                          },  
                          "name": {  
                            "type": "string"  
                          },  
                          "description": {  
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
                          },  
                          "column": {  
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
                    }  
                  },  
                  "additionalProperties": false  
                }  
              }  
            },  
            "additionalProperties": false  
          }  
        }  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference (Riferimento al linguaggio di scripting per modelli tabulari &#40;TMSL&#41;)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  
