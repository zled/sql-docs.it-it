---
title: Oggetto DataSources (TMSL) | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0a83ac3429a3012269a35c64ba5fdcbec18b2d4c
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2018
ms.locfileid: "40392636"
---
# <a name="datasources-object-tmsl"></a>Oggetto DataSources (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Definisce una connessione a un'origine dati utilizzata dal modello sia durante l'importazione per aggiungere dati al modello o in pass-through query tramite la modalità DirectQuery.  I modelli in modalità DirectQuery possono avere solo un **DataSource** oggetto.  
  
 A meno che non si sta creando, sostituzione, oppure modificare l'oggetto di origine dati stesso, qualsiasi origine dati cui viene fatto riferimento nello script (ad esempio script di partizione) deve essere un oggetto esistente **DataSource** oggetto nel modello.  
  
## <a name="object-definition"></a>Definizione dell'oggetto  
 Tutti gli oggetti hanno un set comune di proprietà, inclusi nome, tipo, descrizione, una raccolta di proprietà e le annotazioni. **DataSource** oggetti contengono anche le proprietà seguenti.  
  
 Tipo  
 Tipo di origine dati. Al momento, l'unico valore valido è Provider (1) - stringa di connessione normale.  
  
 connectionString  
 La stringa di connessione che specifica il database e server minima, ma può anche includere altre proprietà supportate dal sistema RDBMS esterno, ad esempio un account utente o del provider di dati. Questo valore è obbligatorio. Visualizzare [classe SqlConnectionStringBuilder](/dotnet/framework/data/adonet/connection-string-syntax) per informazioni dettagliate su SQL Server database di proprietà della stringa di connessione.  
  
 valore di impersonationMode  
 Specifica se Analysis Services deve rappresentare l'identità dell'utente che richiede la query. Questa proprietà è un valore numerico che specifica le credenziali da utilizzare per la rappresentazione. I valori di enumerazione sono i seguenti:  
  
-   Default (1): il server usa il metodo di rappresentazione che ritiene appropriata per il contesto in cui viene utilizzata la rappresentazione.  
  
-   ImpersonateAccount (2): il server utilizza l'account utente specificato.  
  
-   ImpersonateAnonymous (3): il server utilizza l'account utente anonimo.  Questa opzione non è consigliata, ma viene a volte usata in scenari di accesso HTTP per le applicazioni personalizzate che gestiscono l'autenticazione.  
  
-   ImpersonateCurrentUser (4): il server utilizza l'account utente che il client si connette come.  
  
-   ImpersonateServiceAccount (5): il server utilizza l'account utente che il server è in esecuzione come.  
  
-   ImpersonateUnattendedAccount (6): il server utilizza un account di esecuzione automatica. Viene utilizzato per i modelli tabulari o Power Pivot che vengono eseguiti in un ambiente SharePoint.  
  
 La modalità DirectQuery possa usare impersonateCurrentuser se Analysis Services è configurato per la delega trusted, o  
                      impersonateServiceAccount se la richiesta di query viene eseguita nel contesto di sicurezza dell'account del servizio Analysis Services. Visualizzare [Configure Analysis Services for Kerberos per la delega vincolata](../../analysis-services/instances/configure-analysis-services-for-kerberos-constrained-delegation.md).  
  
 account  
 Utilizzato per la rappresentazione. Un account di Windows o un database con un account di accesso valido con autorizzazioni di lettura per il database esterno.  
  
 password  
 Una stringa crittografata specificando la password dell'account.  
  
 maxConnections  
 Numero massimo di connessioni da aprire simultaneamente all'origine dati.  
  
 isolation  
 Il tipo di isolamento utilizzato durante l'esecuzione di comandi sull'origine dati. I valori validi sono ReadCommitted (1) o uno Snapshot (2).  
  
 timeout  
 Valore intero che specifica il timeout in secondi per i comandi eseguiti sull'origine dati.  
  
 provider  
 Stringa facoltativa che identifica il nome del provider di dati gestiti utilizzato per la connessione al database relazionale, se non diversamente specificato nella stringa di connessione.  
  
## <a name="usage"></a>Utilizzo  
 **DataSource** gli oggetti vengono usati [Alter-comando &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/alter-command-tmsl.md), [creare comandi &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/create-command-tmsl.md), [comando CreateOrReplace &#40; TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/createorreplace-command-tmsl.md), [comando Delete &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/delete-command-tmsl.md), [comando Refresh &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/refresh-command-tmsl.md), e [comando MergePartitions &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/mergepartitions-command-tmsl.md).  
  
 Oggetto **DataSource** oggetto è una proprietà di un modello, ma può anche essere specificato come una proprietà di un oggetto di Database ha il mapping uno a uno tra modello e il Database.  Partizioni basate su query SQL specificare anche un **DataSource**, solo con un set ridotto di proprietà.  
  
 Durante la creazione, sostituzione o modifica di un oggetto origine dati, specificare tutte le proprietà di lettura / scrittura della definizione dell'oggetto. Omissione di una proprietà di lettura e scrittura viene considerata un'operazione di eliminazione.  
  
## <a name="examples"></a>Esempi  
 **Esempio 1** -una connessione a un *FoodMart* database in un server remoto un'istanza denominato di *Sales* in un server di rete denominato *Server01*.  
  
```  
"dataSources": [  
      {  
        "name": "SqlServer Server01 FoodMart",  
        "connectionString": "Provider=SQLNCLI11;Data Source=Server01\Sales;Initial Catalog=Foodmart;Integrated Security=SSPI;Persist Security Info=false",  
        "impersonationMode": "impersonateServiceAccount",  
      }  
]  
```  
  
## <a name="full-syntax"></a>Sintassi completa  
 Di seguito è la rappresentazione dello schema di un oggetto origine dati di un modello.  
  
```  
"dataSources": {  
          "type": "array",  
          "items": {  
            "anyOf": [  
              {  
                "description": "ProviderDataSource object of Tabular Object Model (TOM)",  
                "type": "object",  
                "properties": {  
                  "name": {  
                    "type": "string"  
                  },  
                  "description": {  
                    "type": "string"  
                  },  
                  "type": {  
                    "enum": [  
                      "provider"  
                    ]  
                  },  
                  "connectionString": {  
                    "type": "string"  
                  },  
                  "impersonationMode": {  
                    "enum": [  
                      "default",  
                      "impersonateAccount",  
                      "impersonateAnonymous",  
                      "impersonateCurrentUser",  
                      "impersonateServiceAccount",  
                      "impersonateUnattendedAccount"  
                    ]  
                  },  
                  "account": {  
                    "type": "string"  
                  },  
                  "password": {  
                    "type": "string"  
                  },  
                  "maxConnections": {  
                    "type": "integer"  
                  },  
                  "isolation": {  
                    "enum": [  
                      "readCommitted",  
                      "snapshot"  
                    ]  
                  },  
                  "timeout": {  
                    "type": "integer"  
                  },  
                  "provider": {  
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
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference (Riferimento a Tabular Model Scripting Language &#40;TMSL&#41;)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Modalità DirectQuery](../../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)   
 [Configurare l'accesso HTTP ad Analysis Services in Internet Information Services &#40;IIS&#41; 8.0](../../analysis-services/instances/configure-http-access-to-analysis-services-on-iis-8-0.md)  
  
  
