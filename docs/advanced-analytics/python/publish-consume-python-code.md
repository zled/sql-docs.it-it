---
title: Pubblicare e utilizzare il codice Python | Documenti Microsoft
ms.custom: 
ms.date: 11/09/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: python
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 281f3beb3678d74fb03b3dc68a4a9b58d44f261e
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="publish-and-consume-python-web-services"></a>Pubblicare e utilizzare i servizi web di Python

La funzionalità di rendere operativo il Server di Microsoft Machine Learning, è possibile distribuire un soluzione di Python di lavoro a un servizio web. In questo argomento vengono descritti i passaggi per pubblicare correttamente e quindi eseguire la soluzione.

I destinatari di questo articolo sono esperti di dati che desiderano informazioni su come pubblicare codice Python o i modelli come servizi web ospitati nei Server di Microsoft Machine Learning. L'articolo spiega inoltre come le applicazioni possono utilizzare del codice o dei modelli. Questo articolo si presuppone che si è esperti in Python.

> [!IMPORTANT]
>
> In questo esempio è stato sviluppato per la versione di Python incluso in Machine Learning Server (Standalone), che utilizza le funzionalità nella versione Server di Machine Learning **9.1.0**.
 > 
 > Fare clic sul collegamento seguente per vedere l'esempio nella stessa replicato utilizzando le librerie più recenti nel Server di Machine Learning. Vedere [distribuire e gestire i servizi web di Python](https://docs.microsoft.com/machine-learning-server/operationalize/python/how-to-deploy-manage-web-services).

**Si applica a: Microsoft R Server (Standalone)**

## <a name="overview-of-workflow"></a>Panoramica del flusso di lavoro

Il flusso di lavoro di pubblicazione per l'utilizzo di un servizio web di Python può essere riepilogato come segue:

