---
title: Oggetto di origini dati (TMSL) | Documenti Microsoft
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
ms.assetid: 1357ae7e-30a4-481a-831c-7b046fe15aa4
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: f05628f84a33f72332f5e4b9aac2712d0c0baf00
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="datasources-object-tmsl"></a>Oggetto di origini dati (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Definisce una connessione a un'origine dati utilizzata dal modello durante l'importazione per aggiungere dati al modello o in pass-through query tramite la modalità DirectQuery.  I modelli in modalità DirectQuery possono avere solo uno **DataSource** oggetto.  
  
 A meno che non si sta creando, sostituendo, o modificare l'oggetto di origine dati stessa, qualsiasi origine dati a cui fa riferimento nello script (ad esempio script partizione) deve essere un oggetto esistente **DataSource** oggetto nel modello.  
  
## <a name="object-definition"></a>Definizione dell'oggetto  
 Tutti gli oggetti hanno un set comune di proprietà, inclusi nome, tipo, descrizione, una raccolta di proprietà e le annotazioni. **Origine dati** gli oggetti dispongono anche le proprietà seguenti.  
  
 Tipo  
 Tipo di origine dati. Attualmente, l'unico valore valido è Provider (1) - stringa di connessione normale.  
  
 connectionString  
 La stringa di connessione che specifica il server e database minima, ma può includere anche altre proprietà supportate dal sistema RDBMS esterno, ad esempio un account utente o i provider di dati. Questo valore è obbligatorio. Vedere [classe SqlConnectionStringBuilder](https://msdn.microsoft.com/en-us/library/ms254500\(v=vs.110\).aspx) proprietà della stringa di connessione del database per informazioni dettagliate su SQL Server.  
  
 valore di impersonationMode  
 Specifica se Analysis Services deve rappresentare l'identità dell'utente che richiede la query. Questa proprietà è un valore numerico che specifica le credenziali da utilizzare per la rappresentazione. I valori di enumerazione sono i seguenti:  
  
-   Predefinito (1) - il server utilizza il metodo di rappresentazione che ritiene appropriata per il contesto in cui viene utilizzata la rappresentazione.  
  
-   ImpersonateAccount (2) - il server utilizza l'account utente specificato.  
  
-   ImpersonateAnonymous (3) - il server utilizza l'account utente anonimo.  Questa opzione non è consigliata, ma a volte viene utilizzata da applicazioni personalizzate che gestiscono l'autenticazione in scenari di accesso HTTP.  
  
-   ImpersonateCurrentUser (4): il server utilizza l'account utente che il client si connette come.  
  
-   ImpersonateServiceAccount (5): il server utilizza l'account utente che esegue il server.  
  
-   ImpersonateUnattendedAccount (6): il server utilizza un account utente. Viene utilizzato per i modelli Power Pivot o tabulare in esecuzione in un ambiente SharePoint.  
  
 La modalità DirectQuery è possibile utilizzare impersonateCurrentuser se Analysis Services è configurato per la delega trusted, o  
                      impersonateServiceAccount se viene effettuata la richiesta di query nel contesto di sicurezza dell'account del servizio Analysis Services. Vedere [configurare Analysis Services for Kerberos per la delega vincolata](../../analysis-services/instances/configure-analysis-services-for-kerberos-constrained-delegation.md).  
  
 account  
 Utilizzato per la rappresentazione. Un account di Windows o un database che dispone di un account di accesso valido con autorizzazioni di lettura per il database esterno.  
  
 password  
 Una stringa crittografata, fornire la password dell'account.  
  
 maxConnections  
 Numero massimo di connessioni da aprire simultaneamente all'origine dati.  
  
 isolation  
 Il tipo di isolamento utilizzato durante l'esecuzione di comandi sull'origine dati. I valori validi sono ReadCommitted (1) o Snapshot (2).  
  
 timeout  
 Valore intero che specifica il timeout in secondi per i comandi eseguiti sull'origine dati.  
  
 provider  
 Stringa facoltativa che identifica il nome del provider di dati gestito utilizzato per la connessione al database relazionale, se non diversamente specificato nella stringa di connessione.  
  
## <a name="usage"></a>Utilizzo  
 **DataSource** gli oggetti vengono usati [Alter-comando &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/alter-command-tmsl.md), [creare un comando di &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/create-command-tmsl.md), [comando CreateOrReplace &#40; TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/createorreplace-command-tmsl.md), [comando Delete &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/delete-command-tmsl.md), [comando Refresh &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/refresh-command-tmsl.md), e [comando MergePartitions &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/mergepartitions-command-tmsl.md).  
  
 Oggetto **DataSource** oggetto è una proprietà di un modello, ma può anche essere specificato come una proprietà di un oggetto di Database dato il mapping uno a uno tra modello e il Database.  Le partizioni basate su query SQL consente di specificare anche un **DataSource**, solo con un set ridotto di proprietà.  
  
 Durante la creazione, la sostituzione o modifica di un oggetto origine dati, specificare tutte le proprietà di sola lettura della definizione dell'oggetto. Omissione di una proprietà di lettura / scrittura è considerata un'operazione di eliminazione.  
  
## <a name="examples"></a>Esempi  
 **Esempio 1** -una connessione a un *FoodMart* database su un'istanza denominata di remota *Sales* in un server di rete denominato *Server01*.  
  
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
 [Configurare l'accesso HTTP ad Analysis Services in Internet Information Services & #40; IIS & #41; 8.0](../../analysis-services/instances/configure-http-access-to-analysis-services-on-iis-8-0.md)  
  
  
