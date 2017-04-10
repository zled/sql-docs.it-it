---
title: "Distribuire pacchetti nel server Integration Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c26ce7f4-7b34-4c9a-8649-ba767d30c827
caps.latest.revision: 10
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 10
---
# Distribuire pacchetti nel server Integration Services
  La funzionalità di distribuzione dei pacchetti incrementale introdotta in [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] consente di distribuire uno o più pacchetti in un progetto nuovo o esistente senza distribuire l'intero progetto.  
  
##  <a name="DeployWizard"></a> Distribuire pacchetti con la Distribuzione guidata Integration Services  
  
1.  Al prompt dei comandi eseguire **isdeploymentwizard.exe** da **%ProgramFiles%\Microsoft SQL Server\130\DTS\Binn**. Nei computer a 64 bit è presente anche una versione a 32 bit dello strumento in **%ProgramFiles(x86)%\Microsoft SQL Server\130\DTS\Binn**.  
  
2.  Nella pagina **Seleziona origine** passare al **modello di distribuzione del pacchetto**. Selezionare quindi la cartella che contiene i pacchetti di origine e configurare i pacchetti.  
  
3.  Completare la procedura guidata. Eseguire i passaggi successivi descritti in [Modello di distribuzione del pacchetto](../../integration-services/packages/integration-services-deployment-wizard.md#PackageModel).  
  
##  <a name="SSMS"></a> Distribuire pacchetti con SQL Server Management Studio  
  
1.  In SQL Server Management Studio espandere il nodo **Cataloghi di Integration Services** > **SSISDB** in Esplora oggetti.  
  
2.  Fare clic con il pulsante destro del mouse sulla cartella **Progetti** e quindi scegliere **Distribuzione progetto**.  
  
3.  Se viene visualizzata la pagina **Introduzione**, fare clic su **Avanti** per continuare.  
  
4.  Nella pagina **Seleziona origine** passare al **modello di distribuzione del pacchetto**. Selezionare quindi la cartella che contiene i pacchetti di origine e configurare i pacchetti.  
  
5.  Completare la procedura guidata. Eseguire i passaggi successivi descritti in [Modello di distribuzione del pacchetto](../../integration-services/packages/integration-services-deployment-wizard.md#PackageModel).  
  
##  <a name="SSDT"></a> Distribuire pacchetti con SQL Server Data Tools (Visual Studio)  
  
1.  In Visual Studio, con un progetto di Integration Services aperto, selezionare i pacchetti da distribuire.  
  
2.  Fare clic con il pulsante destro del mouse e scegliere **Distribuzione pacchetto**. Viene aperta la Distribuzione guidata con i pacchetti selezionati configurati come pacchetti di origine.  
  
3.  Completare la procedura guidata. Eseguire i passaggi successivi descritti in [Modello di distribuzione del pacchetto](../../integration-services/packages/integration-services-deployment-wizard.md#PackageModel).  
  
##  <a name="StoredProcedure"></a> Distribuire i pacchetti usando la stored procedure deploy_packages  
 Si può usare la stored procedure **[catalog].[deploy_packages]** per distribuire uno o più pacchetti SSIS nel catalogo SSIS. L'esempio di codice seguente mostra come usare questa stored procedure per distribuire pacchetti in un server SSIS. Per altre informazioni, vedere [catalog.deploy_packages](../../integration-services/system-stored-procedures/catalog-deploy-packages.md).  
  
```  
  
private static void Main(string[] args)  
{  
    // Connection string to SSISDB  
    var connectionString = "Data Source=.;Initial Catalog=SSISDB;Integrated Security=True;MultipleActiveResultSets=false";  
  
    using (var sqlConnection = new SqlConnection(connectionString))  
    {  
        sqlConnection.Open();  
  
        var sqlCommand = new SqlCommand  
        {  
            Connection = sqlConnection,  
            CommandType = CommandType.StoredProcedure,  
            CommandText = "[catalog].[deploy_packages]"  
        };  
  
        var packageData = Encoding.UTF8.GetBytes(File.ReadAllText(@"C:\Test\Package.dtsx"));  
  
        // DataTable: name is the package name without extension and package_data is byte array of package.  
        var packageTable = new DataTable();  
        packageTable.Columns.Add("name", typeof(string));  
        packageTable.Columns.Add("package_data", typeof(byte[]));  
        packageTable.Rows.Add("Package", packageData);  
  
        // Set the destination project and folder which is named Folder and Project.  
        sqlCommand.Parameters.Add(new SqlParameter("@folder_name", SqlDbType.NVarChar, ParameterDirection.Input, "Folder", -1));  
        sqlCommand.Parameters.Add(new SqlParameter("@project_name", SqlDbType.NVarChar, ParameterDirection.Input, "Project", -1));  
        sqlCommand.Parameters.Add(new SqlParameter("@packages_table", SqlDbType.Structured, ParameterDirection.Input, packageTable, -1));  
  
        var result = sqlCommand.Parameters.Add("RetVal", SqlDbType.Int);  
        result.Direction = ParameterDirection.ReturnValue;  
  
        sqlCommand.ExecuteNonQuery();  
    }  
}  
  
```  
  
##  <a name="MOMApi"></a> Distribuire pacchetti con l'API del modello a oggetti di gestione  
 L'esempio di codice seguente mostra come usare l'API del modello a oggetti di gestione per distribuire pacchetti in un server.  
  
```  
  
static void Main()  
 {  
     // Before deploying packages, make sure the destination project exists in SSISDB.  
     var connectionString = "Data Source=.;Integrated Security=True;MultipleActiveResultSets=false";  
     var catalogName = "SSISDB";  
     var folderName = "Folder";  
     var projectName = "Project";  
  
     // Get the folder instance.  
     var sqlConnection = new SqlConnection(connectionString);  
     var store = new Microsoft.SqlServer.Management.IntegrationServices.IntegrationServices(sqlConnection);  
     var folder = store.Catalogs[catalogName].Folders[folderName];  
  
     // Key is package name without extension and value is package binaries.  
     var packageDict = new Dictionary<string, string>();  
  
     var packageData = File.ReadAllText(@"C:\Folder\Package.dtsx");  
     packageDict.Add("Package", packageData);  
  
     // Deploy package to the destination project.  
     folder.DeployPackages(projectName, packageDict);  
 }  
  
```  
  
  