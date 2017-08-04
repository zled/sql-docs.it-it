---
title: Esempio di flusso di lavoro personalizzato (Master Data Services) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: dfd1616c-a75c-4f32-bdb1-7569e367bf41
caps.latest.revision: 6
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e2b3ad5ab349456364d2aa0af8826dd6970e55b1
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="create-a-custom-workflow---example"></a>Creare un flusso di lavoro personalizzato - esempio
  In [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], quando si crea una libreria di classi di flusso di lavoro personalizzato, creare una classe che implementa l'interfaccia Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender. Questa interfaccia include il metodo <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A> chiamato da SQL Server MDS Workflow Integration Service all'avvio di un flusso di lavoro. Il <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A> metodo contiene due parametri: *workflowType* contiene il testo immesso nella **tipo flusso di lavoro** casella di testo in [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], e *oggetto dataElement* contiene i metadati e i dati per l'elemento che ha attivato la regola di business del flusso di lavoro.  
  
## <a name="custom-workflow-example"></a>Esempio di flusso di lavoro personalizzato  
 Nell'esempio di codice seguente viene illustrato come implementare il metodo <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A> per estrarre gli attributi Name, Code e LastChgUserName dai dati XML dell'elemento che ha attivato la regola business del flusso di lavoro e come chiamare una stored procedure per inserirli in un altro database. Per un esempio di dati dell'elemento XML e una spiegazione dei tag in esso contenuti, vedere [descrizione in formato XML del flusso di lavoro personalizzato &#40; Master Data Services &#41; ](../../master-data-services/develop/create-a-custom-workflow-xml-description.md).  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.IO;  
using System.Data.SqlClient;  
using System.Xml;  
  
using Microsoft.MasterDataServices.Core.Workflow;  
  
namespace MDSWorkflowTestLib  
{  
    public class WorkflowTester : IWorkflowTypeExtender  
    {  
        #region IWorkflowTypeExtender Members  
  
        public void StartWorkflow(string workflowType, System.Xml.XmlElement dataElement)  
        {  
            // Extract the attributes we want out of the element data.  
            XmlNode NameNode = dataElement.SelectSingleNode("//ExternalAction/MemberData/Name");  
            XmlNode CodeNode = dataElement.SelectSingleNode("//ExternalAction/MemberData/Code");  
            XmlNode EnteringUserNode = dataElement.SelectSingleNode("//ExternalAction/MemberData/LastChgUserName");  
  
            // Open a connection on the workflow database.  
            SqlConnection workflowConn = new SqlConnection(@"Data Source=<Server instance>; Initial Catalog=WorkflowTest; Integrated Security=True");  
  
            // Create a command to call the stored procedure that adds a new user to the workflow database.  
            SqlCommand addCustomerCommand = new SqlCommand("AddNewCustomer", workflowConn);  
            addCustomerCommand.CommandType = System.Data.CommandType.StoredProcedure;  
            addCustomerCommand.Parameters.Add(new SqlParameter("@Name", NameNode.InnerText));  
            addCustomerCommand.Parameters.Add(new SqlParameter("@Code", CodeNode.InnerText));  
            addCustomerCommand.Parameters.Add(new SqlParameter("@EnteringUser", EnteringUserNode.InnerText));  
  
            // Execute the command.  
            workflowConn.Open();  
            addCustomerCommand.ExecuteNonQuery();  
            workflowConn.Close();  
        }  
  
        #endregion  
    }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Creare un flusso di lavoro personalizzato &#40; Master Data Services &#41;](../../master-data-services/develop/create-a-custom-workflow-master-data-services.md)  
  
  