1. Completare il [prerequisito](#prereq) di generazione della libreria client Python dal documento Swagger API core.
2. Aggiungere la logica di autenticazione e l'intestazione per lo script Python.
3. Creare una sessione di Python, preparare l'ambiente e creare uno snapshot per mantenere l'ambiente.
4. Pubblicare il servizio web e incorporare lo snapshot.
5. Provare il servizio web per l'utilizzo nella sessione corrente.
6. Gestire questi servizi.

![Flusso di lavoro swagger](./media/data-scientist-python-workflow.png)

In questo articolo illustra ogni passaggio del flusso di lavoro e include il codice Python di esempio utilizzando il set di dati iris.

## <a name="sample-code"></a>Codice di esempio

Questo codice di esempio si presuppone di avere soddisfatto i [prerequisiti](#prereq) per generare una libreria client Python da tale Swagger file e che è stato usato Autorest.

Dopo il blocco di codice, è disponibile una procedura dettagliata con descrizioni più dettagliate del processo di completamento.

> [!IMPORTANT]
> Questo esempio viene utilizzato locale `admin` account per l'autenticazione. Tuttavia, è necessario sostituire le credenziali e [metodo di autenticazione](#python-auth) configurato dall'amministratore.

```python
##################################################
##       IMPORT GENERATED CLIENT LIBRARY        ##
##################################################

# Import the generated client library. 

import deployrclient

# This example is intended for use with Microsoft R Server 9.0.1. 
# If you are using a newer version of Machine Learning Server, 
# use the mrs_server library instead.

##################################################
##              AUTHENTICATION                  ##
##################################################

#Using client library generated from Autorest
#Create client instance and point it at an R Server. 
#In this case, R Server is local.
client = deployrclient.DeployRClient("http://localhost:12800")
# To use ML Server, replace with mrs_server.MRSServer()

#Define the login request and provide credentials 
#Update values with the connection parameters from your admin
login_request = deployrclient.models.LoginRequest("<<your-username>>","<<your-password>>")

#Make a call to the /login API. 
#Store the returned an access token in a variable.
token_response = client.login(login_request)

#Add the returned access token to the headers variable.
headers = {"Authorization": "Bearer {0}".format(token_response.access_token)}

#Verify that the server is running.
#Remember to include `headers` in all requests!
status_response = client.status(headers) 
print(status_response.status_code)


##################################################
##        CREATE SESSION, MODEL, SNAPSHOT       ##
##################################################

#Since already logged in, create a Python session.
#Define session using name (`Session 1`) and `runtime_type="Python"`.
#Remember to specify the Python runtime type.
create_session_request = deployrclient.models.CreateSessionRequest("Session 1", runtime_type="Python")

#Make the call to start the session. 
#Remember to include headers in all method calls to the server.
#Returns a session ID.
response = client.create_session(create_session_request, headers) 
   
#Store the session ID in a variable called `session_id` 
#to be able to identify it later at execution time.
session_id = response.session_id

#Create model - Import SVM and datasets from the SciKit-Learn library
execute_request = deployrclient.models.ExecuteRequest("from sklearn import svm\nfrom sklearn import datasets")
execute_response = client.execute_code(session_id,execute_request, headers)
#Report if it was a success
execute_response.success
   
#Define the untrained Support Vector Classifier (SVC) object
#and the dataset to be preloaded.
execute_request = deployrclient.models.ExecuteRequest("clf=svm.SVC()\niris=datasets.load_iris()\nnames={0:'I. setosa',1:'I. versicolor',2:'I. virginica'}")
#Now, go create the object and preload Iris Dataset in R Server
execute_response = client.execute_code(session_id,execute_request, headers)
#Report if it was a success
execute_response.success
   
#Define two rows from the Iris Dataset as a sample for scoring
workspace_object = deployrclient.models.WorkspaceObject("species_1",[7,3.2,4.7,1.4])
workspace_object_2 = deployrclient.models.WorkspaceObject("species_2",[3,2.6,3,2.5])

#Define how to train the classifier model; what to predict; what to return
execute_request = deployrclient.models.ExecuteRequest(
    "clf.fit(iris.data, iris.target)\n"+
    "result=clf.predict(species_1)\n"+
    "other_result=clf.predict(species_2)",
    [workspace_object,workspace_object_2], #Input
    ["result", "other_result"]) #Output

#Now, go train that model on the Iris Dataset in R Server
execute_response = client.execute_code(session_id,execute_request, headers)

#If successful, print name and result of each output parameter. Else, print error.
if(execute_response.success):
    for result in execute_response.output_parameters:
        print("{0}: {1}".format(result.name,result.value))
else:
    print (execute_response.error_message)

#Create a snapshot of the current session
response = client.create_snapshot(session_id, deployrclient.models.CreateSnapshotRequest("Iris Snapshot"), headers)
#Return the snapshot ID for reference when you publish later.
response.snapshot_id
#If you forget the ID, list snapshots to get the ID again.
for snapshot in client.list_snapshots(headers):
    print(snapshot)

##################################################
##        PUBLISH AS A SERVICE IN PYTHON        ##
##################################################

#Define a web service that determines the iris species by scoring 
#a vector of sepal length and width, petal length and width

#Set `flower_data` for the sepal and petal length and width
flower_data = deployrclient.models.ParameterDefinition(name = "flower_data", type = "vector")
#Set `iris_species` for the species of iris
iris_species = deployrclient.models.ParameterDefinition(name = "iris_species", type = "vector")

#Define the publish request for the web service and its arguments.
#Specify the code, inputs, outputs, and snapshot.
#Don't forget to set runtime_type="Python"`.
publish_request = deployrclient.models.PublishWebServiceRequest(
       code = "iris_species = [names[x] for x in clf.predict(flower_data)]", 
       input_parameter_definitions = [flower_data], 
       output_parameter_definitions = [iris_species],
       runtime_type = "Python",
       snapshot_id = response.snapshot_id)

#Publish the service using the specified name (iris), version (V1.0)
client.publish_web_service_version("Iris", "V1.0", publish_request, headers)

##################################################
##           CONSUME SERVICE IN PYTHON          ##
##################################################

# Inspect holdings and metadata for service Iris V1.0.
for service in client.get_web_service_version("Iris","V1.0", headers):
    #print service metadata (description, who published,...)
    print(service)
    #Print input and output parameters as defined in service definition object
    print("Input Parameters: {0}".format([str(parameter) for parameter in service.input_parameter_definitions]))
    print("Output Parameters: {0}".format([str(parameter) for parameter in service.output_parameter_definitions]))

#Import the requests library to make requests on the server
import requests
#Import the JSON library to use for pretty printing of json responses
import json

#Create a requests `Session` object.
s = requests.Session()

#Record the R Server endpoint URL hosting the web services you created before
url = "http://localhost:12800"

#Give the request.Session object the authentication headers 
#so you don't have to repeat it with each request.
s.headers = headers

#Retrieve the service-specific swagger file using the requests library.
swagger_resp = s.get(url+"/api/Iris/V1.0/swagger.json")

#Either, download service-specific swagger file using the json library.
with open('iris_swagger.json','w') as f:
   (json.dump(client.get_web_service_swagger("Iris","V1.0",headers),f, indent = 1))

#Or, print just what you need from the Swagger file, 
#such as the routing paths for the endpoints to be consumed.
print(json.dumps(swagger_resp.json()["paths"], indent = 1, sort_keys = True))

#Or, print input and output parameters as defined in the Swagger.io format
print("Input")
print(json.dumps(swagger_resp.json()["definitions"]["InputParameters"], indent = 1, sort_keys = True))
print("Output")
print(json.dumps(swagger_resp.json()["definitions"]["WebServiceResult"], indent = 1, sort_keys = True))

#Make the request to consume the service using these flower_data inputs
resp = s.post(url+"/api/Iris/V1.0",json={"flower_data":[7,3.2,4.7,1.4]})
#Print the output
print(json.dumps(resp.json(), indent = 1, sort_keys = True))

#Use input from another Iris species.
resp = s.post(url+"/api/Iris/V1.0",json={"flower_data":[3,2.6,3,2.5]})
print(json.dumps(resp.json(), indent = 1, sort_keys = True))

#Use input from another Iris species.
resp = s.post(url+"/api/Iris/V1.0",json={"flower_data":[5.1,3.5,1.4,.2]})
print(json.dumps(resp.json(), indent = 1, sort_keys = True))

##################################################
##          MANAGE SERVICES IN PYTHON           ##
##################################################

#Define what needs to be updated. Here we add a description.
#Be sure to specify the runtime_type again.
update_request = deployrclient.models.PublishWebServiceRequest(
    description = "Determines iris species using length and width of sepal and petal", runtime_type = "Python")
#Now update it by specifying the service name and version number
client.patch_web_service_version("Iris", "V1.0", update_request, headers)

#Or, publish another version of the web service, but this time 
#the service returns the species as a string instead of list of strings.
flower_data = deployrclient.models.ParameterDefinition(name = "flower_data", type = "vector")
iris_species = deployrclient.models.ParameterDefinition(name = "iris_species", type = "string")
 
#Define the publish request for the service and its arguments.
#Specify the changed code, inputs, outputs, and snapshot.
#Don't forget to set runtime_type="Python"`.
publish_request = deployrclient.models.PublishWebServiceRequest(
    code = "iris_species = [names[x] for x in clf.predict(flower_data)][0]",
    description = "Determines the species of iris, based on Sepal Length, Sepal Width, Petal Length and Petal Width",
    input_parameter_definitions = [flower_data],
    output_parameter_definitions = [iris_species],
    runtime_type = "Python",
    snapshot_id = response.snapshot_id)
 
#Now, publish the service with version (V2.0)
client.publish_web_service_version("Iris", "V2.0", publish_request, headers)
 
#Make request to consume service using these flower_data inputs; print output
resp = s.post(url+"/api/Iris/V2.0",json={"flower_data":[5.1,3.5,1.4,.2]})
print(json.dumps(resp.json(), indent = 1, sort_keys = True))

#Return the list of all existing web services.
for service in client.get_all_web_services(headers):
    #print the service information
    print(service)
    #Print each input and output parameter
    print("Input Parameters: {0}".format([str(parameter) for parameter in service.input_parameter_definitions]))
    print("Output Parameters: {0}".format([str(parameter) for parameter in service.output_parameter_definitions]))

#Delete the second version we just published.
client.delete_web_service_version("Iris","V2.0",headers)
```

## <a name="walkthrough"></a>Scenario

In questa sezione viene descritto il funzionamento del codice in modo più dettagliato.


### <a name="prereq"></a>Passaggio 1. Creare raccolte di prerequisiti client

Prima di iniziare il Python codice e i modelli mediante Microsoft Machine Learning Server di pubblicazione, è necessario generare una libreria client usando il documento Swagger fornito per questa versione.

1. Installare un generatore di codice Swagger sul computer locale e acquisire familiarità con esso. Si utilizzerà per generare le librerie client API in Python. Gli strumenti più diffusi includono [Azure AutoRest](https://github.com/Azure/autorest) (richiede Node. js) e [Swagger Codegen](https://github.com/swagger-api/swagger-codegen). 

2. Scaricare il file Swagger contenente le API per la versione del Server di Machine Learning. Questo file contiene un modello di Swagger che definisce l'elenco di risorse REST e le operazioni che possono essere chiamate su tali risorse. È possibile trovare questo file in `https://microsoft.github.io/deployr-api-docs/swagger/<version>/rserver-swagger-<version>.json`, dove `<version>` è il numero di versione di R Server 3 cifre. 

   Ad esempio, per R Server 9.1 sarebbe scaricare da: https://microsoft.github.io/deployr-api-docs/9.1.0/swagger/rserver-swagger-9.1.0.json

3. Generare la libreria client generato in modo statico passando il `rserver-swagger-<version>.json` al generatore di codice Swagger di file e specificare la lingua desiderata. In questo caso, è necessario specificare Python.  

    Ad esempio, se si utilizza AutoRest per generare una libreria client Python, potrebbe essere simile al seguente, in cui il numero di 3 cifre rappresenta il numero di versione di R Server:
    
    `AutoRest.exe -Input rserver-swagger-9.1.0.json -CodeGenerator Python  -OutputDirectory C:\Users\rserver-user\Documents\Python`

4. È anche possibile fornire alcune intestazioni personalizzate e apportare altre modifiche prima di utilizzare il client generato lo stub di libreria. Vedere il [interfaccia della riga di comando](https://github.com/Azure/autorest/blob/master/docs/user/cli.md) documentazione su GitHub per i dettagli relativi a diverse opzioni di configurazione e le preferenze, ad esempio rinominare lo spazio dei nomi.
   
5. Esplorare la libreria client di base per visualizzare le varie chiamate API, che è possibile apportare. 

    In questo esempio, Autorest generato alcune directory e file per la libreria client Python nel sistema locale. Per impostazione predefinita, lo spazio dei nomi (e directory) è `deployrclient` e potrebbe essere simile al seguente:
   
   ![Percorso di output Autorest](./media/data-scientist-python-autorest.png)

    Per questo spazio dei nomi predefinito, viene chiamata la stessa libreria client `deploy_rclient.py`. Se questo file si apre l'IDE, ad esempio Visual Studio, si noterà quanto segue:
   
   ![Libreria client Python](./media/data-scientist-python-client-library.png)


### <a name="step-2-add-authentication-and-header-logic"></a>Passaggio 2. Aggiungere la logica di autenticazione e l'intestazione

Tenere presente che tutte le API richiedono l'autenticazione. Pertanto, tutti gli utenti devono eseguire l'autenticazione quando si effettua un'API di chiamare usando il `POST /login` API o tramite Azure Active Directory (AAD). 

Per semplificare questo processo, vengono rilasciati token di accesso di connessione in modo che gli utenti non è necessario specificare le credenziali per ogni chiamata.  Questo token di connessione è un token di sicurezza leggero che concede l'accesso "bearer" a una risorsa protetta: in questo caso, le API del Server Machine Learning. Dopo l'autenticazione dell'utente, l'applicazione deve convalidare i token di connessione dell'utente per assicurarsi che l'autenticazione è riuscita per le parti previste. Per ulteriori informazioni sulla gestione di questi token, vedere [i token di accesso di sicurezza](https://msdn.microsoft.com/microsoft-r/operationalize/security-access-tokens).

Prima che si interagisce con le API principali, innanzitutto l'autenticazione, ottenere l'accesso alla connessione token utilizzando il [metodo di autenticazione](https://msdn.microsoft.com/microsoft-r/operationalize/security-authentication) configurato dall'amministratore e, successivamente, includerla in ogni intestazione per ogni richiesta successiva:

1. Per iniziare, l'importazione della libreria client per rendere accessibile il preferito Python editor di codice, ad esempio Jupyter, Visual Studio, Visual Studio Code o iPython.

   Specificare la directory padre della libreria client. In questo esempio, la libreria client generato Autorest in `C:\Users\rserver-user\Documents\Python\deployrclient`:

   ```python
   # Import the generated client library
   import deployrclient
   ```

2. Aggiungere la logica di autenticazione per l'applicazione per definire una connessione dal computer locale al Server di Machine Learning, fornire le credenziali, acquisire il token di accesso, aggiungere tale token all'intestazione. È quindi possibile utilizzare l'intestazione per tutte le richieste successive.  Utilizzare il metodo di autenticazione definito dall'amministratore: account di amministrazione di base, Active Directory LDAP (Active Directory o LDAP) o Azure Active Directory (AAD).

   **Active Directory o LDAP o `admin` account di autenticazione**

   Chiamare il `POST /login` API per l'autenticazione. Passare il `username` e `password` per l'amministratore locale, o se Active Directory è abilitata, passare le informazioni sull'account LDAP. A sua volta, Machine Learning Server rilascia un token di connessione/accesso. Dopo l'autenticazione, l'utente non deve fornire le credenziali, purché il token è ancora valido e viene inviata un'intestazione con ogni richiesta. Se non si conoscono le impostazioni di connessione, contattare l'amministratore.

   ```python
   #Using client library generated from Autorest
   #Create client instance and point it at an R Server. 
   #In this case, R Server is local.
   client = deployrclient.DeployRClient("http://localhost:12800")
   
   #Define the login request and provide credentials. 
   #Update values with the connection parameters from your admin.
   login_request = deployrclient.models.LoginRequest("<<your-username>>","<<your-password>>")
   #Make a call to the /login API. 
   #Store the returned an access token in a variable.
   token_response = client.login(login_request)
   ```

   **Autenticazione di Azure Active Directory (AAD)**

   Passare le credenziali AAD, autorità e l'ID client. A sua volta, Azure ad rilascia il [token di accesso connessione](https://msdn.microsoft.com/microsoft-r/operationalize/security-access-tokens). Dopo l'autenticazione, l'utente non deve fornire le credenziali, purché il token è ancora valido e viene inviata un'intestazione con ogni richiesta. Se non si conoscono le impostazioni di connessione, contattare l'amministratore.

   ```python
   #Import the AAD authentication library
   import adal
   
   #Define the login request and provide credentials. 
   #Use the AAD connection parameters provided by your admin.
   url = "http://localhost:12800"
   authuri = https://login.windows.net,
   tenantid = "<<AAD_DOMAIN>>", 
   clientid = "<<NATIVE_APP_CLIENT_ID>>", 
   resource = "<<WEB_APP_CLIENT_ID>>", 
   
   #Acquire authentication token using AAD Device Code Login
   context = adal.AuthenticationContext(authuri+'/'+tenantid, api_version=None)
   code = context.acquire_user_code(resource, clientid)
   print(code['message'])
   token = context.acquire_token_with_device_code(resource, code, clientid)
   #The authentication code returned must be entered at https://aka.ms/devicelogin 
   ```     

3. Aggiungere il `Bearer` accedere token e verificare che Server di Machine Learning è attualmente in esecuzione.  Questo token è stato restituito durante l'autenticazione e **deve essere incluso in ogni intestazione di richiesta successiva**. In questo esempio utilizza una libreria client generata da Autorest.

   > [!IMPORTANT]
   > Ogni chiamata API deve essere autenticata. Pertanto, ricordarsi di includere le intestazioni con token a ogni singola richiesta.

   ```python
   #Add the returned access token to the headers variable.
   headers = {"Authorization": "Bearer {0}".format(token_response.access_token)}
   
   #Verify that the server is running.
   #Remember to include `headers` in every request!
   status_response = client.status(headers) 
   print(status_response.status_code)
   ```

### <a name="step-3-prepare-session-and-code"></a>Passaggio 3. Preparare una sessione e codice

Dopo l'autenticazione, è possibile avviare una sessione di Python e creare un modello per la pubblicazione in un secondo momento. È possibile includere qualsiasi codice Python o modelli in un servizio web. Dopo aver impostato l'ambiente di sessione, è possibile salvarla anche come snapshot in modo che è possibile ricaricare la sessione, come in precedenza era. 

> [!IMPORTANT]
> Ricordarsi di includere `headers` in ogni richiesta.

1. Creare una sessione di Python nel Server di R. Assicurarsi di specificare un nome e il linguaggio Python (`runtime_type="Python"`).  Se non si imposta il tipo di runtime di Python, il valore predefinito R.

   Si tratta di una continuazione dell'esempio di utilizzo della libreria client generata da Autorest:

   ```python
   #Since already logged in, create a Python session.
   #Define session using name (`Session 1`) and `runtime_type="Python"`.
   #Remember to specify the Python runtime type.
   create_session_request = deployrclient.models.CreateSessionRequest("Session 1", runtime_type="Python")
   
   #Make the call to start the session. 
   #Remember to include headers in every method call to the server.
   #Returns a session ID.
   response = client.create_session(create_session_request, headers) 
   
   #Store the session ID in a variable called `session_id` 
   #to be able to identify it later at execution time.
   session_id = response.session_id
   ```

2. Creare o chiamare un modello in Python che è possibile pubblicare come servizio web

   In questo esempio è training di un apprendimento SciKit supporto vettore macchine (SVM) modello nel Iris Dataset in un'istanza remota di Server di Machine Learning.  Questo set di dati è disponibile il [scikit-informazioni sito](http://scikit-learn.org/stable/auto_examples/datasets/plot_iris_dataset.html).

   ```python
   #Import SVM and datasets from the SciKit-Learn library
   execute_request = deployrclient.models.ExecuteRequest("from sklearn import svm\nfrom sklearn import datasets")
   execute_response = client.execute_code(session_id,execute_request, headers)
   #Report if it was a success
   execute_response.success
   
   #Define the untrained Support Vector Classifier (SVC) object
   #and the dataset to be preloaded.
   execute_request = deployrclient.models.ExecuteRequest("clf=svm.SVC()\niris=datasets.load_iris()\nnames={0:'I. setosa',1:'I. versicolor',2:'I. virginica'}")
   #Now, go create the object and preload Iris Dataset in R Server
   execute_response = client.execute_code(session_id,execute_request, headers)
   #Report if it was a success
   execute_response.success
   
   #Define two rows from the Iris Dataset as a sample for scoring
   workspace_object = deployrclient.models.WorkspaceObject("species_1",[7,3.2,4.7,1.4])
   workspace_object_2 = deployrclient.models.WorkspaceObject("species_2",[3,2.6,3,2.5])

   #Define how to train the classifier model; what to predict; what to return
   execute_request = deployrclient.models.ExecuteRequest(
       "clf.fit(iris.data, iris.target)\n"+
       "result=clf.predict(species_1)\n"+
       "other_result=clf.predict(species_2)",
       [workspace_object,workspace_object_2], #Input
       ["result", "other_result"]) #Output

   #Now, go train that model on the Iris Dataset in R Server
   execute_response = client.execute_code(session_id,execute_request, headers)

   #If successful, print name and result of each output parameter. Else, print error.
   if(execute_response.success):
       for result in execute_response.output_parameters:
           print("{0}: {1}".format(result.name,result.value))
   else:
       print (execute_response.error_message)
   ```

3. Creare uno snapshot di questa Python sessione in modo da questo ambiente può essere salvato nel servizio web e riprodurre in utilizzano il tempo. Gli snapshot sono utili quando è necessario un ambiente predisposto che include alcune librerie, oggetti, modelli, file e gli elementi. Gli snapshot salvare l'intera area di lavoro e la directory di lavoro. Tuttavia, per la pubblicazione, è possibile utilizzare solo gli snapshot creati.

   ```python
   #Create a snapshot of the current session.
   response = client.create_snapshot(session_id, deployrclient.models.CreateSnapshotRequest("Iris Snapshot"), headers)
   
   #Return the snapshot ID for reference when you publish later.
   response.snapshot_id
   
   #If you forget the ID, list snapshots to get the ID again.
   for snapshot in client.list_snapshots(headers):
       print(snapshot)
   ```

  > [!NOTE] 
   > Mentre gli snapshot possono essere utilizzati anche quando si pubblica un servizio web per le dipendenze di ambiente, potrebbe avere un impatto sulle prestazioni del tempo di utilizzo.  Per prestazioni ottimali, considerare con attenzione le dimensioni dello snapshot e assicurarsi di mantenere solo gli oggetti dell'area di lavoro desiderati e ripulire il resto. In una sessione, è possibile utilizzare la versione di Python `del` funzione o [il `deleteWorkspaceObject` richiesta API](https://microsoft.github.io/deployr-api-docs/#delete-workspace-object) per rimuovere gli oggetti non necessari. 

### <a name="step-4-publish-the-model"></a>Passaggio 4. Pubblicare il modello 

Dopo che la libreria client è stata generata e aver creato la logica di autenticazione nell'applicazione, è possibile interagire con l'API per creare una sessione di Python, creare un modello e quindi pubblicare un servizio web utilizzando il modello di base.

Alcuni aspetti da tenere presente:

+ È necessario essere autenticati prima di apportare tutte le chiamate API. Pertanto, includere `headers` in tutte le richieste.
+ Per garantire che il servizio web è registrato come un servizio di Python, assicurarsi di specificare `runtime_type="Python"`. Se non si imposta il tipo di runtime di Python, il valore predefinito R.
+ Assegnazione dei punteggi richiede un vettore con lunghezza sepal, sepal larghezza, lunghezza petalo e petalo

Il codice seguente pubblica il modello SVM come un servizio web di Python. Questo servizio web genera una categoria stimata in base ai valori passati a esso.

```python
   #Set `flower_data` for the sepal and petal length and width
   flower_data = deployrclient.models.ParameterDefinition(name = "flower_data", type = "vector")
   #Set `iris_species` for the species of iris
   iris_species = deployrclient.models.ParameterDefinition(name = "iris_species", type = "vector")
   
   #Define the publish request for the web service and its arguments.
   #Specify the code, inputs, outputs, and snapshot.
   #Don't forget to set runtime_type="Python"`.
   publish_request = deployrclient.models.PublishWebServiceRequest(
       code = "iris_species = [names[x] for x in clf.predict(flower_data)]", 
       input_parameter_definitions = [flower_data], 
       output_parameter_definitions = [iris_species],
       runtime_type = "Python",
       snapshot_id = response.snapshot_id)

   #Publish the service using the specified name (iris), version (V1.0)
   client.publish_web_service_version("Iris", "V1.0", publish_request, headers)
```

### <a name="step-5-consume-the-web-service"></a>Passaggio 5. Utilizzare il servizio web

In questa sezione viene illustrato come utilizzare il servizio nella stessa sessione in cui è stato creato.

1. Nella stessa sessione, ottenere la disponibilità di servizio e i metadati per il servizio.

   ```python
   # Inspect holdings and metadata for service Iris V1.0.
   for service in client.get_web_service_version("Iris","V1.0", headers):
       #print service metadata (description, who published,...)
       print(service)
       #Print input and output parameters as defined in service definition object
       print("Input Parameters: {0}".format([str(parameter) for parameter in service.input_parameter_definitions]))
       print("Output Parameters: {0}".format([str(parameter) for parameter in service.output_parameter_definitions]))
   ```

2. Esaminare le aziende di servizio e preparazione utilizzare. 
   ```python
   #Import the requests library to make requests on the server
   import requests
   #Import the JSON library to use for pretty printing of json responses
   import json

   #Create a requests `Session` object.
   s = requests.Session()

   #Record the R Server endpoint URL hosting the web services you created
   url = "http://localhost:12800"

   #Include the request.Session object in the authentication headers.
   #By doing so, you don't need to repeat it with each request.
   s.headers = headers

   # Retrieve the service-specific Swagger file using the requests library.
   swagger_resp = s.get(url+"/api/Iris/V1.0/swagger.json")

   #You can download a service-specific Swagger file using the json library.
   with open('iris_swagger.json','w') as f:
      (json.dump(client.get_web_service_swagger("Iris","V1.0",headers),f, indent = 1))

   #Or, you can print just what you need from the Swagger file. 
   #This example gets the routing paths for the endpoints to be consumed.
   print(json.dumps(swagger_resp.json()["paths"], indent = 1, sort_keys = True))

   #You can also print input and output parameters as defined in the Swagger.io format
   print("Input")
   print(json.dumps(swagger_resp.json()["definitions"]["InputParameters"], indent = 1, sort_keys = True))
   print("Output")
   print(json.dumps(swagger_resp.json()["definitions"]["WebServiceResult"], indent = 1, sort_keys = True))
   ```

3. Utilizzare il servizio fornendo alcuni input e il recupero delle specie Iris. 
   ```python
   #Make the request to consume the service using these flower_data inputs
   resp = s.post(url+"/api/Iris/V1.0",json={"flower_data":[7,3.2,4.7,1.4]})
   #Print the output
   print(json.dumps(resp.json(), indent = 1, sort_keys = True))

   ##Use input from another Iris species.
   resp = s.post(url+"/api/Iris/V1.0",json={"flower_data":[3,2.6,3,2.5]})
   print(json.dumps(resp.json(), indent = 1, sort_keys = True))

   ##Use input from another Iris species.
   resp = s.post(url+"/api/Iris/V1.0",json={"flower_data":[5.1,3.5,1.4,.2]})
   print(json.dumps(resp.json(), indent = 1, sort_keys = True))
   ```

## <a name="managing-the-services"></a>Gestione dei servizi

Dopo aver creato un servizio web, aggiornare, eliminare o ripubblicare il servizio. È anche possibile elencare tutti i servizi web sono ospitati usando R Server (o Server di Machine Learning).

### <a name="update-a-web-service"></a>Aggiornare un servizio web

 In questo esempio, aggiornamento del servizio per aggiungere una descrizione utile agli utenti che potrebbero utilizzare questo servizio.

```python
#Define what needs to be updated. Here we add a description.
#Be sure to specify the runtime_type again.
update_request = deployrclient.models.PublishWebServiceRequest(
    description = "Determines iris species using length and width of sepal and petal", runtime_type = "Python")
#Now update it by specifying the service name and version number
client.patch_web_service_version("Iris", "V1.0", update_request, headers)
```

È possibile aggiornare un servizio web per modificare il codice, modello, descrizione, gli input, output e altro ancora.

### <a name="publish-another-version"></a>Un'altra versione di pubblicazione

In questo esempio, il servizio restituirà ora specie iris, conosciuti come stringa anziché come un elenco di stringhe.

```python
#Publish another version of the web service, but this time 
#the service returns the species as a string instead of list of strings.
flower_data = deployrclient.models.ParameterDefinition(name = "flower_data", type = "vector")
iris_species = deployrclient.models.ParameterDefinition(name = "iris_species", type = "string")
 
#Define the publish request for the service and its arguments.
#Specify the changed code, inputs, outputs, and snapshot.
#Don't forget to set runtime_type="Python"`.
publish_request = deployrclient.models.PublishWebServiceRequest(
    code = "iris_species = [names[x] for x in clf.predict(flower_data)][0]",
    description = "Determines the species of iris, based on Sepal Length, Sepal Width, Petal Length and Petal Width",
    input_parameter_definitions = [flower_data],
    output_parameter_definitions = [iris_species],
    runtime_type = "Python",
    snapshot_id = response.snapshot_id)
 
#Now, publish the service with version (V2.0)
client.publish_web_service_version("Iris", "V2.0", publish_request, headers)
 
#Make request to consume service using these flower_data inputs; print output
resp = s.post(url+"/api/Iris/V2.0",json={"flower_data":[5.1,3.5,1.4,.2]})
print(json.dumps(resp.json(), indent = 1, sort_keys = True))
```

È possibile utilizzare questo modello per la pubblicazione di più versioni dello stesso servizio web. 

### <a name="list-services"></a>Elencare i servizi

In questo esempio Ottiene un elenco di tutti i servizi web, inclusi quelli creati da altri utenti o in linguaggi diversi.

```python
#Return the list of all existing web services.
for service in client.get_all_web_services(headers):
    #print the service information
    print(service)
    #Print each input and output parameter
    print("Input Parameters: {0}".format([str(parameter) for parameter in service.input_parameter_definitions]))
    print("Output Parameters: {0}".format([str(parameter) for parameter in service.output_parameter_definitions]))
``` 

### <a name="delete-services"></a>Eliminare i servizi

In questo esempio si elimina la seconda versione del servizio web che è appena pubblicati.

```python
#Delete the second version we just published.
client.delete_web_service_version("Iris","V2.0",headers)
```

È possibile eliminare qualsiasi servizio che è stato creato. È possibile eliminare i servizi di altri utenti solo se è stato assegnato a un ruolo che disponga delle autorizzazioni appropriate.