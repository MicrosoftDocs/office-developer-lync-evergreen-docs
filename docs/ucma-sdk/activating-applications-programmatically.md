---
title: Activating applications programmatically
TOCTitle: Activating applications programmatically
ms:assetid: d75f69cf-5bdd-4194-9ebb-87a06978b5a0
ms:mtpsurl: https://msdn.microsoft.com/library/Dn466133(v=office.15)
ms:contentKeyID: 57103425
ms.date: 07/25/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Activating applications programmatically


**Applies to:** Lync 2013 | Lync Server 2013

Activating a Microsoft Unified Communications Managed API 4.0 application against Microsoft Lync Server 2013 typically involves setting a trust relationship between the application and Lync Server 2013, and setting up routing-specific configurations. PowerShell-based programmable activation enables application developers to easily integrate the details of UCMA 4.0 activation into their overall application activation.

The cmdlets needed to create and manage Lync Server 2013 trusted application pools, trusted applications, and trusted application endpoints can be invoked from C\# and other CLI-compliant languages, just as other Windows PowerShell cmdlets can be. For information about creating a PowerShell Runspace and executing PowerShell cmdlets, see [Writing a Windows PowerShell Host Application](http://msdn.microsoft.com/library/ee706563\(vs.85\).aspx).

The following example demonstrates how to invoke a Lync Server 2013 trusted application cmdlet. Note that this code snippet should be compiled as a 64-bit application. Running Lync Server 2013 Manageability cmdlets from 32-bit instances of Powershell is unsupported. If a 32-bit application is required, care must be taken to enable the execution of scripts for 32-bit PowerShell instances.

```csharp
using System;
using System.Collections.ObjectModel;
using System.Management.Automation;
using System.Management.Automation.Runspaces;

namespace Microsoft.Rtc.Collaboration.Sample.ApplicationActivation
{
  class Program
  {
    static void Main(string[] args)
    {
      // Get the operating environment to run commands.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      iss.ImportPSModule(new[] { "Lync" });
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();

        // Execute the Get-CsTrustedApplication cmdlet.
        using (System.Management.Automation.PowerShell powershell = System.Management.Automation.PowerShell.Create())
        {
          powershell.Runspace = myRunSpace;
          powershell.AddCommand("Get-CsTrustedApplication");

          Collection<PSObject> results = null;
          Collection<ErrorRecord> errors = null;
          try
          {
            results = powershell.Invoke();
            errors = powershell.Streams.Error.ReadAll();
          }

          catch (Exception ex)
          {
            // An error occurred running the cmdlets.
            // TODO (Left to the reader): Error handling code.
            throw;
          }

          if (errors.Count != 0)
          {
            // Errors were reported by the cmdlets.
            // TODO (Left to the reader): Error handling code.
          }

          foreach (PSObject result in results)
          {
            Console.WriteLine("Identity\t: " + result.Members["Identity"].Value);
            Console.WriteLine("ApplicationId\t: " + result.Members["ApplicationId"].Value);
          }
          Console.WriteLine("Press any key to exit...");
          Console.ReadKey();
        }
      }
    }
  }
}
```

