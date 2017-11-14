---
title: Comando CreateOrReplace (TMSL) | Documenti Microsoft
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f77a0e04-461a-4fa8-b997-78057e410d56
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 62d90be2b4fe8aea96534c7c4d8b2b4617ac1ea1
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="createorreplace-command-tmsl"></a>Comando CreateOrReplace (TMSL)

[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

  Crea o sostituisce l'oggetto specificato e tutti gli oggetti discendenti specificati. Vengono creati oggetti inesistente. Gli oggetti esistenti vengono sostituiti con la nuova definizione.  
  
 Ogni volta che si specifica una proprietà di lettura / scrittura, assicurarsi di includere tutti. Omissione di un oggetto di lettura / scrittura è considerata un'operazione di eliminazione.  
  
## <a name="request"></a>Richiesta  
 La struttura della richiesta varia in base all'oggetto. Un oggetto che rappresenta un elemento padre deve includere tutti i relativi figli, anche se le definizioni di oggetto completo degli elementi di pari livello e di elementi padre non sono necessari.  
  
 [Oggetto di database &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/database-object-tmsl.md)  
  
 Sostituisce un database esistente con una definizione di database rinominato, minima che specifica il nome, le proprietà del modello modificato e una connessione. Poiché la definizione dell'oggetto non include le relazioni, partizioni o tabelle, tutti gli oggetti vengono eliminati.  
  
```  
{  
  "createOrReplace": {  
    "object": {  
      "database": "AdventureWorksTabular1200"  
    },  
    "database": {  
      "name": "TestCreateOrReplaceDB",  
      "id": "newID",  
      "compatibilityLevel": 1200,  
      "model": {  
        "defaultMode": "import",  
        "culture": "en-US",  
        "dataSources": [  
          {  
            "name": "SqlServer localhost AdventureworksDW2016",  
            "connectionString": "Provider=SQLNCLI11;Data Source=localhost;Initial Catalog=AdventureworksDW2016;Integrated Security=SSPI;Persist Security Info=false",  
            "impersonationMode": "impersonateAccount",  
            "account": "   ",  
            "annotations": [  
              {  
                "name": "ConnectionEditUISource",  
                "value": "SqlServer"  
              }  
            ]  
          }  
        ]  
      }  
    }  
  }  
}  
```  
  
 [Oggetto di origini dati &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-objects/datasources-object-tmsl.md) Sostituisce il nome della connessione.  
  
```  
{  
  "createOrReplace": {  
    "object": {  
      "database": "TestCreateOrReplaceDB",  
      "dataSource": "SqlServer localhost AdventureworksDW2016"  
    },  
    "dataSource": {  
      "name": "New connection name",  
      "connectionString": "Provider=SQLNCLI11;Data Source=localhost;Initial Catalog=AdventureworksDW2016;Integrated Security=SSPI;Persist Security Info=false",  
      "impersonationMode": "impersonateAccount",  
      "account": "   ",  
      "annotations": [  
        {  
          "name": "ConnectionEditUISource",  
          "value": "SqlServer"  
        }  
      ]  
    }  
  }  
}  
```  
  
 [Oggetto tabelle &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-objects/tables-object-tmsl.md) Sovrascrive le tabelle esistenti, lasciando solo a quella specificata.  
  
```  
{  
  "createOrReplace": {  
    "object": {  
      "database": "AdventureWorksTabular1200"  
    },  
    "database": {  
      "name": "AdventureWorksTabular1200",  
      "id": "New-AdventureWorksTabular1200",  
      "compatibilityLevel": 1200,  
      "model": {  
        "defaultMode": "import",  
        "culture": "en-US",  
        "dataSources": [  
          {  
            "name": "SqlServer localhost AdventureworksDW2016",  
            "connectionString": "Provider=SQLNCLI11;Data Source=localhost;Initial Catalog=AdventureworksDW2016;Integrated Security=SSPI;Persist Security Info=false",  
            "impersonationMode": "impersonateAccount",  
            "account": "   ",  
            "annotations": [  
              {  
                "name": "ConnectionEditUISource",  
                "value": "SqlServer"  
              }  
            ]  
          }  
        ],  
        "tables": [  
          {  
            "name": "Date",  
            "columns": [  
              {  
                "name": "DateKey",  
                "dataType": "int64",  
                "sourceColumn": "DateKey",  
                "sourceProviderType": "Integer"  
              },  
              {  
                "name": "FullDateAlternateKey",  
                "dataType": "dateTime",  
                "sourceColumn": "FullDateAlternateKey",  
                "formatString": "General Date",  
                "sourceProviderType": "DBDate"  
              },  
              {  
                "name": "CalendarYear",  
                "dataType": "int64",  
                "sourceColumn": "CalendarYear",  
                "sourceProviderType": "SmallInt"  
              }  
            ],  
            "partitions": [  
              {  
                "name": "DimDate",  
                "dataView": "full",  
                "source": {  
                  "query": " SELECT [dbo].[DimDate].* FROM [dbo].[DimDate] ",  
                  "dataSource": "SqlServer localhost AdventureworksDW2016"  
                }  
              }  
            ],  
            "annotations": [  
              {  
                "name": "_TM_ExtProp_QueryDefinition",  
                "value": " SELECT [dbo].[DimDate].* FROM [dbo].[DimDate] "  
              },  
              {  
                "name": "_TM_ExtProp_DbTableName",  
                "value": "DimDate"  
              },  
              {  
                "name": "_TM_ExtProp_DbSchemaName",  
                "value": "dbo"  
              }  
            ]  
          }  
        ]  
     }  
   }  
 }  
}   
```  
  
 [Oggetto partizioni &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/partitions-object-tmsl.md)  
  
 Sostituire un nome di partizione. Oggetti partizione dispongono di tre proprietà di lettura / scrittura: nome, origine, descrizione. Ogni volta che si specifica una proprietà di lettura / scrittura, assicurarsi di includere tutti. Omissione di un oggetto di lettura / scrittura è considerata un'operazione di eliminazione.  
  
 Poiché la definizione dell'oggetto è la partizione, è stata interessata solo la partizione denominata e la relativa definizione. Altre tabelle, relazioni e le partizioni non sono interessate.  
  
 A meno che non si sta creando, sostituendo, o modificare l'oggetto di origine dati stessa, qualsiasi origine dati a cui fa riferimento nello script (ad esempio lo script di partizione seguente) deve essere un oggetto esistente **DataSource** oggetto nel modello. Se è necessario modificare l'origine dati, aggiungerlo alla  
  
```  
{  
  "createOrReplace": {  
    "object": {  
      "database": "AdventureWorksTabular1200",  
      "table": "FactSalesQuota",  
      "partition": "FactSalesQuota - 2011"  
    },  
    "partition": {  
      "name": "Sales Quota for 2011",  
      "mode": "import",  
      "dataView": "full",  
      "source": {  
        "query": [  
          "SELECT [dbo].[FactSalesQuota].* FROM [dbo].[FactSalesQuota]",  
          "JOIN DimDate as DD",  
          "on DD.DateKey = FactSalesQuota.DateKey",  
          "WHERE DD.CalendarYear='2011'"  
        ],  
        "dataSource": "SqlServer localhost AdventureworksDW2016"  
      }  
    }  
  }  
}  
```  
  
 [Oggetto ruoli &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md) Sostituisce una definizione di ruolo con uno che include i membri.  
  
```  
{  
  "createOrReplace": {  
    "object": {  
      "database": "AdventureWorksTabular1200",  
      "role": "DataReader"  
    },  
    "role": {  
      "name": "DataReader",  
      "modelPermission": "read",  
      "members": [  
        {  
          "memberName": "ADVENTUREWORKS\\InternalSalesGrp"  
        }  
      ]  
    }  
  }  
}  
```  
  
## <a name="response"></a>Risposta  
 Quando il comando ha esito positivo, restituisce un risultato vuoto. In caso contrario, viene restituita un'eccezione di XMLA.  
  
## <a name="examples"></a>Esempi  
 **Esempio 1** -crea un nuovo database, sovrascrivendo un database esistente con lo stesso nome.  
  
```  
{  
  "createOrReplace": {  
    "object": {  
      "database": "AdventureWorksTabular1200"  
    },  
    "database": {  
      "name": "AdventureWorksTabular1200",  
      "id": "AdventureWorksTabular1200",  
      "compatibilityLevel": 1200,  
      "model": {  
        "defaultMode": "directQuery",  
        "culture": "en-US",  
        "dataSources": [  
          {  
            "name": "SqlServer localhost AdventureworksDW2016",  
            "connectionString": "Provider=SQLNCLI11;Data Source=localhost;Initial Catalog=AdventureworksDW2016;Integrated Security=SSPI;Persist Security Info=false",  
            "impersonationMode": "impersonateAccount",  
            "account": "   ",  
            "annotations": [  
              {  
                "name": "ConnectionEditUISource",  
                "value": "SqlServer"  
              }  
            ]  
          }  
        ],  
        "tables": [  
          {  
            "name": "DimDate",  
            "columns": [  
              {  
                "name": "DateKey",  
                "dataType": "int64",  
                "sourceColumn": "DateKey",  
                "sourceProviderType": "Integer"  
              },  
              {  
                "name": "FullDateAlternateKey",  
                "dataType": "dateTime",  
                "sourceColumn": "FullDateAlternateKey",  
                "formatString": "General Date",  
                "sourceProviderType": "DBDate"  
              },  
              {  
                "name": "CalendarYear",  
                "dataType": "int64",  
                "sourceColumn": "CalendarYear",  
                "sourceProviderType": "SmallInt"  
              }  
            ],  
            "partitions": [  
              {  
                "name": "DimDate",  
                "dataView": "full",  
                "source": {  
                  "query": " SELECT [dbo].[DimDate].* FROM [dbo].[DimDate] ",  
                  "dataSource": "SqlServer localhost AdventureworksDW2016"  
                }  
              }  
            ],  
            "annotations": [  
              {  
                "name": "_TM_ExtProp_QueryDefinition",  
                "value": " SELECT [dbo].[DimDate].* FROM [dbo].[DimDate] "  
              },  
              {  
                "name": "_TM_ExtProp_DbTableName",  
                "value": "DimDate"  
              },  
              {  
                "name": "_TM_ExtProp_DbSchemaName",  
                "value": "dbo"  
              }  
            ]  
          },  
          {  
            "name": "DimEmployee",  
            "columns": [  
              {  
                "name": "EmployeeKey",  
                "dataType": "int64",  
                "sourceColumn": "EmployeeKey",  
                "sourceProviderType": "Integer"  
              },  
              {  
                "name": "SalesTerritoryKey",  
                "dataType": "int64",  
                "sourceColumn": "SalesTerritoryKey",  
                "sourceProviderType": "Integer"  
              },  
              {  
                "name": "FirstName",  
                "dataType": "string",  
                "sourceColumn": "FirstName",  
                "sourceProviderType": "WChar"  
              },  
              {  
                "name": "LastName",  
                "dataType": "string",  
                "sourceColumn": "LastName",  
                "sourceProviderType": "WChar"  
              },  
              {  
                "name": "MiddleName",  
                "dataType": "string",  
                "sourceColumn": "MiddleName",  
                "sourceProviderType": "WChar"  
              },  
              {  
                "name": "SalesPersonFlag",  
                "dataType": "boolean",  
                "sourceColumn": "SalesPersonFlag",  
                "formatString": "\"TRUE\";\"TRUE\";\"FALSE\"",  
                "sourceProviderType": "Boolean"  
              },  
              {  
                "name": "DepartmentName",  
                "dataType": "string",  
                "sourceColumn": "DepartmentName",  
                "sourceProviderType": "WChar"  
              }  
            ],  
            "partitions": [  
              {  
                "name": "DimEmployee",  
                "dataView": "full",  
                "source": {  
                  "query": " SELECT [dbo].[DimEmployee].* FROM [dbo].[DimEmployee] ",  
                  "dataSource": "SqlServer localhost AdventureworksDW2016"  
                }  
              }  
            ],  
            "annotations": [  
              {  
                "name": "_TM_ExtProp_QueryDefinition",  
                "value": " SELECT [dbo].[DimEmployee].* FROM [dbo].[DimEmployee] "  
              },  
              {  
                "name": "_TM_ExtProp_DbTableName",  
                "value": "DimEmployee"  
              },  
              {  
                "name": "_TM_ExtProp_DbSchemaName",  
                "value": "dbo"  
              }  
            ]  
          },  
          {  
            "name": "FactSalesQuota",  
            "columns": [  
              {  
                "name": "SalesQuotaKey",  
                "dataType": "int64",  
                "sourceColumn": "SalesQuotaKey",  
                "sourceProviderType": "Integer"  
              },  
              {  
                "name": "EmployeeKey",  
                "dataType": "int64",  
                "sourceColumn": "EmployeeKey",  
                "sourceProviderType": "Integer"  
              },  
              {  
                "name": "DateKey",  
                "dataType": "int64",  
                "sourceColumn": "DateKey",  
                "sourceProviderType": "Integer"  
              },  
              {  
                "name": "CalendarYear",  
                "dataType": "int64",  
                "sourceColumn": "CalendarYear",  
                "sourceProviderType": "SmallInt"  
              },  
              {  
                "name": "SalesAmountQuota",  
                "dataType": "decimal",  
                "sourceColumn": "SalesAmountQuota",  
                "formatString": "\\$#,0.00;(\\$#,0.00);\\$#,0.00",  
                "sourceProviderType": "Currency",  
                "annotations": [  
                  {  
                    "name": "Format",  
                    "value": "\<Format Format=\"Currency\" Accuracy=\"2\" ThousandSeparator=\"True\">\<Currency LCID=\"1033\" DisplayName=\"$ English (United States)\" Symbol=\"$\" PositivePattern=\"0\" NegativePattern=\"0\" /></Format>"  
                  }  
                ]  
              },  
              {  
                "name": "Date",  
                "dataType": "dateTime",  
                "sourceColumn": "Date",  
                "formatString": "General Date",  
                "sourceProviderType": "DBTimeStamp"  
              }  
            ],  
            "partitions": [  
              {  
                "name": "FactSalesQuota",  
                "dataView": "full",  
                "source": {  
                  "query": " SELECT [dbo].[FactSalesQuota].* FROM [dbo].[FactSalesQuota] ",  
                  "dataSource": "SqlServer localhost AdventureworksDW2016"  
                }  
              },  
              {  
                "name": "FactSalesQuota - 2011",  
                "mode": "import",  
                "dataView": "sample",  
                "source": {  
                  "query": [  
                    "SELECT [dbo].[FactSalesQuota].* FROM [dbo].[FactSalesQuota]",  
                    "JOIN DimDate as DD",  
                    "on DD.DateKey = FactSalesQuota.DateKey",  
                    "WHERE DD.CalendarYear='2011'"  
                  ],  
                  "dataSource": "SqlServer localhost AdventureworksDW2016"  
                },  
                "annotations": [  
                  {  
                    "name": "QueryEditorSerialization",  
                    "value": [  
                      "\<?xml version=\"1.0\" encoding=\"UTF-16\"?>\<Gemini xmlns=\"QueryEditorSerialization\"><AnnotationContent><![CDATA[<RSQueryCommandText>SELECT [dbo].[FactSalesQuota].* FROM [dbo].[FactSalesQuota]",  
                      "JOIN DimDate as DD",  
                      "on DD.DateKey = FactSalesQuota.DateKey",  
                      "WHERE DD.CalendarYear='2011'</RSQueryCommandText><RSQueryCommandType>Text</RSQueryCommandType><RSQueryDesignState></RSQueryDesignState>]]></AnnotationContent></Gemini>"  
                    ]  
                  }  
                ]  
              }  
            ],  
            "annotations": [  
              {  
                "name": "_TM_ExtProp_QueryDefinition",  
                "value": " SELECT [dbo].[FactSalesQuota].* FROM [dbo].[FactSalesQuota] "  
              },  
              {  
                "name": "_TM_ExtProp_DbTableName",  
                "value": "FactSalesQuota"  
              },  
              {  
                "name": "_TM_ExtProp_DbSchemaName",  
                "value": "dbo"  
              }  
            ]  
          }  
        ],  
        "relationships": [  
          {  
            "name": "4426b078-193f-4a59-bc52-33f990bfb7da",  
            "fromTable": "FactSalesQuota",  
            "fromColumn": "DateKey",  
            "toTable": "DimDate",  
            "toColumn": "DateKey"  
          },  
          {  
            "name": "cde1e139-4553-4d0a-a025-1cd98e35aab2",  
            "fromTable": "FactSalesQuota",  
            "fromColumn": "EmployeeKey",  
            "toTable": "DimEmployee",  
            "toColumn": "EmployeeKey"  
          }  
        ]  
      }  
    }  
  }  
}  
  
```  
  
## <a name="usage-endpoints"></a>Utilizzo (endpoint)  
 Questo elemento di comando viene utilizzato in un'istruzione del [metodo Execute &#40; XMLA &#41; ](../../analysis-services/xmla/xml-elements-methods-execute.md) chiamata su un endpoint XMLA, esposto nei modi seguenti:  
  
-   Come una finestra XMLA in SQL Server Management Studio (SSMS)  
  
-   Come un file di input per il **invoke-ascmd** cmdlet di PowerShell  
  
-   Come input per un processo di SQL Server Agent o l'attività SSIS  
  
 È possibile generare uno script già pronto per questo comando da SSMS.  Ad esempio, è possibile fare doppio clic su un database esistente > **Script** > **crea Script per Database** > **creare o sostituire a**.  
  
 Il [ \[SSAS-MS-T\]: QL Server tabulare di Analysis Services (SQL Server tecniche Protocol)](http://go.microsoft.com/fwlink/p/?LinkId=784855) documento include una sezione 3.1.5.2.2 che descrive la struttura di oggetti e i comandi di metadati tabulari JSON. Attualmente, tale documento vengono illustrati i comandi e le funzionalità non ancora implementata nello script TMSL. Vedere l'argomento [tabulare Model Scripting Language &#40; TMSL &#41; Riferimento](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md) per chiarimenti sui quali è supportata  

## <a name="see-also"></a>Vedere anche  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference (Riferimento al linguaggio di scripting per modelli tabulari &#40;TMSL&#41;)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  

