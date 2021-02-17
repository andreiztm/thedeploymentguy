# List all updates in a "broken" state (aka not installed or superseded)

Sample output:  
> PS C:\WINDOWS\system32> C:\Tools\Get-BrokenUpdates.ps1
>
> Cumulative/rollup package(s) in broken state                 
> \--------------------------------------------                 
> Package_for_RollupFix\~31bf3856ad364e35\~amd64\~\~7601.24180.1.8 
> Package_for_RollupFix\~31bf3856ad364e35\~amd64\~\~7601.24208.1.11
> Package_for_RollupFix\~31bf3856ad364e35\~amd64\~\~7601.24261.1.6 

> Standalone package(s) in broken state                 
> \-------------------------------------                 
> Package_for_KB4339093\~31bf3856ad364e35\~amd64\~\~11.2.1.0
> Package_for_KB4462949\~31bf3856ad364e35\~amd64\~\~11.2.1.0
> Package_for_KB4531786\~31bf3856ad364e35\~amd64\~\~6.1.1.0 

The updates listed as broken should be removed using DISM to clear the "stuck" packages:  
> dism /Online /Remove-Package /PackagePath:Package_for_RollupFix\~31bf3856ad364e35\~amd64\~\~7601.24180.1.8  
> dism /Online /Remove-Package /PackagePath:Package_for_RollupFix\~31bf3856ad364e35\~amd64\~\~7601.24208.1.11  
> dism /Online /Remove-Package /PackagePath:Package_for_RollupFix\~31bf3856ad364e35\~amd64\~\~7601.24261.1.6              
> dism /Online /Remove-Package /PackagePath:Package_for_KB4339093\~31bf3856ad364e35\~amd64\~\~11.2.1.0  
> dism /Online /Remove-Package /PackagePath:Package_for_KB4462949\~31bf3856ad364e35\~amd64\~\~11.2.1.0  
> dism /Online /Remove-Package /PackagePath:Package_for_KB4531786\~31bf3856ad364e35\~amd64\~\~6.1.1.0  
